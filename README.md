复制代码
### 作者介绍：
* author：Siwen
### 博客地址：
* http://www.cnblogs.com/Sigua666/p/python.html

### 功能实现
    1. 创建北京、上海 2 所学校
    2. 创建linux , python , go 3个课程 ， linux\py 在北京开， go 在上海开
    3. 课程包含，周期，价格，通过学校创建课程
    4. 通过学校创建班级， 班级关联课程、讲师
    5. 创建学员时，选择学校，关联班级
    5. 创建讲师角色时要关联学校，
    6. 提供两个角色接口
    6.1 学员视图， 可以注册， 交学费， 选择班级，
    6.2 讲师视图， 讲师可管理自己的班级， 上课时选择班级， 查看班级学员列表 ， 修改所管理的学员的成绩
    6.3 管理视图，创建讲师， 创建班级，创建课程
    7. 上面的操作产生的数据都通过pickle序列化保存到文件里
    （所有功能均实现）

###程序需知
    2.程序为初始化状态，执行程序，数据库进行初始化，初始化只生成北京、上海学校名
    3. 数据库结构main_dict 储存主要的逻辑结构：
        {学校名：{课程名1：{"teacher":讲师，"class"：班级}，课程名2：{"teacher":讲师2，"class"：班级2}}，
        学校名：{课程名3：{"teacher":讲师3，"class"：班级3}，课程名4：{"teacher":讲师4，"class"：班级4}}}
        存储的数据类型都为实例对象
       数据库结构teacher_dict 存储讲师与班级的对应关系，用于方便讲师登录系统认证，结构为
        {讲师：{class：班级}
        两个数据库文件均可扩展
    4. 程序实现了以下严格限制：
       ①一个学校里面不能出现同名的课程
       ②一个课程只能有一个讲师
       ③讲师被聘用后，不能再进行聘用，一个讲师也只能教一门课程(教python，就不能再教linux了)
       ④班级只能对应一门课程，班级名只能出现一次，不能重复(python班级s14，linux的班级就不能再出现s14班级了）

     程序按功能分出不同的模块，可以更简洁