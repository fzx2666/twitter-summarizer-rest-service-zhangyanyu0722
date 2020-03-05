# Twitter Summarizer Based on Flask and Restful
## Step 1: Learn Flask and RESTful as WEB service platform
### Flask
- Run hello.py in FLASK_APP
```env FLASK_APP=hello.py flask run```
- Open the HostLocal, like ```http://127.0.0.1:5000/```
- Or run it in Postman

- Reference 1: [Flask] ([Github])
- Reference 2: [Flask-RESTFUL] ([Github.])
## Step 2: Integrate module to become a RESTFUL system
- First, connect to the AWS API, replace the token(****.pem) to yours.
```
scp -i /directory/to/abc.pem /your/local/file/to/copy user@ec2-xx-xx-xxx-xxx.compute-1.amazonaws.com:path/to/file
```
For example:
```
ssh -i zhangyanyu.pem ec2-user@ec2-52-87-190-21.compute-1.amazonaws.com
```
When you succeed, you can see the following feedback in the terminal.
<p align="center">
  <img src= "https://github.com/BUEC500C1/twitter-summarizer-rest-service-zhangyanyu0722/blob/master/img/1.png" width=200>
</p>
  
- Second, enter the twitter_summarizer under the /home
```
cd twitter_summarizer
```
- Third, enable the flask_rest:
```
python3 flask_rest.py
```
Now we have entered the RESTful ststem
<p align="center">
  <img src= "https://github.com/BUEC500C1/twitter-summarizer-rest-service-zhangyanyu0722/blob/master/img/2.png">
</p>

- Now in order to download the videos, we need to open another terminal, and also connect to the AWS API 
```
ssh -i zhangyanyu.pem ec2-user@ec2-52-87-190-21.compute-1.amazonaws.com
```
```
cd twitter_summarizer
```
- The last step is to download all the videos based on the keywords you input. For example, we want to make two summarizer for  'BU_ece' and 'BU_Tweets'
```
python download.py BU_ece BU_Tweets
```
- Wait for 10 seconds, when you see the following line shown in the terminal.
<p align="center">
  <img src= "https://github.com/BUEC500C1/twitter-summarizer-rest-service-zhangyanyu0722/blob/master/img/3.png">
</p>
- Now you can download the videos using the following command in a new termianl.

```
scp -i /directory/to/abc.pem user@ec2-xx-xx-xxx-xxx.compute-1.amazonaws.com:path/to/file /your/local/directory/files/to/download
```
For example: 
```
scp -i Desktop/zhangyanyu.pem ec2-user@ec2-52-87-190-21.compute-1.amazonaws.com:/home/ec2-user/twitter_summarizer/BU_ece.avi Desktop/
```
<p align="center">
  <img src= "https://github.com/BUEC500C1/twitter-summarizer-rest-service-zhangyanyu0722/blob/master/img/4.png">
</p>
<p align="center">
  <img src= "https://github.com/BUEC500C1/twitter-summarizer-rest-service-zhangyanyu0722/blob/master/img/5.png">
</p>
  







[Flask]: https://palletsprojects.com/p/flask/
[Github]: https://github.com/pallets/flask
[Flask-RESTFUL]: https://flask-restful.readthedocs.io/en/latest/
[Github.]: https://github.com/flask-restful/flask-restful
[AWS Services]: https://aws.amazon.com/free/?all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc
