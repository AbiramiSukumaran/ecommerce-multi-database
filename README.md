# Polyglot Ecommerce Application

## Run the Application Yourself

To test this multi-modal application, you need to clone the repository and set up your environment variables to connect to the databases you provisioned in Steps 2, 3, and 5.

---

### 1. Go to you Cloud Shell Terminal, clone the repo and navigate into the project folder:

```bash
git clone https://github.com/AbiramiSukumaran/ecommerce-multi-database.git
```
```bash
cd ecommerce-multi-database
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Update the .env file you cloned from the repo with your values:
```bash
# --- DATABASE SECRETS ---
# 1. MongoDB Connection String (from MongoDB Atlas)
MONGODB_CONNECTION_STRING="mongodb+srv://<db_user>:<db_password>@YOUR_CLUSTER.mongodb.net"
```
```bash
# 2. Google Cloud Storage Bucket Name (from Step 5)
GCS_PRODUCT_BUCKET="your-ecommerce-product-media-bucket"
```
```bash
# 3. MCP Toolbox Server Location
# Must match the address where you run the toolbox server (usually localhost:5000)
MCP_TOOLBOX_SERVER_URL="http://localhost:5000"
```
### 4. Update the data layer
Update tools.yaml for placeholder with your values.
Test your tools.yaml tools locally:
```bash
./toolbox --tools-file "tools.yaml"
```
or
```bash
./TOOLBOX 
```
### 5. Test your app locally
(Assuming you have completed all the prior sections and configurations in the blog):
```bash
python app.py
```
### 6. Check your Docker file and app.py starting point
Make sure your Docker file is updated as required based on the original that you cloned from the repo.

### 7. Check if the app.py is updated
It should have the following snippet in case you had it changed for our local tests. (The file from the repo should already have this):
```bash
if __name__ == '__main__':
    port = int(os.environ.get('PORT', 8080))
    app.run(host='0.0.0.0', port=port, debug=False) 
    # NOTE: debug=False is crucial for production environments like Cloud Run
```
### 8. Deploy your app to Cloud Run
```bash
gcloud run deploy multi-db-app --source
```
Select the region number (say 34 for us-central1) and allow unauthenticated option (“y”), when prompted.

Check out the blog for initial configurations:

> **Architecting for Data Diversity – The Intelligent E-Commerce Catalog**  
> *by [Abirami Sukumaran](https://medium.com/@abidsukumaran)*  
>  
> [Click here to read on Medium →](https://medium.com/@abidsukumaran/architecting-for-data-diversity-the-intelligent-e-commerce-catalog-4ceadf4bf104)

