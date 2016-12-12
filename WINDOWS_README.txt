Running the project on your local machine is easiest by installing Docker. Docker is a software container that runs the project on a linux-based virtual machine. This simplifies installation of the project, allowing it to run independent from the physical machine being used. 

1) **Install Docker**

A. Can be downloaded from: https://www.docker.com/

B. Depending on your Version of Windows you might need to install Docker Toolbox. Found here: https://github.com/docker/toolbox/releases/tag/v1.12.3
*comes with Docker Quickstart, Kitematic, Oracle VM VirtualBox

2) **Ensure Virtualization** (Enable Intel Virtualization Technology (also known as Intel VT) or AMD-V depending on the brand of the processor.)

-Otherwise, Docker will not be able to create a Virtual Machine for the project to run from.
A. Reboot computer and enter BIOS to change it. The exact button to enter the menu varies from manufacturer to manufacturer. 
B. Once in the BIOS, open the Processor submenu 
C. Open the Processor submenu The processor settings menu may be hidden in the Chipset, Advanced CPU Configuration or Northbridge.
D. Enable Intel Virtualization Technology (also known as Intel VT) or AMD-V depending on the brand of the processor. The virtualization extensions may be labeled Virtualization Extensions, Vanderpool or various other names depending on the OEM and system BIOS.
E. Save and Exit


3) **Download project**

A. A copy can be found/forked from:
 https://github.com/bebingando/cs673f16-team1/tree/develop

B. Unzip contents into your preferred directory

4.1) **Run Docker and Creat Image** [Version 1.12.1]

If running the latest version follow these instructions, if not, skip to 4.2

A. Click Docker icon
B. Powershell window will be opened, navigate to the directory you placed to project in. 
C. Open the subfolder 'docker'
D. Copy resources into folder using command: 
   > cp -r ../group1/ resources/group1
E. Build the image and container using the command:
   > docker build -t cs673/team_alpha_project:latest ./ 
F. Run the server:
   > docker-compose up
G. Open browser and navigate to 127.0.0.1:8000

4.2.)**Run Docker and Creat Image** (Older Docker version)

A. Click Docker icon
B. Powershell window will be opened, navigate to the directory you placed to project in. 
C. Open the subfolder 'docker'
D. Create project image and container with the command:
  > ./build_image
E. Run Kitematic to display running container. On Web preview box, click arrow above preview. Note IP address for running project.

5.)**Login Credentials, API interfaces

1. Superuser: test, Password: testpw
2. Navigate to Issue Tracker
3. You can access Admin page through Admin option on page. 
4. Through Powershell, pip install httpie. You can interact with API    endpoints/make REST calls i.e. GET, POST, PATCH.
   Cheatsheet: http://ricostacruz.com/cheatsheets/httpie.html

A. You must get a token to interact with API:
-http POST localhost:8000/api-token-auth/ username='test' password='testpw'
-you will get a token in the form: token:----------------------------------
-use token with REST calls. i.e.:
http GET localhost:8000/issue_tracker/api/users/ 'Authorization: Token 686025567253f9265af2a28e1c022932836e0813'

B. Chat client is under Communications tab to the left
   Command Calls:

-Create a new comment for an issue:

`/issue-comment issue=123 comment='comment'`

-Modify existing issue fields:

`/set-issue-status issue=123 status='valid status'`

`/set-issue-priority issue=123 priority='valid priority'`

`/set-issue-type issue=123 type='valid type'`

-Creat a new issue:
`/new-issue title='My sweet title'`

or

`/new-issue name='My sweet title'`
