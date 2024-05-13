# Firebase Auth & Bootstrap Site Example
I have made a basic Web Site to demonstrate how to use Firebase Auth product for registeration and signing in functionalities in your sites.

# Prerequisites
To use this web app correctly, you should have an app on Firebase that has Auth and Firestore products created.

# How to Use
This project is so straigthforward. Just clone it or download it to your workspace directly.

Sign in page is: signin.html
Register page is: register.html
Main page is: index.html

# Details that You Won't Care
Both of our sign in and register pages use the same css file since they need the same look. 
Main page is empty now. Y
# Pages

### signin.html
To sign in, you should pass your credentials, mail and password, into the input fields. After submitting with the Sign In button, the button's text turns into a spinner and become deactivated to prevent multiple sign in attempts at the same time where we are checking if there is a corresponding user in our Auth database with given firebase config. 
If there is, then we are redirect our user the main page, index.html. But if there is not, then the user will see an alert with an error message. Input fields are cleared. The button gets it's original text back.

### index.html
Not so much here. I assumed you named your main page as index.html. If not, you should replace "index.html" with the name of your main page. To do this, go to the 78th line of signin.html and replace index.html with the name of your page. 

### register.html
To register or sign up, I wanted to get the user's email, password, first name, surname and a nickname. Normally, Firebase auth only stores the email, password and user id of our users. Assuming that if there is a user, then there should be lots of data about him/her. Registering with Firebase Auth is so easy since it is done with just one built-in function : createUserWithEmailAndPassword() but it is not enough in most cases. I have created an algorithm to add values on each inputs to a collection as a document with Firebase Firestore product. Now, when you are creating a new user in this page, I am creating a new document inside of the collection named "Users" in your Firestore besides creating a new user with just email and password. So, what I am doing here is connecting Auth and Firestore on User registration.


*I used localStorage to store our user's id locally for manipulating fields that depend on each user. For example, if this app is a social media app, our user should be able to post things to this site. Suppose the posting process involves adding this data to our database. If done correctly, we should be able to see who posted it. Since we can find out who is using our application by logging in or by using the uid corresponding to the email, we should add this information to our main page. To do this, I set up a field called "uid" and get it with the same name.

**Why I chose to store the uid has a straightforward purpose. Dealing with email is hard, but uid is not, since the user has nothing to do with it and it doesn't need to be changed. When a user successfully logs in, Auth creates a new line with their email and password. This line has a string called "uid". Basically, we get that uid and pass it to the ID field of the new user's document for easy access, since accessing a document in a collection by its ID is faster, I think. Adding any input values to this document is the end of creating the new user. Now we have successfully connected Auth and Firebase. I think it is a must.

