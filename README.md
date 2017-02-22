# jquery-rss-feeder

The purpose of this code is to create a CSS driven vertical ticking scroll of an RSS feed from a Twitter page (or anywhere actualy including a blog). It not only scrolls vertically, but will stop when you hover over it.

### Version
1.0.0

### Tech

jquery-rss-feeder uses a number of open source projects to work properly:

  - [jQuery.com]
  - [feed.informer.com]

### Development

Want to contribute? Great!


### To Dos

  - Write Tests
  - Rethink Github Save
  - Add Code Comments
  
### Details

The main code was written in classic ASP because that is what we use on our current system.  

Basically the RSS feed is being converted by Feed Informer to HTML using the template (see below). I am importing that template into blogObject and then writing that object to the console. ASP is a very strick language with lots of limitations. It took us a while to figure this out, but it is actually very simple.


####ASP (vbScript)
----------------------------------------------

```
<%
  On Error Resume Next
  dim blogObject
  set blogObject = CreateObject("MSXML2.XMLHTTP")
  Call blogObject.Open("GET", "http://feed.informer.com/widgets/1PE6GMRN1P.html", false)
  Call blogObject.Send()
  Response.Write(blogObject.responseText)
  Response.Flush()
  set blogObject = nothing
%>
```

####Feed Informer Template
----------------------------------------------

Here is the custom widget template code you need for Feed Informer. Just create your own custom widget, put this template in the Header, Per-Item and Footer and save it. It will create the HTML code for the ASP code I am using above. Feel free to hit preview to see the actually output. You can use this same custome widget code for any RSS feed. 


Header Template:
```
<div class="news-wrap">
  <div class="twitter-news marquee">
```

Per-Item Template:
```
    <div class="twitter-news-item marquee-item" onclick="window.open('%URL%');"><span></span>
      <div><a href="%URL%" title="%DESCRIPTIONPLAIN,150%" target="_blank">%DESCRIPTIONPLAIN,150%</a></div>
    </div>
```

Footer Template:
```
  </div>
</div>
```

----------------------------------------------

###Additional Info

The included HTML file in this project is just an exmaple of what the RSS feed will look like after the ASP has imported and parced the RSS feed to HTML. I included it only because I helps when to see when styling the CSS and working with the JQuery code. However, the ASP is actually able to create the HTML on the fly from any RSS feed. 

I was using this code on the footer our company website. You are welcome to look at there for an example.
www.internetbuilderconsulting.com

Also, fyi, Feed Informer does not offer their own code for what I am doing and they do not offer ASP (vbScript) code. However, we (a friend Carol) worked with me to write the ASP code to convert the ASP.net script they offer to ASP and import the outputed HTML. I wrote all the rest of the code. 

Once you know your Widget ID, and you have set up the Widget Template, all you need is the Widget ID from Feed Informer to make the ASP code work. You do not need to use ANY their code, the code I am providing below is all you will need.

The rest of the code is in this project including the JS, JQuery and CSS. Hopefully you can follow it fairly easy. 

I do appolgize, I normally I put better comments in my help files. I was just throwing it up on my GitHub so I could archive it for sharing with others (I am just now starting to do that more).

Enjoy.



