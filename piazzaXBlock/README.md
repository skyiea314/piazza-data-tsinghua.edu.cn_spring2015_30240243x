#一、文件介绍

   1.piazza_cid_xblock:是根据cid只显示某个特定的讨论记录的xblock
   
   2.piazza_feed_xblock:是根据标签筛选讨论记录的xblock。其中下拉菜单列出所有的标签，其他的是popular的标签。
   
   3.piazza_together_xblock：是提供了三种显示方式的xblock：
   
      （1）只显示指定cid的讨论记录的页面；
      （2）只显示根据标的签筛选讨论记录的页面；
      （3）两者同时显示，与piazza界面基本相同；
      
      
#二、XBlock的安装。(以piazza_together_xblock的安装为例)

   1.把在线代码编辑器xblock克隆到edx服务器

        sudo git clone https://github.com/xyongcn/piazza-data-tsinghua.edu.cn_spring2015_30240243x.git
        
   2.进入到xblock安装目录，更改piazza.html
   
        cd piazza-data-tsinghua.edu.cn_spring2015_30240243x/piazzaXBlock/piazza_together_xblock/piazza/static/html/
        vi piazza.html
        
     把所有的166.111.68.45:11133  改为你的open edx域名，保存更改
        
       
   3.安装xblock
```
        cd piazza-data-tsinghua.edu.cn_spring2015_30240243x/piazzaXBlock/piazza_together_xblock/
        sudo -u edxapp /edx/bin/pip.edxapp install .
 
```         
   4.把example-together复制到 /edx/var/edxapp/staticfiles/目录下,并
      增加所有人对其的读权限 
        
        cd piazza-data-tsinghua.edu.cn_spring2015_30240243x
        
        sudo cp -r staticfiles/* /edx/var/edxapp/staticfiles/
        sudo chmod a+r -R /edx/var/edxapp/staticfiles/example-together/
        
   5.使xblock可用(如果studio中高级设己开启，此步骤可跳过)

     1）edx-platform/lms/envs/common.py中去掉注释：

         # from xmodule.x_module import prefer_xmodules
         # XBLOCK_SELECT_FUNCTION = prefer_xmodules
 
     2）edx-platform/cms/envs/common.py,中去掉注释：

        # from xmodule.x_module import prefer_xmodules
        # XBLOCK_SELECT_FUNCTION = prefer_xmodules、
 
     3）edx-platform/cms/envs/common.py中把

       'ALLOW_ALL_ADVANCED_COMPONENTS': False,
        改成：
       'ALLOW_ALL_ADVANCED_COMPONENTS': True,

  6.重启edx服务（一定不能忘了重启，否则block无法在studio中显示）
  
         sudo /edx/bin/supervisorctl restart edxapp:
         sudo /edx/bin/supervisorctl restart edxapp_worker:
         
  7.在Studio中把在线代码编辑器block添加到课程的高级设置中。

         1）登录到Studio,打开你的课程
         2）settings->Advanced Setting
         3)把键”advanced_modules”的值改为piazza.

  8.把在线代码编辑器block添加到课程，在studio中

       1）Edit编辑一个单元
       2）Advanced->piazza

   如果在高级按钮中没有看到piazza选项，通常情况下是权限问题，请确认用户www-data对路径/edx/app/edxapp/venvs/edxapp/lib/python2.7/site-packages/piazza以及/edx/app/edxapp/venvs/edxapp/lib/python2.7/site-packages/piazza_xblock.egg-info有读权限
  
安装好之后就可以在cms中看到并使用该组件


      
