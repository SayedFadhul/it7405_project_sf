# it7405_project_sf

# Car Sales Website

Django-based car sales web application using:

- Python
- Django
- MongoDB (via Djongo)
- HTML, CSS, JavaScript, Bootstrap

This README explains how to run the project using a **pre-configured Anaconda environment** (`Anaconda_Navigator_Env.yaml`) and load the demo data (`full_data.json`).

---

## Requirements

Install these on your machine:

- **MongoDB Community Server** (running on `mongodb://localhost:27017`)
- **Anaconda Navigator**
- **VS Code**

---

## Setup (Preferred Method – Import Anaconda Environment)

### 1. Get the Project

- Download the repo as a ZIP from GitHub and extract it, **or**
- Clone it:

```bash
git clone <REPO_URL>
cd <PROJECT_FOLDER>
````

The project folder should contain:

* `manage.py`
* `requirements.txt`
* `full_data.json`
* `car_sales_site/`
* `cars/`

(Example: `C:\Users\sayed\Downloads\it7405_project_sf-main`)

---

### 2. Import the Conda Environment

1. Open **Anaconda Navigator**.
2. Go to **Environments → Import**.
3. Select `Anaconda_Navigator_Env.yaml` from the project folder.
4. Give it a name (for example `Anaconda_Navigator_Env`) and click **Import**.

This environment already includes Python, Django, Djongo, and other required packages.

---

### 3. Open the Project in VS Code

1. Open **VS Code**.
2. Go to **File → Open Folder…** and select your project folder
   (e.g. `C:\Users\sayed\Downloads\it7405_project_sf-main`).
3. Open the integrated terminal:
   **View → Terminal** (or <kbd>Ctrl</kbd> + <kbd>`</kbd>).
4. Make sure the terminal path is the project root (folder with `manage.py`).
   If not, move there:

   ```bash
   cd <PROJECT_FOLDER>   # e.g. cd C:\Users\sayed\Downloads\it7405_project_sf-main
   ```

(If you need to choose the correct Python/Conda environment in VS Code, do it via the VS Code Python interpreter selector.)


---

### 4. (Optional but Recommended) Drop Existing MongoDB Database

If you have run this project before on the same machine, the database
`car_sales_db` might already exist and cause duplicate key errors.
You can drop it first:

```bash
mongosh
```

In the `mongosh` shell:

```javascript
use car_sales_db
```
```javascript
db.dropDatabase()
```
```javascript
exit
```

Now you start with a clean database.

---

### 4. Apply Migrations

Create the database structure in MongoDB:

```bash
python manage.py migrate
```

---

### 5. Load Demo Data

Load initial data (users, cars, reviews, orders, etc.) from `full_data.json`:

```bash
python manage.py loaddata full_data.json --exclude contenttypes
```

You should see:

```text
Installed X object(s) from 1 fixture(s)
```

---

### 6. Run the Development Server

```bash
python manage.py runserver
```

Open in your browser:

* Home: `http://127.0.0.1:8000/`
* Cars list: `http://127.0.0.1:8000/cars/`
* Admin: `http://127.0.0.1:8000/admin/`

If the JSON fixture loaded correctly, you’ll see **Available Cars** and other sample data.

---

## Admin Login

To access the Django admin panel:

```
Username: admin
Password: admin
```

### Notes:

* If you're already logged in as another user, **log out first**.
* Then open:
  **[http://127.0.0.1:8000/admin/](http://127.0.0.1:8000/admin/)**
* If the page does not refresh properly, perform a **hard refresh**:

```
Ctrl + Shift + R
```

### What You Can Do in Admin:

* Add new **Cars**
* Edit or delete existing cars
* Add **Reviews**, **Orders**, **Offers**, **Appointments**
* Manage **Users**
* Any car you add in the admin panel will automatically appear on the website under **Available Cars**.

---




