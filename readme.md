# How to run this project with Docker and Docker Compose:
### Author: Ben Matela

#### NB: You need `Docker Desktop` installed on your machine or you can just install `Docker` and `Docker Compose`.

Clone project:

```bash
git clone https://github.com/benmatela/nodejs-ts-gcp-functions-docker.git
```

To create our new container, we run `docker-compose` from the root project folder.

```bash
docker compose -f nodejs-ts-gcp-functions-docker-v1-container/docker-compose.yml up --build
```

`-f`: Specifies the path to your docker-compose.yml

`up`: Brings up the container

`--build`: Rebuilds the image before starting (useful after code changes)

More commands will be shown at the bottom of the terminal once the container is running.

### 1. Using your new container:

#### 1.1 Via Docker Desktop:

1. Enter `v` on the terminal to open container in Docker Desktop.
2. Click on your `container` from the container list
3. Click `exec` to access the terminal.

#### 1.2 Via Terminal(no Docker Desktop):

1. Run `docker ps` to find the name of your container.
2. Run `docker exec -it your_container_name sh` to enter the terminal of your container.

Create a Firebase project on the official site if you don't have one already. 
You'll need the gmail account used to create the Firebase project to login via the container terminal.

### 2. From inside your container:

- Login to Firebase:

``` bash
firebase login --no-localhost
```

Follow the steps and end with copying the token from your browser and pasting it inside the container terminal.

- List all available projects:

``` bash
firebase projects:list
```

- Select project using the project ID from the list above:

``` bash
firebase use your_project_id
```

### 3. Run project: 

If this is the first time running the project, you may need to wait a bit for emulators to be downloaded.

``` bash
npm run serve
```

- Your endpoints and emulator URLs will now be shown in the logs.

### 4. Using exported data from Firestore:

- Imported data from your live Firebase can be saved in `/firebase_data/...`;

- When working with local Firebase Emulators, the data you create will automatically be saved in `/firebase_data/...`;

- Exported data will load everytime you run the serve command.

- To delete data in `/firebase_data/...`, stop the project and:

```sh
# Go into the folder
cd firebase_data
```

- Other useful commands:

* Delete all files in the current directory(optional):

```sh
rm -r *
```

* Run project again after deleting files(optional):

```sh
cd ..
```

``` bash
npm run serve
```

### 5. Working with files from within your container(OPTIONAL):

- You can use `nano` to edit/create local files eg:

Use `"cntrl + c"` to stop the terminal then go to the directory/folder you want to work in eg:

```bash
cd lib # Go to "lib" folder
```

```bash
nano .env # Update existing file
```

Use `"cntrl + x"` to exit `nano`.

```bash
nano my_new_file.txt # Create new file
```

Use `"cntrl + x"` to exit `nano`.

### Happy hacking!
