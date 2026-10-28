# BioMed_Application
My application is biomedical data exploration platform that integrates disease, genetic, epidemiological, and scientific literature data from multiple external sources. The application allows users to search for diseases, explore related biomedical information, visualize available statistics, and save personal research notes.

<b> BiodMed Explorer</b>

<b> Explanation of application </b> 
<br>
I wanted to make an application that will allow explore disease descriptions, associated genes, scientific publications, and public health statistics through a single application instead of manually searching separate websites.
<br>

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
Biomed explorer can be found online: [https://itec4012-skilled-krill.projects.carleton.university/](https://itec4012-skilled-krill.projects.carleton.university/?sandbox_share=eyJ0Ijoic2hhcmVsaW5rIiwiaCI6Iml0ZWM0MDEyLXNraWxsZWQta3JpbGwucHJvamVjdHMuY2FybGV0b24udW5pdmVyc2l0eSIsInMiOjMsImUiOjE3OTU4MDIzODV9.OOw7y6uhbhaFGndhaqysTBXZIXeEPJk6jhd01DrXTfE)

<b> Application Overview </b>

Home page:

<img width="700" alt="image" src="https://github.com/user-attachments/assets/a52884ad-26bf-4161-9b98-6e478e913f34" />


In my application I used HTMX to retrieve and display matching disease suggestions dynamically while a user types.

Search: <br>
<img width="700" alt="image" src="https://github.com/user-attachments/assets/8e28324f-a742-43c7-a235-bc672e36b198" />

The retrieve information contain name of the disease, its ID, its description. Then below I show a table of associated genes containing gene names, Ensembl IDs, and association scores. And after there are relevant scientific publications from PubMed. For publications users can we choose how many they want to be displayed (5, 10, 20,35 50). Each publication has an additional information, which the users can enable or disable. HTMX allows the publication results to update without reloading the entire disease detail page.

<img width="700" alt="image" src="https://github.com/user-attachments/assets/92e5f43e-95c8-4020-b4ae-e6d5c4ee12a6" />
<img width="700" alt="image" src="https://github.com/user-attachments/assets/9efec7b9-3b1e-498e-a725-4bb6a5ef9194" />
<img width="700" alt="image" src="https://github.com/user-attachments/assets/dd00d3f3-b78f-4683-a5ff-b7c8aa19742e" />
<img width="700" alt="image" src="https://github.com/user-attachments/assets/a23f9026-78c2-463e-92de-9e6d1c53a1ea" />

For not overwhelming users with too much information and avoid too much scrolling, I created pagination for my publications - they are divided into pages containing up to four publication cards.
<br>
<img width="700" alt="image" src="https://github.com/user-attachments/assets/ebaee802-3456-4c1b-accb-f531cbe3b353" />

For displaying information in graphs I integrated Plotly library (https://plotly.com/python/basic-charts/) for making graphs look perfect and I also used HTMX to update the display results when a selection changes.

<br>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/9941e77d-d345-4175-95e3-fa86b02c5681" />

Users can also change WHO indicator (what they want to see) and a country where it this statistics was conducted. It might take a second to get updated. Here I need tonot ehtat WHO indicators are suggested using keyword matching and these suggestions may not always represent statistics directly associated with the selected disease.

<img width="700" alt="image" src="https://github.com/user-attachments/assets/21806cb0-a445-4e49-8812-0c3a38ccf390" />
<img width="700" alt="image" src="https://github.com/user-attachments/assets/ab8ca6fe-67a9-46ab-b447-28bd6e8c3343" />

Some indicators contain only one available observation, while others can provide data across multiple years. Same happens with gens or description, so there is always a visble feedback for users.

<br>
   <img width="500" alt="image" src="https://github.com/user-attachments/assets/21c344e9-301b-4eff-ad88-fa1f91ca3c06" />
   <img width="500" alt="image" src="https://github.com/user-attachments/assets/3d93ffc1-7f36-4caf-a8e4-d4be620a08b0" />
   <img width="500" alt="image" src="https://github.com/user-attachments/assets/edfed9e8-5b76-4414-b484-6b6fd32d463f" />

Another cool thing is that Plotly allows users to zoom into charts, select regions, inspect values, and download charts as PNG images.

<br>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/00b2e0c9-76b2-4a01-bd70-47cb8b4f3af3" />

That's how downloaded graph looks like:
<br>
<img width="600" alt="image" src="https://github.com/user-attachments/assets/5f1b6ccd-d36e-475f-9a9e-3291dceb4e5a" />

And last but not the least in my application users can leave notes:
<br>

<img width="700" alt="image" src="https://github.com/user-attachments/assets/80a44f64-0441-4f96-8a1b-093f6a1d727c" />
<img width="700" alt="image" src="https://github.com/user-attachments/assets/c8c8e72c-3482-48b6-bc17-709529526b71" />

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
   <img width="800" alt="image" src="https://github.com/user-attachments/assets/029e6969-9399-4a8b-b7aa-f2a38c3d0334" />
   <img width="200" alt="image" src="https://github.com/user-attachments/assets/416d11af-32ca-4e91-ba74-02693ca6d3c5" />

</p>
