---
title: "Zadávání poznámek k typové datové sady"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 4528393d3d9491d9c1f12a867eb093e75d028f3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="annotating-typed-datasets"></a>Zadávání poznámek k typové datové sady
Poznámky umožňují změnit názvy elementů v váš zadaný <xref:System.Data.DataSet> beze změny základní schéma. Úprava názvy elementů v základní schéma by způsobilo zadaného objektu **datovou sadu** k odkazování na objekty, které není neexistuje ve zdroji dat, a také dojít ke ztrátě odkaz na objekty, které existují v datovém zdroji.  
  
 Použití poznámek, můžete přizpůsobit názvy objektů v váš zadaný **datovou sadu** smysluplnější názvy, provedení čtení kódu a váš zadaný **datovou sadu** usnadňuje klientům používat, a nechat základní schématu beze změn. Například následující element schématu pro **zákazníci** tabulky **Northwind** by způsobilo databáze **DataRow** název objektu  **CustomersRow** a <xref:System.Data.DataRowCollection> s názvem **zákazníci**.  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 A **kolekci DataRowCollection** název **zákazníci** má smysl v kódu klienta, ale **DataRow** název **CustomersRow** je zavádějící protože je jediný objekt. Společné scénáře, objekt by se označovat taky bez **řádek** identifikátor a místo toho by se jednoduše označovat jako **zákazníka** objektu. Řešení, je přidání poznámek ke schématu a identifikovat nové názvy pro **DataRow** a **kolekci DataRowCollection** objekty. Toto je poznámkami verze předchozí schématu.  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 Určení **TypedName služby Active Directory** hodnotu **zákazníka** bude mít za následek **DataRow** název objektu **zákazníka**. Určení **typedPlural** hodnotu **zákazníci** zachovává **kolekci DataRowCollection** název **zákazníci**.  
  
 V následující tabulce jsou k dispozici pro použití poznámky.  
  
|Poznámka|Popis|  
|----------------|-----------------|  
|**TypedName služby Active Directory**|Název objektu.|  
|**typedPlural**|Název kolekce objektů.|  
|**typedParent**|Název objektu při uvedených v nadřazené vztahy.|  
|**typedChildren**|Název metody, které mají být vráceny od vztahu podřízené objekty.|  
|**nullValue**|Hodnotu, pokud je zadaná hodnota **DBNull**. V následující tabulce najdete **nullValue** poznámky. Výchozí hodnota je **_throw**.|  
  
 V následující tabulce jsou uvedeny hodnoty, které lze zadat pro **nullValue** poznámky.  
  
|nullValue hodnota|Popis|  
|---------------------|-----------------|  
|*Nahrazující hodnotou*|Zadejte hodnotu, který se má vrátit. Vrácená hodnota se musí shodovat s typem elementu. Například použít `nullValue="0"` vrátit 0 pro pole hodnotu null celé číslo.|  
|**_throw**|Vyvolejte výjimku. Toto nastavení je výchozí.|  
|**_null**|Vrátí hodnotu null nebo vyvolána výjimka, pokud je zjištěn primitivní typ.|  
|**_empty**|Řetězce, vrátí **String.Empty**, jinak vrátí objekt vytvořený z prázdný konstruktor. Jestliže je primitivní typ, vyvolá výjimku.|  
  
 Následující tabulka uvádí výchozí hodnoty pro objekty v zadaný **datovou sadu** a poznámky k dispozici.  
  
