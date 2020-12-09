# 实验目的
  掌握Java中抽象类和抽象方法的定义；
  掌握Java中接口的定义，熟练掌握接口的定义形式以及接口的实现方法；
  了解异常的使用方法，并在程序中根据输入情况做异常处理。
  
  
# 实验内容

  某学校为了给学生提供勤工俭学机会，也减轻授课教师的部分压力，准许博士研究生参与课程的助教工作。
  此时，该博士研究生有双重身份：学生和助教教师。
   1.设计两个管理接口：学生管理接口和教师管理接口。
   学生接口必须包括缴纳学费、查学费的方法；教师接口包括发放薪水和查询薪水的方法。
   2.设计博士研究生类，实现上述的两个接口，
   该博士研究生应具有姓名、性别、年龄、每学期学费、每月薪水等属性。（其他属性及方法，可自行发挥）
   3.编写测试类，并实例化至少两名博士研究生，统计他们的年收入和学费。
   根据两者之差，算出每名博士研究生的年应纳税金额（国家最新工资纳税标准，请自行检索）。
   
   
   
   
# 实验要求
  1.在博士研究生类中实现各个接口定义的抽象方法;
  2.对年学费和年收入进行统计，用收入减去学费，求得纳税额；
  3.国家最新纳税标准（系数），属于某一时期的特定固定值，与实例化对象没有关系，考虑如何用static final修饰定义。
  4.实例化研究生类时，可采用运行时通过main方法的参数args一次性赋值，也可采用Scanner类实现运行时交互式输入。
  5.根据输入情况，要在程序中做异常处理。
  
  
  
#  实验过程
  1.创建2个接口 
  用public main void setFee(double fee)定义学生缴纳学费
  public double getFee()定义学生查每年学费 应当缴纳的费用；
 用public main void setPay(double pay)定义教师发放薪水
  public double getPay()定义教师查询薪水的方法。

  创建博士研究生类 DoctoralStu ，用implements实现2个接口 StuManage和TchManage ，
  定义姓名、性别、年龄、每学期学费、每月薪水等属性，设置姓名、性别、年龄的set、get方法；
  重写前两个接口中所有方法

  创建测试类Test，
  用Scanner相关方法实现运行，即实例化博士生；
  写出年收入和学费的计算方法以及两者之差；
  查询国家最新工资纳税标准，写出该博士生的年应纳税金额，用税率 乘（年收入-学费）。

  异常处理，根据具体情况而定（方法多样）。
  try-catch语句：
  将可能出现异常的语句放在try部分，一旦try部分抛出异常对象，那么try部分将立刻结束执行
  （如果try部分没有抛出异常，则继续执行try部分的语句。即try部分不受任何影响。）
  转而执行相应的catch部分，异常后的处理放在catch部分。


核心代码
package java3;
class Java3 {

    public static void main(String[] args) {
        try {
            System.out.println("******************研究生一*********************");
            Doctor xm = new Doctor();
            xm.setName("王一");
            xm.setAge(18);
            xm.setNumber(2019666888);
            xm.setSex("男");
            xm.setTuition(8000);
            xm.setSalary(1200);
            System.out.println("学生姓名:" + xm.getName());
            System.out.println("学生年龄:" + xm.getAge());
            System.out.println("学生编号:" + xm.getNumber());
            System.out.println("学生性别:" + xm.getSex());
            xm.find_tuition();
            xm.find_salary();
            xm.taxation();
            System.out.println("******************研究生二*********************");
            Doctor xf = new Doctor();
            xf.setName("张二");
            xf.setAge(20);
            xf.setNumber(2019666999);
            xf.setSex("女");
            xf.setTuition(8000);
            xf.setSalary(1185);
            System.out.println("学生姓名:" + xf.getName());
            System.out.println("学生年龄:" + xf.getAge());
            System.out.println("学生编号:" + xf.getNumber());
            System.out.println("学生性别:" + xf.getSex());
            xf.find_tuition();
            xf.find_salary();
            xf.taxation();
        } catch (Exception e) {
            System.out.println("数据异常");
        }

    }

    interface Manger_student {
        double find_tuition();

        double afford_tuition();
    }

    interface Manger_teacher {
        double STANDARD = 0.2;

        double find_salary();

        double get_salary();
    }


    public static class Doctor implements Manger_student, Manger_teacher {
        public Doctor() {

        }

        public Doctor(String name, int age, int number, String sex, double tuition, double salary) {
            this.name = name;
            this.age = age;
            this.number = number;
            this.sex = sex;
            this.tuition = tuition;
            this.salary = salary;
        }

        private String name;
        private int age;
        private int number;
        private String sex;
        private double tuition;
        private double salary;


        public void setName(String name) {
            this.name = name;
        }

        public void setAge(int age) {
            this.age = age;
        }

        public void setNumber(int number) {
            this.number = number;
        }

        public void setSex(String sex) {
            this.sex = sex;
        }

        public void setTuition(double tuition) {
            this.tuition = tuition;
        }

        public void setSalary(double salary) {
            this.salary = salary;
        }

        public String getName() {
            return name;
        }

        public int getAge() {
            return age;
        }

        public String getSex() {
            return sex;
        }

        public double getTuition() {
            return tuition;
        }

        public int getNumber() {
            return number;
        }

        public double getSalary() {
            return salary;
        }


        public double find_tuition() {
            System.out.println("每年学费：" + tuition);
            return tuition;
        }

        public double find_salary() {
            System.out.println("每月工资：" + salary);
            return salary;
        }

        public double afford_tuition() {
            System.out.println("缴纳成功，已缴纳学费" + tuition);
            return tuition;
        }

        public double get_salary() {
            double c;
            c = salary - (salary - 800) * STANDARD;
            System.out.println("薪水已经发放，发放金额：" + c);
            return salary;
        }

        public void taxation() {
            double a;
            a = 12 * ((salary - 800) * STANDARD);
            System.out.println("每年应纳税为：" + a);
        }
    }
}

#   实验结果
******************研究生一*********************
学生姓名:王一
学生年龄:18
学生编号:2019666888
学生性别:男
每年学费：8000.0
每月工资：1200.0
每年应纳税为：960.0
******************研究生二*********************
学生姓名:张二
学生年龄:20
学生编号:2019666999
学生性别:女
每年学费：8000.0
每月工资：1185.0
每年应纳税为：924.0
![image](https://github.com/2019311131/java3-/blob/main/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20201209215721.png)
![image](https://github.com/2019311131/java3-/blob/main/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20201209215751.png)
#       实验感想
实验很成功 感觉非常好 再接再厉 继续努力 做大做强
