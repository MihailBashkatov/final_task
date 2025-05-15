# Project Tracker for Good Habits on remote server

### Project is aimed to build SPA backend part and be available on the external server

There are two options to use project materials

1. Run as ready solution
2. Adapt solution for your needs

1. Run as ready solution. 

   1) Create a directory 

            mkdir <directory_name>

1) Copy docker-compose.yml (branch celery) to your directory
2) Set there file .env 

            touch .env

3) Insert next variables

            nano .env

Generate SECRET_KEY

     tr -dc 'A-Za-z0-9!#$%&\()*+,-./:;<=>?@[\]^_{|}~' </dev/urandom | head -c 50  ; echo

Generate BOT_TOKEN follow instructions here https://t.me/BotFather

SECRET_KEY=     
DEBUG=True  

POSTGRES_DB=test_final_task  
POSTGRES_USER=postgres  
POSTGRES_PASSWORD=postgres  
POSTGRES_HOST=db  
POSTGRES_PORT=5432  

BOT_TOKEN=

CELERY_BROKER_URL=redis://redis:6379/0
CELERY_RESULT_BACKEND=redis://redis:6379/0

4) Insert command in the terminal

       docker compose up --build

6) If container final_task_celery_beat does not get connection to the postgres (log error ), stop the container and and start it again

       docker stop final_task_celery_beat

       docker start final_task_celery_beat

5) App is available
http://84.201.144.206/habits/

5) To stop the programme

            docker stop $(docker ps -aq)

6) To remove all container

            docker compose down

If you want to recieve reminder via Telegram

#### Add your user profile

##### 2) Find out you Telegram ID (e.g via @userinfobot)
##### 3) Add field telegram_chat_id (Telegram ID) when you creating your profile 


#### Add habit. For that next fields are compulsory:

"habit_name"

"habit_place"

"habit_action"

habit_date" (format YYYY-MM-DD hh:mm)

"habit_time_duration" (reflected in seconds, max is 120 seconds)


#### Project documentation is placed 

http://84.201.144.206/swagger/