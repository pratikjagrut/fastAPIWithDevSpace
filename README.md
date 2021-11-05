# fastAPIWithDevSpace

```
git clone git@github.com:pratikjagrut/fastAPIWithDevSpace.git
cd fastAPIWithDevSpace
```

## Init DevSpace

NOTE: The project already contains devspace.yaml so this step is not necessary.

Select all the default options, if you don't need any extra configs.
```
➜  fastAPIWithDevSpace git:(main) ✗ devspace init         

     ____              ____                       
    |  _ \  _____   __/ ___| _ __   __ _  ___ ___ 
    | | | |/ _ \ \ / /\___ \| '_ \ / _` |/ __/ _ \
    | |_| |  __/\ V /  ___) | |_) | (_| | (_|  __/
    |____/ \___| \_/  |____/| .__/ \__,_|\___\___|
                            |_|


? How do you want to deploy this project? helm: Use Component Helm Chart [QUICKSTART] (https://devspace.sh/component-chart/docs)

? How should DevSpace build the container image for this project? Create a new Dockerfile for this project
                                                  
? Select the programming language of this project python


[info]   DevSpace does *not* require pushing your images to a registry but let's assume you wanted to do that (optional)

? Which registry would you want to use to push images to? Skip Registry

[info]   Configuration saved in devspace.yaml - you can make adjustments as needed
[done] √ Project successfully initialized
         
You can now run:
- `devspace use namespace` to pick which Kubernetes namespace to work in
- `devspace dev` to start developing your project in Kubernetes
- `devspace deploy -p production` to deploy your project to Kubernetes
- `devspace -h` to get a list of available commands
```

## Update the devspace_start.sh script

Replace the command `bash` on last line with `python ./main.py` to directly start the server.
## DevSpace Dev

```
((fastAPIWithDevSpace) ) ➜  fastAPIWithDevSpace git:(main) ✗ devspace dev -n test-3        

[warn]   Are you using the correct namespace?
[warn]   Current namespace: 'test-3'
[warn]   Last    namespace: 'test-2'

[info]   Use the '-s / --switch-context' flag to switch to the context and namespace previously used to deploy this project
[info]   Or use the '--no-warn' flag to ignore this warning
                                                  
[info]   Using namespace 'test-3'
[info]   Using kube context 'docker-desktop'
[done] √ Created namespace: test-3
[info]   Execute 'helm upgrade fastapiwithdevspace component-chart --namespace test-3 --values /var/folders/9c/mv8m0y2j5_13zyd93yxwl71m0000gn/T/381283089 --install --repo https://charts.devspace.sh --repository-config='' --version 0.8.2 --kube-context docker-desktop'
[info]   Execute 'helm list --namespace test-3 --output json --kube-context docker-desktop'
[done] √ Deployed helm chart (Release revision: 1)                                 
[done] √ Successfully deployed fastapiwithdevspace with helm                       
[0:replacePod] Try to find replaced pod...
[0:replacePod] Try to find replaceable pod...
[0:replacePod] Replacing Pod test-3/fastapiwithdevspace-fcd57c7bd-dbwg5...
[0:replacePod] Scaled down Deployment test-3/fastapiwithdevspace
[0:replacePod] Waiting for Pod fastapiwithdevspace-fcd57c7bd-dbwg5 to get terminated...
[0:replacePod] Successfully replaced pod test-3/fastapiwithdevspace-fcd57c7bd-dbwg5
                                             
#########################################################
[info]   DevSpace UI available at: http://localhost:8090
#########################################################

[0:ports] Port-Forwarding: Waiting for containers to start...
[0:sync] Waiting for containers to start...
[0:sync] Starting sync...
[0:ports] Port forwarding started on 8080:8080 (test-3/fastapiwithdevspace-fcd57c7bd-dbwg5-zttn4)
[0:sync] Sync started on /Users/pratikjagrut/github.com/pratikjagrut/fastAPIWithDevSpace <-> . (Pod: test-3/fastapiwithdevspace-fcd57c7bd-dbwg5-zttn4)
[0:sync] Waiting for initial sync to complete
[info]   Opening 'http://localhost:8080' as soon as application will be started (timeout: 4m0s)
[info]   Terminal: Waiting for containers to start...
[info]   Opening shell to pod:container fastapiwithdevspace-fcd57c7bd-dbwg5-zttn4:container-0
Installing Python Dependencies
Collecting fastapi
  Downloading fastapi-0.70.0-py3-none-any.whl (51 kB)
     |████████████████████████████████| 51 kB 568 kB/s 
Collecting uvicorn
  Downloading uvicorn-0.15.0-py3-none-any.whl (54 kB)
     |████████████████████████████████| 54 kB 745 kB/s 
Collecting starlette==0.16.0
  Downloading starlette-0.16.0-py3-none-any.whl (61 kB)
     |████████████████████████████████| 61 kB 530 kB/s 
Collecting pydantic!=1.7,!=1.7.1,!=1.7.2,!=1.7.3,!=1.8,!=1.8.1,<2.0.0,>=1.6.2
  Downloading pydantic-1.8.2-py3-none-any.whl (126 kB)
     |████████████████████████████████| 126 kB 1.1 MB/s 
Collecting anyio<4,>=3.0.0
  Downloading anyio-3.3.4-py3-none-any.whl (78 kB)
     |████████████████████████████████| 78 kB 388 kB/s 
Collecting asgiref>=3.4.0
  Downloading asgiref-3.4.1-py3-none-any.whl (25 kB)
Collecting h11>=0.8
  Downloading h11-0.12.0-py3-none-any.whl (54 kB)
     |████████████████████████████████| 54 kB 361 kB/s 
Collecting click>=7.0
  Downloading click-8.0.3-py3-none-any.whl (97 kB)
     |████████████████████████████████| 97 kB 1.3 MB/s 
Collecting idna>=2.8
  Downloading idna-3.3-py3-none-any.whl (61 kB)
     |████████████████████████████████| 61 kB 1.1 MB/s 
Collecting sniffio>=1.1
  Downloading sniffio-1.2.0-py3-none-any.whl (10 kB)
Collecting typing-extensions>=3.7.4.3
  Downloading typing_extensions-3.10.0.2-py3-none-any.whl (26 kB)
Installing collected packages: sniffio, idna, typing-extensions, anyio, starlette, pydantic, h11, click, asgiref, uvicorn, fastapi
Successfully installed anyio-3.3.4 asgiref-3.4.1 click-8.0.3 fastapi-0.70.0 h11-0.12.0 idna-3.3 pydantic-1.8.2 sniffio-1.2.0 starlette-0.16.0 typing-extensions-3.10.0.2 uvicorn-0.15.0
WARNING: Running pip as the 'root' user can result in broken permissions and conflicting behaviour with the system package manager. It is recommended to use a virtual environment instead: https://pip.pypa.io/warnings/venv
WARNING: You are using pip version 21.2.4; however, version 21.3.1 is available.
You should consider upgrading via the '/usr/local/bin/python -m pip install --upgrade pip' command.

   ____              ____
  |  _ \  _____   __/ ___| _ __   __ _  ___ ___
  | | | |/ _ \ \ / /\___ \| '_ \ / _` |/ __/ _ \
  | |_| |  __/\ V /  ___) | |_) | (_| | (_|  __/
  |____/ \___| \_/  |____/| .__/ \__,_|\___\___|
                          |_|

Welcome to your development container!

This is how you can work with it:
- Run `python main.py` to build the application
- Files will be synchronized between your local machine and this container
- Some ports will be forwarded, so you can access this container on your local machine via http://localhost:8080

INFO:     Will watch for changes in these directories: ['/app']
INFO:     Uvicorn running on http://0.0.0.0:8080 (Press CTRL+C to quit)
INFO:     Started reloader process [92] using statreload
INFO:     Started server process [94]
INFO:     Waiting for application startup.
INFO:     Application startup complete.
```

Hit the link in browser http://0.0.0.0:8080 to see the page.

## Hot reload

Change the `Hello world` to `Hello DevSpace` and save the file. Notice the logs in terminal and refresh the browser once the change server is reloaded.