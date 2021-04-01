# GarretaUI
Garreta UI development projects
[customersURI.txt](https://github.com/FrankeeAl/GarretaUI/files/6242064/customersURI.txt)

----------------------------------------------------------------------------------
Validate Number
URI
http://garreta.infinityfreeapp.com/customers.php?operation=validateContactNumber&contactNumber=09265866985
Props:
{
	operation : validateContactNumber
	contactNumbert: ex.09265866985

}
Description
validates if the inputted/extracted contact number is valid or not yet in use.
RETURNS
		if valid contact number 
			it will return a validation code in JSON format
					[{"validation_code":4527}]
			- the validation code is a 4 digit random number that simulates the SMS response from a server
		else
			returns the message "Contact number already in use." 

------------------------------------------------------------------------------------
Add New
URI
http://garreta.infinityfreeapp.com/customers.php?operation=addNew&name=Benjamin%20Button&contactNumber=09265844562&email=benj@yahoo.com&address=bulua,%20cagayan%20de%20oro%20city&birthDate=92/08/21&gender=male&password=benj156
Props {
	operation="addNew"
		name
		contactNumber
		email
		address
		birthDate (NOTE: format is Y-m-d)
		gender
		passsword
}
Description
adds a new customer record. This is done after checking the inputted/extracted contact number does not exist in the database.
RETURN
			[{"new_Id":4}]

------------------------------------------------------------------------------------
updateProfile
URI
http://garreta.infinityfreeapp.com/customers.php?operation=updateProfile&id=14&name=Benjamin%20Button&contactNumber=09356418675&email=benjamin@gmail.com&address=bulua,%20cagayan%20de%20oro%20city&birthDate=92/08/21&gender=male&password=benjamin123

Props
[
  {
    "return_code": "1"
  }
]

Description
updates customer profile. This is called when customer updates his profile
	operation = "updateProfile"
		id
		name
		email
		address
		birthDate (NOTE: format is Y-m-d)
		gender
		passsword
		NOTE: contactNumber cannot be edited

------------------------------------------------------------------------------------
Get Customer Details
URI
http://garreta.infinityfreeapp.com/customers.php?operation=getCustomerDetails&id=2
Props	
[
  {
    "cust_id": 2,
    "cust_name": "Pitok Batolata",
    "cust_email": "pitok@yahoo.com",
    "cust_contactNumber": "22222222222",
    "cust_address": "Malaybalay",
    "cust_birthDate": "1999-04-10",
    "cust_registrationDate": "2021-02-26",
    "cust_status": 1,
    "cust_gender": "Male",
    "cust_reputation": 0,
    "cust_numberOfOrders": 0,
    "cust_numberOfCancelledOrders": 0,
    "cust_password": "lasku"
  }
]
Description
this returns all data from a customer's profile
RETURNS
		- customer details in JSON format, returns blank if customer id is not found 

------------------------------------------------------------------------------------

Login
URI
http://garreta.infinityfreeapp.com/customers.php?operation=login&contactNumber=09265844562&password=benj156

Props
[
  {
    "cust_id": 15,
    "cust_name": "Benjamin Button",
    "cust_email": "benj@yahoo.com",
    "cust_contactNumber": "09265844562",
    "cust_address": "bulua, cagayan de oro city",
    "cust_birthDate": "1992-08-21",
    "cust_registrationDate": "2021-03-31",
    "cust_status": 1,
    "cust_gender": "male",
    "cust_reputation": 0,
    "cust_numberOfOrders": 0,
    "cust_numberOfCancelledOrders": 0,
    "cust_password": "benj156"
  }
]
Description
handles customer normal login procedure.	
RETURNS
		if successful
			returns customer's personal details
		else
			returns blank
------------------------------------------------------------------------------------

Login2
URI
http://garreta.infinityfreeapp.com/customers.php?operation=login2&contactNumber=09265844562&password=benj156
Props 

[
  {
    "personalDetails": {
      "cust_id": 14,
      "cust_name": "Benjamin Button",
      "cust_email": "benj@yahoo.com",
      "cust_contactNumber": "09265844562",
      "cust_address": "bulua, cagayan de oro city",
      "cust_birthDate": "1992-08-21",
      "cust_registrationDate": "2021-03-30",
      "cust_status": 1,
      "cust_gender": "male",
      "cust_reputation": 0,
      "cust_numberOfOrders": 0,
      "cust_numberOfCancelledOrders": 0,
      "cust_password": "benj156"
    }
  },
  {
    "deliveryAddress": [
      {
        "del_id": 13,
        "del_customerId": 14,
        "del_address": "zone 8, bulua, cagayan de oro city",
        "del_longitude": 124.619204999999993788151186890900135040283203125,
        "del_latitude": 8.504374999999999573674358543939888477325439453125,
        "del_notes": "Along Bulua National High School"
      },
      {
        "del_id": 16,
        "del_customerId": 14,
        "del_address": "zone 8, bulua, cagayan de oro city",
        "del_longitude": 124.619204999999993788151186890900135040283203125,
        "del_latitude": 8.504374999999999573674358543939888477325439453125,
        "del_notes": "Along Bulua National High School"
      }
    ]
  }
]
Description
handles customer login procedure but returns a customer details with delivery address details.
RETURNS
		if successful
			returns customer's personal details and all delivery address of that customer in nested JSON format
		else
			returns blank
------------------------------------------------------------------------------------
Get All Records
URI
http://garreta.infinityfreeapp.com/customers.php?operation=getAllRecords
Props
[
  {
    "cust_id": 14,
    "cust_name": "Benjamin Button",
    "cust_email": "benjamin@gmail.com",
    "cust_contactNumber": "09265844562",
    "cust_address": "bulua, cagayan de oro city",
    "cust_birthDate": "1992-08-21",
    "cust_registrationDate": "2021-03-30",
    "cust_status": 1,
    "cust_gender": "male",
    "cust_reputation": 0,
    "cust_numberOfOrders": 0,
    "cust_numberOfCancelledOrders": 0,
    "cust_password": "benjamin123"
  },
  {
    "cust_id": 4,
    "cust_name": "John Ruiz Borja",
    "cust_email": "johnruizborja@gmail.com",
    "cust_contactNumber": "44444444444",
    "cust_address": "Simaya Malaybalay CIty",
    "cust_birthDate": "1972-04-10",
    "cust_registrationDate": "2021-03-06",
    "cust_status": 1,
    "cust_gender": "Male",
    "cust_reputation": 0,
    "cust_numberOfOrders": 0,
    "cust_numberOfCancelledOrders": 0,
    "cust_password": "ambotlang"
  },
  {
    "cust_id": 1,
    "cust_name": "Kulas Dimalas",
    "cust_email": "kulas@yahoo.com",
    "cust_contactNumber": "11111111111",
    "cust_address": "Cogon",
    "cust_birthDate": "0000-00-00",
    "cust_registrationDate": "0000-00-00",
    "cust_status": 1,
    "cust_gender": "1987-0",
    "cust_reputation": 0,
    "cust_numberOfOrders": 0,
    "cust_numberOfCancelledOrders": 0,
    "cust_password": "tokpi"
  },
  {
    "cust_id": 12,
    "cust_name": "Marilou Lebria",
    "cust_email": "marilou@gmail.com",
    "cust_contactNumber": "55555555555",
    "cust_address": "Kalasungay Malaybalay CIty",
    "cust_birthDate": "1994-04-10",
    "cust_registrationDate": "2021-03-07",
    "cust_status": 1,
    "cust_gender": "Female",
    "cust_reputation": 0,
    "cust_numberOfOrders": 0,
    "cust_numberOfCancelledOrders": 0,
    "cust_password": "password"
  },
  {
    "cust_id": 5,
    "cust_name": "Noel Ambador",
    "cust_email": "ambador@gmail.com",
    "cust_contactNumber": "09265866985",
    "cust_address": "Carmen Cagayan de Oro City",
    "cust_birthDate": "0000-00-00",
    "cust_registrationDate": "2021-03-07",
    "cust_status": 1,
    "cust_gender": "Male",
    "cust_reputation": 0,
    "cust_numberOfOrders": 0,
    "cust_numberOfCancelledOrders": 0,
    "cust_password": "noel123"
  },
  {
    "cust_id": 2,
    "cust_name": "Pitok Batolata",
    "cust_email": "pitok@yahoo.com",
    "cust_contactNumber": "22222222222",
    "cust_address": "Malaybalay",
    "cust_birthDate": "1999-04-10",
    "cust_registrationDate": "2021-02-26",
    "cust_status": 1,
    "cust_gender": "Male",
    "cust_reputation": 0,
    "cust_numberOfOrders": 0,
    "cust_numberOfCancelledOrders": 0,
    "cust_password": "lasku"
  }
]
Description
retrieves all customer records from the database in JSON format

------------------------------------------------------------------------------------
Change Password
URI
http://garreta.infinityfreeapp.com/customers.php?operation=changePassword&id=12&password=marilou2021

Props
[
  {
    "return_code": 1
  }
]

DESCRIPTION
	enables users to change their password
PARAMETERS
	operation = "changePassword"
	id
	password

------------------------------------------------------------------------------------

Customer's DeliveryAddressRoutines

------------------------------------------------------------------------------------
addNewDeliveryAddress
URI
http://garreta.infinityfreeapp.com/customers.php?operation=addNewDeliveryAddress&id=14&deliveryAddress=zone%208,%20bulua,%20cagayan%20de%20oro%20city&latitude=8.504375&longitude=124.619205&notes=Along%20Bulua%20National%20High%20School

Props
[
  {
    "new_Id": 17
  }
]
Description

add new customer's delivery address
PARAMETERS
		operation = "addNewDeliveryAddress"
		id
		deliveryAddress
		longitude
		latitude
		notes
RETURNS:
	the new delivery address id 
------------------------------------------------------------------------------------
updateDeliveryAddress
URI
http://garreta.infinityfreeapp.com/customers.php?operation=updateDeliveryAddress&id=4&deliveryAddress=Centro%20Malaybalay%20City,%20Bukidnon&longitude=125.1678&latitude=8.0041&notes=Beside%20bakery%20store
Props

[
  {
    "return_code": "1"
  }
]

Description
add new customer's delivery address
RETURNS:
	the new delivery address id 
	[{"new_Id":10}]
-------------------------------------------------------------------------------------
getAllDeliveryAddressByCustomer
URI
http://garreta.infinityfreeapp.com/customers.php?operation=getAllDeliveryAddressByCustomer&id=4
Props
[
  {
    "del_id": 15,
    "del_customerId": 4,
    "del_address": "Centro Malaybalay City, Bukidnon",
    "del_longitude": 125.16779999999999972715158946812152862548828125,
    "del_latitude": 8.0040999999999993264054864994250237941741943359375,
    "del_notes": "Beside bakery store"
  }
]
Description
returns all delivery address for a certain customer
customer's all delivery addresses in JSON format

-------------------------------------------------------------------------------------
