# `Deployment With Netlify and Vercel`

## `Section Overview`

So, you have worked really hard on this stunning project that's sitting on your computer, but you don't just want to leave it there, right? No, you want to actually share it with the world to show your friends and even potential employers that you have built this project, even if it was with the help of this course. And so, to make that happen, let's finish this project by deploying it using two of the top hosting providers in the industry, Netlify and Vercel. So we're gonna start small and just upload the production build to Netlify.

Then after that, we'll take it one step further and set up a git and github repository for continuous deployment with Vercel, which is actually similar to what real companies do. So don't miss this final step and let's bring your project to the world.

## `Deploying to Netlify`

So let's start with a very easy way of deploying our application by simply uploading it to a free service called Netlify. But first of all we actually need to first go back to our login form, so right in the authentication folder, because we actually left our credentials in the default state. So let's of course clean this, otherwise everyone could just log into our application.

Now it is time to build our actual application bundle. So remember how we learned earlier that our development tool, so in this case that's Vite, will take all the files that we have created during development and will all bundle them into one single file. And so that file is what we then deploy to production. So not just that file, but really the output that we will get.

So in our terminal, let's ***`run npm run build.`*** And we actually already did this earlier with the WorldWise application.

Okay, so we have one bundle here, which is indeed pretty huge, as we can see in this warning here from Vite.  

Now, in an earlier project, and I think it was in the WorldWise project, we actually did code splitting in order to avoid this problem. However, this application will be fully hidden behind a login.

And also only a few users will ever use this application, which, remember, is also the reason why we're not doing server-side rendering as well. And so in this situation, this is actually perfectly fine. And also, we already learned how to do this.

And let's see what we actually got. So the folder that was created is this **`dist folder`**. So here we have the assets, which is that huge JavaScript bundle. So that one or almost one megabyte of JavaScript. And then we have the HTML and all the images that are necessary.

**All right. And so now we are ready to take this folder(dist folder) and deploy it to that service that I mentioned earlier called Netlify.**

So as soon as you're logged into Netlify, your dashboard should look something like this. Or maybe in the future, they will have changed it again.

But basically,  all we have to do is to create a new site simply with this option of deploying manually.

So let's click there. And now all we have to do is really drag and drop that folder that Vite built for us earlier. So that's this dist folder.

But actually, there is something that we still need to do, because otherwise our single page application is not going to work on Netlify.

So let's first come back to VS Code. And then in the **`dist folder`**, I need you to create a new file called **`netlify.toml`**, which is like some special data format. Then here you need square brackets two times, then redirects, and then from this URL to index.html. And then with the status code of 200.

```toml
<!-- netlify.toml File-->

[[redirects]]
from = "/*"
to = "/index.html"
status = 200

```

Okay, so now here we have that important file. And so now we can indeed grab the entire folder and just drop it here. So that's going to take some time uploading everything.

And once that's done, open our production deploy, and then here is our application live on a web server. <https://roaring-meerkat-603bfd.netlify.app/>

But, this URL here is not really that nice to be shared, right? And so we can actually change this. So let's come here to the site's overview now. And so then here is that URL, and here in the site settings we can then change the site name.
<https://the-whild.netlify.app/login>

And so I will now change it to the wild oasis, which will then give me the wild oasis on this .netlify.app subdomain.

And that's actually it. So this is the very easy way of very quickly getting your site up and running on a real domain, ready to be shared with the world.

And so in order to show you how to do that, in the next lecture we will set up a Git repository and upload your code to GitHub.

## `Setting Up a Git and GitHub Repository`

And so if your Git installation was successful, you should be able to run in this folder, `git init`. And so this will then transform this folder here into a Git repository. **And a Git repository is basically just a special kind of folder which will track every single change that you do to every single file in this folder.**  

So untracked just means that we didn't add them yet to our so-called staging area. So let's actually run a comment called `Git status`.

So we are on the main branch, because in Git we can have multiple branches where different versions of your code can live in different branches. And you can then easily switch back and forth between them.

But anyway, before we actually add this here to our staging area, let's create a brand new file called readme.md. And MD stands for Markdown. And so usually all repositories should have a readme file

**And so now let's add all the files to the so-called staging area.** **So that's git add and then dash a.** So an uppercase a. And then here are these files changed from untracked to added.  All right. If we then check git status again, then here we see that we have all of these new files.

