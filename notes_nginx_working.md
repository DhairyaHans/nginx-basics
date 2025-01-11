
# How Nginx is working

* Whenever we install Nginx, `/etc/nginx` is created

* This folder contains all the files, that help the nginx server to run

* We can list the files of this folder, using -

    > ls /etc/nginx

* From all these files, the `nginx.conf` file, is the most important, as it defines the redirection logic of the NGINX server   

* After every change in the `nginx.conf` file, we need to **reload** the nginx server, using -

    > nginx -s reload

* We can update the nginx.conf file, say, we use the content of the file - [basic nginx conf file](basic_nginx.conf) and reload the nginx server, then we can see on `localhost:8080`, that the content of nginx server changes


# Serving Static Content

* Nginx serves an index.html file by default

* We can create our own index.html file and use it in nginx.conf file to serve as static content

* For this, we need to create a folder, say _website_, in the `/etc/nginx/` directory and create an index.html in the _website_ folder. We can take example of [static content index.html](static_content_index.html) file

> **NOTE **- We can test, if our nginx.conf file is right or not, using the command `nginx -t`

* In the nginx.conf file, we can use `root` to specify the absolute path, where the index.html file is stored, which will serve as the default page for nginx server, just like the [static content nginx.conf](static_content_nginx.conf) file

> **Note :** By default, Nginx considers all the files as *TEXT* files, apart from *HTML files* 

* Say, we created a style.css file in the `/etc/nginx/website/` directory, just like [style.css](style.css) and we linked the file in our index.html file, like [styled index.html](type_specific_index.html)

* If we check the content-type of the `localhost:8080/style.css`, we will get `text/plain`

* Nginx treats all other files types as Plain text, apart from HTML

* To prevent this, we need to define **types** in the nginx.conf file, just like [Type specific Nginx.conf](type_specific_nginx.conf) file, based on the type of file

> **NOTE** : If you are defining the *types* in the nginx.conf file, then we need to specify all the types explicitly, else nginx will treat the data as text/plain

* One can have multiple types of files, so it is not practical to define each and every content type and file type

* So, there is a file in the `/etc/nginx/` folder, named `mime.types`, which contains the *types* definition of all the popular content types

* We can *include* this mime.types file in our nginx.conf file, just like - [Include Mimi Types nginx.conf](include_mime_types_nginx.conf) file