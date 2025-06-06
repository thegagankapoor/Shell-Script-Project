# 🛠️ GitHub Repository Access Tracker (Shell Script)  

## 📌 Project Overview  
This is my **second DevOps project** where I built a **shell script to track GitHub repository access** using the **GitHub API**. As a DevOps engineer manually checking repository access through GitHub UI is inefficient. This script automates the process.

---

## 🎯 Why This Project?  
✅ Check who has access to a GitHub repository.  
✅ Ensure only authorized users have access.  
✅ Avoid manually navigating through GitHub settings.  

Instead of logging into **GitHub UI** every time this **shell script automates** the process using the **GitHub API** 🚀  

---

## 🚀 Features  
- **Lists all users** who have **access** to a GitHub repository.  
- **Uses GitHub API** to fetch data programmatically.  
- **Eliminates manual UI checks**, saving time and effort.  
- **Simple and lightweight shell script**.  

---

## 📋 Prerequisites  

### 🔧 System Requirements  
- **Linux machine (EC2 or local)**  
- **GitHub API Token** (for authentication)  
- **GitHub CLI (`gh`)** installed  
- **`jq`** installed (for JSON parsing)  

### 🔗 Setup GitHub API Token  
To access the **GitHub API** you need a **Personal Access Token**. Follow these steps to generate one:  

1️⃣ **Go to GitHub Settings:**  
   - Click on your profile picture (top-right corner) → **Settings**.  
   - Scroll down to **Developer Settings** → Click **Personal Access Tokens**.  

2️⃣ **Select "Tokens (classic)"** (⚠️ **Do not use Fine-grained tokens**).  

3️⃣ **Generate a new token (classic):**  
   - Click **"Generate new token (classic)"**.  
   - Set an **expiration date** (optional but recommended).  
   - **Select the necessary permissions:**  
     As shown in the Image

![Screenshot_7](https://github.com/user-attachments/assets/5990a2fd-1256-4b68-839c-e58069e7b6f5)
![Screenshot_8](https://github.com/user-attachments/assets/596b3293-f16a-41ac-88f8-79e43ff835af)
![Screenshot_9](https://github.com/user-attachments/assets/73c22dca-052b-4fe2-ad91-c481c64a6cdc)



4️⃣ **Generate and Copy the Token:**  
   - Click **"Generate Token"**.  
   - Copy the **token immediately** (you won’t be able to see it again).  

---


## 📜 Installation & Setup  

### 1️⃣ Launch an EC2 Instance  
Tutorial how to launch EC2 Instance:
👉 [LinkedIn Post](https://www.linkedin.com/posts/thegagankapoor_virtual-machines-cloud-aws-apis-activity-7292493343488389120-u7Nu?utm_source=share&utm_medium=member_desktop&rcm=ACoAAFcwqqYBw0quEruUZMAfYQQX55vo42H15V0)
- SSH into your instance:  
  ```bash
  ssh -i "your-key.pem" ubuntu@your-instance-ip
  ```

### 2️⃣ Clone the GitHub Repository  
```bash
git clone https://github.com/thegagankapoor/Shell-Script-Project.git
cd Shell-Script-Project/GitHub-Repo-Access-Tracker
```

### 3️⃣ Install Dependencies  
IF you are using AWS EC2 instance then jq will be installed 
```bash
sudo apt update
jq --version #If it's installed then don't install jq
sudo apt install jq -y  # Install jq for JSON processing
```

### 4️⃣ Set Up API Authentication  
Before running the script, export your **GitHub username and API token**:  
```bash
export username="your-username"
export token="your-api-token"
```

---

## 🏃 Running the Script  
1️⃣ **Give Execute Permission**  
```bash
chmod 700 list-users.sh
```


2️⃣ **Run the script with org & repo name** 
To do this you have to make your own organization on GitHub then make repository and then give access to that organization with another GitHub account.
![Screenshot_988](https://github.com/user-attachments/assets/91f4402a-643f-4ef7-a71a-3c84caf7bf34)


```bash
./list-users.sh devops-by-gagan practice
```
3️⃣ **Check the output**  
- The script will display a list of users with **access** to the repository.  

---

## 🕒 Automating with Cron Job  
To check repo access **every day at 4:30 PM**, add this to your crontab:  
```bash
crontab -e
```
Add:  
```
30 16 * * * /path/to/list-users.sh your-org your-repo
```

---

## 📸 Script Output  
![Screenshot_13](https://github.com/user-attachments/assets/9151c2c8-30af-4152-93f7-e71b9c2dfb7e)




---

## 🛠️ Troubleshooting  
### ❌ Issues You Might Face  
1. **GitHub API Token Not Working?**  
   ➜ Ensure it has **repo read access** in GitHub Developer Settings.  
2. **jq not found?**  
   ➜ Install it using `sudo apt install jq`.  
3. **Permission denied?**  
   ➜ Ensure `chmod 700 list-users.sh` is executed before running the script.  


---

## 🎯 Final Thoughts

This is my **second DevOps project** and it has been a great learning experience! 🚀 

- **This project helped me understand API integration.** 
- At first, **GitHub API looked complex** but after testing and exploring it, I realized it's just about **sending requests and reading responses**.  
- **Shell scripting is powerful**
- I faced **small issues** like typo issuses.
---

💡 If you're a **beginner**, I highly recommend trying this project. It helps you **understand API integration, GitHub automation, and DevOps scripting**.

