<h1 align="center" style="margin: 10px; font-weight: 700" > Morpheus </h1>
<h3 align="center" style="margin: 5px; font-weight: 400"> Front-end - Version.1 React-app </h3>
<h2 align="center" style="margin: 10px" > 🌍 🔋 ⚡ ☀️ ♻️ </h2>

## Table of Contents:

- [What is this?](#what-is-this)
- [Getting Started](#getting-started)
  - [SSH-keys](#ssh-keys)
  - [install create-react-app](#create-react-app)
  - [clone this repo](#clone-this-repo)
  - [start your own branch](#start-your-own-branch)
  - [run the server](#run-the-server)
- [Deploying to firebase](#deploying-to-firebase)
  - [install firebase CLI](#firebase-cli)
  - [create production build](#production-build)
  - [initialise firebase](#init-firebase)
  - [deploy the app](#deploy-the-app)
  - [teardown the app](#teardown-app)
- [Project Structure](#project-structure)
  - [naming files](#naming-files)
  - [placing files](#placing-files)
  - [importing files](#importing-files)
- [Git Workflow](#git-workflow)
  - [contributing](#contributing)
  - [branch naming](#branch-naming)
  - [git processes](#git-processes)
- [Standard Practices](#standard-practices)
  - [Javascript](#javascript)
  - [CSS](#CSS)
  - [SCSS](#SCSS)
  - [JSX/HTML](#jsx)

<a name="what-is-this"></a>

## what is this?

This repository contains the Front-End development code-base of the Morpheus website.

#### Built With:

<p align="center">
    <img src="https://upload.wikimedia.org/wikipedia/commons/a/a7/React-icon.svg" width="50px" />
    <img src="https://upload.wikimedia.org/wikipedia/commons/4/49/Redux.png" width="50px"  />
    <img src="https://upload.wikimedia.org/wikipedia/commons/d/d9/Node.js_logo.svg" width="70px"  />
    <img src="https://gblobscdn.gitbook.com/spaces%2F-L9iS6WpW81N7RGRTQ-K%2Favatar.png?alt=media" width="40px"  />
    <img src="https://upload.wikimedia.org/wikipedia/commons/9/96/Sass_Logo_Color.svg" width="40px"  />
</p>
Morpheus' front-end is primarily built on React via the create-react-app with Redux, Node, i18next for internationalisation and utilising SASS for CSS pre-processing.

---

#### README summary:

This README acts as a comprehensive guide to the daily development for the Morpheus front-end team.

The information contained here is as follows:

- a step-by-step guideline on how to install React and get the app up and running on your machine.
- The provided structure of the project files. I.E directories, filenames, spelling and casing.
- The standard team workflow for Git usage. I.E committing, pushing, merging and rebasing your work.
- General code standards and practices used within the project.
- Teamwork methods, tools and general information.

## Getting Started

<a name="ssh-keys"></a>

##### 1. Connecting your machine to the Gitlab account.

To begin with, you should set up your Gitlab account with an SSH-Key from your machine.

If you are unfamiliar with SSH keys, you can check the official Gitlab or Github (more detailed) documentation on generating keys and connecting with them:

- [Gitlab](https://docs.gitlab.com/ee/ssh/)
- [Github](https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/connecting-to-github-with-ssh)
- [Dev.to tutorial](https://dev.to/sndrx/how-to-set-up-an-ssh-key-and-use-it-in-gitlab--42p1)

To do this, on gitlab, click on your user icon & go to settings/SSH Keys and add your entire key which should look something like:

```bash
ssh-rsa [a long string of numbers and letters...] your-git-config-email@mail.com
```

If you are unable to do this, you can always connect to the repository via `HTTPS`.
This will result in you having to enter your Git config username & password for each Git action you do.

<a name="create-react-app"></a>

##### 2. Install the create-react-app package globally.

You should make sure that you have a recent version of `Node` & `npm` on your machine. To use create-react-app it must be at least Version **8.10** & **5.12** respectively.

In your terminal run these 2 commands:

- `$ npm install -g create-react-app`
- `$ npm list -g --depth=0`

This last command will inform you of all your globally installed packages. If you do not see `create-react-app` in the list, try prefixing the install command with **sudo**.

The list should look something like this:

```python
├── npm@6.14.6
├── create-react-app@3.4.1
```

<a name="clone-this-repo"></a>

##### 3. Clone this repository

Now that you have a connection to Gitlab and the necessary packages, we can download the existing code and get a server up and running.

In your terminal, `CD` into an appropriate directory and run this command to clone the master branch with **SSH**:

```bash
$ git clone git@gitlab.com:joinmorpheus/morpheus-website-v.1-react.js.git
```

or, **HTTPS**:

```bash
$ git clone https://gitlab.com/joinmorpheus/morpheus-website-v.1-react.js.git
```

Once this has downloaded, you should be able to see the basic react-app files from this repo.

<h3 style="color: red; font-weight: bold"> DO NOT PUSH ANY CHANGES TO THIS BRANCH!</h3>

None of the development work is done on Master.
The most **up to date code** will be on the `develop branch`.

Your next command should be to switch to the develop branch, pull that code and then make your own branch from there.

<a name="start-your-own-branch"></a>

##### 4. Start your own branch

Before we begin, we need to cover the naming convention of our branches. To avoid cluttering the repo with branches that have vague and useless names like "mikes-branch", we should stick to using the name of the appointed task on the Trello/Asana card you should have been given for the feature/issue you are working on.

For instance, if you are working on a task called "Figma Desktop 10 - create notifications icon" on Trello/Asana, you should name your branch something that lets everyone know:

- who worked on the branch
- what categorical relation to the project the branch has (WIP, feat, test, bug, junk)
- what the new code on this branch will be in relation to

This is a perfect example `mike/feat/create-notifications-icon`
We now have an idea of who is working on it, and what code we should expect to find in there. Let's move on.

Whilst we are still on the master branch run these commands in the following order:

- `$ git fetch --all`
- `$ git checkout develop`
- `$ git checkout -b name-of-your-branch`
- `$ git push origin name-of-your-branch`

You might receive a warning saying something like:

> The authenticity of host 'github.com (140.82.121.4)' can't be established.
> RSA key fingerprint is .....
> Are you sure you want to continue connecting (yes/no)?

    This is normal. Type "yes", enter and move on.

Now you should have your own branch which is a copy of the development branch where you are able to work on new code without accidentally overwriting the basic code-base of the whole project.

<a name="run-the-server"></a>

##### 5. Run the server

From the top level of the project directory, you only need to run a couple of commands to get a development server up and running:

```bash
$ npm install
$ npm start
```

From here you should have a developmental server running on your localhost in your default browser.

If for any reason you need to run a create-react-app server on a different port, you can do this by editing the `scripts` section in the Package.JSON:

change `"start": "react-scripts start"`
to:

- For Linux systems: `"start": "PORT=3006 react-scripts start"`
  - or `"start": "export PORT=3006 react-scripts start"`
- For Windows systems: `"start": "set PORT=3006 && react-scripts start"`

You can replace the port number with anything other than the default 3000.

## Deploying To Firebase

During the development process, we will be deploying a usability-testing version of the production app for the benefit of team cohesion, gaining real-time feedback and highlighting issues.
The standard process is currently done by the frontend team leader, but this is subject to change as Morpheus grows. The 4-step process is as follows:

1.  Any up-to-date changes are merged onto the development branch.
2.  create a production build of the app with `npm run build`
3.  initialise the develop branch if it isn't already, connecting to the "morpheus-frontent-testing" firebase project.
4.  deploy a live version with `firebase deploy`

<a name="firebase-cli"></a>

### Install Firebase CLI

To begin with, if you haven't already installed the firebase CLI with firebase tools, you will need these to be able to deploy to the project. Run this npm command to install the CLI:

`npm install -g firebase-tools`

You will now have the globally available firebase command on your local machine.
After installation you must authenticate yourself with firebase. Login with:

`firebase login`

This will open a browser page where you can login with the `user.name@joinmorpheus.com` you should have connected to the Morpheus firebase account. Once successfully logged in, you can test your connection with:

`firebase projects:list`

**Quick note:** If for some reason you have logged into another firebase account on your machine, you can log out with `firebase logout` and repeat the login process.

<a name="production-build"></a>

### Create Production Build

Before you can deploy the testing version of the app, you must generate a production version with the Webpack-Babel bundle command. In order to get to this point you should have the most up-to-date code in a functioning state that won't crash the site.

Create a production build with this command:

`npm run build`

If you run into any errors, the terminal will output these to you and abort the process. If everything goes to plan you should be informed that it "Compiled successfully" with an indication of the file size.

<a name="init-firebase"></a>

### Initialise firebase

**DISCLAIMER:** You should only have to run this command if the project is not already connected to a firebase-project.

Once you have the production build, you are ready to connect the app to the firebase project. To interact with the firebase init form, you will move up and down with the arrow-keys and select options with the `space-bar`. After you use the `enter-key` to confirm a choice. Follow these steps exactly:

1. run `firebase init`
2. choose the "use an existing project" option.
3. Select the "morpheus-frontend-testing" project.
4. select the "hosting" option.
5. When asked what to use as a public directory, type `build` and press enter. You do not want to use the `public` directory.
6. When asked to configure as a single-page-app, agree to this by typing "Y" and pressing enter.
**THIS STEP IS IMPORTANT. DO NOT PRESS ENTER WITHOUT LOOKING**
7. When asked if you want to overwrite the index.html, **disagree** with **"N"** and press enter. This will avoid firebase overwriting the index.html we have in the public directory with the default firebase index.html.

The firebase initialisation should now be complete.

**DISCLAIMER:** If for some reason the initialisation went wrong, you can undo these changes by deleting the files created by firebase in the `.firebase` directory, as well as `.firebaserc` and `firebase.json`.

<a name="deploy-the-app"></a>

### Deploy The App

Now that we have a production build and the repo is connected to the firebase project we can deploy a live version of the app to the web for usability testing. All you need to do at this stage is run this command:

`firebase deploy`

You should be presented with a success statement and a URL with which you can share with team members.

<a name="teardown-app"></a>

### Teardown The App

If you need to disable the live version of the production app, you just need to run this command:

`firebase hosting:disable -s morpheus-frontend-development`

## Project Structure

To create a clear and efficient system of working on features, we have a strictly organised system of arranging sub-directories, files and naming conventions within the project. This helps to prevents issues with merge-conflicts where different developers might accidentally create files and folders with the same name but different contents. This can dramatically impact progress and waste valuable time. To offset this we have built a standard structure as follows.

---

<a name="naming-files"></a>

### Directory and File names

Except for the items in the root directory (public, src, package.json, etc),
directories should have capitalised `CamelCase` names without spaces.
Javascript and most other file-types should follow the same rule.

Wrong:

- [ ] `/src/components/common/special button/special button.js`

Correct:

- [x] `src/Components/Common/SpecialButton/SpecialButton.js`

#### Exceptions:

- `SCSS/CSS` files are all lowercase. This is standard convention and helps to discern between the filetypes when you have similar named files in a directory together.

Example:

```
📦Components
 ┣ 📂Base
 ┣ 📂Common
 ┃ ┗ 📂Button
 ┣    ┗ 🟨 Button.js
 ┣    ┗ 🟦 button.css

```

- If a component contains a set of smaller components that are relative only to that parent component, it can be okay to create a containing sub-directory using an underscore and a distinct element name to separate the child components from the parent.

Example:

```
📦Components
 ┣ 📂Common
 ┣ 📂Forms
 ┃ ┗ 📂DataForm
 ┣    ┗ 📜 DataForm.js
 ┣    ┗ 📜 DataForm.scss
 ┃    ┗ 📂 DataForm_Blocks
 ┣        ┗ 📜 AcceptTerms.js
 ┣        ┗ 📜 UserAddressInput.js
```

- Utility functions under the `Utils` directory are currently standard camelCase named: I.E:
`src/Utils/Validation/dateFuncs.js`

---

<a name="placing-files"></a>

### Where to place your files

**NESTING**:
Generally speaking, it is a poor practice to nest any more than 4 directories deeper than the core folder inside of src. This can become inconvenient when your imports start to look like - `import * from "../Components/Common/Buttons/LargeButtons/LargeGreenButtons/LargeGreenButtons.js"`

**MAJOR COMPS**: As of the moment, the size of Morpheus code-base is not so large that there are a wide range of functions within the site. Therefore major Components such as "SwitchingProcess" and "Compare" live directly in the top-level of `src/Components`.
As the size of the Morpheus project grows, this may be subject to change.

**REUSABLE COMPS**: We advise keeping small reusable features in a self-contained, clearly labelled sub-folder in `/src/Components/Common`. Think customised buttons, checkboxes, popups etc.

**ASSETS**: Images, icons, and other general assets should be imported into their required places via Javascript. They should be contained in the `/Assets` directory inside of `/src` in an appropriate place such as:

```
📦src
 ┣ 📂Assets
 ┣     ┗ 📂Logos
 ┣        ┗ 📜 MorpheusLogo.svg
 ┣ 📂Components
 ┣ ...
```

Files inside the `/public` directory in the top level will not be processed by Webpack. Only static files like `index.html` and `favicon.ico` should live in public.

**ROUTES**: Any component that will be explicitly rendered via the `React-Router` in `/src/App.js` is considered a "Route" and as such is a "Super-Parent" to all further child components that come from it. To keep this concept simple, the Route's and their respective files will live in `/src/Routes`. This way you can track the process of which Super-Parent is rendering the components out.

**TESTS**: Testing suite files should belong in the directory of which specific Component the tests belong to.

**HOOKS**: For the time being, there are only a few implemented custom hooks so these will live in a separate Directory in `/src/Components/Hooks`

**UTILITIES**: Reusable functions that can be imported and used throughout the project should live in a separate directory in `/src/Utils`

**REDUX REDUCERS/ACTIONS**: We follow the 'rails' convention with our Redux libraries. Therefore reducers and actions will live in their respective folders alongside each other in the `/src` directory:

```
📦src
 ┣ 📂Actions
 ┣    ┗ 📜 UserActions.js
 ┣    ┗ 📜 RatesActions.js
  ...
 ┣ 📂Reducers
 ┣    ┗ 📜 UserReducers.js
 ┣    ┗ 📜 RatesReducers.js
```

<a name="importing-files"></a>

**i18n JSON**: The internationalisation files for German and English are kept in the `public/locales` directory under their respective locations of `de` and `en`. These files must be named exactly the same, in English writing.

---

### Importing files

This project allows the import of modules from absolute paths under the `src` directory.
you can read more about this [here.](https://create-react-app.dev/docs/importing-a-component/#absolute-imports)
What this means is it allows you to avoid unnecessarily long imports that go up and down the directory structure. Instead you can import directly downwards from the `src` folder.

Example:
Wrong:

- [ ] `import * from /../../../../Assets/Logos/logo.png`

Correct:

- [x] `Assets/Logos/logo.png`

**DISCLAIMER:** Importing files from the top-level `src` director will need to be explicitly imported with the file extension. An example would be using the `Axios` instance from `src/Axios.js`. This would be done as such:

`import axios from "Axios.js"`

## Git workflow

### contributing

To begin with we will use the following diagram to show our system on contributing to the Morpheus codebase

<img width="500px" src="https://trello-attachments.s3.amazonaws.com/5ef9c8ccf312d730a8cda4eb/5f14d8d12f6c4b4db39f33cb/c427f9c013839201a5221cf93d9cee92/GitLab_Workflow.png"/>

As shown in the diagram , we have two main-branches:

- Master
- Develop

and two sub sets of branches:

- Hotfix
- Feature

To clearly explain how you should be contributing code to the project, whilst you are working on a feature, testing or fixing issues etc, you should never be working on the `Master` or `Develop` branch. Your Git account should always be located in a `Feature` or `Hotfix` branch.

From here, as you finish tasks you will then proceed to merge your feature branch to the Develop branch. This code will be reviewed and tested, and once it is proven to be stable, the `Develop` branch will be merged into the `Master` upon a new version of the project.

Hotfixes work on a principle of introducing a quick change to the live version of the project. Perhaps a bug occurred in production. A `Hotfix` branch when finished will be quickly merged back into the `Master` to solve that issue, and then also merged back down into `Develop` to keep all the code up to date. `Hotfix` branches can be deleted after the code has been merged across the project to avoid clutter.

---

### Branch Naming:

First we will re-discuss the issue of naming branches as outlined in the installation process.

All branches should be **completely lowercase** and delimited by only forward slashes `/` and hyphens `-`.

branch names should follow a simple convention of 3 parts.

1. The author of the code (as short as possible. i.e "char"/ instead of "charlotte")
2. The category of the branch
3. The name of the feature/issue relating to the code

The 4 categories of branching are:

| category | purpose                                                                |
| -------- | ---------------------------------------------------------------------- |
| W.I.P    | A work in progress, tasks that don't have a deadline                   |
| Feature  | A feature you are adding to, expanding on or in the process of testing |
| Bug      | You are explicitly fixing bugs or experimenting                        |
| Junk     | A throwaway branch created to experiment, then delete                  |

The name of the feature/issue should be as simple as possible to explain the relevance of the code added within this branch. 3-4 words max should be plenty.

This way, all branches should be easy to see who they belong to, categorise and track issues. Here are some examples:

```bash
├── john/wip/intro-animation-screen
├── sarah/feat/footer-links
└── dieter/bug/homepage-zindex-css-fix
└── alison/junk/merging-john-sarah-dieter
```

### Git processes

To avoid painful mistakes with overwriting code and losing files with bad merges, we should all endeavour to use the same Git processes. Outlined are the standards for every operation you should need:

<h3 style="color: red; font-weight: bold">Careful Consideration:</h3>

If you are concerned about merging your work with others or vice-versa, a safe way to trial this is to create a **test-branch** of your current one where you can attempt to merge/rebase other branches to it. This way you will have a throwaway branch that can be deleted in the extreme case something damaging occurs. If everything works as planned, you can push to develop and delete the original branch you left behind.

> Helpful tip: To speed up the process of using git actions in the terminal, you should consider adding "aliases" to your .bashrc file.
> This way you can use shorthands for often repeated actions like typing "gs" for "git status" or "gcom" to replace "git commit -m"

---

**MERGING BRANCHES**
In some circumstances you may prefer to merge another person's work into your own without altering the commit history. The following method is a standard procedure for this action:

1. `$ git checkout other-branch`
2. `$ git pull origin`
3. `$ git checkout your-branch`
4. `$ git merge other-branch`

Your branch should now have received the code from "other-branch"

---

**RESOLVING CONFLICTS**
If merge conflicts occur, resolve them in this manner:

1. In your text-editor/IDE open the files that contain merge issues.
2. Keep or remove the changes that you require.
3. Delete the merge tags from the file. These will look something like this:

```
<<<<<<<< HEAD
=======
>>>>>>>> other-branch
```

4. Save the files in the editor/IDE
5. `$ git add .`
6. `$ git commit`
7. `$ git log --oneline`

Committing without a message will open up an editor in the terminal such as VIM or Nano. Simply save and exit the editor without any changes. This will prevent from creating an unnecessary merge commit log to the history. The last command will show you an up to date history of commits after the merge.

---

**SQUASHING COMMITS**
If you are working on a branch with a lot of commits, but you don't want to clutter the commit history, for example perhaps you were iterating on some documentation. You can use the interactive rebase editor to squash your commit history down to a single commit. Use the following method to achieve this

1. `$ git checkout your-feature-branch`
2. `$ git rebase -i` or `$ git rebase -i HEAD~[the number of commits you want to squash down]`

This will bring up an editor such as VIM or Nano. You will be shown a list of commits and a verb at the start.
The philosophy here is that you are squashing the more recent commits down on to the head of the branch. Essentially when the branch was last pushed to remote.

3. Next you want to edit the verbs at the start of the commits, squashing newest down to oldest. It should look something like this:

```
pick 596d1e1 fixed image url <--- oldest commit / location of HEAD
squash 924430f fixed about page link
squash 596d1e1 renamed file
squash 924430f imported css file <--- newest commit
```

As the editor suggests, you can use a short hand for these verbs such as "p" for pick and "s" for squash.

4. After you save and exit the editor, you will see a new editor screen asking what commit message you want to use. We recommend simply commenting out all but the most recent message so it is clear that the squash occurred at the point in time from when that commit was made.
   If you feel it necessary, you can add a tag "-- squashed" to the end to make it clear a history change occurred.

5. save and exit the editor once more and check the log with `$ git log --oneline`

If everything went to plan, you should see a commit history with only one extra commit message that you chose.

---

**PUSHING A FINISHED FEATURE TO DEVELOP**:
In the process of pushing our work to the develop branch, we need to take the utmost care to not cause any damage. This process might seem lengthy, but it is a sure-fire way to avoid any mistakes. with this method we are pulling any new changes on the develop branch to our local version, rebasing to our feature to avoid any conflicts, rebasing them back and then pushing develop to the remote.

**DISCLAIMER:** Rebasing should only ever be performed on a branch that a single developer is working on. Rebasing re-writes commit history which can be harmful if two authors are changing a branch simultaneously. In this circumstance, Merging is the preferred method.

1. `$ git checkout develop`
2. `$ git pull`
3. `$ git checkout your-feature-branch`
4. `$ git rebase develop your-feature-branch`

> Here, rebasing the develop branch onto your feature will move any recent commits on develop to the base of the feature branch, thus catching it up to any potential changes since your branch originally diverged from develop.

5. `$ git checkout develop`
6. `$ git rebase your-feature-branch develop`

> Now we are taking the commits on the feature branch and placing them at the head of the develop branch.

7. Solve any merge conflicts if existing.
8. `$ git add .`
9. `$ git rebase --continue`
10. `$ git push develop origin`

If at any point in the rebasing process you are unable to solve an issue, you can use the following command to halt the rebase process: `$ git rebase --abort`

done!

---

**CHECKING OUT A CO-WORKERS' BRANCH FOR REVIEW**:
First commit or stash any work before moving branch.
You should then proceed to pull the most recent changes from your co-worker and if need be run a `npm install` to resolve any changes to the package.json their might be.

1. `$ git add .`
2. `$ git commit -m "simple commit message"`
3. `$ git checkout coworkers-branch`
4. `$ git pull`
5. `$ npm install`
6. Review the code.

> Try to avoid making any changes yourself unless necessary. Otherwise your co-worker will have to pull updates back to themselves. This is not an unusual thing to do, but for the sake of cohesion within our small team, it should be avoided.

7. `$ git checkout your-branch-name`
   > (always make sure to switch back to your original branch to avoid accidental changes)

## Standard Practices

<a name="javascript"></a>

### Javascript / General Development

- First of all, please check your **developer console** in the browser for **errors**. This is where React is giving you crucial information that without being resolved, these errors will make it to production.

- If you are using a state value without needing to set it again, just declare the state value inside an array `[ ]` without a state-setter . This way you wont end up with an unused setState variable. Example:

```
Incorrect:
const [value, setValue] = useState(0)
Correct:
const [value] = useState(0);
```

- The "React Devtools", and "Redux Devtools" extensions for Google Chrome are invaluable resources for information. You can avoid writing a lot of unnecessary Console.log's by using these tools correctly.

---

### CSS

- At the moment we are following the **BEM** convention for naming css classes.
  You can read succinct documentation about that here: [link](https://css-tricks.com/bem-101/)

- Use **comments** in your CSS/SCSS files to break down the styles into sections, and also clearly explain more complicated rules.

- Lay out your Stylesheet elements & classes in the same order. This should follow a general pattern from top to bottom:

1. Generic Classes / Main body of an element
2. Specific elements
3. Pseudo classes and effects / animations.
4. Media Queries

- Lay out your style rules for each element / class in the same pattern. This helps team-members to predict what your css will look like and save time. Generally this should be something like:

```
.example-class{
// 1. Display, Positioning, Cursor, user-select & Content:
        cursor: pointer;
        user-select: text;
        content: "";
        display: flex;
        position: absolute;
        top: 0;
        left: 0;
// 2. Overflow, resize & scroll-behaviour:
        overflow-x: hidden;
        resize: scroll;
// 3. Grid-rules, Alignment & float:
        grid-gap: 5px
        justify-content: flex-start;
        align-self: center;
        float: left;
// 4. Margins, Paddings & Sizing:
        margin: 10px 20px;
        padding: 5px;
        height: auto;
        width: 100%
// 5. Colouring, background & object-fit:
        color: #ffdab9
        background-image: linear-gradient(90deg, #000, #fff)
        background-repeat: no-repeat
        object-fit: cover;
// 6. Bordering:
        border: 2px solid #000;
        border-radius: 20px;
        border-top-left-radius: 0px;
// 7. Text:
        font-family: "Montserrat", sans-serif;
        font-size: 2rem;
        line-height: 20px;
        white-space: no-wrap;
// 8. Visibility, Opacity & Z-indexing:
        visibility: visible;
        opacity: 0.5
        z-index: -1
// 9. Transitions, Animations & Transforms:
        transition: all 1s ease-in-out;
        animation: pop-up 1s linear;
        transform: translateX(10px);
// 10. Box-shadow, backface-visibility;
        box-shadow: 5px 5px 0px 20px (#000. 0.5)
        backface-visibility: hidden;
}
```

- If you are using a set of styles often enough, consider creating a **generic class** of those styles and apply the class to elements in the standard BEM fashion. example:

```
.flex-column {
    display: flex;
    flex-direction: column
}
= = =
<div className="flex-column">
    \\ children
</div>
```

- Creating an extra wrapping element to apply one specific style or ID should be avoided if possible. Styles should be respective of the children themselves. Thus targeting an element with **CSS selector combinators** would be the better option. Example:

```
.parent-with-child > ul:nth-child(2){
    //styling here
}
```

- Use **CSS shorthand** wherever possible. This creates a cleaner layout and less overall code. Example:

```
Incorrect:
#example {
    margin-top: 0px;
    margin-right: 10px;
    margin-bottom: 20px;
    margin-left: 5px;
}
Correct:
#example {
    margin: 0px 10px 20px 5px;
}
```

- Use **absolute positioning** sparingly! While tempting to style something specific using positioning, this can be hard to maintain and can quickly cause unwanted behaviour.

---

### SCSS

- General SCSS files for shared variables, extenders & mixins should be located in the `src/Assets/Sass` directory.

- Due to the SASS_PATH environment variable in the `.env` file in the root directory, you can now import your SCSS files with an absolute path down from `src` much like you would any other file. example:

A deeply nested SCSS file in /Components/...

```
@import "src/Assets/Sass/variables.scss";

.container{
    // Variables from the imported SCSS file are now exposed for use
    color: $some-sass-variable
}
```

**An important reminder:** Sass imports must be terminated with a semi-colon `;`. This will throw an error otherwise.

- Common colors, gradients, fonts and other styling choices are a safe choice for implementing as **Sass variables**.

- If you are using a group of styles often enough, consider making a **Sass placeholder** to then implement in your stylesheets. A good example here would be a css rule that allows an element to take up the entire space of a parent with absolute positioning:

```
.some-class{
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
}
```

Here you could turn this into a Sass placeholder class with the modulo operator `%`to save on repeated use of this styling. Here is an example of use:

```
%my-placeholder-box-shadow {
    margin:0
    box-shadow: 0 0 0 100vmax rgba(0,0,0,0.2)
}

.class-to-extend{
    @extend %my-placeholder-box-shadow;
}
```

<a name="jsx"></a>

## JSX / HTML

- As image and icon files are located inside of `Assets` under `src`, you should be importing the image directly into javascript. This way, React will define an error if the file is not found, instead of showing a missing file icon in the browser. You should import like this:

  > `import` image-name `from` `"relative-path-location"`

- Try to avoid creating unnecessary wrapping divs for the return statement in a function component. You can use `React.Fragment` elements or the shorthand `<> </>` to solve this issue.
  example:

```
export default function ExampleComp(){
    return (
        <>
            <h1> We are children elements </h1>
            <br/>
            <p> Without a wrapping div! </p>
        </>
        )
}
```


- Modified by `Henry J. E. Crookes` on `24.11.2020`