But in this case, let's again just put it back. And now if we want to basically upload this to some remote repository, then we need to create an account on a service like GitHub or GitLab. And GitHub  is by far the most popular one. And so let's go there. So github.com.

Let's create ourselves a new repository.

Now here are some instructions to how to connect this remote repository. So this repository that we have, which is living in the cloud essentially with the local repository that we created earlier on your computer.

**Now before we can actually do that connection, let's quickly set up something called an access token.**

So that's a token that you will use instead of a password when you want to connect these two repositories. So let's come here to your avatar and go to the settings. And then all the way down here, we go to developer settings. And if this here has changed in the meantime, then you can just Google for how to access or how to create GitHub personal access tokens. So here then

select one of these two. I will just go with the classic ones. And then here, just generate new token. And again, I think you can choose both of them. Then here, you give it a name. I will just call it test. Then here, you can select for how long you want this token to be valid. So you can choose no expiration, but that is not the most secure option. So let's leave it at 30.

Now, maybe you're wondering why we only have the source and the public folder. If here in our VS Code we actually have also node modules and the dist folder. Well, the reason for that  is that vite gave us this git ignore file. And so this git ignore contains all kinds of files and folders that will be ignored by git. So those are files that will not be committed into the git repository. And so that includes the node modules folder and also the dist folder.

And the reason for the dist folder is that this is a folder that we can very easily just recompute. And so really only the source code itself should be committed into the repository.

---

## `Deploying to Vercel`

So now let's use our GitHub repo that we just created to set up a very simple continuous integration on Vercel, which is another very popular free, at least for small projects and also very easy to use hosting provider for React applications.

But first of all, we could actually also set up a continuous integration on Netlify. So for that, we would again add a new site and then here, this time we would select import an existing project. And so then here it says exactly what I mentioned in the beginning. So basically importing an existing project from a Git repo. And so then here you would connect your GitHub account and then just follow these steps. So if you want, you can do this here on Netlify. That's very easy as well, but I just want to show you another alternative. And so that is... So this is actually the company that created the Next.js framework. And so they are specialized on hosting Next.js applications, but we can of course also very easily host basically vanilla React applications here. So you can just sign up for a new account and then, well, here you just choose the hobby option. then your name and yeah, then this is the part that I wanted to show you. So here you should now actually use your newly created GitHub account because that will then make it really easy to set up the new project that is hosted on GitHub. So just sign up here and I will meet you once you're done with that. So this is what Vercel's dashboard should look like or maybe in the future again it will change but somewhere you will find a button that says add new. So here we want to add a new project and then it is as easy as selecting one git repo from this list. So here should be all of your repos. And so you can just select this one that you want and then configure it a little bit. So here the framework has automatically been figured out as Vite, right? So that's exactly what we used to build this project. And then let's take a look here at the build and output settings. So here is where we specify that build command. And so here we can see again, npm run build, which is exactly the command that we used earlier to create or bundle. So to create or production build, right? And so now, instead of having to do that manually, Vercel will do that for us each time that it detects a change in the GitHub repo. And so that's why we call this a continuous integration. So again, with this project set up, each time that we commit something new to our repo and then push it to GitHub, Vercel will automatically detect that a change has happened, will run this command and then deploy our application from the dist folder. And so here we can just leave all of these defaults and click on deploy. And so you see that it takes like one minute maybe to deploy this application to Vercel. And beautiful. So we are done. We can see our confetti raining here. And so with this, we have our project now successfully deployed to Vercel as well. So let's then continue to this project's dashboard where we can actually see the domain. And Vercel actually chose this domain based on the name of the repo. So here we already have this nicely named domain. So basically exactly the same as earlier with Netlify, but here it is .Vercel instead of .Netlify. But our project here just works in the exact same way. All right, and so if you wanted to change this URL, then you could do so right here in the settings, and then you can also change everything else that you want about the project here. So this is actually, in my opinion, the preferred way of deploying a project because it just makes it so simple to push updates to our application. Alright, and that does it for this video and for this application as well. So now we are really finished and so once again huge congratulations for making it this far and for achieving this really important milestone of having such a large and real-world application now deployed to a real production server. So make sure to share this with all your friends and family and also tell them maybe where you have learned how to build something like that. And then I see you soon in the next video in some next section.

---
