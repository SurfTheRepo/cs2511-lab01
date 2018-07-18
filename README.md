# Lab 01 (Due: Week 01, Sunday, 11:59 pm)

## Aim
 * Become familiar with course practices for lab/assignment release
 * Learn how to use git and GitHub effectively
 * Learn how to create, compile and run a java program from the command-line
 * Gain familiarity with java development using Eclipse IDE
 * Introduce simple Java exercises based on topics covered in week 1 (java basics - declaring, initialising and using variables, control-flow, arrays and strings)


# Setup (Please make sure these tasks are completed prior to your lab in week 1)
## 1. Sign up for GitHub
Github is a version control platform (like Bitbucket or GitLab) that uses git. It is a great way for developers to collaborate with one another. It will be the primary source of starter code distribution as well as where you will submit labs/assignments for automarking before being marked by your tutors. You will have to create an account here before you can start. Getting familiar with Github and how to use is is the aim of this lab.

**Summary:**
 * I DON'T have an account on Github: Create an account at Github using your student (zID@student.unsw.edu.au) email.
    - **Make sure to verify your email address. If you do not get an email straight away, go to https://github.com/settings/emails and click resend**

       ![email validation](https://www.cse.unsw.edu.au/~cs2511/18s2/labs/lab01/img/email_validate.png)
 * I ALREADY have an account on Github: Continue to the next step.

## 2. CS2511 Github Organisation Membership
A Github organisation is a way that people can work together and have group ownership of repositories. You will be added to our organisation where we will release the starter code and solutions.

**Summary:**
1. Follow the link and sign in. First with your cse credentials (if the *Authentication required* alert box is shown), then click the **Sign in with Github** button and use your Github credentials https://cgi.cse.unsw.edu.au/~cs2511/github/run.cgi/login
2. Click on the **Setup** button and complete the instructions on the page (should be adding student email and registering for education pack)
3. You will have to verify your student email as well before continuing onto the student education pack. If a verification email was not sent automatically, go to https://github.com/settings/emails and click resend (as in the above image)

## 3. Add your ssh key
There are two ways to authenticate with Github when you are working on your own machine:
 1. Use your username and password everytime
 2. Authenticate using your SSH key which effectively links a certain machine to Github

Option 1 can get quite tedious when working consistently so we will be using the second option. Open up a terminal and run the following commands in terminal (use the email you have used for GitHub):

**Summary:**
 1. `ssh-keygen -t rsa -C "github_email@example.com"`
 2. Hit Enter 3 times to accept default location and skip the password creation step. (You can **ignore** the output of this command)
 3. `cat ~/.ssh/id_rsa.pub`
 4. Copy the entire output of the above command, including the *ssh-rsa* at the start
 5. Go to https://github.com/settings/keys and click **New SSH Key**
 6. Enter your name as the title and paste the key (copied in the above step) into the text field. It should look something like below
 ![enter key](https://www.cse.unsw.edu.au/~cs2511/18s2/labs/lab01/img/new_key.png)

 **NOTE:** You will have to repeat this process if you change machines.

# Week 01 Lab Instructions:

This lab must be completed and solution must be uploaded to Github by Sunday, 11:59 pm, week 01. Tutors will check the time-stamp, when the lab is marked in week02 lab session. Tasks in this lab must be completed individually.


# Task 1 - GitHub Exercises (10 marks)
## 0. Install git
Throughout the course you will need to be comfortable with git. It comes pre-installed on most linux releases and is already installed on the CSE machines. To check if git is installed on your local machine use the command
```bash
git status
```
If it is installed you will see something like
> fatal: Not a git repository (or any of the parent directories):

If you do not have git installed, you will see something like
> bash: git: command not recognized

If this is the case, you will have to set it up using the following instructions
 - **Linux** - Follow instructions at https://git-scm.com/download/linux
 - **Mac** - `brew install git`

We also have to configure the installation. Instructions on how to do this are in the summary section.

**Summary:**
1. Try `git status` to check whether git is installed
    - If not, follow one of the above instructions depending on your OS
2. Configure git if you have not used it before with the following commands (including the quotes)
```bash
git config --global user.name "Your Name"
git config --global user.email "github_email@example.com"
```

## 1. Clone your first repo
Cloning a **repo** (a repo is just a directory that is linked with git) is how the codebase is linked from GitHub to your local computer so changes you make can be saved and shared with others. It is the final step before you can start making changes and contributing. A repo can be cloned at any time by someone who has access, so they can start working whenever they want. When a repo is cloned, all code that is uploaded on the server is copied to a desired location on your local machine.

In this course, starter code will be distributed through https://cgi.cse.unsw.edu.au/~cs2511/18s2/github/run.cgi/. As labs get released, the dropdown menu will populate with starter code options. When you select one and the starter code will be imported to your local github account.

This is the process you will follow every lab to get your starter code.

**Summary:**
 1. Go to https://cgi.cse.unsw.edu.au/~cs2511/18s2/github/run.cgi/ and got to the Labs tab.
 2. Select lab01 and click **Import**
 3. Follow the link that is shown in the green banner that is flashed at the top of the screen to go to the place where the repo has been imported
 4. Click on the Clone or download button.
 ![Click the Green Button](https://www.cse.unsw.edu.au/~cs2511/18s2/labs/lab01/img/buttons.png)
 6. If the title for the dropdown box is *Clone with HTTPS* click on the Use SSH link on the right. The box should look like the below
 ![enter image description here](https://www.cse.unsw.edu.au/~cs2511/18s2/labs/lab01/img/clone.png)
 7. Copy the link in the text box
 8. Open a Terminal and navigate to the folder you want the lab to be in
 9. `git clone [link]` (Replace [link] with the copied link from above step)
 10. Type `ls` to ensure the folder has been copied correctly
 11. `cd [repo_name]` to navigate into the cloned repo
 12. Type `ls` again to see the copied files.

## 2. Make your first commit
Now that you have cloned the repo, you are ready to work on the codebase locally.

A commit is an update of the remote (on the GitHub's server) state of the repository. It saves changes that you have made and can be given a message to describe those changes. A good use of git involves a lot of commits with detailed messages.

Before you can commit, you have to do what is called staging your changes, which effectively tells git what changes you actually want to commit and what changes you don't at the moment.

Commits are often followed by pushing which is how git actually uploads your commits to the remote server.

The command to commit and push are as follows:
```bash
git add [files_to_commit] # Stage
git commit -m"Detailed message describing the changes" # Commit
git push # Push
```
**Summary:**
1. Add a new file called `HelloWorld.java` in the repo directory
2. Add the following lines of code to the file using your favourite text editor and save.

```java
class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Welcome to COMP2511!");
    }
}
```
3. Go back to your terminal and enter the following commands:
```bash
git add HelloWorld.java
git commit -m "Created first java program HelloWorld.java"
git push
```
4. **MAKE SURE YOU UNDERSTAND THE PURPOSE OF EACH OF THE 3 ABOVE COMMANDS!** If you are unsure about any of them, ask your tutor.
5. Go back to GitHub and confirm that your changes have been pushed to the server.

## 3. Do your first pull
Usually when you are using git, it is in a team. That means that you will not be the only one who is making the changes. If someone else makes a change and pushes it to the server, your local repo will not have the most up to date version of the files. Luckily, git makes it easy to update our local copy with the `git pull` command.

This command checks the remote server that your local repo is linked to and makes sure that all of your files are up to date. This ensures that you don't accidentally do things like implement the same thing someone else has already done and also lets you use other people's work (e.g. new functions) when developing.

Pulling regularly is one of the **most important** practices in git!

Unfortunately, at the moment you are just working individually. But GitHub still gives us a nice way to practice a `git pull`.

**Summary:**
1. View your repo on GitHub. (The same link as step 1 in section 1 of the Laboratory activities)
2. Click on the HelloWorld.java file
3. Click the small ‘edit’ pencil icon in the top right
4. Add a Java comment to the top of the file as shown below and click the ‘Commit Changes’ button at the bottom of the screen
```java
// A simple Java Program
```
5. This will have changed the HelloWorld.java file on the server but not on your local environment. To fetch these changes use the git pull command from your terminal
6. Confirm that your version of HelloWorld.java now has the changes you made on the web page


## 4. Create your first branch
**Branches** are a vital part of git and are used so people can work on separate parts of the codebase and not interfere with one another or risk breaking a product that is visible to the client. Breaking something on one branch does not have an impact on any other.

Good use of git will involve separating parts of the project that can be worked on separately and having them in their own feature branch. These branches can then be merged when they are ready.

Useful commands for branches:
```bash
git checkout -b [new_branch_name] # Create a new branch and switch to it
git branch                        # List all current branches
git checkout [branch_name]        # Switch to an existing branch
```

**Summary:**
1. Make your new branch with: `git checkout -b first_new_branch`
2. List your branches to see that you have indeed swapped (use the above commands)
3. Open the `HelloWorld.java` file and change the comment at the top of the file to Javadoc style comment as shown below:
```java
/**
 * A simple java program that prints a hello world message to the console
 *
 */
```
4. Try to push your changes to the server using the commands you learnt in the *Make your first* commit section
5. The above step should have given you the following error:
> fatal: The current branch first_new_branch has no upstream branch.
This means that the branch you tried to make a change on doesn’t exist on the server yet which makes sense because we only created it on our local machine.
6. To fix this, we need to add a copy of our branch on the server and link them up so git knows that this new branch maps to a corresponding branch on the server
> git push -u origin first_new_branch


**Note:** The final step above must be run on the 1st push to every new branch that you have created on your local machine. After you have run this once, you should go back to simply using git push

## 5. Merge your two branches
Merging branches is used to combine the work done on two different branches and is where gits magic really comes in. Git will compare the changes done on both branches and decide (based on what changes were done to what sections of the file and when) what to keep. Merges are most often done when a feature branch is complete and ready to be integrated with the master branch.

Since we have finished all that we are going to do (and think there are no bugs) on our *first_new_branch* we can merge it back into master. It is a strong recommendation to have a version of the code that at least runs on master so people are not completely blocked. (DO NOT PUSH BROKEN CODE TO MASTER)

Another recommendation is to merge master into your branch before merging your branch into master as this will ensure that any merge into master will go smoothly.

**Commands for merging two branches**
```bash
git merge [target] # Merge the target branch into current
```
**Note:** A successful merge automatically uses the commits from the source branch. This means that the commits have already been made, you just need to push these to the server (`git push`)

**Summary:**
1. Switch back to the master branch using one of the commands fom the above section
2. Merge in the changes you made in the other branch
`git merge first_new_branch`
3. Push the successful merge to the server to update the master branch on the server

## 6. Engineer a merge conflict
Merge conflicts are the one necessary downside to git. Luckily, they can be avoided most of the time through good use of techniques like branches and regular commits, pushes and pulls. They happen when git cannot work out which particular change to a file you really want.

For this step we will engineer one so you can get a taste of what they are, how they occur and how to fix them. This will be the LAST time you will want one. The process may seem involved but it is quite common when multiple people are working at a time.

**Summary:** (All commands have been presented above)
1. Change line 3 of `HelloWorld.java` to
```java
System.out.println("Hello, Welcome to Java!");
```
2. Add, commit and push your changes
3. Switch to your *first_new_branch*
4. Change line 3 of `HelloWorld.java`
```java
System.out.println("Hello, Welcome to merge conflicts!");
```
5. Add, commit and push your changes
6. Merge master into your current branch
7. This sequence of steps should make a merge conflict at the third line of `HelloWorld.java`

## 7. Resolve your merge conflict
Resolving a merge conflict is as simple as editing the file normally, choosing what you want to have in the places git wasn't sure.

This is a very simple example, but merge conflicts can be large and in many different places across a file/repo. If possible, avoid merge conflicts. This can be done by regularly pulling from the server to update your local copy and by making your branches in such a way that they handle only one feature/section of the code.

A merge conflict is physically shown in the file in which it occurs.
`<<<<<<<` marks the beginning of the conflicting changes made on the **current** (merged into) branch.
`=======` marks the beginning of the conflicting changes made on the **target** (merged) branch.
`>>>>>>>` marks the end of the conflict zone.

E.g.
```
This line could be merged automatically.
There was no change here either
<<<<<<< current:sample.txt
Merges are too hard. This change was on the 'merged into' branch
=======
Merges are easy. This change was made on the 'merged' branch
>>>>>>> target:sample.txt
This is another line that could be merged automatically
```

This above example could be solved in many ways, one way would be to just use the changes made on the target branch and delete those made on the current branch. Once we have decided on this we just need to remove the syntax. The resolved file would be as follows

```
This line could be merged automatically.
There was no change here either
Merges are easy. This change was made on the 'merged' branch
This is another line that could be merged automatically
```

We would then just commit the resolved file and the merge conflict is finished!

**Summary:**
1. Open the `HelloWorld.java` file and decide which change you want to keep
2. Remove the merge conflict syntax
3. Add, commit and push the resolved merge conflict
## Testing
You can run the `test_git.sh` file to check whether you have done most of the git exercises. Make sure you checkout the master branch before running this script.

# Task 02 - Java Introduction (5 marks)

Create a new branch called `java_exercises` to complete the following exercises. Remember to merge back into master when you are finished.

## 1. Compiling and running your first Java program at the command line
* At the terminal, to compile your java program HelloWorld.java invoke the Java compiler as follows: `javac HelloWorld.java`
* Once, your program has compiled successfully into Java bytecode, you should be able to see a file `HelloWorld.class` Next, to interpret and run the java program, invoke the Java VM byte code interpreter as follows:
`java HelloWorld`
* At the terminal, you should be able to see:
`Hello, Welcome to Java!` or `Hello, Welcome to merge conflicts!`

## 2. Setting up Eclipse on Lab Machines and importing the HelloWorld.java (1 mark)
From a terminal, execute **eclipse**: this should start up a version of eclipse in a new window – make sure it is Eclipse 4.7.2 Oxygen
* Follow the prompts, and set up a workspace directory for eclipse in your home (or sub-) directory
* Follow any recommended instructions concerning the Scala IDE plugin
* If you see a welcome screen, close it to reveal a Java perspective
  - If (instead) you see a Java EE perspective, open a Java perspective (click the Open Perspective button just to the left of the Java EE button and choose Java from the list), then close the Java EE perspective (right click on it and select Close)
* Make sure Java SE 8 is the default execution environment: check this via Window > Preferences > Java > Installed JREs
  - The JRE should be called java-8-openjdk-i386; if it is not there, add the JRE which should be located at `/usr/lib/jvm/java-8-openjdk-i386`
* Create a new Java project (via **New** > **Java Project** or using the **New** button drop-down): choose the default JRE for the execution environment and specify `HelloWorld` as the Project Name.  Click on the **Finish** button.
  - Eclipse should be set up to automatically (re-)compile your projects when editing (check via the Project menu that Build Automatically is ticked): saves time!
* In the Package Explorer (panel on the left), locate the HelloWorld project and click on it.  You should see a folder named **src**.  Right click on **src** folder and choose **Import**.  An Import Wizard is launched.  Choose **General** > **FileSystem** and click on **Next**.  Click on **Browse**: locate the folder under which the file `HelloWorld.java` (from the previous task) was created and select the file HelloWorld.java.  Now, click on the Finish button.  This file has now been imported into the eclipse project.
* Run this programs in Eclipse via **Run** > **Run As ...** > **Java Application** or hit the Play button after setting up a Run Configuration
* Look at the **Console** to see the output (or at the **Problems** tab for any bugs)

## 3. Calculate the average of an array of numbers (4 marks)
A class is similar to a struct in the C language in that it stores related data in fields, where the fields can be different types.
1. Open the file `Average.java`. You will find a class named Average.
2. This class defines a method `computeAverage()` that takes in an array of integers and returns the average of this numbers.  You are required to implement this method.
  Hint:
   * To complete this task, you need to compute the sum of the numbers and the total number of elements
   * Use a `for` loop to traverse the list of numbers and compute the sum of the number.
   * Use `nums.length` to get the length of the array, after the sum has been computed.
3. Next, define a `main()` method.

    Note: Every Java application needs one class with a `main()` method. This class is the entry point for the Java application and is the class name passed to the `java`  command to run the application. The interpreter executes the code in the `main()` method when the program starts, and is the point from which all other classes and corresponding methods are invoked.

4. Inside the `main()` method, initialise an array of integers inside the `main()` method and invoke the method `computeAverage()`, passing in the array of integers
Hint: `computeAverage()` is an instance method, hence you must create an instance of the class Average and invoke the method on this instance
5. Assign the result of this method to a variable and print the variable


# Show your tutor and finish
That's it for the first lab, please show your tutor your work and get them to mark you off.

# Optional Exercises for Bonus (1 mark)

Create a java program that reads from `System.in` a line consisting of words separated by a space and prints out the individual words in the string e.g.,

If the input was: `The Mocking Jay`
The output should display as:
```
The
Mocking
Jay
```

**Hint:**  Use the string function ‘split’ to help you with this task
