# The Web
## Introduction
- The Internet is the basic infrastructure.
- Web Server serves Web Pages to clients, which we call Web Browsers.
- The communication happens through some rules set by a protocol called HTTP (Hyper Text Transfer Protocol), which works on top of TCP.
- Basically, that says how the browser should talk to the server, and vice versa.
- A Web Page is a text file, encoded in a special format called HTML (Hyper Text Markup Language).

## The HTTP protocol
- HTTP (Hyper Text Transfer Protocol) is one of the application protocols of TCP/IP, the suite of protocols that powers the Internet.
- HTTP is what makes the World Wide Web work, giving browsers a language to communicate to remote servers that host web pages.
- HTTP was first standardized in 1991.
- In 1993 Mosaic, the first graphical web browser, was released, and things skyrocketed from there.
- HTTP now powers, in addition to web pages, REST APIs, one common way to programmatically access a service over the Internet.
- HTTP got a minor revision in 1997 with HTTP/1.1, and in 2015 its successor, HTTP/2, was standardized and it’s now being implemented by the major Web Servers used across the globe.
- The HTTP protocol is considered insecure, just like any other protocol (SMTP, FTP..) not served over an encrypted connection. This is why there is a big push nowadays towards using HTTPS, which is HTTP served over TLS.
- HTTP is the way web browsers like Chrome, Firefox, Edge and many others (also called clients from here on) communicate with web servers.
- The name Hyper Text Transfer Protocol derives from the need of transferring not just files, like in FTP - the “File Transfer Protocol”, but hypertexts, which would be written using HTML, and then represented graphically by the browser with a nice presentation and interactive links.
- Links were the driving force that drove adoption, along with the ease of creation of new web pages.
- An HTTP server will not just transfer HTML files, but typically it will also serve other files: CSS, JS, SVG, PNG, JPG, lots of different file types.
- HTTP is perfectly capable of transferring those files as well, and the client will know about the file type, thus interpret them in the right way.
- when an HTML page is retrieved by the browser, it’s interpreted and any other resource it needs to display property (CSS, JavaScript, images..) is retrieved through additional HTTP requests to the same server.

## Hyperlinks
- Inside a web browser, a document can point to another document using links.
- A link is composed by a first part that determines the protocol and the server address, either through a domain name or an IP.
- Anything appended to the address part represents the document path.
- The web server is responsible for interpreting the request and, once analyzed, serving the correct response.

## What is a Web server
- A Web Server is a program that listens for HTTP requests coming from clients over the network.
- We sometimes call Web Server the computer that hosts the Web Server, too.
- But in the specific, the Server is the computer, which is running somewhere on the Internet, and the Web Server is the program running on that computer whose job is to listen for HTTP requests.
- We have many different programs that we can run and they do the Web Server job for us. Apache and Nginx are two traditionally popular solutions.
- Those are the solutions you would use to install a Web Server on your own Linux server on the Internet. What we call your VPS (Virtual Private Server).

## What is a Web browser
- The Web is built on standards. The whole HTTP protocol thing, HTML, and all the stuff built on top of the Web is open, it’s something anyone can participate in.
- You and I could even create a browser, distribute it, and people could use it.
- Web is open like Linux is open.
- They allow you to type a URL, which is the address of a resource on the Web.
- The browser internally looks up the URL, contacts the Web Server that hosts it, sends the URL of the resource requested, receives the information back, and displays it.
- The browser starts the DNS lookup to get the server IP address.
- First, it checks the DNS local cache, to see if the domain has already been resolved recently.
- The address of the DNS server is stored in your system preferences. It’s typically defined by your router to be the internet provider’s DNS, that’s the default most people use. Or you can set it to Google’s or Cloudflare’s DNS, or anything else you want.
- The provider’s DNS server might have the domain IP in the cache. If not, it will in turn ask the root DNS server. That’s a system (composed of 13 actual servers, distributed across the planet) that drives the entire internet.
- The DNS server does not know the address of each and every domain name on the planet. What it knows is where the top-level DNS resolvers are.
- Once the root DNS server receives the request, it forwards the request to that top-level domain (TLD) DNS server.
- Say you are looking for flaviocopes.com. The root domain DNS server returns the IP of the .com TLD server.
- Now our DNS resolver will cache the IP of that TLD server, so it does not have to ask the root DNS server again for it.
- The TLD DNS server will have the IP addresses of the authoritative Name Servers for the domain we are looking for.
- Those are the DNS servers of the hosting provider or cloud platform used. They are usually more than 1, to serve as backup.
- The DNS resolver starts with the first, and tries to ask for the IP of the domain (with the subdomain, too) you are looking for.
- If the first doesn’t know (or doesn’t work), it asks the second, and this procedure ends when an IP address (or an error!) is returned.
- With the server IP address available, now the browser can initiate a TCP connection to that.
- A TCP connection requires a bit of handshaking 🤝 before it can be fully initialized and you can start sending data.
- Once the connection is established, we can send the request.
- The request is a plain text document structured in a precise way determined by the communication protocol.
- It’s composed of 3 parts:
  - the request line
  - the request header
  - the request body
- The request line sets, on a single line, the HTTP method, the resource location, and the protocol version.
- Note GET. That’s the HTTP method. We want to GET a document from the server.
- We have other methods, including POST, PUT, and DELETE, to do other things like sending, updating, or deleting data.
- Next, the request header. This is a set of key: value pairs that set certain values.
- There are 2 mandatory fields, one of which is Host, and the other is Connection, while all the other fields are optional.
- Host indicates the domain name which we want to target, while Connection is always set to close unless the connection must be kept open.
- Some of the most used header fields are:
  - Origin
  - Accept
  - Accept-Encoding
  - Cookie
  - Cache-Control
  - Dnt
- The header part is terminated by a blank line.
- The request body is optional, not used in GET requests but very much used in POST requests and sometimes in other verbs too, to send data to the server, and it can contain data in JSON format.
- Once the request is sent, the server processes it and sends back a response.
- The response starts with the status code and the status message. If the request is successful and returns a 200, it will start with.
- The response then contains a list of HTTP headers and the response body (which, since we’re making the request in the browser, is going to be HTML)
- The browser now has received the HTML and starts to parse it, and will repeat the exact same process we did for all the resources required by the page:
  - CSS files
  - images
  - the favicon
  - JavaScript files, etc
- Any of those items will be downloaded using the same exact workflow. It all happens very very fast, of course depending on your network speed.
- From here, interaction can be managed in different ways, including clicking links, navigating with the keyboard, and much more.
- Browsers also offer us developers a way to better debug and inspect web pages and web applications, using what are usually called Developer Tools. Developer Tools are an essential set of tools for us Web developers, and you’ll get to know them soon.
