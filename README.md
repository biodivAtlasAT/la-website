## Quick start guide for the Living Atlases website



### Intro
The website use Jekyll. 

### How to add an event to the website

1. Create a new file in the __events_ folder with the extension (.md for markdown). The name does not matter. There is **no html or css code** inside this file. It is quite easy to maintain for non tech people.  
2. Participant list (see example below):
    - Create a new CSV file in the __data/events_ folder using the name of the event. 
    - The mendatory fields of the header are: name, organisation and country (using this ortographe). You can add other fields if you want. 
    - Add the list of the participants (you can add as many as participant you need)
    
      ```
      name,organisation,country
      Héctor Armando Hernández Samayoa, CONAP Consejo Nacional de Areas Protegida, Guatemala
      Reuben Roberts, National Biodiversity Network, United Kingdom
      Kourouma Koura, GBIF Benin, Benin
      ```
    
3. This file will be divided in two parts : the front matter, and the body. 
    - Inside the front matter, you will find all the variables needed for the document, but also for the _events.markdown_ page. Each field follow this format: **field_name: field_description**. The following fields are mandatory, but you can add other fields if needed after "status". 
   
            --- 
            - layout: single-page
            - title: <name of the event>
            - date: <starting_date>
            - date_shown: <date shown on the events page with the format YYYY-MM-DD to YYYY-MM_DD>
            - type: <choose between: workshop, conference, online conference, or any new type of events>
            - status: <choose between: finish, in progress, soon>
            ---
     
            
    - The body with the following schema. You are free to add any other part or modify the existing ones. This is just an example. Be aware, if you change the number of # inside the file, you might have some CSS errors. 

      ```
      ## {{ page.title }}
      
      #### Description 
      
      Description of the event. These are some example of useful information that you can add to the page:
        - goal of the event;
        - place of the event;
        - link to the project (if exist)
        
      #### Participants 
  
      | Name | Organization | Country |
      |------|--------------|---------|
      {% for participant in site.data.events.participant_list -%}
      | {{ participant.name }}  | {{ participant.organisation }}  | {{ participant.country }}
      {% endfor %}
      
      >> We recommand to copy and paste the above table to avoid any mistake. Replace participant_list with the name of your CSV file (participant list created before). 

      #### Resources 

      ##### Presentations & Exercises
          List of presentations and/or exercises made during the event:
          - Day 1: [Name of the presentation](URL to the presentation) (PPT, Google Folder, or website) done by ...
          - Day 2: [Name of the presentation](URL to the presentation) (PPT, Google Folder, or website) done by ...
          - Exercises: [Name of the document](URL to the document) created by ....
         
      ##### Resources 
          - [Agenda](URL to the agenda)
          - [Official Website of the event](URL to the website)
          - usefull links 

      ##### Photos
      ```
4. The event will be automatically added to the events page (sorted by date). 


            



### Licence
Apache-2.0 © [Living Atlases](https://living-atlases.gbif.org)