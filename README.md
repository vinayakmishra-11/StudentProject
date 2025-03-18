# StudentProject  

## 📌 Project Overview  
StudentProject is a Django-based multi-app project designed for deployment using Docker and automated CI/CD with Jenkins.  

## 🚀 Getting Started  

### **1️⃣ Clone the Repository**  
Run the following command in your terminal:  
```bash
git clone https://github.com/vinayakmishra-11/StudentProject.git
cd StudentProject

2️⃣ Set Up a Virtual Environment (Optional but Recommended)
For Python dependency management, create a virtual environment:

bash
Copy
Edit
python -m venv venv  
source venv/bin/activate  # (Linux/macOS)  
venv\Scripts\activate     # (Windows)
3️⃣ Install Dependencies

pip install -r requirements.txt
4️⃣ Run the Django Server Locally

python manage.py runserver
The app should now be accessible at http://127.0.0.1:8000/.
🐳 Running with Docker
1️⃣ Build the Docker Image

docker build -t studentproject .
2️⃣ Run the Container

docker run -p 8000:8000 studentproject
The application will be available at http://localhost:8000/.

🔄 CI/CD with Jenkins
1️⃣ Ensure Jenkins is Running

net start jenkins  # For Windows  
sudo systemctl start jenkins  # For Linux
2️⃣ Push Code to GitHub to Trigger Jenkins Pipeline

git add .
git commit -m "Initial commit"
git push origin main
Make sure your Jenkinsfile is correctly set up in your repository.

📌 Docker Hub Image
You can pull the prebuilt Docker image using:


docker pull vinayakmishra11/studentproject
Find the Docker image here.

❗ Troubleshooting
If you face issues:

Check logs using docker logs <container_id>.
Verify that ports are correctly mapped.
Ensure Jenkinsfile and Dockerfile are correctly configured.
📜 License
This project is licensed under the MIT License.



---

This README covers **project overview, installation, running locally, Docker deployment, and Jenkins CI/CD**.  

Let me know if you need any modifications! 🚀
