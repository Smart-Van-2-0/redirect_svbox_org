# Redirect www.svbox.org

SYSTEM repository for www.svbox.org redirects.

This repo contains only a simple `index.html` file that will be published as
[GitHub Pages](https://pages.github.com/). At the same time the DNS records for
the  use the GitHub.io servers as `A` records.

So, when the user require the [http[s]://svbox.org](https://www.svbox.org)
url the DNS redirects it to the GitHub.io server where the `index.html` (or the
`404.html`) page is returned.<br/>
If the user required an `http` url, the GitHub.io server redirects it to the
`https` version of the same url.<br/>
Then, this page contains a JavaScript code that replace the `window.location`'s
protocol and domain.

That's all.


## Run

Open a browser and go to the one of the following links:
* [http://www.svbox.org](http://www.svbox.org)
* [https://www.svbox.org](https://www.svbox.org)

After some redirect it should display the [https://www.smartvanbox.org](https://www.smartvanbox.org)
page and url.


## Test

Execute the following `curl` command into a shell:

```shell
curl -v -L -o /dev/null http://www.svbox.org 2>&1 | egrep -i "> Host:|> GET|* Connected|< Server|< Location|SSL:"

* Connected to www.svbox.org (185.199.109.153) port 80 (#0)
> GET / HTTP/1.1
> Host: www.svbox.org
< Server: GitHub.com
< Location: https://www.svbox.org/

* Connected to www.svbox.org (185.199.109.153) port 443 (#1)
> GET / HTTP/2
> Host: www.svbox.org
< server: GitHub.com
```

