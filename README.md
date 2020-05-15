# 青年大学习打卡
### 使用方法：
1、创建一个Cloudflare worker （具体方法自行Google）

2、复制index.js中的代码到Cloudflare worker中

3、通过抓包获取你所在学校的打卡配置信息，或去issue中查看有没有同省份的同学分享

4、根据获得的打卡配置信息修改代码中的配置项

5、部署worker

6、通过向worker发送post请求即可完成打卡,请求内容为包含姓名和手机号码的json文件{name:"xxx",number:"13309909090"}

post请求示例：

url:xxx.xxx.workers.dev

{name:"xxx",number:"13309909090"}

### 注意事项：
这个程序目前还不是很完善，因为每个班级的ID号是有区别的，不同省份的打卡方式好像也不太一样（即打卡对应的url，还有组织id是不一样的），具体的我就不是很清楚了，因为别的班级或是学校我都没试过。

如果需要在不同的省份或者班级使用可能还是需要重新抓包分析他的打卡请求才行。

附上我们学校的打卡请求参考：
{"stage_id":"23","name":"x'","tel":"xx","org":[2,2000,2000,2003],"last_org":2003,"org_name":"xxx团支部"}
单从请求上看至少org、last_org和org_name不同的班级会是不同的
然后具体打卡请求的url不同省份也估计是不一样的


还有就是这个worker脚本只是请求了填报的页面，因为我们学校只是检查你有没有填报，只是发个请求即可完成打卡，比较简单，不会检查有没有做完，所以就没有做完成整个流程的请求。不同学校的政策不太一样，需要自行抓包处理对应学校的流程，处理完后如果可以通过pull requests的方式分享出来或是通过issue的方式分享出来给大家就更好了！

另外本人代码水平不高，第一次发开源项目，写的不好的地方还请各位多多包涵！最后，此脚本仅供学习交流使用，不要拿去干坏事哦，被辅导员抓到了的话后果自行承担~~

