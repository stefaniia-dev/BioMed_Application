# BioMed_Application
My application is biomedical data exploration platform that integrates disease, genetic, epidemiological, and scientific literature data from multiple external sources. The application allows users to search for diseases, explore related biomedical information, visualize available statistics, and save personal research notes.

<b> BiodMed Explorer</b>

<b> Explanation of application </b> 
<br>
My application is biomedical data exploration platform that integrates disease, genetic, epidemiological, and scientific literature data from multiple external sources. The application allows users to search for diseases, explore related biomedical information, visualize available statistics, and save personal research notes.
<br>
I wanted to make an application that will allow explore disease descriptions, associated genes, scientific publications, and public health statistics through a single application instead of manually searching separate websites.
<br>
The original proposal included both disease and drug exploration, along with possible statistical forecasting. However, during development, I decided to focus on creating a more complete disease research workflow rather than expanding into additional areas. I also realized that drug exploration feature would not go well with my application and will shift the main purpose of it.
<br>
Statistical forecasting was another feature I considered implementing. For it my main challenge was that there would the limited availability of consistent historical data from the WHO API. Not all diseases have corresponding statistical indicators, and some indicators have gaps in their time series or only provide data for a single year. This limits a lot time-series analysis and makes forecasting less meaningful and reliable and I decided not to do it.

<b> Technologies used </b> 
<br>
- Django - Backend framework, URL, templates, and database models,
- HTMX - Dynamic updates without reloading the entire page,
- Plotly - Interactive statistical visualizations,
- SQLite - Storage for research notes,
- HTML and CSS - User interface and responsive design.

External Data Sources <br>
- Monarch Initiative - Disease information, their ids and descriptions,
- Open Targets Platform - Disease-associated genes,
- NCBI E-utilities (PubMed) - Scientific publications,
- World Health Organization (WHO GHO OData API) - Public health statistics.

<b> Running application </b> 
<br>
Biomed explorer can be found online: https://itec4012-skilled-krill.projects.carleton.university/

But for running locally it is needed to
1) Clone the repository and open the project directory.
2) Create and activate a Python virtual environment (using python -m venv .venv)
3) Install required dependencies (pip install -r requirements.txt)
4) Run migrations (python manage.py migrate)
5) Open server (python manage.py runserver)
   
No external API keys are required. An internet connection is necessary to retrieve data from the external APIs.

<b> Application Overview </b>

Home page:

<img width="700" alt="image" src="https://github.com/user-attachments/assets/d94bc0b5-4a0a-4bb8-8145-447a73439f37" />

In my application I used HTMX to retrieve and display matching disease suggestions dynamically while a user types.

Search: <br>
<img width="700" alt="image" src="https://github.com/user-attachments/assets/3f538264-4ca7-4e4b-a1d0-6c42cbdc05df" />

The retrieve information contain name of the disease, its ID, its description. Then below I show a table of associated genes containing gene names, Ensembl IDs, and association scores. And after there are relevant scientific publications from PubMed. For publications users can we choose how many they want to be displayed (5, 10, 20,35 50). Each publication has an additional information, which the users can enable or disable. HTMX allows the publication results to update without reloading the entire disease detail page.

<img width="700"  alt="image" src="https://github.com/user-attachments/assets/7f6ea5b7-d3ba-436a-8317-cbf10829c320" />
<img width="700"  alt="image" src="https://github.com/user-attachments/assets/7ac00a23-30b8-4484-816c-e4c694cf182d" />
<img width="700"  alt="image" src="https://github.com/user-attachments/assets/9cc22cf6-c61d-4cf0-b5cf-bd9ed03bf69d" />
<img width="700"  alt="image" src="https://github.com/user-attachments/assets/af5e5b5b-6d4c-4b1e-aa8f-d78f5cb71732" />

For not overwhelming users with too much information and avoid too much scrolling, I created pagination for my publications - they are divided into pages containing up to four publication cards.
<br>
<img width="700"  alt="image" src="https://github.com/user-attachments/assets/bc7cb8d2-ae55-4ce6-9c49-8d99c51d01a3" />

For displaying information in graphs I integrated Plotly library (https://plotly.com/python/basic-charts/) for making graphs look perfect and I also used HTMX to update the display results when a selection changes.

<br>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/7304fe1a-7cad-4739-ac3b-e26e995f49bb" />

Users can also change WHO indicator (what they want to see) and a country where it this statistics was conducted. It might take a second to get updated. Here I need tonot ehtat WHO indicators are suggested using keyword matching and these suggestions may not always represent statistics directly associated with the selected disease.

<img width="700" alt="image" src="https://github.com/user-attachments/assets/09214dca-78fb-4038-8e54-733fba8409cd" />
<img width="700" alt="image" src="https://github.com/user-attachments/assets/9c3c66af-eb23-4289-a967-c3c9812373cf" />

Some indicators contain only one available observation, while others can provide data across multiple years. Same happens with gens or description, so there is always a visble feedback for users.

<br>
   <img width="500" alt="image" src="https://github.com/user-attachments/assets/694160cc-e5a2-46ec-bf6f-c44186109f31" />
   <img width="500" alt="image" src="https://github.com/user-attachments/assets/f76b8c10-a356-4bd6-a3a2-9c5545461eb7" />
   <img width="500" alt="image" src="https://github.com/user-attachments/assets/d509b5de-2a09-43a3-9dd9-19fcc09ccb99" />

Another cool thing is that Plotly allows users to zoom into charts, select regions, inspect values, and download charts as PNG images.

<br>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/0cd9a88e-396c-4974-a3f3-71e40f50bd7c" />

That's how downloaded graph looks like:
<br>
<img width="600" alt="prevalence-of-diabetes-age-standardized" src="https://github.com/user-attachments/assets/e6ab4307-5d25-4acc-9b40-a89a7b062e2a" />

And last but not the least in my application users can leave notes:
<br>
<img width="700" alt="image" src="https://github.com/user-attachments/assets/17c09462-53e2-4c28-808f-1651be8fabd6" />
<img width="700" alt="image" src="https://github.com/user-attachments/assets/85897fbd-77f3-47cc-a35a-6dbf4c9d546c" />

Users can simply click on the title of the note or button "view details" and it will redirect to back to the page (to a s pecfic disease that was searched).

The functionalities of notes are the following:
- Create notes associated with specific diseases,
- View previously saved notes,
- Edit existing notes,
- Delete notes,
- Return to the corresponding disease detail page.

My website on the mobile version:
<br>
<p align="center">
   <img width="200"  alt="image" src="https://github.com/user-attachments/assets/ed14ddeb-6799-4e74-b453-c5fc375cb996" />
   <img width="200"  alt="image" src="https://github.com/user-attachments/assets/de421bc4-dc22-42ba-a8c5-b3c113d9c6c5" />
   <img width="200"  alt="image" src="https://github.com/user-attachments/assets/2dc78b0d-3171-45a8-bbb1-607c23de012e" />
   <img width="200"  alt="image" src="https://github.com/user-attachments/assets/3f5b1e29-8ee6-4a48-adf6-77056cafba9c" />
   <img width="200"  alt="image" src="https://github.com/user-attachments/assets/8962ced0-b9be-4fb1-bb1d-58438ac2d14a" />
</p>
