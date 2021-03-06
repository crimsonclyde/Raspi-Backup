Raspi-Backup
============

Simple Raspberry pi backup script.

Temporarily shuts down all running services and disables swap to prevent writes.

Backs up image of the SD card to an external HDD/thumb drive

**To configure:**

Copy this repository:

    git clone https://github.com/diffra/Raspi-Backup.git

Then add an entry to your root crontab:

    sudo crontab -e

That looks like this:

    MAILTO=you@domain.com
    # m h  dom mon dow   command
    00 03 * * 1 /path/to/backup.sh

Then set the backup location at the top of the script, and it will run early monday morning, emailing you a report. You want to run it late at night as any services (webserver, ssh, etc.) will be down while it takes the snapshot.  The services are then restarted, then it gzips the SD card image to use less space.

*Make sure to update the list of services to be stopped to include anything you're running that may write to the SD card.*

While you're here, check out my other Pi related repositories:

https://github.com/diffra/pitweetbot

https://github.com/diffra/RaspberryHome