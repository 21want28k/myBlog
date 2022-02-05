𝑰'𝒎 𝒉𝒉𝒈, 𝑰 𝒂𝒎 𝒂 𝒈𝒓𝒂𝒅𝒖𝒂𝒕𝒆 𝒔𝒕𝒖𝒅𝒆𝒏𝒕 𝒇𝒓𝒐𝒎 𝑵𝒂𝒏𝒋𝒊𝒏𝒈, 𝑪𝒉𝒊𝒏𝒂.

- :school: 𝑺𝒉𝒄𝒐𝒐𝒍: 𝑯𝒐𝒉𝒂𝒊 𝑼𝒏𝒊𝒗𝒆𝒓𝒔𝒊𝒕𝒚 
- 🌱 𝑳𝒆𝒂𝒓𝒏𝒊𝒏𝒈: 𝑰’𝒎 𝒄𝒖𝒓𝒓𝒆𝒏𝒕𝒍𝒚 𝒍𝒆𝒂𝒓𝒏𝒊𝒏𝒈 𝒅𝒆𝒔𝒊𝒈𝒏 𝒑𝒂𝒕𝒕𝒆𝒓𝒏, 𝑳𝒆𝒆𝒕𝒄𝒐𝒅𝒆, 𝒅𝒊𝒔𝒕𝒓𝒊𝒃𝒖𝒕𝒆𝒅 𝒔𝒚𝒔𝒕𝒆𝒎, 𝒎𝒊𝒅𝒅𝒍𝒆𝒘𝒂𝒓𝒆 𝒂𝒏𝒅 𝒔𝒐 𝒐𝒏.
- :heartbeat: 𝑯𝒐𝒘 𝒕𝒐 𝒓𝒆𝒂𝒄𝒉 𝒎𝒆：[𝑽𝑿](https://github.com/21want28k/pictures/blob/master/3143332f70bca07d7a6d8aaa85632f8.jpg)
- :books: 𝑴𝒚 𝒃𝒍𝒐𝒈: 𝒉𝒕𝒕𝒑𝒔://𝒉𝒉𝒈𝒚𝒚𝒅𝒔.𝒃𝒍𝒐𝒈.𝒄𝒔𝒅𝒏.𝒏𝒆𝒕/ 
- :briefcase: 𝑷𝒓𝒐𝒇𝒆𝒔𝒔𝒊𝒐𝒏𝒂𝒍 𝒔𝒌𝒊𝒍𝒍𝒔：𝒎𝒚 𝒅𝒓𝒆𝒂𝒎
![<img   height="19px" src="https://img.shields.io/badge/java-grey.svg?&logo=java&logoColor=white"/> <img
        height="19px" src="https://img.shields.io/badge/spring-%236DB33F.svg?logo=spring&logoColor=green"/> <img
        height="19px" src="https://img.shields.io/badge/ubuntu-%23E95420.svg?&logo=ubuntu&logoColor=white"/> <img
        height="19px" src="https://img.shields.io/badge/docker-%232496ED.svg?&logo=docker&logoColor=white"/> <img
        height="19px" src="https://img.shields.io/badge/mysql-%234479A1.svg?&logo=mysql&logoColor=white"/> <img
        height="19px" src="https://img.shields.io/badge/git-%23F05032.svg?&logo=git&logoColor=white"/> <img
        height="19px" src="https://img.shields.io/badge/redis-%23DC382D.svg?&logo=redis&logoColor=white"/> <img
        height="19px" src="https://img.shields.io/badge/rabbitmq-%23FF6600.svg?logo=rabbitmq&logoColor=white"/>](https://img-blog.csdnimg.cn/2b1281caade2476d99f13878fc24e111.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5rKz5rW35ZOleXlkcw==,size_20,color_FFFFFF,t_70,g_se,x_16)

# Distributed System：CAP and BASE Theorem
CAP is the basic theoremin distributed theory. This blog aims to summarize what CAP and BASE are.
## 1-1: CAP Theorem
**C: consistency**   
There are much backup data in a distributed system. One backup data may differ from another. Consistency make sure that all backup data is **the same ,  correct and the newest** at **every** time. So, when a request arrive the distributed system, it mush give a response with the newest data.

**A: available**   
If the distributed system get a request, it must feedback this request. Differentiaed from C, data returned may not be the newest. For example, as times go. Data goes through several stages: A B C. C is the newest,  B is the second. So B hasn't be updated into the newest in time. i.e. B is also correct but a little old.

**P: partition Tolerance**  
In a distributed system, nodes are connected. Network fluctuations are inenvitable. For this reason,  nodes are invided into some partitions. There maybe some differences between data in those partitions. For example, the data is A in partition\_1. The data is B newer than A in partition\_2. A and B is all correct, the only difference is that A is newer than B. Network fluctuations exist in all conditions, so P principle must be guaranteed.
## 1-2: AP or CP or CAP
As above, P principle must be guaranteed for network fluctuations. So the next step is choose A or C. You may have the question that could C A P be select at the same time? The answer is no. Why? Imaging that consistency feature makes sure every data is the newest. Changing from the old to the newest needs time. Right? The changing process one request must wait until the process done. However, the available feature requrie get the response immediately.  So both A(availability) and C(consistency) are contradictory.

## 1-2: BASE Theorem
BA: 
