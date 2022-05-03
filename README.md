# firebase-cli
Simple install of nodejs, npm and firebase-cli

## Usage

### Download

```
git clone https://github.com/rglonek/firebase-cli.git
```

### Build

```
cd firebase-cli/cli
bash ./build.sh
cd ..
```

### Run

```
docker run -it -v $(pwd)/files:/firebase -v $(pwd)/login:/root/.config/configstore --rm firebase-cli
```

NOTE: Login tokens are stored on the local machine. If you do not want that (reauthanticate every time a container is run for firebase), run this instead:

```
docker run -it -v $(pwd)/files:/firebase --rm firebase-cli
```

### Use

#### Basics

Action | Command
--- | ---
login | `firebase login --no-localhost`
init project | `firebase init`
local hosting | `firebase serve -o 0.0.0.0`
list sites | `firebase hosting:sites:list`
add target for multi-page hosting - name must match site name created in firebase web interface | `firebase target:apply hosting mysite mysite`
deploy target | `firebase deploy --only hosting:mysite`

#### Multi-target

Once the `firebase target:apply` command has been run, the `firebase.json` must be modified prior to deployments. Example command below (modify `mysite` with your site name):

```
sitename="mysite"
cat <<EOF > firebase.json
{
  "hosting": [
    {
      "public": "public",
      "target": "${sitename}",
      "ignore": [
        "firebase.json",
        "**/.*",
        "**/node_modules/**"
      ]
    }
  ]
}
EOF
```

#### Directories

On your host machine, access the `$(pwd)/firebase` directory. Put all hosting files in `/public` once `firebase init` has been executed. This way development can happen on the local machine, and the docker image is purely for the `firebase` commands. Login tokens are also stored on the local machine!
