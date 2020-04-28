## 在google colab使用个人数据
使用colab时我们经常需要用到自己的数据做训练，如何上传个人数据呢？

### Import from local

运行下述代码后，在notebook结尾会有上传本地文件的界面。

```
uploaded = files.upload()
```

注意运行后，文件就保留在colab了，不需要重复上传。

读取文件：

```
import io
with io.BytesIO(uploaded['node.txt']) as f:
  for line in f:
    print(line)
```


### Import from google drive 

```
!pip install -U -q PyDrive
from pydrive.auth import GoogleAuth
from pydrive.drive import GoogleDrive
from google.colab import auth
from oauth2client.client import GoogleCredentials

# Authenticate and create the PyDrive client.
auth.authenticate_user()
gauth = GoogleAuth()
gauth.credentials = GoogleCredentials.get_application_default()
drive = GoogleDrive(gauth)
```
运行上述代码后，需要打开notebook下方的链接复制验证码，然后粘贴到输入框。这时候colab已经和我们的google账户建立连接了。

在google drive里，选择数据文件，点击共享文件，得到文件的共享链接，拿到链接中的id序列，如下述:

```
link = "https://drive.google.com/file/d/11V-rt_meXkOMnRGbE6LG8-YA98ab7pvi/view?usp=sharing"
downloaded = drive.CreateFile({'id':"18V-rt_meXkOMmRGbE6LG8-YF97dg7pvi"}) 
downloaded.GetContentFile('node.txt')  
```

随后对数据进行正常读取:

```
with open('node.txt', 'r') as f:
  for line in f:
    print(line)
```