---
title: Zadávání poznámek k typovým datovým sadám
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: d8a1a12a4d8ab5e6f4b0fe6ad6c2a3759aa65aa9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085126"
---
# <a name="annotating-typed-datasets"></a>Zadávání poznámek k typovým datovým sadám
Anotace umožňují změnit názvy prvků v váš zadaný <xref:System.Data.DataSet> beze změny podkladového schématu. Úprava názvy prvků v podkladové schéma by způsobilo zadaného **datovou sadu** k odkazování na objekty, které nejsou existují ve zdroji dat, jakož i odkazovaly, ztratily odkaz na objekty, které existují ve zdroji dat.  
  
 Použití poznámek, můžete přizpůsobit názvy objektů v váš zadaný **datovou sadu** s více smysluplné názvy, takže kód lépe čitelný a váš zadaný **datovou sadu** usnadňuje klientům používat při opuštění základní schéma beze změn. Například následující element schématu pro **zákazníkům** tabulku **Northwind** výsledkem by byla databáze **DataRow** název objektu  **CustomersRow** a <xref:System.Data.DataRowCollection> s názvem **zákazníkům**.  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 A **kolekci DataRowCollection** název **zákazníkům** má smysl v klientském kódu, ale **DataRow** název **CustomersRow** je zavádějící protože je jeden objekt. V běžných scénářů, objekt by se označovat taky bez **řádek** identifikátor a místo toho by jednoduše odkazovat jako **zákazníka** objektu. Řešením je přidání poznámek ke schématu a identifikovat nové názvy pro **DataRow** a **kolekci DataRowCollection** objekty. Tady je s poznámkami verzi předchozí schématu.  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 Určení **TypedName služby Active Directory** hodnotu **zákazníka** bude mít za následek **DataRow** název objektu **zákazníka**. Určení **typedPlural** hodnotu **zákazníkům** zachová **kolekci DataRowCollection** název **zákazníkům**.  
  
 Poznámky k dispozici pro použití v následující tabulce.  
  
|Poznámka|Popis|  
|----------------|-----------------|  
|**TypedName služby Active Directory**|Název objektu.|  
|**typedPlural**|Název kolekce objektů.|  
|**typedParent**|Název objektu podle nadřazenou relací.|  
|**typedChildren**|Název metody, která vrací objekty z podřízeného vztahu.|  
|**nullValue**|Hodnotu, pokud je zadaná hodnota **DBNull**. V následující tabulce najdete **nullValue** poznámky. Výchozí hodnota je **_throw**.|  
  
 V následující tabulce jsou uvedeny hodnoty, které je možné zadat pro **nullValue** poznámky.  
  
|nullValue hodnotu|Popis|  
|---------------------|-----------------|  
|*Nahrazující hodnotou*|Zadejte hodnotu má být vrácen. Vrácená hodnota musí odpovídat typu elementu. Například použít `nullValue="0"` vrátit 0 pro pole null typu integer.|  
|**_throw**|Vyvolejte výjimku. Toto nastavení je výchozí.|  
|**_null**|Vrátí odkaz s hodnotou null nebo vyvolat výjimku, pokud je primitivního typu.|  
|**_prázdný**|Pro řetězce, vrátí **String.Empty**, jinak vrátí objekt vytvořený z prázdného konstruktoru. Pokud je nalezen primitivní typ, vyvolejte výjimku.|  
  
 V následující tabulce jsou uvedeny výchozí hodnoty pro objekty v typovaného **datovou sadu** a poznámky k dispozici.  
  
|Objekt nebo metoda/událost|Výchozí|Poznámka|  
|---------------------------|-------------|----------------|  
|**DataTable**|TableNameDataTable|typedPlural|  
|**Objekt DataTable** metody|NewTableNameRow<br /><br /> AddTableNameRow<br /><br /> DeleteTableNameRow|TypedName služby Active Directory|  
|**DataRowCollection**|TableName|typedPlural|  
|**DataRow**|TableNameRow|TypedName služby Active Directory|  
|**DataColumn**|DataTable.ColumnNameColumn<br /><br /> DataRow.ColumnName|TypedName služby Active Directory|  
|**Vlastnost**|Vlastnost PropertyName|TypedName služby Active Directory|  
|**Podřízené** přístupového objektu|GetChildTableNameRows|typedChildren|  
|**Nadřazené** přístupového objektu|TableNameRow|typedParent|  
|**Datová sada** události|TableNameRowChangeEvent<br /><br /> TableNameRowChangeEventHandler|TypedName služby Active Directory|  
  
 Použití typu **datovou sadu** poznámky, musí zahrnovat následující **xmlns** odkaz ve schématu schématu XML definice jazyk (XSD). Vytvoření xsd z tabulky databáze najdete v tématu <xref:System.Data.DataSet.WriteXmlSchema%2A> nebo [práce s datovými sadami v sadě Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
```  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 Tady je ukázka s poznámkami schématu, která zveřejňuje **zákazníkům** tabulku **Northwind** databáze s vztah k položce **objednávky** tabulku obsahuje.  
  
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
  
 Následující příklad kódu používá silného typu **datovou sadu** vytvořené ze vzorku schématu. Používá jednu <xref:System.Data.SqlClient.SqlDataAdapter> k naplnění **zákazníkům** tabulkami <xref:System.Data.SqlClient.SqlDataAdapter> k naplnění **objednávky** tabulky. Silného typu **datovou sadu** definuje **datových relací**.  
  
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
    customers.Customers.NewCustomer()  
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
    customers.Customers.NewCustomer();  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [Typové datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)
- [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
