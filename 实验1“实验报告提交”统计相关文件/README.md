# get_student_info_lab1.py

       1. 该脚本用于根据edx中 [实验一“实验报告报交”]（http://crl.ptopenlab.com/:8811/courses/Tsinghua/CS101/2015_T1/courseware/9fef5f36997942edab64944a33fd4ac2/146a389c15a646eaa879fd8e74b54c96/）
       练习的回答结果进行统计。
    
       2. 运行该脚本前需要把get_student_info_lab1()中的参数answer_list_dir换成你clone下来的后台数据路径
          answer_list_dir=r"C:\Users\zhangyanni\Desktop\answer-master-004957cb911c1481f53eab3c3a626e5d361b6b5d"
      
      
# student_info_lab1.json


       是运行get_student_info_lab1.py后得到的结果
        格式为：
    
          {"lab_number": "lab1", //实验编号
           "sum": 102,  //学生总人数
           "result": [
                      {"student_ucore_gitlab_url": gitlab地址, 
                       "student_name": 学生姓名,
                       "student_id_or_email": 学生学号或email
                      }, 
                       …………
                     ]
          }
