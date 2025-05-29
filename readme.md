# How to run this project with Docker and Docker Compose:

To create our new container, we run `docker-compose` from the root project folder.

```bash
docker compose -f nodejs-ts-gcp-functions-docker-v1-container/docker-compose.yml up --build
```

If you've previously ran the command above and nothing has changed in your `Dockerfile` and `docker-compose.yml` files, you can run the container without building it again:

```bash
docker compose -f nodejs-ts-gcp-functions-docker-v1-container/docker-compose.yml up # --build is removed
```

`-f`: Specifies the path to your docker-compose.yml

`up`: Brings up the container

`--build`: Rebuilds the image before starting (useful after code changes)

More commands will also be shown at the bottom of the terminal once the container is running.

### 1. Using your new container:

#### 1.1 Via Docker Desktop:

1. Enter `v` to open container in Docker Desktop.
2. Click on your `container` from the container list
3. Click `exec` to access the terminal.

#### 1.2 Via Terminal(no Docker Desktop):

1. Run `docker ps` to find the name of your container.
2. Run `docker exec -it your_container_name sh` to enter the terminal of your container.

Create a Firebase project on the official site if you don't have one already.

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

- Exported data from Firestore, Storage, Authentication or the Emulators(local Firestore, Storage, Auth) will be saved in your container in `/firebase_data/...`;

- Exported data will load everytime you run the serve command.

- To delete data in `/firebase_data/...`, stop the project and:

```sh
# Go into the folder
cd firebase_data
```

- Other useful commands:

```sh
# Deletes all files in the current directory
rm -r *
```

```sh
# Go back to root folder and continue coding
cd ..
```

### 5. Working with files from within your container:

- You can use `nano` to edit/create local files eg:(OPTIONAL TO TRY OUT)

Use `"cntrl + c"` to stop the terminal then go to the directory/folder you want to work in eg `cd lib`.

```bash
nano .env # Update existing file
```

```bash
nano my_new_file.txt # Create new file
```

Use `"cntrl + x"` to exit `nano`.

### Happy hacking!
