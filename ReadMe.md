Orders.py为整个程序中最主要的组件，其中包含了对于一些重要数据的调用，数据库的调用以及创建，以及给客户发送相关订单信息，可以通过运行main.py来对orders.py进行调用。其中与orders.py文件相关联的文件包括了sqlite_database.Py，restaurant_is_open.py以及OrderWebsiteList.json。

如果有对于twilio信息改写的需求的话可以通过修改.bashrc文件中的account_sid，auth_token以及from_phone（位于.bashrc 的第22行到第24行）

![img1](https://github.com/Gilria/Orders_Pictures/blob/main/Order_Pictures/%E5%9B%BE%E7%89%871.png) 

如果需要对餐厅Api地址进行添加的话可以对OrderWebsiteList.json中的数据进行修改，具体格式如下：![img2](https://github.com/Gilria/Orders_Pictures/blob/main/Order_Pictures/%E5%9B%BE%E7%89%872.png)

restaurantName代表了餐厅的名字，restaurantUrl为Api地址，由于本程序经过了多次的更新，所以其中的timeInterval数据其实并没有调用，所以只需要按照上面的格式填写timeInterval的值为23即可。

通过改写confirm_string，miss_string，reject_string，以及pending_string，可以实现对客户发送接受，丢失，拒单和待处理方面信息的修正（位于orders.py的29行到64行）。

![img3](https://github.com/Gilria/Orders_Pictures/blob/main/Order_Pictures/%E5%9B%BE%E7%89%873.png) 

a,b格式分别代表了订单与订位。

餐厅的营业时间以及关闭时间可以通过修改restaurant_open_time.json文件来实现，当然其中还包含了餐厅的停运时间（closed_days）以及同一个星期但营业时间不同的改动（operating_days），只需要将星期几填写入对应的中括号中。当然如果有operating_days相关需求的话需要创建新的start以及end信息。具体例子为

![img4](https://github.com/Gilria/Orders_Pictures/blob/main/Order_Pictures/%E5%9B%BE%E7%89%874.png) 

运行script.py可以生成excel表格来查看之前的所有订单信息，可以通过修改search_index.json中餐馆的starting_datatime以及ending_time来对excel文件中的订单数据进行检索，以用来排除设定时间外的订单信息，具体参考下图：

![img5](https://github.com/Gilria/Orders_Pictures/blob/main/Order_Pictures/%E5%9B%BE%E7%89%875.png) 

第三行以及第四行为检索的时间段，第五行为餐厅所在的时区，如果需要改写excel表格的名字则可通过改写第七行中的数据来达成，第8行则是如果需要额外显示其他value的话，可以进行添加，具体的value name位于sqlite_database.py中的json_keys当中（第9行到第21行）。

![img6](https://github.com/Gilria/Orders_Pictures/blob/main/Order_Pictures/%E5%9B%BE%E7%89%876.png) 