
# Ansible LEMP and SSL Roles & Playbooks

We can use this repo to setup a LEMP stack on a fresh server. Setup Craft CMS or Laravel website and install Free SSL certificate (Letsencrypt).

### Things to note

Before going any further. Make sure you have ansible installed on your machine.It is really simple. If you are using a Mac, simply run the follwowing commands in terminal:

```
sudo easy_install pip
sudo pip install ansible
```

You can also read Ansible's installation docs [here](http://docs.ansible.com/ansible/intro_installation.html)

### Server Setup

To setup the server, First create a Ubuntu (At the time of writing the latest LTS is 16.04) server on Digital Ocean or Linode. Make a note if the IP address. Make sure you can SSH or have a root password for the server.

1. Clone this repo, open up the `hosts` file and add you server's IP address.
2. Run this command to make server ready for Ansible `ansible-playbook -i hosts pre.yml`
3. Once above command has successfully ran, You can now setup LEMP stack by running this command `ansible-playbook -i hosts lemp.yml`. This will take few minutes.
4. You can now type in your server's IP address in the browser and should see a success page. Your server is now provisioned and ready to host website.

### Setup a website on the server

Once your server is up and running, you can now setup the website on it using `site.yml` playbook.

1. Open up `site.yml` file and update the domain name and the user name to the user you have created when setting up the server.
2. Run this command to setup the website `ansible-playbook -Ki hosts site.yml`. It will ask for the user's password. Type in the password and hit enter.
3. Once above command has successfully ran. It will create a website folder in `/var/www/YOUR.DOMAIN` You can now copy your website files in this folder.

### Setting up SSL for the domain

This step should be carried after setting up a website on the server and pointing a domain name to the server. If you have successfully setup a website using the instructions provided in the above section then you can now setup and SSL certificate.

1. Open up `ssl.yml` file and update the domain name and the email address.
2. In terminal run `ansible-playbook -Ki hosts ssl.yml`. If ran successfully, you will now have SSL setup on your website. Simply test it by typing in your domain in a web browser.

## Questions?

Should you have any questions or issues, feel free to send me a messsage. [Contact me](https://naveedziarab.co.uk/contact)