|Objekt nebo metoda/událost|Výchozí|Poznámka|  
|---------------------------|-------------|----------------|  
|**DataTable**|TableNameDataTable|typedPlural|  
|**DataTable** metody|NewTableNameRow<br /><br /> AddTableNameRow<br /><br /> DeleteTableNameRow|TypedName služby Active Directory|  
|**Kolekci DataRowCollection**|Název tabulky|typedPlural|  
|**DataRow**|TableNameRow|TypedName služby Active Directory|  
|**DataColumn**|DataTable.ColumnNameColumn<br /><br /> DataRow.ColumnName|TypedName služby Active Directory|  
|**Vlastnost**|PropertyName|TypedName služby Active Directory|  
|**Podřízené** přístupového objektu|GetChildTableNameRows|typedChildren|  
|**Nadřazené** přístupového objektu|TableNameRow|typedParent|  
|**Datová sada** události|TableNameRowChangeEvent<br /><br /> TableNameRowChangeEventHandler|TypedName služby Active Directory|  
  
 Použít zadali **datovou sadu** poznámky, musí zahrnovat následující **xmlns** odkaz v schéma schématu XML definition language (XSD). (Vytvoření xsd z tabulek databáze naleznete v tématu <xref:System.Data.DataSet.WriteXmlSchema%2A> nebo [práce s datovými sadami v sadě Visual Studio](http://msdn.microsoft.com/library/8bw9ksd6.aspx)).  
  
```  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 Tady je ukázka poznámkou schéma, které zpřístupní **zákazníci** tabulky **Northwind** databáze s vztah k **objednávky** tabulku obsahuje.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet"   
      xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
      xmlns=""   
      xmlns:xs="http://www.w3.org/2001/XMLSchema"   
      xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID" type="xs:string" minOccurs="0" />  
              <xs:element name="CompanyName"  
codegen:typedName="CompanyName" type="xs:string" minOccurs="0" />  
              <xs:element name="Phone" codegen:typedName="Phone" codegen:nullValue="" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="Orders" codegen:typedName="Order" codegen:typedPlural="Orders">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="OrderID" codegen:typedName="OrderID"  
type="xs:int" minOccurs="0" />  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID"                  codegen:nullValue="" type="xs:string" minOccurs="0" />  
              <xs:element name="EmployeeID"  
codegen:typedName="EmployeeID" codegen:nullValue="0"   
type="xs:int" minOccurs="0" />  
              <xs:element name="OrderAdapter"  
codegen:typedName="OrderAdapter" codegen:nullValue="1980-01-01T00:00:00"   
type="xs:dateTime" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
    <xs:unique name="Constraint1">  
      <xs:selector xpath=".//Customers" />  
      <xs:field xpath="CustomerID" />  
    </xs:unique>  
    <xs:keyref name="CustOrders" refer="Constraint1"  
codegen:typedParent="Customer" codegen:typedChildren="GetOrders">  
      <xs:selector xpath=".//Orders" />  
      <xs:field xpath="CustomerID" />  
    </xs:keyref>  
  </xs:element>  
</xs:schema>  
```  
  
 Následující příklad kódu používá silného typu **datovou sadu** vytvořené z ukázkové schéma. Používá jednu <xref:System.Data.SqlClient.SqlDataAdapter> k naplnění **zákazníci** tabulky a druhý <xref:System.Data.SqlClient.SqlDataAdapter> k naplnění **objednávky** tabulky. Silného typu **datovou sadu** definuje **DataRelations**.  
  
```vb  
' Assumes a valid SqlConnection object named connection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT CustomerID, CompanyName, Phone FROM Customers", &  
    connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders", &  
    connection)  
  
' Populate a strongly typed DataSet.  
connection.Open()  
Dim customers As CustomerDataSet = New CustomerDataSet()  
customerAdapter.Fill(customers, "Customers")  
orderAdapter.Fill(customers, "Orders")  
connection.Close()  
  
' Add a strongly typed event.  
AddHandler customers.Customers.CustomerChanged, &  
    New CustomerDataSet.CustomerChangeEventHandler( _  
    AddressOf OnCustomerChanged)  
  
' Add a strongly typed DataRow.  
Dim newCustomer As CustomerDataSet.Customer = _  
    customers.Customers.NewCustomeromer()  
newCustomer.CustomerID = "NEW01"  
newCustomer.CompanyName = "My New Company"  
customers.Customers.AddCustomer(newCustomer)  
  
' Navigate the child relation.  
Dim customer As CustomerDataSet.Customer  
Dim order As CustomerDataSet.Order  
  
For Each customer In customers.Customers  
  Console.WriteLine(customer.CustomerID)  
  For Each order In customer.GetOrders()  
    Console.WriteLine(vbTab & order.OrderID)  
  Next  
Next  
  
Private Shared Sub OnCustomerChanged( _  
    sender As Object, e As CustomerDataSet.CustomerChangeEvent)  
  
End Sub  
```  
  
```csharp  
// Assumes a valid SqlConnection object named connection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
    "SELECT CustomerID, CompanyName, Phone FROM Customers",  
    connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders",   
    connection);  
  
// Populate a strongly typed DataSet.  
connection.Open();  
CustomerDataSet customers = new CustomerDataSet();  
customerAdapter.Fill(customers, "Customers");  
orderAdapter.Fill(customers, "Orders");  
connection.Close();  
  
// Add a strongly typed event.  
customers.Customers.CustomerChanged += new   
  CustomerDataSet.CustomerChangeEventHandler(OnCustomerChanged);  
  
// Add a strongly typed DataRow.  
CustomerDataSet.Customer newCustomer =   
    customers.Customers.NewCustomeromer();  
newCustomer.CustomerID = "NEW01";  
newCustomer.CompanyName = "My New Company";  
customers.Customers.AddCustomer(newCustomer);  
  
// Navigate the child relation.  
foreach(CustomerDataSet.Customer customer in customers.Customers)  
{  
  Console.WriteLine(customer.CustomerID);  
  foreach(CustomerDataSet.Order order in customer.GetOrders())  
    Console.WriteLine("\t" + order.OrderID);  
}  
  
protected static void OnCustomerChanged(object sender, CustomerDataSet.CustomerChangeEvent e)  
    {  
  
    }  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataSet>  
 [Typové datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
