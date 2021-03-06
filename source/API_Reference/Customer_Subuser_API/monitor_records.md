---
layout: page
weight: 0
title: Monitor Records
navigation:
   show: true
---

Receive a sample of an outgoing message by a specific subuser.

The first step is to create a Monitor Record. Once the monitor record has been created, a reseller can append a monitor record to a subuser. Multiple subuser can be appended to a single monitor record.

{% anchor h2 %}
Create Monitor Record 
{% endanchor %}
Obtain a complete list of all subuser.


{% parameters create %}
 {% parameter 'task' 'Yes' 'Must be set to *create*' 'Create a monitor record' %}
 {% parameter 'name' 'Yes' 'Name must be unique. Can not be more than 255 characters' 'The unique name to identify this monitor record' %}
 {% parameter 'email' 'Yes' 'Must be in email format' 'The email destination to send the email sample to' %}
 {% parameter 'frequency' 'Yes' 'Subuser must be registered under your account' 'The frequency of emails to be sent out' %}
{% endparameters %}


{% apiexample create POST https://api.sendgrid.com/apiv2/customer.monitor api_user=your_sendgrid_username&api_key=your_sendgrid_password&task=create&name=myMonitor&email=example@example.com&frequency=1000 %}
  {% response json %}
{
  "message": "success"
}
  {% endresponse %}
  {% response xml %}
<result>
   <message>success</message>
</result>

  {% endresponse %}
{% endapiexample %}

* * * * *

{% anchor h2 %}
Edit Monitor Record 
{% endanchor %}
Make modifications to an existing Monitor record.


{% parameters edit %}
 {% parameter 'task' 'Yes' 'Must be set to *edit*' 'The task required to edit a monitor' %}
 {% parameter 'name' 'Yes' 'The name of the previous monitor record' 'The monitor record we are going to edit' %}
 {% parameter 'new_name' 'No' 'New name must be unique and can not be more than 255 characters' 'The new monitor record name' %}
 {% parameter 'new_email' 'No' 'Must be in email format' 'The new email destination to send the email sample to' %}
 {% parameter 'new_frequency' 'No' 'Must be an integer and greater than 0' 'The new frequency of emails to be sent out' %}
{% endparameters %}


{% apiexample edit POST https://api.sendgrid.com/apiv2/customer.monitor api_user=your_sendgrid_username&api_key=your_sendgrid_password&task=edit&name=myMonitor&new_name=updatedMonitor&new_email=example@example.com&new_frequency=5 %}
  {% response json %}
{
  "message": "success"
}
  {% endresponse %}
  {% response xml %}
<result>
   <message>success</message>
</result>

  {% endresponse %}
{% endapiexample %}

* * * * *

{% anchor h2 %}
Delete Monitor Record 
{% endanchor %}
Deleting a monitor record will remove it from SendGrid's system. **Make sure no users are currently using the monitor record when removing, or removal will fail.**


{% parameters delete %}
 {% parameter 'task' 'Yes' 'Must be set to *delete*' 'The task required to remove a monitor' %}
 {% parameter 'name' 'Yes' 'Must be a monitor record to remove' 'The unique name to identify this monitor record' %}
{% endparameters %}


{% apiexample delete POST https://api.sendgrid.com/apiv2/customer.monitor api_user=your_sendgrid_username&api_key=your_sendgrid_password&task=delete&name=recordToDelete %}
  {% response json %}
{
  "message": "success"
}
  {% endresponse %}
  {% response xml %}
<result>
   <message>success</message>
</result>

  {% endresponse %}
{% endapiexample %}

* * * * *

{% anchor h2 %}
List All Monitor Records 
{% endanchor %}
List all available monitor records a reseller has.


{% parameters listrecords %}
 {% parameter 'task' 'Yes' 'Must be set to *list*' 'The task required to list all monitor records' %}
{% endparameters %}


{% apiexample listrecords POST https://api.sendgrid.com/apiv2/customer.monitor api_user=your_sendgrid_username&api_key=your_sendgrid_password&task=list %}
  {% response json %}
[
  {
    "name": "sampleNameA",
    "email": "example@example.com",
    "frequency": "1000",
    "users": [

    ]
  },
  {
    "name": "sampleNameB",
    "email": "example@example.com",
    "frequency": "10000",
    "users": [
      "user1@example.com",
      "user2@example.com"
    ]
  }
]
  {% endresponse %}
  {% response xml %}
<monitors>
   <monitor>
      <name>sampleNameA</name>
      <email>example@example.com</email>
      <frequency>1000</frequency>
      <users/>
   </monitor>
   <monitor>
      <name>sampleNameB</name>
      <email>example@example.com</email>
      <frequency>10000</frequency>
      <users>
         <user>user1@example.com</user>
         <user>user2@example.com</user>
      </users>
   </monitor>
</monitors>

  {% endresponse %}
{% endapiexample %}

* * * * *

{% anchor h2 %}
Append A Subuser To A Monitor Record 
{% endanchor %}
Append a monitor record to a existing record onto a subuser.


{% parameters append %}
 {% parameter 'task' 'Yes' 'Must be set to *append*' 'The task required to append a monitor record to a subuser' %}
 {% parameter 'user' 'Yes' 'Subuser must be registered under your account' 'The user we will append a monitor record to' %}
 {% parameter 'name' 'No' 'Must be a valid monitor record' 'The name of the monitor record we will be appending' %}
{% endparameters %}


{% apiexample append POST https://api.sendgrid.com/apiv2/customer.monitor api_user=your_sendgrid_username&api_key=your_sendgrid_password&task=append&name=myMonitor&user=example@example.com %}
  {% response json %}
{
  "message": "success"
}
  {% endresponse %}
  {% response xml %}
<result>
   <message>success</message>
</result>

  {% endresponse %}
{% endapiexample %}

* * * * *

{% anchor h2 %}
Detach A Monitor Record From A Subuser 
{% endanchor %}
Detach a subuser from a monitor record.


{% parameters detach %}
 {% parameter 'task' 'Yes' 'Must be set to *detach*' 'The task required to detach a monitor record to a subuser' %}
 {% parameter 'user' 'Yes' 'Subuser must be registered under your account' 'The subuser we will detach the monitor record from' %}
{% endparameters %}


{% apiexample detach POST https://api.sendgrid.com/apiv2/customer.monitor api_user=your_sendgrid_username&api_key=your_sendgrid_password&task=detach&user=example@example.com %}
  {% response json %}
{
  "message": "success"
}
  {% endresponse %}
  {% response xml %}
<result>
   <message>success</message>
</result>

  {% endresponse %}
{% endapiexample %}
