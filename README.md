# Text-Classification-using-BERT-Classifier

# DeepQA-Miner

## Purpose
The data provided in this repository is used by a method named DeepQA-Miner. This deep learning-based method uses the data to classify the software project managers' questions from four different viewpoints. These questions are great candidates to represent practitioners' daily technical concerns and challenges.

## Data source
To access the project managers' concerns [Project Management StackExchange](https://pm.stackexchange.com) is targeted. This Question-Answer community is a platform specified for project management that lets the experts ask their questions and answer the existing questions.  

## Data description
5335 questions are scraped from the Project Management StackExchange Question-Answer community. The questioner equips his question with a short title and tags to describe it. The other members of the community can vote up or vote down the question and also answer it. The question is accessible to be viewed by anyone, registered or not registered in the community. Therefore, the set of attributes we scrape for each question includes the body of the question, its title, assigned tags, the number of votes/answers/views, the user id of the questioner, the date when the question is asked, and the status of the question. The staus can be unanswered (when there is no answer), answered (when there is at least an answer but not marked as accepted by the questioner), or answered-accepted (when one of the answers is marked as the accepted one by the questioner). 

## Data Labels
Each question is labeled (and then classified) through the following four viewpoints:

- PMBOK Area: The Project Management Body of Knowledge (PMBOK) is a set of standard terminology and guidelines for project management. This set is getting evolved over time, and till now, the sixth edition is released. According to the PMBOK, all the processes and concepts in project management lie under ten main areas. In this classification task, each question is assigned to one or more of the PMBOK areas. Therefore the classes are:

  - Project Integration Management
  - Project Scope Management
  - Project Schedule Management
  - Project Cost Management
  - Project Quality Management
  - Project Resource Management
  - Project Communication Management
  - Project Risk Management
  - Project Procurement Management
  - Project Stakeholder Management
  - Not Applicable

As each question may have relevance to more than one area, this task is a multi-class multi-label classification.

- PMBOK Process Group: The PMBOK also provides another categorization for project management processes called Process Groups. A process group's activities mostly operate around the same time on a project or with similar input and outputs. Due to the definitions of the process group, each question can belong to only one group. This makes the classifier perform a multi-class single-label classification task. Classes in this task are:

  - Initiating
  - Planning
  - Executing
  - Monitoring and Controlling
  - Closing
  - Not Applicable


- Managerial-level vs Technical-level: Binary classification is performed to determine if an asked question is at the managerial or the technical level. This perspective mainly considers the level and type of information requested by the questioner. If it has been asked around project management concepts, concerns, or situation handling, a question is at the managerial level. On the other side, there are questions regarding technical challenges of this career that are not connected to any of the main PM concepts, such as finding/editing a feature in a PM tool like Microsoft Project, best resources to get ready for the PMP certification exam, etc.

- Situational-describing vs Knowledge-seeking: Here, through another binary classification task, we dive deeper into the questions classified as the Managerial-level ones in the last perspective. This perspective target the way of asking the question chosen by the questioner regarding the question's context. The questions are separated into two groups. First, the questions that the user describes a situation (scenario) to ask for advice in dealing with it (decision-making). This class is named Situational-describing. The second class, named Knowledge-seeking, refers to the questions where the questioner asks to know about a technique, method, definition, or concept related to the project management. Note that there is a chance that the questioner in the second class is dealing with a decision-making scenario as well, but he has been able to formulate his need for a knowledge-seeking question.

## Description of files
As a contribution to OpenScience, the data used in this study is provided publicly in this repository. The data is organized in three folders, representing it through different phases of analysis. 

### Folder: Scraped_Data
This folder includes one CSV file containing the raw data scaped from the website. For each question, the content and its attributes from the community are provided.

### Folder: Cleaned_Data
The title and body of the questions are separated in this folder. These two CSV filed include the cleaned text. The cleaning mechanism includes the following processes with the same ordering: Removing Links, Removing Users' Mentions, Removing HTML Snippets, Removing Numbers, Removing Punctuation, Removing Stop Words, Removing White Spaces, Replacing Accented Characters, Expanding Contractions, Removing Custom Stop Words, Text Lowering, Lemmatization, Removing Words Less Than 3 Characters.

### Folder: Labelled_Data
Eventually, a thousand randomly-selected samples are labeled. The 'questions-1000.csv' file includes the labeling values that corresponded with the question index (obviously, the index matches the index value in files from other folders). The 'Legend.csv' file has clarified the coding used for labeling across all four classification viewpoints.


