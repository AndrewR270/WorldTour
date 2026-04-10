

## 1. `agent_responses` Table — Where It's Used

The table is referenced in **4 places**:

| Location | Usage |
|---|---|
| `supabase/functions/fetchai-agent/index.ts` | Inserts pending rows, polls for completed responses |
| `supabase/functions/rooted-webhook/index.ts` | Updates rows when the Fetch.ai agent responds |
| `supabase/migrations/20260404224722_...sql` | Creates the table, RLS policies, and indexes |
| `src/integrations/supabase/types.ts` | Auto-generated type definitions (updates automatically) |

**You are correct** — the `agent_responses` table exists solely to support `fetchai-agent` and `rooted-webhook`, neither of which is called by the frontend. It can be safely removed.

### Plan to Remove

1. Create a new migration: `DROP TABLE IF EXISTS public.agent_responses;`
2. Delete `supabase/functions/fetchai-agent/` folder
3. Delete `supabase/functions/rooted-webhook/` folder
4. The `types.ts` file will auto-regenerate without the table

---

## 2. Could a Different LLM Be Used?

**Yes.** The app uses a standard OpenAI-compatible chat completions API. Any model available through the Lovable AI Gateway works as a drop-in replacement. You'd only change the `model` string.

### Where the Model Is Specified

| File | Current Model | What It Powers |
|---|---|---|
| `supabase/functions/explore-locations/index.ts` | `google/gemini-2.5-flash` | Converting search queries → map pins |
| `supabase/functions/location-culture/index.ts` | `google/gemini-3-flash-preview` | Location culture/history descriptions |
| `supabase/functions/topic-rundown/index.ts` | `google/gemini-2.5-flash` | Topic summary panel |

To switch models, change the `model` value in each file's `fetch()` body. Available alternatives include `openai/gpt-5`, `openai/gpt-5-mini`, `google/gemini-2.5-pro`, etc.

### Where the Key Is

The `LOVABLE_API_KEY` is auto-provisioned by Lovable Cloud and stored as a backend secret. It's read via `Deno.env.get("LOVABLE_API_KEY")` inside each edge function. You never need to manage this key manually.

### Where the AI Prompts Are Written

All prompts live inside the edge functions (backend-only):

- **`explore-locations/index.ts`** — a short prompt asking the AI to return a JSON array of locations
- **`location-culture/index.ts`** — a detailed system prompt requesting sections: Historical Significance, Food, Culture, Hidden Stories, Current News, Issues
- **`topic-rundown/index.ts`** — a system prompt requesting sections: Overview, Key Figures, Notable Achievements, Cultural Impact, Current Status, Fun Facts, Sources

---

## 3. What Is Supabase and Why It's Used

**Supabase** is an open-source backend-as-a-service platform that provides a PostgreSQL database, authentication, file storage, and **Edge Functions** (serverless functions that run close to users). In this project it's branded as **Lovable Cloud**.

**Why it's used in WorldTour:**

- **Edge Functions** — The three AI functions (`explore-locations`, `location-culture`, `topic-rundown`) run as serverless functions. This keeps AI API keys secret (never exposed to the browser) and lets prompts live server-side.
- **No custom server needed** — Supabase/Lovable Cloud provides the backend infrastructure automatically, so the app is purely a React frontend + serverless functions with zero server management.
- **Database** — Used for the `agent_responses` table (which we're removing). Currently no other tables are needed.

In short: Supabase is the reason the app can call AI models securely without running a backend server.

