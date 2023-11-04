#

### add server
```bash
adduser gary
adduser gary sudo

#ssh part



sudo visudo # add gary ALL=(ALL:ALL) NOPASSWD:ALL


sudo apt-get update
sudo apt-get update
sudo apt-get install ufw

sudo ufw default allow outgoing
sudo ufw default deny incoming
sudo ufw allow ssh
sudo ufw allow 8000
sudo ufw enable


#
sudo apt-get install apache2-dev
pip install wheel 
pip install mod_wsgi

sudo chown -R gary:gary /home/gary/resume_demo/venv/


# deploy  part
git clone

sudo apt-get install python3-pip
sudo apt-get install python3-venv
sudo python3 -m venv venv
source venv/bin/activate
sudo pip install -r requirements.txt
pip install -r requirements.txt
python manage.py makemigrations
python manage.py migrate
python manage.py collectstatic


# 
sudo apt-get install apache2
sudo apt-get install libapache2-mod-wsgi-py3
sudo apt-get install libapache2-mod-wsgi-py3
sudo a2enmod wsgi

#venv




cd /etc/apache2/sites-available/
cp 000-default.conf resume_demo.conf
sudo vim resume_demo.conf

# add
sudo a2ensite resume_demo
sudo a2dissite 000-default.conf
sudo chown :www-data resume_demo/db.sqlite3 # for apache to access db
sudo chmod 664 resume_demo/db.sqlite3 # for apache to access db, owner can read and write, group can read, others can read
sudo chown :www-data resume_demo/ # for apache to access db

ls -la # check permission, www-data is the owner of project folder


sudo chown -R :www-data resume_demo/mediafiles/ # for apache to access db
sudo chmod -R 775 resume_demo/mediafiles/ # for apache to access mediafiles, 

sudo chown -R www-data:www-data /home/gary/resume_demo/
sudo chmod -R 775 resume_demo/

sudo touch /etc/config.json
sudo vim resume_demo/resume_demo/settings.py

SECRET_KEY = 'django-insecure-=@-5)vns*sv2f!4nk!x+(=_d+9$o*@bbmc^@$u-&(&j+-d5&gh'

DEBUG = False


##
sudo ufw allow http/tcp





```

