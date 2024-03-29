# Java-Assignment

##REST Service - Web Application
####Configurations
* Data Base Configuration
  * mvc-dispatcher-servlet - assignment_rest\src\main\webapp\WEB-INF\mvc-dispatcher-servlet.xml
    * ```xml
    	.....
        <!-- Data Source -->
	      <bean id="dataSource" class="org.apache.commons.dbcp.BasicDataSource" destroy-method="close">

    		<property name="driverClassName" value="com.mysql.jdbc.Driver" />
    		<!-- local -->
    		<property name="url" value="jdbc:mysql://localhost:3306/<data_base>" />
    		<property name="username" value="<user_name>" />
    		<property name="password" value="<password>" />
		
	      </bean>
	      <!-- Data Source End -->
	      
	 
####REST Operations
*  List All Hotels - GET /hotel
  *  <http://localhost:8081/assignment_rest/hotel/>
*  Find By Id - GET /hotel/{id}
  *  <http://localhost:8081/assignment_rest/hotel/{id}>
*  Find By Hotel Name - GET /hotel/name/{name}
  *  <http://localhost:8081/assignment_rest/hotel/name/{name}>
*  Find By Hotel Name Keyword - GET /hotel/keyword/{keyword}
  *  <http://localhost:8081/assignment_rest/hotel/keyword/{keyword}>
*  Add New Hotel - POST /hotel
  *  <http://localhost:8081/assignment_rest/hotel/>

####Source Code
* Model (Persistence layer - Mapped with Data Base) - com.assignment.rest.models
  * Hotel
  * Address
* DAO (Handle all the CRUD Operations for the Models) - com.assignment.rest.models.dao
  * DAOFacade - Contain implementaion of the CRUD operations.This is a Genaric class.Performs according to the requested Model
  * HotelDAO - Supplly Hotel model to the DAOFacade
* Controller (Contain REST opration implementation) - com.assignment.rest.controllers
  * HotelController
  
##Android - Mobile Client
####Configurations
* Server Location Configuration
  * AndroidManifest - Assignment\app\src\main\AndroidManifest.xml
    * ```xml

        <!-- http://host_address -->
        <meta-data
            android:name="server_base_url"
            android:value="http://<server_path>/assignment_rest" />
    


####Source Code
* MainActivity - com.assignment
  * this is the application's launcher activity.And contaion implementaion of the Navigator
* AddHotelFragment - com.assignment.fragments
  * Perform the Add new Hotel operation. User provides hotel name and hotel address.Hotel current location is get by using Android Location API(latitude and longitude). Then the new hotel details are sent to the REST service.[LegoRoid](https://github.com/TharangaLOVI/LegoRoid) lib is used as a Android HTTP client.
* SearchHotelsFragment - com.assignment.fragments
  * User is able to search hotel by name(or name keyword).application call the /hotel/keyword/{keyword} REST operation, if there are any hotels available for the requested name , application list down the hotel details. 

  


