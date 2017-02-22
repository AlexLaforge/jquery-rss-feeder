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

The main code was written in classic ASP because that is what we use on our current system. It can easy be converted to other laguages. The HTML is just an exmaple of what the RSS feed will look like after the ASP has inported and parced the RSS feed. I included it only because I helps when styling the CSS and working with the JQuery code. However, the ASP is actually able to create the HTML on the fly from any RSS feed.

I was using this code on the footer our our company website. You are welcome to look at there for an example.
www.internetbuilderconsulting.com

I used http://feed.informer.com to convert the RSS feed to HTML that I can import into our site. 

Feed Informer does not offer their own code for this, but we (a friend Carol) worked with me to write this to convert the ASP.net script to ASP and import it into our page. I wrote all the rest of the code. All you need is the Widget ID from Feed Informer. You do not need to use their code, the code I am providing below is what you will need.

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


The rest of the code is in this project including the JS, JQuery and CSS. Hopefully you can follow it fairly easy. 

I do appolgize, I normally I put better comments in my help files. I was just throwing it up on my GitHub so I could archive it for sharing with others (I am just now starting to do that more).

Enjoy.



