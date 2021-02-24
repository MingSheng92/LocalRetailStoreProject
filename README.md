# Online Retail Store Project

# Task Deskscription
I was tasked to propose a all around digital solution to the business owner, where the main purpose of this project is to: <br />
1. Increase online footprint 
2. Increase efficiency of current workflow
3. Make an early preparation for e-commerce 
4. low maintaining cost while having reliable uptime and services

# Framework 

### Backend infrastructure 
#### Why serverless and not the traditional server approach? 
Sure, traditional method to run a server and host a website may be more straight forward, but if we calculate the total uptime of the backend server it is not sufficient for a smaller retail business to sustain itself, additional fees will occur once the budget expires. Hence we want something else that is billed only when it is used. This is where serverless platform like Netlify or Firebase comes into play.

##### Why Netlify ? 
Netlify has built in CI/CD, meaning that build and deploy is automated with Netlify once you have authorized the repository. This ensures really fast build and deploy timing and we have sites updates in minutes. Though now Firebase supports github repository build and deploy hook to be set up through firebase CLI, but Netlify still has overall cleaner UI. 

### fontend framework 

According to google analytics, 80% of the users is from Malaysia, next would be Singapore. 

![GoogleGeoAnalytics](https://github.com/MingSheng92/LocalRetailStoreProject/blob/main/proj_images/googleAnalyticsMap.JPG)

Next up, customer mainly consist of mobile users, when we look further into mobile sections, we find almost even split in both Apple and Andriod phones, that means that if we want to match our goal and fufil our customer base we need the below criteria:
1. A framework that can work with both Apple and Andriod (native app is out of scope since there will be the need the effort for continuous support and managing the app)
2. Web like feature that can be hosted on the internet where customer can have their exposure through web ranking (SEO)
3. fufil customer's requirements;
    i. moving member registration step into the clouds
    ii. create an online store like application for the customer

In early 2020, when tallking to a friend in China they mentioned that they have wechat mini program where you can have an app like program without downloading and managing it. After having some research, this is an almost perfect match with what we want to do and I began to search for an alternatives.

##### Why not just go with Wechat mini program? 
According to this [article](https://wechatwiki.com/wechat-resources/wechat-mini-program-epic-tutorial-guide/) Wechat mini program is widely used in China, such as [xiaohongshu](https://www.xiaohongshu.com/), [bilibili](https://www.bilibili.com/) and so on. But we have to think about our geographic location and our user base.Even though Wechat is already widely used in South East Asia, but it is popular within the chinese community but not so much for the others, and mini programs is not widely used in this region as compared to traditional websites and applications.

One other downside of using Wechat miniprogram is that we will need to be tied down to the Wechat ecosystems, moreover we would still need a seperate website to host our landing page online to improve footprint, which is similar to the native smart phone app situation that was mentioned earlier.

After some research I have found progressive web application, which is lying around for awhile now. It matches all our criterias where it can be hosted on the web and also allows user to download and to be used as an app. In addition, PWA supports offline browsing with caching.

For more information on PWA you can refer to these sites below:  <br />
https://web.dev/what-are-pwas/  <br />
https://web.dev/drive-business-success/  <br />
https://www.simicart.com/blog/progressive-web-apps-examples/  <br />

React was an easy choice because it was one of the supported framework on Netlify.

### Database 

Since we have now chosen serverless framework, we may not have the flexibility of using mysql in traditional server setup. So ended up using firestore for our backend storage purpose, while Netlify also has their own nosql solution (FaunaDb) but I find firestore is easier to work with.

It offers 50k read operations and 10k write operations per day which is reasonable for starters.

### UI Libraries 

As for landing page it is coded with pure CSS stylings, but I found that it is hard to keep it consistent with pure css only. 

Hence in admin and store site, we implemented the UI with Material UI, where we could store the theme color so the look and feel across the board is the same, we could also extend components to create custom components to speed up development times and align with react coding standards. 

Notistack is also used for admin panel and store application, this could provide better user experience on application presentation where we provide feedback to user based on application's state or user's action.

### Global state managing  

In development of store application, I often faced with the situation where I had to passed down information to child components for rendering purpose but with that it always comes with the infamous "prop-drilling" problem. So in order to better manage our state in our store page, we need to have some sort of architecture to manage this. For this, I picked both Context and React-Redux, we will further discussed them in later sections. 

### Image hosting 

Both firebase and Netlify supports generous image storage options but the problem with that is that business users have to learn on how to work with git which is not the thing that we want, so we went for a better approach. 

Google photos, with google photos we get to choose how to upload the image and with some workaround we can make it to work just as the same as CDNs, just losing some basic funtionalities such as image crops and dynamic size loadings.

## 

With all the basic information listed, we will now proceed to the final product proposed.

3 diffierent web applications were proposed to the business users, whereas the 3 products are all PWA enabled products.

# Landing page/Official webpage

#### https://www.mymringredient.com/
[![Netlify Status](https://api.netlify.com/api/v1/badges/9afe8b4a-b45a-499d-8196-d1b1b7d384cb/deploy-status)](https://app.netlify.com/sites/sad-perlman-0afef9/deploys)

This is a basic brand homepage where user can reach from different refferal points such as facebook, google cards and also google search. 

The landing page is fully set up with google SEO and it is rich result enabled website, where you get card like information when display in google search. 

![googleSearch](https://github.com/MingSheng92/LocalRetailStoreProject/blob/main/proj_images/google%20%20search.JPG)

Below is the guided recipe in action below: 
![jsonld](https://github.com/MingSheng92/LocalRetailStoreProject/blob/main/proj_images/richResults.JPG)

Next, we have moved our member registration workflow to the app, by submitting the form react will call netlify serverless fucntion to add an entry to google excel file, which will later be added into the POS system.

By doing this we have completely remove the manual registering process by using whatsapp or written down format compared to before. This will also eliminate any possible human error when adding a new member entry. 

The site is also google analytic and facebook pixel enabled for better advertising segmentation in the future, so that business can spend their advertising budget to the right customer segments.

images is also load with lazy functions to further optimize the website.

# Store page and admin panel 

#### https://store.mymringredient.com/ 
[![Netlify Status](https://api.netlify.com/api/v1/badges/e83ab672-ef1c-4491-817c-d818c367c9e0/deploy-status)](https://app.netlify.com/sites/admiring-pasteur-7c667a/deploys)

Admin panel will be shown only in image form as there is security concerns, so it is best to leave it out of this documentation.

Next up, is the store like page for the business user. The concept for this is for customer to check out the latest items from the store and place order for in store pick up or grab delivery to their doorsteps.

The final product is shown as below, where user can download and use as an app.

In before, business order will need to answer enquiries, accept orders all from whatsapp, which is not efficient where they will have to find all products for the customer before they can place an order. With a marketplace like app, customer can freely browse the application and place an order when they are ready, once the order is place business user will proceed to approach the user. 

This will further streamline the process as business user can look for the latest order in admin panels and answering user queries in whatsapp, where we seperated the workflow to make it clearer and more efficient.

Admin panel also servers as a store item editor, where business users can perform CRUD operations on the production product store.

### Technical Details on the products: 

Below is the rough representation on how the application works.

Frontend built with react + material ui and we have redux for state management, this allows us to seperate our frontend code with business logic. We can add UI state for theme customization later if required.

Webpage product loader function is created with createAsyncthunk to load data from firebase firestore with asynchronous functions, where react-router-dom for handling application routing. 

In order to conserve read operation counts, autocomplete searchbar has been implemented on the storepage, where the searchbar will provide match based on the online hosted JSON file to complete the search action from user, then it will load from memory if the item has already been load to DOM else it will retrive the item information from cloud to display item informations.

![Structure](https://github.com/MingSheng92/LocalRetailStoreProject/blob/main/proj_images/OnlineStoreStructure.png)

As for admin panel, we do not want anyone to access the panel so we have implemented single sign on feature with firebase, so that user will need to signin in order to view the data, only authorised user may access the webpage or else a blannk page is shown.


The application will dispatch states based on user interactions, 
for example: <br />
fetchProduct when user first open the application. <br />
fetchMore when user click to load more items <br />
addToCart when user add new items to shopping cart <br />
getCartItems when accessing cart page <br />
submitOrder when user place an order <br />

Below is an example where user placed an order from the store application, and business user will see the order in the admin panel instantly. Then he could proceed with the order and contact the customer as before.

### future work 
We have successfullly implemented a proof of concept where we implement a set of products to drive business sales. In short, we have optimized the workflow, increase online footprint of retail brand, streamlined workflow by adding new funcstions to the application.

As all the basic infrastructure has been laid down, there is a few that we could do in the future.
1. Analyse customer segmentation 
    We could do customer segmentation based on google analytics and facebook pixels gathered inforamtion, based on this we can perform the following:
    i . Place specific Ad for certain customer segment groups
    ii. Analyse custormers CTR (Clicked through rate) based on A/B test results
2. A/B test, since Netlify has integrate CI/CD, we can branch from root repository and perform live user test on UI changes.
3. Add online payment gateway, as the business progress business will need to add payment options to the application, we could add in serverless payment option such as [Stripe](https://stripe.com/en-my) or [Snipcart](https://snipcart.com/).

### Lighthouse Scores
#### Landing page Lighthouse score: 
![lighthouseScore](https://github.com/MingSheng92/LocalRetailStoreProject/blob/main/proj_images/mymringredient_Score.JPG)

#### Store application Lighthouse score 
![storelighthouseScore](https://github.com/MingSheng92/LocalRetailStoreProject/blob/main/proj_images/store.JPG)

### Webpagetest.org scores
#### Landing page Lighthouse score: 
https://www.webpagetest.org/result/210210_DiBY_42bb22002bdac21f8c9c75cda5495b48/

#### Store application Lighthouse score 
https://www.webpagetest.org/result/210210_Di05_150a509fe8d4d93cc4776196f16def66/

