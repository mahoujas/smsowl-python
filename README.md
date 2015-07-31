## Sms Owl Python Wrapper

This package is wrapper of Sms Owl REST API hosted at [https://smsowl.in](https://smsowl.in). Sms Owl provides transactional and promotional SMS Gateway services.

### Installing Sms Owl package

Use following command to install python package.

	$ pip install smsowl

### Import the Class

	from smsowl.client import SmsOwl

### Configuring credentials

Credentials should be configured before sending SMS. Credential should be passed as constructor argument for SmsOwl constructor
	
	smsowl = SmsOwl("YOUR-ACCOUNT-ID", "YOUR-API-KEY")


### Sending promotional SMS


##### sendPromotionalSms(senderId,to,message,smsType)

 - senderId: Sender Id registered and approved in Sms Owl portal.
 - to: Either single number with country code or list of phone numbers.
 - message: Message to be sent.
 - smsType: It can have either of two values `normal` or `flash` (optional)
	
	
	
		try:
		   smsId = smsowl.sendPromotionalSms("TESTER", "+9189876543210", "Hello Python", "flash");
		   	//Process smsId if you need to
		except Exception as e:
		    //Handle exception.

Return value is Sms Id for single SMS and List of SMS ids for Bulk Sms


##### sendPromotionalSms(senderId,to,message)

Same as above but smsType defaults to `normal`

### Sending Transactional SMS

##### sendTransactionalSms(senderId,to,templateId,placeholderDict);

 - senderId: Sender Id registered and approved in Sms Owl portal.
 - to: Destination number with country prefix. Only single number can be specified.
 - templateId: Template Id of message. Only template message can be send via transactional route.
 - placeholderDict: Placeholder values.

Lets assume templateId of `39ec9de0efa8a48cb6e60ee5` with following template.

	Hello {customerName}, your invoice amount is Rs. {amount}.

-


	try:
        smsId = smsowl.sendTransactionalSms("TESTER", "+919876543210", "39ec9de0efa8a48cb6e60ee5",{"CustomerName": "Bob", "Amount": 200 });
        //Process smsid if needed.
    except Exception as e:
        //Handle exception


Return value is Sms Id.