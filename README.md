## drone邮箱通知的中文主题

drone发送email的插件说明文档： http://plugins.drone.io/drillster/drone-email/

上述插件的github地址：https://github.com/Drillster/drone-email


#### 由于英文的推送邮件看的不舒服所以弄了个中文主题

大致配置文件
```yml
- name: notify
    image: drillster/drone-email
    environment:
      EMAIL_HOST: smtp.qq.com
      EMAIL_USERNAME: xanwidtf@foxmail.com
      EMAIL_PASSWORD:
        from_secret: mail_password
    settings: 
      from: xanwidtf@foxmail.com
      recipients: [xanwidtf@foxmail.com]
      subject: >
        [{{ build.status }}]
        {{ repo.owner }}/{{ repo.name }}
        ({{ build.branch }} - {{ truncate build.commit 8 }})
      body:
        http://qvvtaxa26.hn-bkt.clouddn.com/defaults-CN.html   #中文模板,使用了七牛云托管，国内用户建议使用
    when: 
      status: [success,changed,failure]
 
```


也推荐查看我的博文使用 [地址](http://docs.liangzaiya.com/#/gogs+drone%E6%95%B4%E5%90%88)

