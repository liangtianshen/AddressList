# AddressList
使用nodejs的express框架和mysql实现的通讯录系统

### 数据库结构详解
* 数据库使用mysql编写
* 数据库中有两个基本表，用户表users和联系人表contacts
* 用户表users的字段有用户名username和密码password
* 联系人表contacts的字段有：序号id、所属用户名user、联系人名name、固话telephone、手机mobile、公司company、职位post

###建表代码
#### 用户表users
    CREATE TABLE users(
    username VARCHAR(15) PRIMARY KEY,
    password VARCHAR(16)
    );

#### 联系人表contacts
    CREATE TABLE contacts(
    id INT(5) PRIMARY KEY AUTO_INCREMENT,
    user VARCHAR(15) ,
    name VARCHAR(15) NOT NULL,
    telephone VARCHAR(15),
    mobile VARCHAR(15),
    company VARCHAR(15),
    post VARCHAR(15),
    FOREIGN KEY (user) REFERENCES users(username) ON DELETE CASCADE
    );

### 插入数据
#### 用户表
    insert into users values("WIGER","123456");

#### 联系人表
    insert into contacts (user,name,telephone,mobile,company,post) values("WIGER","林则徐","88923416","18000100010","清政府","提督");
    insert into contacts (user,name,telephone,mobile,company,post) values("WIGER","Bill Gates","87799201","18086882131","Microsoft","CEO");
    insert into contacts (user,name,telephone,mobile,company,post) values("WIGER","比利海灵顿","88399201","181231482131","新日暮里","森之妖精");
    insert into contacts (user,name,telephone,mobile,company,post) values("WIGER","佟大为","88387301","181231489120","新日暮里","黑暗dark Fa师");
    insert into contacts (user,name,telephone,mobile,company,post) values("WIGER","马化腾","81256983","13923417895","Tencent","CEO");
    insert into contacts (user,name,telephone,mobile,company,post) values("WIGER","马云","88888888","13688129934","Alibaba","CEO");

### 数据操作
#### 选择
    SELECT name,telephone,mobile,company,post FROM contacts WHERE name LIKE 'Ma%' and user='WIGER';
    SELECT name,telephone,mobile,company,post FROM contacts WHERE company LIKE 'T%' and user='WIGER';

#### 修改
    UPDATE contacts SET mobile='18086882131' WHERE name='MaHuaTeng';

#### 删除
    DELETE FROM contacts WHERE user='WIGER"' AND name='林则徐';

#### 插入
    INSERT INTO contacts VALUES('WIGER','木吉','12345678','11223344556','新日暮里','社长');