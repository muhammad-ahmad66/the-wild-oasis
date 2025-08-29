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

03:57
And if we then go ahead and change one of them, then  here the color should change.

04:04
So let's delete this. And indeed, then we get here  M for modified. But let's put it back. And so then that will go away. And so then what we can do  is to basically save a snapshot of the current state of the repository. And that is what we call a commit. So Git is all about committing. And so let's now  use this very important command. So many times we actually use git add.

04:34
and git commit right one after the other. So we add everything and then we commit it to the repository. So git commit then dash  m for the uh commit message. And then here in the beginning, we usually write initial commit.

04:58
Okay, and so this then basically clears  all of our working tree because these files are now safely committed inside our Git repository. And again, if we then changed something here in one of them, then that color would change here again. So now that's modified again. And so if we then check Git status again, here we can see that this one has been modified.

05:27
And so if we wanted, we could then add this file again and commit again.

05:34
But in this case, let's again just put it back. And now if we want to basically upload this to some remote repository, then we need to create an account on a service like GitHub or GitLab. And GitHub  is by far the most popular one. And so let's go there. So github.com. And then once again, you need to sign in for your own account right here.  Or actually right here.

06:04
And once you're done doing that, I will meet you back here. So,  once you're done creating your account and verifying your email, which is very important for this to work, let's create ourselves a new repository by clicking here on this plus, then here, or you can also just click here.

06:27
So then you need to give it a name. Let's say the wild oasis. And here you can actually use the same one because they are scoped to your own  username, basically. And then you can choose to make it public or private, which I will do private. And then here, don't do any of this. So no read me, no git ignore, and no license. And then let's create this repository.

06:58
So this is our new and for now empty repository. Now here are some instructions to how to connect this remote repository. So this repository that we have here, which is living here in the cloud essentially with the local repository that we created earlier on your computer. Now before we can actually do that connection, let's quickly set up something called an access token.

07:27
So that's a token that you will use instead of a password when you want to connect these two repositories. So let's come here to your avatar and go to the settings. And then all the way down here, we go to developer settings. And if this here has changed in the meantime, then you can just Google for how to access or how to create GitHub personal access tokens. So here then

07:57
select one of these two. I will just go with the classic ones. And then here, just generate new token. And again, I think you can choose both of them. Then here, you give it a name. I will just call it test. Then here, you can select for how long you want this token to be valid. So you can choose no expiration, but that is not the most secure option. So let's leave it at 30.

08:25
And so then every 30 days you will have to create a new one. And then here you will have to select this repo option so that with this token you can get complete access and complete control over repositories. Now these stuff here I think we don't need. And so then let's click on generate token, which I'm not going to do because I don't need it. Or well, maybe I will.

08:54
So let's generate this token. of course, will,  after this video is finished, delete it immediately. But what you need to do now is to copy this and store it somewhere safe. So as it says here, you won't be able to see it again, because this here is now basically just like a password. So you need to treat this as a password. And again, you will need this to connect the remote repo with your local repo.

09:24
And actually, let's now go back to our terminal in VS Code and do that. So that's git remote  add. And then we call this new branch here an origin.

09:41
And then here we need the URL of that Git repository. So make sure you copy this.  And then let's come to our repositories.

09:54
And so this is the one that we just created. So here we need to copy this part.  We could also just have copied all of this.

10:06
So then let's add that here and then hit enter. And so now with this, your local repository knows about this remote repository, which again we called here origin. And so now to get all our code from this repository into this remote one on GitHub, we just use the command git push. Then we need the dash u.

10:35
for upstream and then the name of the remote one. So origin and then the name of our current branch or of the branch that we want to push to that remote branch. And so that name of the branch is main as we can see here, which in your case will not show up here, but you can probably also see it here. Or also if you uh use the command of git status, but

11:05
Anyway, this is the command that you will need by default. So git push dash u origin main. And now here, git will probably ask you for your credentials. So that's going to be your GitHub email address and that access token that we created earlier. So that's what you're going to use instead of a password. So that token is going to be necessary each time that you push your code to

11:34
the remote branch. And so each time you did this, probably asked for your credentials. Now here in my case, it didn't ask me because I stored those  right inside of Git. But here, let's keep it simple. So you can just give it your email and your access token as a password each time that it asks for it. But anyway, in the meantime,  as we can see here, all our files have actually been uploaded

12:03
to our remote GitHub repository. Now, Now, if we reload this, we should see everything here. And indeed, there it is. Great. So here we have also the readme.md, which is giving us basically some overview over what this repository is. And so that's why each repo should have a readme like this.  So here we have the name of our latest commit.

