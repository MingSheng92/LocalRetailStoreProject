# Move to cloud 
Documentation on the project.

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

Next up, customer mainly consist of mobile users as shown in the graph below:

But when we look further into mobile sections, we find almost even split in both Apple and Andriod phones, that means that if we want to match our goal and fufil our customer base we need the below criteria:
1. A framework that can work with both Apple and Andriod (native app is out of scope since there will be the need the effort for continuous support and managing the app)
2. Web like feature that can be hosted on the internet where customer can have their exposure through web ranking (SEO)
3. fufil customer's requirements;
    i. moving member registration step into the clouds
    ii. create an online store like application for the customer

In early 2020, when tallking to a freidn in China they mentioned that they have wechat mini program where you can have an app like program without downloading and managing it. After having some research, this is an almost perfect match with what we want to do and I began to search for an alternatives.

##### Why not just go with Wechat mini program? 
According to this article[1] Wechat mini program is widely used in China, such as xhs[2], bilibili[3] and so on. But we have to think about our geographic location and our user base.Even though Wechat is already widely used in South East Asia, but it is popular within the chinese community but not so much for the others, and mini programs is not widely used in this region as compared to traditional websites and applications.

One other downside of using Wechat miniprogram is that we will need to be tied down to the Wechat ecosystems, moreover we would still need a seperate website to host our landing page online to improve footprint, which is similar to the native smart phone app situation that was mentioned earlier.

After some research I have found progressive web application, which is lying around for awhile now. It matches all our criterias where it can be hosted on the web and also allows user to download and to be used as an app. In addition, PWA supports offline browsing with caching.

For more information on PWA you can refer to these sites below:  <br />
https://web.dev/what-are-pwas/  <br />
https://web.dev/drive-business-success/  <br />
https://www.simicart.com/blog/progressive-web-apps-examples/  <br />

React was an easy choice because it was one of the supported framework on Netlify and most of the companies uses React framework. <br />
Facebook, Uber, foodpanda, Instagram, reddit and so on.  <br />

### Database 

Since we have now chosen serverless framework, we may not have the flexibility of using mysql in traditional server setup. So ended up using firestore for our backend storage purpose, while Netlify also has their own nosql solution (FaunaDb) but I find firestore is easier to work with.

It offers 50k read operations and 10k write operations per day which is reasonable for starters.

### UI Libraries 



### Global state managing  

In development of store application, I often faced with the situation where I had to passed down information to child components for rendering purpose but with that it always comes with the infamous "prop-drilling" problem. So in order to better manage our state in our store page, we need to have some sort of architecture to manage this. For this, I picked both Context and React-Redux, we will further discussed them in later sections. 

### Image hosting 

Both firebase and Netlify supports generous image storage options but the problem with that is that business users have to learn on how to work with git which is not the thing that we want, so we went for a better approach. 

Google photos, with google photos we get to choose how to upload the image and with some workaround we can make it to work just as the same as CDNs, just losing some basic funtionalities such as image crops and dynamic size loadings.

## 

With all the basic information listed, we will now proceed to the final product proposed.

3 diffierent web applications were proposed to the business users, whereas the 3 products are all PWA enabled products.

### Landing page/Official webpage

#### https://www.mymringredient.com/
This is a basic brand homepage where user can reach from different refferal points such as facebook, google cards and also google search. 

The landing page is fully set up with google SEO as shown below and it is rich result enabled website, where you get card like information when display in google search. 

Below is the guided recipe in action below: 

Next, we have moved our member registration workflow to the app, by submitting the form react will call netlify serverless fucntion to add an entry to google excel file, which will later be added into the POS system.

By doing this we have completely remove the manual registering process by using whatsapp or written down format compared to before. This will also eliminate any possible human error when adding a new member entry. 

The site is also google analytic and facebook pixel enabled for better advertising segmentation in the future, so that business can spend their advertising budget to the right customer segments.

images is also load with lazy functions to further optimize the website.

#### https://store.mymringredient.com/ and admin panel 

Admin panel will be shown only in image form as there is security concerns, so it is best to leave it out of this documentation.

Next up, is the store like page for the business user. The concept for this is for customer to check out the latest items from the store and place order for in store pick up or grab delivery to their doorsteps.

The final product is shown as below, where user can download and use as an app.

In before, business order will need to answer enquiries, accept orders all from whatsapp, which is not efficient where they will have to find all products for the customer before they can place an order. With a marketplace like app, customer can freely browse the application and place an order when they are ready, once the order is place business user will proceed to approach the user. 

This will further streamline the process as business user can look for the latest order in admin panels and answering user queries in whatsapp, where we seperated the workflow to make it clearer and more efficient.

Admin panel also servers as a store item editor, where business users can perform CRUD operations on the production product store.



https://wechatwiki.com/wechat-resources/wechat-mini-program-epic-tutorial-guide/
https://www.xiaohongshu.com/
https://www.bilibili.com/
