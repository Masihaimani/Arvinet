# How to Migrate From Live to Local Server (Manually)
🔻 <sub>Please note that this guide assumes you have a basic understanding of WordPress and working with web servers. <sub />
## Step 1 : Exporting the WordPress Database from the Live Site
- Log in to the database management tool provided by your hosting provider (e.g., phpMyAdmin).
- Select the database associated with your WordPress site.
- Locate the "Export" option and choose the appropriate settings (e.g., export method, format).
- Click on "Go" or a similar button to initiate the export process.
## Step 2 : Downloading WordPress Files from the Live Site
- Connect to your live server using FTP or a file manager provided by your hosting provider.
- Navigate to the root directory of your WordPress installation.
- Download all the files and folders in the WordPress directory to your local machine.
## Step 3 : Importing the Database and WordPress Files to the Local Server
- If you're using XAMPP, create a new folder inside "C:/XAMPP/htdocs" for your local site.
- Copy all the WordPress files and folders from the downloaded package into the newly created folder.
- Open the database management tool (e.g., phpMyAdmin) on your local server.
- Create a new database for your local WordPress installation.
- Import the previously exported database file into the newly created database.
## Step 4 : Updating the URLs inside the WordPress Database
- In the SQL screen of phpMyAdmin, execute the following SQL query (replace "example.com" with your live site's URL and "http://localhost/mylocalsite" with the local server URL of your site):
```
UPDATE wp_options SET option_value = replace(option_value, 'http://www.example.com', 'http://localhost/mylocalsite') WHERE option_name = 'home' OR option_name = 'siteurl';
UPDATE wp_posts SET post_content = replace(post_content, 'http://www.example.com', 'http://localhost/mylocalsite');
UPDATE wp_postmeta SET meta_value = replace(meta_value, 'http://www.example.com', 'http://localhost/mylocalsite');
```
## Step 5 : Updating the wp-config.php File
- Locate the folder where you installed WordPress on your local server.
- Find the "wp-config.php" file and open it in a text editor.
- Replace the database name in the file with the one you created in phpMyAdmin.
- Set the database username to "root" and leave the database password empty.
- Save the changes made to the wp-config.php file.
## Step 6 : Accessing Your Local WordPress Site
- Open a web browser and enter the following URL in the address bar:
```
http://localhost/mylocalsite/
```
- Replace "mylocalsite" with the name of the folder you created in step 3.
- Press Enter to load your local WordPress site in the browser.
- 
