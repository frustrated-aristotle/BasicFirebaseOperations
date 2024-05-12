# Firebase Auth & Bootstrap Site Example
I have made a basic Web Site to demonstrate how to use Firebase Auth product for registeration and signing in functionalities in your sites.

# Pages

signin.html: To sign in, you should pass your credentials, mail and password, to input fields. After submitting with the Sign in button, button's text turns into a spinner and become deactivated to prevent multiple signing try at the same time, we are checking if there is a corresponding user in our Auth database with given firebase config. 
If there is, then we are directing our user to main page, index.html. But if there is not, then an alert with the error message appears to the user. Input fields will be cleared. Button gets it's original text again.

index.html: Not so much in here. I assumed you named your main page as index.html. If you were not, you should change the "index.html" with your main pages name. To do so, go to 78th line of signin.html, change index.html with your page's name. 

register.html: To register or sign up, I wanted to get email, password, name, surname and a nickname. Normally, Firebase auth only stores mail, password and user id of our users. Assuming that if there is a user, than there should be lots of data about him/her. Registering with Firebase Auth is so easy since it is done with just one built-in function : createUserWithEmailAndPassword() but it is not enough in most cases. I have created an algorithm to add values on each inputs to a collection as document with Firebase Firestore product. Now, when you are creating a new user in this page, I am creating a new document inside of the collection named "Users" in your Firestore besides creating a new user with just email and password. So, what I am doing here is connecting Auth and Firestore on User registration.

*I have used localStorage to store our user's id locally for manipulating fields that depends on each user. For example, if this app is a social media app, our user should be able to post things in this site. Assuming the proccess of posting contains adding these datas to our database. When its done correctly, we should see who has posted it. Since we learning who is using  our app with sign in or sign up via uid correspoding to the email, we should carry this info to our main page. To do so, I am setting a field called "uid" and getting it with the same name.

*Why I choosed storing uid has a straigth purpose. Dealing with email is hard but uid is not since user has nothing with it and it won't needed to be changed. When a user successfully signed up, Auth creates a new line with its email and given password. That line has a string called "uid". Basically, we are getting that uid and giving it to the ID field of new user document for easy access since reaching a document in a collection with its ID is faster, I think. Adding each input values to this document is the end of creating new user. Now, we have successfully completed connecting Auth and Firebase. I think it is a must.

# Functionalities
