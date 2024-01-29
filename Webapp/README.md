# phishing-email-detector
<img src="https://github.com/conan-nhat-nguyen/phishing-email-detector/blob/main/logo.png" width="100" height="100">

## This is our TAMUhack X application and chrome-extension for detecting phishing emails.
## Date: January 28th, 2024 CST
## Location: Texas A&M - Memorial Student Center

___

## Table of Contents
### [1. The Attacker's Mindset. ](#section-1)
### [2. Our Prevention Solution.](#section-2)
### [3. The Future of Our Solution.](#section-3)
### [4. Sandia's Step-by-Step Approach to deploy our idea in action.](#section-4)

___

## <a name="section-1">1. The Attacker's Mindset. </a>
We try to think as an attacker. Here is our scenario of the a phishing attacker who web scrape personally identifiable information (PII) of users from Linkedin in addition with the highly valuable personal information scraped from their social media profiles (such as, Facebook) to prompt large language model (LLM) (in this case, ChatGPT) to draft emails to potential victims to ask them to send sensitive personal information (e.g. credit card information) to fake AI-generated emails.

An example:
Anonymous Attacker has looked through Quoc (Giza) Nguyen Linkedin profile and has chosen him to be the next victim. Through pasting the victim's Linkedin profile into ChatGPT, Anonymous Attacker has found:

~~~
1. Name: Quoc (Giza) Nguyen

2. List of skills:
Salesforce.com
Microsoft Excel
Automation
Debugging
Problem Solving

3. List of companies Quoc has worked for:
Xtreme Lashes by Jo Mousselli
Rockwell Career Center
International University - VNU HCMC

4. Quoc's extracurricular activities:
Salesforce Workshops
MISSO Technology Officer
Database Education Officer
Data Administrator & Airtable Specialist
ConocoPhillips Innovation Challenge

~~~

From these information, Anonymous Attacker would put it into ChatGPT using the following prompt:
~~~
"List the top 5 companies that Quoc is most likely to apply for."
~~~


From ChatGPT: 

~~~
"Certainly, here is a list of five types of companies or industries where Quoc Giza Nguyen might be most likely to apply:
Salesforce Consulting Firms
Technology Companies with a Focus on AI and Machine Learning
Cloud Computing Providers (e.g., AWS, Microsoft Azure, Google Cloud)
Companies in the Beauty and Cosmetics Industry
Consulting Firms Specializing in Business Process Optimization"
~~~

From that, Anonymous Attacker would use Salesforce Consulting Firms to send a phishing email to Quoc. Through webscraping, the attacker may find the name of a hiring manager at Salesforce on Linkedin:
~~~
Name: Robert Edson
Location: Dallas-Fort Worth Metroplex.
~~~

Through a simple Google search, Robert Edson's email and phone number are available online in one of the open-source intelligence websites (e.g. RocketReach)

Thus, Anonymous Attacker found: 
~~~
Email: ending in @salesforce.com
Phone Number: starting at:
913485XXXX
503409XXXX 
913488XXXX 
713485XXXX 
617619XXXX
~~~

The Anonymous Attacker could sign up to one of the open-source intelligence agencies to get the rest of the four digits. However, this may not be necessary. Why? Yes, ChatGPT.
The Anonymous Attacker continues to prompt ChatGPT:
~~~
"Generate 5 emails ending in '@salesforce.com' using the following information:
Name: Robert Edson
Location: Dallas-Fort Worth Metroplex.
Also, generate a list of 5 randomly-generated phone numbers from this:
913485XXXX
503409XXXX 
913488XXXX 
713485XXXX 
617619XXXX"
~~~

Here is ChatGPT's response:

~~~
Certainly, here are five email addresses ending in '@salesforce.com' for Robert Edson based in the Dallas-Fort Worth Metroplex:
robert.edson@salesforce.com
r.edson@salesforce.com
robert.edsonTX@salesforce.com
redson@salesforce.com
robert.edsonDFW@salesforce.com
And here is a list of five randomly-generated phone numbers:
9134851234
5034095678
9134887890
7134852345
6176198765
~~~

The Anonymous Attacker then decided to use the top result as the "fake" email and phone number for phishing purposes:
~~~
robert.edson@salesforce.com 
9134851234
~~~