12:33
and also  when it was done. Then here we can just explore our code base  as we wish. So here is all the code that we have written. Here we even have this nice tree. And yeah, now your code  is basically safely stored in here. Now, maybe you're wondering why we only have the source and the public folder. If here in our VS Code we actually have also node modules

13:02
and the dist folder. Well, the reason for that  is that Veed gave us this git ignore file. And so this git ignore contains all kinds of files and folders that will be ignored by git. So those are files that will not be committed into the git repository. And so that includes the node modules folder and also the dist folder. And the reason for the dist folder is

13:31
that this is a folder that we can very easily just recompute. And so really only the source code itself should be committed into the repository.

13:43
All right. Now here, let's just change something just so we can see the workflow of using Git in action. So let's say we say build with React query and  super base. So then we modified this file, which again is visible here in this yellow color and the modified part. And indeed, if we do Git status, then here we can see the same

14:13
And we can see that we are on the main branch.

14:18
So now let's commit this to a repo. And for that, we first need to add it to the staging area, which are all the files that will later be committed, because we might not want to commit all of the files that we changed and only some of them. And therefore, that's why first we have to place the files in this staging area. So git add. And so here we could even just add some of them. So just like readme.md,

14:49
But usually what I like to do when I'm working on my own is to just add all the files. And so then after that, we can immediately commit. So git commit-m and then or commit message. And so usually the message here is written like a command. So update, read me. So not updated, but update. So that's committed. And then finally,

15:18
Let's push it also to our remote repo. So git push-u origin main. So let's wait for it. And if we now reload, then we will see that our latest commit  is now update readme. And so all of these have been made 15 minutes ago, but this one was right now. And so then here we have indeed that updated file.

15:49
And so this is in a nutshell how you use Git and GitHub in the easiest way possible. So we can do really a lot of very complex and very complicated stuff, but these  are the bare essentials. And so with this, I think we finished and can now move on to the next lecture where we actually use this GitHub repo to deploy your application.

---

## `Deploying to Vercel`

So now let's use our GitHub repo that we just created to set up a very simple continuous integration on Vercel, which is another very popular free, at least for small projects and also very easy to use hosting provider for React applications. But first of all, we could actually also set up a continuous integration here on Netlify. So for that, we would again add a new site and then here, this time we would select import an existing project. And so then here it says exactly what I mentioned in the beginning. So basically importing an existing project from a Git repo. And so then here you would connect your GitHub account and then just follow these steps. So if you want, you can do this here on Netlify. That's very easy as well, but I just want to show you another alternative. And so that is... So this is actually the company that created the Next.js framework. And so they are specialized on hosting Next.js applications, but we can of course also very easily host basically vanilla React applications here. So you can just sign up for a new account and then, well, here you just choose the hobby option. then your name and yeah, then this is the part that I wanted to show you. So here you should now actually use your newly created GitHub account because that will then make it really easy to set up the new project that is hosted on GitHub. So just sign up here and I will meet you once you're done with that. So this is what Vercel's dashboard should look like or maybe in the future again it will change but somewhere you will find a button that says add new. So here we want to add a new project and then it is as easy as selecting one git repo from this list. So here should be all of your repos. And so you can just select this one that you want and then configure it a little bit. So here the framework has automatically been figured out as Vite, right? So that's exactly what we used to build this project. And then let's take a look here at the build and output settings. So here is where we specify that build command. And so here we can see again, npm run build, which is exactly the command that we used earlier to create or bundle. So to create or production build, right? And so now, instead of having to do that manually, Vercel will do that for us each time that it detects a change in the GitHub repo. And so that's why we call this a continuous integration. So again, with this project set up, each time that we commit something new to our repo and then push it to GitHub, Vercel will automatically detect that a change has happened, will run this command and then deploy our application from the dist folder. And so here we can just leave all of these defaults and click on deploy. And so you see that it takes like one minute maybe to deploy this application to Vercel. And beautiful. So we are done. We can see our confetti raining here. And so with this, we have our project now successfully deployed to Vercel as well. So let's then continue to this project's dashboard where we can actually see the domain. And Vercel actually chose this domain based on the name of the repo. So here we already have this nicely named domain. So basically exactly the same as earlier with Netlify, but here it is .Vercel instead of .Netlify. But our project here just works in the exact same way. All right, and so if you wanted to change this URL, then you could do so right here in the settings, and then you can also change everything else that you want about the project here. So this is actually, in my opinion, the preferred way of deploying a project because it just makes it so simple to push updates to our application. Alright, and that does it for this video and for this application as well. So now we are really finished and so once again huge congratulations for making it this far and for achieving this really important milestone of having such a large and real-world application now deployed to a real production server. So make sure to share this with all your friends and family and also tell them maybe where you have learned how to build something like that. And then I see you soon in the next video in some next section.

---
