# gh-pages-react-demo
## A guide for hosting a react app on GitHub Pages

1.  Create a react app in a new github repo and publish your project to GitHub

    If you don't already have a react app, you can find all the information required at [reactjs.org](https://reactjs.org/docs/create-a-new-react-app.html "Create react app")
2.  Go to the repository settings page, then select **Pages** 

    ![Go to pages menu](img\go-to-pages-menu.JPG)

3.  Change the source branch from **None** to **Main** and press **Save** 

    ![Source as none](img\change-source-branch.JPG)
    ![Source as main](img\with-main-branch-as-source.JPG)

    You should now see your GitHub Pages URL for the current repository

    ![GitHub Pages URL example](img\gh-pages-url.JPG)

4.  Back in your react app, navigate to your project's **package.json** file and (towards the top) add the GitHub pages URL

    In my case: 
    ```json
    "name": "react-app-github-pages",
    "version": "0.1.0",
    "homepage" : "https://aussiedev81.github.io/react-app-github-pages/",
    "private": true,
    ...
    ```
5.  In the console (making sure to be in your app's root directory), run the following command
    ```npm install gh-pages --save-dev```

6.  Again, back in the **package.json** file, in the **scripts** section we need to add the following 2 commands
    ```json
    "predeploy": "npm run build",
    "deploy": "gh-pages -d build",
    ```

    Your scripts section should now look like this
    ```json
    "scripts": {
        "start": "react-scripts start",
        "build": "react-scripts build",
        "test": "react-scripts test",
        "eject": "react-scripts eject",
        "predeploy": "npm run build",
        "deploy": "gh-pages -d build"
    },
    ````

7.  Now that we've got everything plumbed in, we should be able to run command ```npm run deploy```

    *Note: Make sure you have pushed your latest changes to the main branch of your repository*

8.  Lastly, after running the command in the last step you're probably wondering why your web page is showing your projects **README** file... Not to worry though, all we have to go is go back to the **Pages** page in our GitHub repo and change the source branch from **main** to **gh-pages** 👌

    The changes might take a minute to be visible so be patient