However, here is the catch! To make the phishing more trusting, the attackers may check if the emails and phone numbers have been used by simply putting them into the websites such as:
~~~
https://email-checker.net/check
~~~
![Email Checker](https://github.com/conan-nhat-nguyen/phishing-email-detector/blob/main/email-checker.png)
~~~
https://www.numlookup.com/report
~~~
![Robert Edson Contact Info](https://github.com/conan-nhat-nguyen/phishing-email-detector/blob/main/robert-edson-contact-info.png)


Good! If the Anonymous Attacker wants to be extra-trustworthy, the Anonymous Attacker may make that account robert.edson@salesforce.com and/or may make the phone number 9134851234 to contact the potential victim. 

Finally, the Anonymous Attacker assembles all of the publicly scraped information from Linkedin and the internet to prompt ChatGPT
~~~
"You are the recruiter with the following information:

From: Recruiter
Name: Robert Edson
Location: Dallas-Fort Worth Metroplex. 
Email: robert.edson@salesforce.com 
Phone Number: 1(913) 485-1234

To: Candidate
1. Name: Quoc (Giza) Nguyen
2. List of skills:
Salesforce.com
Microsoft Excel
Automation
Debugging
Problem Solving
3. List of companies Quoc has worked for:
Xtreme Lashes by Jo Mousselli
Rockwell Career Center
International University - VNU HCMC
4. Quoc's extracurricular activities:
Salesforce Workshops
MISSO Technology Officer
Database Education Officer
Data Administrator & Airtable Specialist
ConocoPhillips Innovation Challenge

Write an email in 500 words to invite this candidate to click on the official website of salesforce and on a generated url for scheduling an appointment for the interview.
Make it appealing for candidate"
~~~


Here is what ChatGPT gives us back:
~~~
"Subject: Exclusive Invitation for an Exciting Opportunity at Salesforce!

Dear Quoc (Giza) Nguyen,

I hope this message finds you in great spirits. My name is Robert Edson, and I am a recruiter at Salesforce, currently based in the dynamic Dallas-Fort Worth Metroplex. I came across your impressive profile and couldn't help but be intrigued by your extensive skill set and valuable experiences.

Your proficiency in Salesforce.com, Microsoft Excel, and your adeptness in automation, debugging, and problem-solving caught our attention. It's clear that your journey with Xtreme Lashes by Jo Mousselli, the Rockwell Career Center, and International University - VNU HCMC has equipped you with a diverse range of skills and experiences. Your extracurricular activities, such as leading Salesforce workshops and serving as the MISSO Technology Officer and Database Education Officer, demonstrate your commitment to continuous learning and innovation.

At Salesforce, we are constantly on the lookout for talented individuals like yourself who bring a unique blend of skills, experience, and passion to the table. We believe that your background aligns perfectly with the kind of talent we value at Salesforce, and we would be delighted to explore the possibility of you joining our team.

To take the first step in this exciting journey, we invite you to schedule an interview with us. You can do so by visiting our official website at [Salesforce Official Website]. On the website, you'll find a personalized URL created just for you to facilitate the scheduling process. Simply click on the link, and you'll be directed to our interview scheduling platform, where you can choose a time that suits you best.

We understand the value of your time and appreciate the effort it takes to explore new career opportunities. As a token of our appreciation, all candidates who schedule an interview through the provided link will be entered into a draw for a chance to win a special Salesforce swag bag!

Our team is eager to learn more about you and discuss how your skills and experiences can contribute to the success of Salesforce. Join us on this journey, and let's explore the incredible opportunities that await you within our organization.

If you have any questions or need further assistance, feel free to reach out to me at robert.edson@salesforce.com or call me at 1(913) 485-1234.

Thank you for considering this invitation, Quoc. We look forward to the prospect of having you on board and contributing to the success of Salesforce.

Best regards,

Robert Edson
Salesforce Recruiter
Dallas-Fort Worth Metroplex"
~~~


As you can see, the email is not perfect. However, with more prompts, the email will be very convincing to the potential victim, and he may send important credit card information to the Anonymous Attacker.

This is just an example of how a cyber-criminal may take advantage of a job-seeking victim's PII to phish the victim to sending out important personal information. With advancement in artificial intelligence, phishing emails can get sophisticated and pass many standard spam detection system. 

This is where our solution comes in – a phishing emails detection system with consideration of the use of artificial intelligence. 



## <a name="section-2">2. Our Prevention Solution.</a>

## <a name="section-3">3. The Future of Our Solution.</a>

## <a name="section-4">4. Sandia's Step-by-Step Approach to deploy our idea in action.</a>

