# soap-over-http
Activity example – SOAP over HTTP Example

Example Description

This example illustrates both the creation and invocation of a SOAP over HTTP web service using TIBCO BusinessWorks. 

The web service created in this example queries all the books in a bookstore by their Author. The web service has one operation, which is implemented in a Process Definition. A client for this web service is configured using the service’s WSDL file. At run-time, the client sends a SOAP request that contains a name of an Author and receives a list of books.

Description of the project

The following shared resources are defined in the project:

-          Books.xsd – The XSD Schema file that contains the definition of the types used by the web service’s interface

-          BooksInterface.wsdl – The WSDL file that represents the interface of the web service

-          BookStore.xml – An XML document that represents the bookstore database

-          BooksService.wsdl – The WSDL file that describes the web service

-          HTTPConnection.sharedHttp – The HTTP Connection Shared Resource that contains the transport configuration

-          QueryBooksByAuthor.process – The process definition that represents the web service. The first activity in this process definition is the SOAP Event Source, which stores the Web Service’s configuration. The event source’s output schema contains the Author parameter that is used for querying the bookstore. This parameter is mapped to the input of a Call Process activity, which calls another process definition (see bellow) that defines the query.  The Call Process activity returns a list of books that is mapped to the input of the SOAP Send Reply activity.

-          Query.process – The process definition that represents the business logic of the service. This contains a Read File activity that reads the bookstore (XML document) and an XML Parse activity that parses the XML document. Finally, the filter is executed at the end of the process flow in the End activity (see the End activity’s Input tab).

-          WSClient.process – The client of the web service. This process definition contains a Timer activity, that is used for triggering the client and a SOAP Request Reply activity that is the actual client of the web service.

Setup

All the resources needed to run this example are part of the project. There is just one global variable that must be set:

ReadBookStoreXML – This is the full name of the XML file that contains the bookstore database (BookStore.xml).

Running the example

To run the example, follow these steps:

Set the global variable that is used in this project, as specified in the “Setup” section.
In TIBCO Designer, create a new project and import the project zip file “soap_over_http.zip” by selecting the Project->Import Full Project menu selection.
Once the project is imported, save the project.
Click the Tester tab, and then click the Start Testing Viewed Process icon in the tester window.
Select the following Process Definitions: QueryBooksByAuthor and WSClient.
Click on Load Selected button.
The activities and transition lines are highlighted in green as incoming information is processed.
Click on the SOAP Request Reply activity and then select the “Output Data” tab. Verify that the query was executed properly.
Expected Results

The SOAP Request Reply Activity should execute successfully. The query should return one book with the following title: “The Power of Now”.

Troubleshooting

If you have any issues when running this example, please contact support@tibco.com including a detailed desc
