# 95-702 Distributed Systems

# Project 1

## Assigned: Friday, January 27, 2023

## Due: Friday, February 10, 2023, 11:59 PM

## Late by one minute is late!

This project has five objectives:

**First**, you are introduced to IntelliJ and TomEE. You already have some practice with these. In this assignment, you'll build several web apps to gain more experience.

**Second**, you build your first set of distributed systems. These are two small web applications using Servlets and Java Server Pages.

**Third**, you are introduced to web scraping, API processing, and JSON records.

**Fourth**, you are introduced to the MVC pattern if you have not used it before.

And **fifth**, as in all projects this semester, you should reflect on the functional and non-functional characteristics (e.g. security, scalability, failure handling, interoperability) of your solutions. There will be questions on the final exam concerning these characteristics. You should be able to demonstrate a nuanced comprehension of course content and be able to explain the technical aspects in relation to potential real-world applications. For each project task, software documentation is required. The software that you write (Java files and so on) must contain comments that describe what each significant piece of code is intended to accomplish. Points will be deducted if code is not well documented. Read the documentation-related links provided on the course schedule (for class #1) to understand what is expected. Be sure to consult the rubric for details on grading.

# Deliverables

There are two parts to deliver, all zipped into one file for upload, with the name Project1_andrewID.zip, where "andrewID" is replaced with your actual andrew id:

- one PDF containing relevant screeenshots of all the parts followed by code snippets (which is relative: how much to include is up to you for each part) that produced the result shown in the screenshot. Each section of the PDF must be clearly labeled.
- your three projects, each zipped, with all of the three tasks zipped together.

See the end for more detail, but read the project task descriptions first so that you know what the details are talking about.

# Task 1

## Use the IntelliJ Project Name:  Project1Task1

Create an index.jsp page that asks the user to enter a string of text data, and to make a choice of two hash functions using radio buttons. The hash function choices should be MD5 and SHA-256, with MD5 being the default.  When the submit button is pressed a request is sent to a servlet. The servlet must be named ComputeHashes.java. The servlet will compute the requested cryptographic hash value (MD5 or SHA-256) from the text transmitted by the browser. You will need to employ the Java crypto API to compute the hash of the text. The original text will be echoed back to the browser along with the name of the hash, and the hash value. The hash values sent back to the browser should be displayed in two forms: as hexadecimal text and as base 64 notation. We will discuss the use of such hash values later in the course.  To compute the MD5 and SHA-256 hashes, use these standard java packages:

    import java.security.MessageDigest;
    import java.security.NoSuchAlgorithmException;

To print the Base64 encoding, use the following method:

    javax.xml.bind.DatatypeConverter.printBase64Binary

To print the hexadecimal encoding, use the following method:

    javax.xml.bind.DatatypeConverter.printHexBinary

Be sure to provide a simple and user friendly interface.  If you are unfamiliar with HTML forms, a simple explanation can be found at:

    http://www.w3schools.com/html/html_forms.asp .

Because Task 1 is fairly simple, you do not have to use MVC for it. Do the simplest thing possible (however, feel free to use MVC if you'd like).

Be sure to create screen shots of your working application and submit them as described in the Submission section at the end of this document.

---

## Experiment with GitHub Copilot to help you with this task

1. Create an index.jsp page. Within the \<body\> of the html, write the following comment and then press enter key to wait for Copilot to generate code for you. 

```
<%--asks the user to enter a string of text data, and to make a choice of two hash functions using radio buttons. The hash function choices should be MD5 and SHA-256, with MD5 being the default.  When the submit button is pressed a request is sent to a servlet.--%>
```

2. Create a servlet named ComputeHashes.java. And give the following comment to Copilot to write a function computing the requested cryptographic hash value (MD5 or SHA-256) of some texts.

```
//this computeHashes() method would be used to compute the hash value of a string using the given hash method and return the hash value in bytes array. To compute the MD5 and SHA-256 hashes, use these standard java packages: java.security.MessageDigest, java.security.NoSuchAlgorithmException;
```

3. giving the following comment to Copilot to write a function computing the hash value as hexadecimal text.

```
//This convertToHex() method use the printHexBinary method of the DatatypeConverter class to convert the hash value in bytes array to a string in hexadecimal format.
```

4. giving the following comment to Copilot to write a function computing the hash value as base 64 notation.

```
//This convertToBase64() method use the printBase64Binary method of the DatatypeConverter class to convert the hash value in bytes array to a string in Base64 format.
```

5. giving the following comment to Copilot to write the doPut() methods to display the results on the browser.

```
//In this doPut() method, first get the hash method and the text from the request object, compute the hash value of the text using the hash method, and return the hash string, hash and the hash value to the browser in hexadecimal, and Base64 format, using javax.xml.bind.DatatypeConverter.printBase64Binary, javax.xml.bind.DatatypeConverter.printHexBinary.
```

*Remember: The code generated by Copilot is not perfect. Sometimes, you have to modify these code to satisfy your own demand, such as changing the return type of the method or the name of parameter in the request. The comments you provide to Copilot greatly influence the outcomes it generates for you. You can also change the aforementioned comments or even alter the sequence of these steps to observe the resulting effects.*

# Task 2

## Use IntelliJ Project Name: Project1Task2

Task 2 is meant to give you practice with several things: servlet programming, web scraping, API's, JSON, and MVC. It gives some information about the upcoming Women's World Cup in Australia and New Zealand.

Your program will present a welcome screen containing a title, your name, and a drop-down menu of of countries, as in Figure 1 and Figure 2. Note that there are still a few participants to be decided through playoff games; we will ignore those countries. The Submit button is used to record the user's choice. Note that you will need to learn about HTML drop-down menus on your own.

## Input

![Figure 1](figure1.png)
***Figure 1: Welcome Screen***

---

![Figure 2](figure2.png)
***Figure 2: Drop-down Menu (partial)***

Use the file "countries" to create the drop-down list. It is okay to hard-code the country names in the jsp file.

## Output

Figure 3 shows the output screen. Several facts have been gathered from the web sites listed.

![Figure 3](figure3.png)
***Figure 3: Output for Argentina***

Argentina's nickname is shown first, followed by its capital city. Argentina did not have any player in the top 50 scorers in the 2019 tournament, so "N/A" is shown. The flag is the official country flag, but the flag emoji is an idealized version. The credit for each part of the output is shown - ***but note*** that you will have to construct the URL appropriate to each site (e.g. perhaps by adding the country name).

The Continue button should send the user back to the Welcome screen.

Figure 4 shows the results for the United States.

![Figure 4](figure4.png)
***Figure 4: Output for the United States***

The U.S. team does not have a nickname (according to this web site), so "Not found" is shown. The top scorer in the 2019 tournament for the U.S. was Alex Morgan, with 6 goals (there are other U.S players in the top 50; choose only the highest).

A few notes:

1. Do not complain if the name of a country in "countries" is not exactly correct (e.g. "Republic of Robonia" instead of "Robonia", I'm just making that country up).

2. The nickname site seems a little sketchy; I'm not sure those are all correct - *BUT:* if there is no nickname for some team, display "Not found". For example - as shown in Figure 4 - the United States does not have a nickname.

3. The capital city site may have duplicates of country names, because some of its listings are territories of other countries or use the same currency - so be careful while scraping this site. For example, the capital of Ireland is Dublin, not London, as my first attempt claimed.

4. You are responsible for correctly handling any outliers on all the sites we're using. For example, "England" is not a country, but show Great Britain's capital. The flag of England should be the United Kingdom's flag, but the emoji should be England's. The flag site uses a dash for any space in the name, as in "Costa-Rica", so make that adjustment.

5. When scraping the top scorer's list, beware that there's a second table on that page showing assists - don't include those players. Only choose a country's top scorer. If the country does not have a player in this list, display "N/A" (that is, not applicable).

6. The country flag's size and the emoji flag's size should be approximately as shown.

7. The flag emoji image URL *MUST* be obtained by parsing a ***JSON record*** returned from this site. This API returns an array of JSON records; convert it to an array of Java objects. Create a Java class with the appropriate String keys (see what the API returns to figure this out) as private data, an overloaded constructor, and getters/setters for each of the data fields. Only the "image" field (*not* the emoji field) will be used, but you'll need all the fields to do the conversion. Create a Java array from the JSON records containing *only* the needed countries (there are a lot more than that in the JSON record).

Only create this array ***once***, not again and again for every new country being searched. Points will be deducted if you do this incorrectly.

You ***MUST*** use the gson library for this - see below for details about including it in your project.

(*Note:* we could have scraped the flag emoji URL by treating the returned data as a string, but the point here is to use an API and JSON.)

8. When the user presses the "Continue" button, return to the original screen.

9. You *MUST* use the MVC pattern for Task 2.

## Notes and hints

## Screen Scraping

Screen scraping is programmatically processing the HTML that typically is displayed by a browser and can be a useful tool when your data source does not have an API that provides structured data. Instead, you can search or parse the HTML to find and extract the data that you need. For more information, see

> https://en.wikipedia.org/wiki/Web_scraping

Your application should work similarly to InterestingPicture, but instead of searching Flickr, it will use the sites mentioned above.

- You are allowed to and encouraged to build your solution based on the InterestingPicture code you have been given in class. You MUST refactor it, however, so that it has project, variable, and class names that make sense for your application. For example, <b>you will lose points</b> if your class is still named InterestingPictureServlet.

- You do not need to, but you are welcome to, use jsoup (https://jsoup.org/) which is a Java HTML Parser, to do the flag scraping.  It is the Java version of Beautiful Soup, which you may have used in Python. The downsides of using jsoup are you will first need to understand the Document Object Model (DOM) and CSS Selectors. These are both useful to know. The upside of using jsoup is that it makes it much easier to find and select content from HTML (i.e. screen scrape). Refer to the JSON Maven notes below; adding jsoup will require a similar process.

## HTML

Refer to http://www.w3schools.com for good help on the basic HTML you need for this task. This has examples of drop-down boxes.

## JSON and gson

JSON records are text records containing tag-value pairs, where the tag is the field name - think of it as a dictionary or map with nesting. It is much shorter than XML. In order to find what you need, use the JSON library GSON. To use GSON, download the gson v.2.10.1 jar file to a place you'll remember. To add it to your project, go to File->Project Structure->Modules, choose the Dependencies tab, click the + icon at the bottom choose Jars or Directories, navigate to where you put the jar file, click that, then Apply and OK. It should show up in your pom.xml file as the last entry in <dependiences> as:

  ```
<dependency>
    <groupId>com.google.code.gson</groupId>
    <artifactId>gson</artifactId>
    <version>2.10.1</version>
</dependency>
  ```

If this does not appear, add the above lines manually to pom.xml.

Finally, reload the Maven dependencies to have this new dependency take effect - an icon will probably appear in the pom.xml window, but if you don't see it, got to the Project View window, find the pom.xml entry (it should be near the bottom of the tree), right click it, choose Maven -> Reload Project. (FYI, Maven is a build management tool, different from the usual Gradle build; Maven uses the Project Object Model (pom) file to keep track of properties and dependencies.)

Please use gson and not some other JSON library.

## SSLHandshakeException

Most modern sites require you to make https, not http requests. When you do so from your Java program, you will hit an SSLHandshakeException. We will be covering SSL and related topics in a few weeks. In the meantime, you will have to deal with this exception.

If you use jsoup, you should use validateTLSCertificates(false). (Refer to the jsoup API to understand this when you need it.)

If you do not use jsoup, here is a code to replace the fetch method in InterestingPictureModel to ignore the exception. The parameter "certType" should be set to the string "TLSV1.3".

```
private String fetch(String searchURL, String certType) {
    try {
        // Create trust manager, which lets you ignore SSLHandshakeExceptions
        createTrustManager(certType);
    } catch (KeyManagementException ex) {
        System.out.println("Shouldn't come here: ");
        ex.printStackTrace();
    } catch (NoSuchAlgorithmException ex) {
        System.out.println("Shouldn't come here: ");
        ex.printStackTrace();
    }

    String response = "";
    try {
        URL url = new URL(searchURL);
        HttpURLConnection connection = (HttpURLConnection) url.openConnection();

        // Read all the text returned by the server
        BufferedReader in = new BufferedReader(new InputStreamReader(connection.getInputStream(), "UTF-8"));
        String str;
        // Read each line of "in" until done, adding each to "response"
        while ((str = in.readLine()) != null) {
            // str is one line of text readLine() strips newline characters
            response += str;
        }
        in.close();
    } catch (IOException e) {
        System.err.println("Something wrong with URL");
        return null;
    }
    return response;
}

private void createTrustManager(String certType) throws KeyManagementException, NoSuchAlgorithmException{
    /**
     * Annoying SSLHandShakeException. After trying several methods, finally this
     * seemed to work.
     * Taken from: http://www.nakov.com/blog/2009/07/16/disable-certificate-validation-in-java-ssl-connections/
     */
    // Create a trust manager that does not validate certificate chains
    TrustManager[] trustAllCerts = new TrustManager[] {new X509TrustManager() {
        public X509Certificate[] getAcceptedIssuers() {
            return null;
        }
        public void checkClientTrusted(X509Certificate[] certs, String authType) {
        }
        public void checkServerTrusted(X509Certificate[] certs, String authType) {
        }
    }
    };

    // Install the all-trusting trust manager
    SSLContext sc = SSLContext.getInstance(certType);
    sc.init(null, trustAllCerts, new java.security.SecureRandom());
    HttpsURLConnection.setDefaultSSLSocketFactory(sc.getSocketFactory());

    // Create all-trusting host name verifier
    HostnameVerifier allHostsValid = new HostnameVerifier() {
        public boolean verify(String hostname, SSLSession session) {
            return true;
        }
    };

    // Install the all-trusting host verifier
    HttpsURLConnection.setDefaultHostnameVerifier(allHostsValid);
}

```

Track Piazza for additional hints and answers to questions.

# Task 3 – Use the IntelliJ Project Name: Project1Task3

Implement a web application that implements a simple desktop and mobile “clicker” for class.  Your app should allow users to submit answers to questions posed in class, and should provide a separate URL end point for getting the results of the submitted responses.  The welcome page for your app should be similar to Figure 5.  You can make it more stylish if you like, but it is not required.

![Figure 5](figure5.png)
***Figure 5***

When the user makes a choice and hits “submit”, their answer should be stored in your MVC model.  The response should be similar to the picture on the left. Notice that it is **required** to provide feedback to the user regarding the choice that they made (i.e. “D” in this example).

The user should also have the ability to submit another answer as shown in the screenshot.

![Figure 6](figure6.png)
***Figure 6***

You can test the application by repeatedly submitting answers and allowing your model to tally the results.  Your web app should also have a URL path “/getResults” (shown in Figure 7) for listing the results of user voting.

![Figure 7](figure7.png)
***Figure 7***

## Requirements for the /getResults path:

1. List each answer that has been given, and the number of times a user has submitted that answer.
2. You do not have to list options that have been chosen zero times.
3. The results should be displayed sorted in alphabetical order.
4. /getResults should also clear the stored results so that a new question can be posed.
5. If there are no results available, then report this as shown in Figure 8.

![Figure 8](figure8.png)
***Figure 8***

Note that requirement 4 does not adhere to the HTTP standard for a GET request. You should understand why this is bad behavior according to the standard, and how you could fix it (It might be on the exam).

The web app should work with a mobile browser.  For this project you can use a simple check like the one that was used in InterestingPicture and then use an appropriate mobile doctype. An easy way to check your web app for mobile is to use the Google Chrome DevTools Using the Google Chrome browser.

- Browse to your web application in Chrome
- Access the Chrome DevTools
  (https://developers.google.com/web/tools/chrome-devtools/?hl=en#access-devtools).  
- Toggle device mode to mobile and choose an Android or iPhone device
  (https://developers.google.com/web/tools/chrome-devtools/iterate/device-mode/?hl=en)
- Reload the page.
- In addition to testing, you use this to produce a screen shot showing your web app working for mobile.  If your page looks like the one on the right, even after reloading, then the doctype is not being set correctly.   

Figure 9 is what the web app should look like for mobile if the doctype is set correctly.

![Figure 9](figure9.png)
***Figure 9***

## Overall web app requirements:

- You must use MVC to separate concerns.
- Implement only one HttpServlet

## Hints:

- You can have multiple URL patterns in a WebServlet annotation.  For example, you can indicate that a servlet can be called by two paths such as: urlPatterns = {"/submit", "/getResults"}

 - In order to determine within the servlet which path was actually requested, you can use request.getServletPath();

Produce screen shots of your application:

- With the answer options on desktop
- With the getResults on desktop
- With the answer options on mobile
- With the getResults on mobile

## Questions:

If you have questions, you can post them to the class Piazza and tag them as “Project1”.

# Summary & Submission:

Be sure to review the Rubric linked on the course schedule for the first day.

Submit ***one*** PDF naned Project1_andrewID.zip, where "andrewID" is replaced with your actual andrew id, containing the following; each part should begin with the headers shown (that is, "Task 1") and subheaders for the subparts. "Code snippet" means a copy of the relevant code, **not** all of the .java or .jsp file.

### Task 1:

1. **Screen shots** of input, MD5 and SHA-256 output, both in hex and base 64
2. **Code snippets** of computation of each hash

### Task 2:

1. **Screen shots** of input page, drop-down menu, output page for England and South Africa.

2. **Code snippets** for:

- scraping of the nickname
- scraping of the capital
- scraping of the top scorer with number of goals
- scraping of the flag
- api call for the flag emoji JSON record, including the conversion to a Java array of objects.

### Task 3:

1. **Screen shots** of the input page, output page (one vote), results page
2. **Code snippets** from the Java code that produces the output page and the results page.

### Code: ###

Create three zip files, each one of which is the zip of your WHOLE project for task 1, 2 and 3. For each project, zip the whole project, you need to use "File->Export Project->To Zip" in IDEA.

### Finally: ###

***Zip the one PDF and the three project zip files into one big zip file for submission.***
