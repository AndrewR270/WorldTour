# WorldTour

**Explore** and **learn** about the world through your own unique lens. **Journey** to anywhere on the map, or **discover** places associated with any topic you can dream of. *The story of our world, visualized.*

## Inspiration

Learning about world history and culture has always been one of our favorite pastimes - geography being the other. **With WorldTour, we leverage AI** to combine the two - **making history visible** on the map through relevant locations, **providing cultural enrichment** about any place in the world through dynamic prompts, and **raising awareness** about news and social issues across the world. WorldTour connects any interest a user may have to geography, history, and culture. In short, **WorldTour is the story of humanity on the map** - serving as anything from an astounding research tool to a fun way to pass the time.

## Functionality

WorldTour is a visual research tool that lets users learn about anything while seeing it on the map. 
- Clicking anywhere on the map brings the local scoop about that specific location, including history, food, and culture. This enables users to learn more about a very specific area easily, which may be much more difficult using Google. 
- It is also helpful during research, as WorldTour brings up relevant locations to “Explore” search prompts. Users can learn about their prompt’s connections to different places around the world and aid them in their discovery of the more intricate details of whatever they need to research. 
- Includes features like search history and “Surprise me!”
- Works as a functional, up-to-date map, geographical and political map. 

WorldTour can be described as a visual and interactive Wikipedia, but as opposed to static information, content is newly generated upon the user’s request. 

## How we built it

We used the following tools, frameworks, and GenAIs to build the project:
- Lovable Pro
- Gemini 3 Flash
- Github Copilot
- Microsoft Copilot
- OpenStreetMaps API
- Leaflet.js
- Vite
- React.js a
- Node Package Manager
- Render
- GitHub

Lovable was used to generate the boilerplate for our Vite app as well as the frontend functionality. Gemini is used by our web app to find locations which are relevant to our search queries, and generates informational snippets about those locations. Github and Microsoft Copilot were used for debugging.

OpenStreetMaps API with Leaflet.js provides a set of map tiles and translates them to english, respectively. Additionally, we use Vite and React.js as frameworks for the project, Node Package Manager for running it, Render for hosting it online, and GitHub for version control.

## Development Challenges

We struggled with the **OpenStreetMap API,** as panning and zooming among the map tiles is more difficult than we first imagined. We also had to wrestle with configuring our program to choose the nearest location when clicked on an invalid area or uninhabited land. Lastly, we had a lot of trial-and-error and tweaking of the UI to make it look like an old journal.

## Development Successes

We were very proud of our **prompt engineering** for Gemini to make responses consistent and reliable. We also find the maps API and UI stunning. Getting the program to auto pan and zoom and have hyperlinks make the entire project look more professional and polished. 

## What We Learned

This was our second hackathon, and the **first time using AI to generate code.** Apart from the impressive end result, we got a very strong **understanding** of what the **future of the programming** workforce would look like. We believe we are great at prompt engineering now, since we used it to generate parts of our code and give responses in the program itself. 

## Next Steps

We want to make it like a visual alternative to Wikipedia. We would like to create user profiles, where search results can be tailored to the individual as it learns about them. Further, we want to implement more features that can aid in research, such as search parameters like recency, response length/detail, and source control. We also have some work to do with the UI, including implementing images and audio. 
