# gh-pages-react-demo
## A guide for hosting a react app on GitHub Pages

1.  Create a react app in a new github repo and publish your project to GitHub

    If you don't already have a react app, you can find all the information required at [reactjs.org](https://reactjs.org/docs/create-a-new-react-app.html "Create react app")
2.  Go to the repository settings page, then select **Pages** 

    ![Go to pages menu](img\pages.JPG)

3.  Change the source branch from **None** to **Master** (or main) and press **Save**.
We'll change this again in the last step, but for now we need to set it to master so we can get the URL

    ![changing source to master](img\change-branch-to-master.JPG)

    You should now see your GitHub Pages URL for the current repository... We need to copy this link

    ![GitHub Pages URL example](img\after-save.JPG)

4.  Back in your react app, navigate to your project's **package.json** file and (towards the top) add the GitHub pages URL

    In my case: 
    ```json
    "name": "gh-pages-react-demo",
    "version": "0.1.0",
    "homepage": "https://aussiedev81.github.io/gh-pages-react-demo/",
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

7.  Now that we've got everything plumbed in, we should be able to run command ```npm run deploy```. 

    This action will add a **build** folder to your project which will contain the static files that GitHub Pages requires, but also publish the new deployment branch (gh-pages) that we declared in the last step
    ![new gh-pages branch](img\new-branch.JPG)

8.  If you go to your GitHub Pages web page, you'll notice that the react app's README file is being shown. This is because in step 3 we set the source branch to be **Master** so we could get the page URL, but the master branch contains our source code, not the static content we need.
What we need to do is head back to that page and change the source branch from **master** to our new **gh-pages** branch that we created in the last step.
![Changed the source branch from master to gh-pages](img\source-branch-changed.JPG)

**And that's it!**


A few things to consider:
-   Changes to your GitHub page can sometimes take a few minutes to take effect, so remember to be patient (after all... it is a free service 😉).
-   It is also possible to change the source branches to be whatever branch you choose with a little tweaking, this is just a basic guide to get it working.
-   It is definitely possible (and quite common) to create a dynamic single page web application (SPA) on GitHub pages, however mobile devices may not display content as expected due to relying on JavaScript.
