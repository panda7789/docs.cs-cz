---
title: Zadávání poznámek k typovým datovým sadám
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: 351175b96d354a264a9280018ce21de8870beda2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784801"
---
# <a name="annotating-typed-datasets"></a>Zadávání poznámek k typovým datovým sadám
Poznámky umožňují upravit názvy elementů ve vašem typu <xref:System.Data.DataSet> bez změny v podkladovém schématu. Změna názvů prvků v základním schématu způsobí, že zadaná **datová sada** odkazuje na objekty, které neexistují ve zdroji dat, a také ztratí odkaz na objekty, které existují ve zdroji dat.  
  
 Pomocí poznámek můžete přizpůsobit názvy objektů v zadané **datové sadě** s smysluplnými názvy, což usnadňuje čtení kódu a zadaná **datová sada** je pro klienty snazší a přitom ponechá základní schéma beze změny. Například následující prvek schématu pro tabulku **Customers** v databázi **Northwind** by měl <xref:System.Data.DataRowCollection> mít název objektu **DataRow** **CustomersRow** a pojmenované **zákazníky**.  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 **Kolekci DataRowCollection** jména **zákazníků** jsou v kódu klienta smysluplná, **ale název objektu** **CustomersRow** je zavádějící, protože se jedná o jediný objekt. Také v běžných scénářích by se objekt odkazoval bez identifikátoru **řádku** a místo toho by se mu musel jednoduše odkazovat jako na objekt **zákazníka** . Řešením je opatřit poznámkami od schématu a identifikovat nové názvy pro objekty **DataRow** a **kolekci DataRowCollection** . Níže je uvedena verze předchozího schématu s poznámkou.  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 Zadání hodnoty **názvu** **zákazníka** bude mít za následek název objektu **DataRow** **zákazníka**. Zadáním hodnoty **TypedPlural** **zákazníkům** zachováte **kolekci DataRowCollection** jména **zákazníků**.  
  
 V následující tabulce jsou uvedeny poznámky k dispozici pro použití.  
  
|Poznámka|Popis|  
|----------------|-----------------|  
|**typ typu**|Název objektu.|  
|**typedPlural**|Název kolekce objektů.|  
|**typedParent**|Název objektu, který je odkazován v nadřazené relaci.|  
|**typedChildren**|Název metody pro vrácení objektů z podřízené relace.|  
|**nullValue**|Hodnota, pokud je podkladová hodnota **DBNull**. Poznámky **NullValue** naleznete v následující tabulce. Výchozí hodnota je **_throw**.|  
  
 V následující tabulce jsou uvedeny hodnoty, které lze zadat pro **NullValue** anotaci.  
  
|Hodnota nullValue|Popis|  
|---------------------|-----------------|  
|*Nahrazující hodnota*|Zadejte hodnotu, která se má vrátit. Vrácená hodnota musí odpovídat typu elementu. Například použijte `nullValue="0"` k vrácení 0 pro pole s hodnotou null.|  
|**_throw**|Vyvolejte výjimku. Toto nastavení je výchozí.|  
|**_null**|Vrátí nulový odkaz nebo vyvolá výjimku, pokud se zjistil primitivní typ.|  
|**_empty**|V případě řetězců vrátí **řetězec. Empty**, jinak vrátí objekt vytvořený z prázdného konstruktoru. Pokud je zjištěn primitivní typ, vyvolejte výjimku.|  
  
 V následující tabulce jsou uvedeny výchozí hodnoty pro objekty v zadané **datové sadě** a poznámky k dispozici.  
  
|Objekt/metoda/událost|Výchozí|Poznámka|  
|---------------------------|-------------|----------------|  
|**DataTable**|TableNameDataTable|typedPlural|  
|**DataTable** Způsobů|NewTableNameRow<br /><br /> AddTableNameRow<br /><br /> DeleteTableNameRow|typ typu|  
|**DataRowCollection**|TableName|typedPlural|  
|**DataRow**|TableNameRow|typ typu|  
|**DataColumn**|DataTable.ColumnNameColumn<br /><br /> DataRow.ColumnName|typ typu|  
|**Majetek**|Vlastnost PropertyName|typ typu|  
|**Podřízená položka** Zbývá|GetChildTableNameRows|typedChildren|  
|**Nadřazený prvek** Zbývá|TableNameRow|typedParent|  
|**Datová sada** Událost|TableNameRowChangeEvent<br /><br /> TableNameRowChangeEventHandler|typ typu|  
  
 Chcete-li použít typové anotace **datové sady** , musíte zahrnout následující odkaz **xmlns** do schématu XML schématu definice jazyka (XSD). Chcete-li vytvořit XSD z databázových tabulek <xref:System.Data.DataSet.WriteXmlSchema%2A> , přečtěte si nebo [práce s datovými sadami v sadě Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
```  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 Následuje ukázka schématu s poznámkou, které zveřejňuje tabulku **Customers (zákazníci** ) databáze **Northwind** s relací k uvedené tabulce **Orders** .  
  
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
  
 Následující příklad kódu používá **datovou sadu** silného typu vytvořenou z ukázkového schématu. Používá jeden <xref:System.Data.SqlClient.SqlDataAdapter> k naplnění tabulky **Customers** a <xref:System.Data.SqlClient.SqlDataAdapter> druhý k naplnění tabulky **Orders** . **Datová sada** silného typu definuje **DataRelations**.  
  
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
- [Typové datové sady](typed-datasets.md)
- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [Přehled ADO.NET](../ado-net-overview.md)
