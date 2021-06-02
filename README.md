# Heroku-Django-Hosting

* Before getting started one must make sure to have following things done

   [Installed Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
   
   [Make a Heroku account](https://signup.heroku.com/)
   
   [Download Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli)
      
       

* Create and activate virtual environment in manage.py directory,

      virtualenv YOUR_ENV_NAME
      
      YOUR_ENV_NAME\Scripts\activate

* In settings.py make

      * DEBUG = False
      * ALLOWED_HOSTS = ['your_app_name.herokuapp.com', 'localhost', '127.0.0.1']

* Hold on to settings.py and add following

      import django_heroku
      import os
      STATIC_ROOT = os.path.join(BASE_DIR, 'static')
      django_heroku.settings(locals())
      
* Make a new file named ```Procfile``` in manage.py directory and add

      web: gunicorn your_project_name.wsgi --log-file -
      
* Make another file ```.gitignore``` in manage.py directory and add content from [here](https://www.toptal.com/developers/gitignore/api/django)

* Add your dependencies to requirements.txt by typing in the terminal,

      pip freeze > requirements.txt

* Now it's time for git

        git init
        git add .
        git commit -m "first commit"
        
        heroku login -i
        heroku create your_app_name  (this your_app_name should be same as the one which was added in ALLOWED_HOSTS)
        git push --set-upstream heroku master
        heroku run python manage.py migrate
* And boom your website is deployed, you can check with below command

        heroku open

