# it7405_project_sf



Perfect, let’s lock this into a clean README using **your exact method** as Method 1.
You can copy–paste this into a file called **`README.md`** in your project.

---

````markdown
# Car Sales Website – Setup & Run Guide

This project is a Django web application using:

- Django (via a pre-configured Anaconda environment)
- MongoDB (via Djongo)
- HTML, CSS, JavaScript, Bootstrap

This guide explains how to run the project on a **new laptop/PC** using:

- The ZIP file of the GitHub repo
- An imported Anaconda environment (`Anaconda_Navigator_Env.yaml`)
- MongoDB installed on the machine

---

## Method 1 (Preferred) – Using the Imported Anaconda Environment

### 1. Prerequisites

Install these on the laptop:

1. **MongoDB Community Server**
   - Install from the MongoDB website.
   - Default connection: `mongodb://localhost:27017`
   - Make sure the MongoDB service is running.

2. **Anaconda / Miniconda**
   - We will import an existing environment `.yaml` file.

3. **VS Code** (recommended as the editor).

4. **Environment file**
   - `Anaconda_Navigator_Env.yaml`  
   - This file contains the full environment (Python + Django + Djongo, etc.).

---

### 2. Download and Extract the Project (ZIP)

1. Go to the GitHub repo in your browser.
2. Click **“Download ZIP”**.
3. Save it somewhere (for example, `Downloads`).
4. Extract the ZIP. After extraction, you should have a folder similar to:

```text
C:\Users\sayed\Downloads\it7405_project_sf-main
````

Inside that folder you should see:

* `manage.py`
* `requirements.txt`
* `full_data.json`
* `car_sales_site/`
* `cars/`
* (other project files)

---

### 3. Import the Anaconda Environment (`Anaconda_Navigator_Env.yaml`)

1. Open **Anaconda Navigator**.
2. Click on the **“Environments”** tab on the left.
3. At the bottom, click **“Import”**.
4. In the dialog:

   * **Specification file:** choose `Anaconda_Navigator_Env.yaml`
   * **Name:** for example `Anaconda_Navigator_Env` (or keep the default).
5. Click **Import** and wait until the environment finishes creating.

This environment already has:

* Python (correct version for this project)
* Django
* Djongo
* All required packages

You **do not** need to manually install packages with `pip` if this environment imports correctly.

---

### 4. Open VS Code Inside This Environment

There are two common ways:

#### Option A – From Anaconda Navigator

1. In **Environments**, select `Anaconda_Navigator_Env`.
2. Click the small **▶ (play)** button.
3. Choose **“Open with VS Code”** (or similar option if available).
4. In VS Code, go to **File → Open Folder…** and open:

   ```text
   C:\Users\sayed\Downloads\it7405_project_sf-main
   ```

#### Option B – From Terminal

1. In Anaconda Navigator, select `Anaconda_Navigator_Env`.
2. Click the **▶ (play)** button → choose **“Open Terminal”**.
3. In that terminal (which is already using this env), run:

   ```bash
   cd C:\Users\sayed\Downloads\it7405_project_sf-main
   code .
   ```

VS Code will open the project folder and use the environment.

---

### 5. Run Migrations (Create Database Structure)

In VS Code, open the **Terminal** (it should be using the `Anaconda_Navigator_Env` environment).
Make sure the current folder is the project root:

```bash
cd C:\Users\sayed\Downloads\it7405_project_sf-main
```

Now run:

```bash
python manage.py migrate
```

This will create the necessary collections/tables in MongoDB for the project.

---

### 6. Load Sample Data from `full_data.json`

The file `full_data.json` contains:

* Users
* Cars (Available Cars)
* Reviews
* Orders
* Appointments
* Offers
* Sessions

Sometimes loading `contenttypes` from the fixture causes a duplicate key error, so we **exclude** it.

In the same terminal, run:

```bash
python manage.py loaddata full_data.json --exclude contenttypes
```

If it works, you should see something like:

```text
Installed X object(s) from 1 fixture(s)
```

#### (Optional) Verify That Data Is Loaded

Check how many cars were loaded:

```bash
python manage.py shell -c "from cars.models import Car; print(Car.objects.count())"
```

You should see a number greater than `0`.

Check how many users were loaded:

```bash
python manage.py shell -c "from django.contrib.auth.models import User; print(User.objects.count())"
```

Again, you should see a number greater than `0`.

---

### 7. Run the Development Server

In the same terminal:

```bash
python manage.py runserver
```

You should see output similar to:

```text
Starting development server at http://127.0.0.1:8000/
```

Now open your browser and visit:

* Home page (landing page / hero section):
  `http://127.0.0.1:8000/`

* Car list page (Available Cars):
  `http://127.0.0.1:8000/cars/`

* Admin site (to see users, cars, reviews, etc.):
  `http://127.0.0.1:8000/admin/`

Log in with one of the users from the JSON fixture (e.g., the admin user if included).

If things are set up correctly, you should see:

* Cars listed on the website.
* Data (users, cars, reviews, orders, etc.) inside the Django admin.

---

### 8. Resetting the Data (Optional)

If the data becomes messy during testing and you want a clean reset:

1. **Drop the MongoDB database `car_sales_db`:**

   Using mongosh:

   ```bash
   mongosh
   ```

   Then in the shell:

   ```javascript
   use car_sales_db
   db.dropDatabase()
   exit
   ```

2. Run migrations again:

   ```bash
   cd C:\Users\sayed\Downloads\it7405_project_sf-main
   python manage.py migrate
   ```

3. Load the JSON again:

   ```bash
   python manage.py loaddata full_data.json --exclude contenttypes
   ```

Now you’re back to a fresh state.

---

### 9. Quick Command Summary (Method 1)

After importing `Anaconda_Navigator_Env.yaml` and opening the project folder:

```bash
# 1. Go to project folder
cd C:\Users\sayed\Downloads\it7405_project_sf-main

# 2. Run migrations
python manage.py migrate

# 3. Load initial data
python manage.py loaddata full_data.json --exclude contenttypes

# 4. Run the development server
python manage.py runserver
```

Then open:

```text
http://127.0.0.1:8000/
```

and the site should be fully working with data.

```

---

When you’re ready, tell me “add Method 2” and I’ll append a second method that explains how to set everything up **without** importing the YAML (creating the env manually with `conda create`, etc.).
::contentReference[oaicite:0]{index=0}
```
