# Issues Encountered / Lessons Learned

This section documents problems encountered while building the lab and how they were resolved.

---

## Editing the Nginx Web Page

When modifying the default Nginx web page, the file had to be edited with elevated privileges because it is located in a system directory.

File path:

/var/www/html/index.html

The file was opened using:

sudo nano /var/www/html/index.html

Screenshot reference:
screenshots/nginx-page-edit.png

The page was updated with the following content:

<h1>Suleiman Lab Server</h1>
<p>First VM deployed</p>

Important note:
When using Nano, the file must be saved using **CTRL+O** before exiting. Forgetting to save will result in no changes being applied.

---

## Remembering to Save Changes in Nano

One issue encountered during editing was remembering the correct save and exit sequence.

Nano uses keyboard shortcuts rather than menu options.

Correct process:

CTRL+O → save file  
Enter → confirm file name  
CTRL+X → exit editor

This was not immediately obvious when first editing files on Linux.

---

## Verifying Nginx Is Running

After installation, the service needed to be confirmed running.

Command used:

sudo systemctl status nginx

If the service is not active, it can be started manually:

sudo systemctl start nginx

This step is important because installing a package does not always guarantee the service is running.

---

## Finding the Correct VM IP Address

To access the server from the host machine, the correct IP address of the VM needed to be identified.

Command used:

ip a

The relevant line shows:

inet 192.168.x.x

This IP address is then used in a browser on the host machine.

Example:

http://192.168.x.x

---

## Testing Connectivity from the Host Machine

Once Nginx was installed and the webpage edited, the server needed to be accessed from outside the VM.

Opening the VM IP address in a browser confirmed the server was reachable.

Expected result:

The custom page containing "Suleiman Lab Server" should appear.

---

## General Observations

- Editing configuration files directly on Linux servers is common for service configuration.
- Verifying service status with `systemctl` is an important troubleshooting step.
- Knowing how to quickly identify a machine's IP address is necessary when working with servers in a virtual environment.

These basic tasks form the foundation of Linux system administration.
