---
title: Zadávání poznámek k typovým datovým sadám
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: 757a87f92d8dc6049de1844fed892d95dc57c990
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151517"
---
# <a name="annotating-typed-datasets"></a>Zadávání poznámek k typovým datovým sadám
Poznámky umožňují změnit názvy prvků v zadaném <xref:System.Data.DataSet> textu bez úpravy základního schématu. Změna názvů prvků v podkladovém schématu by způsobila, že zadaný **DataSet** odkazuje na objekty, které ve zdroji dat neexistují, a také ztratí odkaz na objekty, které existují ve zdroji dat.  
  
 Pomocí anotací můžete přizpůsobit názvy objektů v zadané **datové sadě** s smysluplnějšími názvy, čímž usnadníte čitelný kód a zadávaný **soubor DataSet** snadněji používajíte klientům, přičemž základní schéma zůstane beze změny. Například následující prvek schématu pro tabulku **Zákazníci** databáze **Northwind** by mělo za následek název <xref:System.Data.DataRowCollection> objektu **DataRow** **customersrow** a pojmenované **zákazníci**.  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 A **DataRowCollection** název **customers** je smysluplné v kódu klienta, ale **Název DataRow** **CustomersRow** je zavádějící, protože je jeden objekt. Také v běžných scénářích by objekt být odkazoval se na bez identifikátor **u řádku** a místo toho by jednoduše označovány jako **objekt Zákazník.** Řešením je anotovat schéma a identifikovat nové názvy pro **DataRow** a **DataRowCollection** objekty. Následuje anotovaná verze předchozího schématu.  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 Zadání hodnoty **typedName** **zákazníka** bude mít za následek název objektu **DataRow** **zákazníka**. Zadání **množného** čísla **Hodnota Zákazníci** zachová název **DataRowCollection** **zákazníky**.  
  
 V následující tabulce jsou uvedeny poznámky, které jsou k dispozici pro použití.  
  
|Poznámka|Popis|  
|----------------|-----------------|  
|**typedName**|Název objektu.|  
|**typedPlural**|Název kolekce objektů.|  
|**typedParent**|Název objektu, na který se odkazuje v nadřazeném vztahu.|  
|**typedChildren**|Název metody pro vrácení objektů z podřízeného vztahu.|  
|**nullValue**|Hodnota, pokud je základní hodnota **DBNull**. V následující tabulce naleznete poznámky **nullValue.** Výchozí hodnota je **_throw**.|  
  
 V následující tabulce jsou uvedeny hodnoty, které lze zadat pro poznámku **nullValue.**  
  
|hodnota nullHodnota|Popis|  
|---------------------|-----------------|  
|*Náhradní hodnota*|Zadejte hodnotu, která má být vrácena. Vrácená hodnota musí odpovídat typu prvku. Slouží `nullValue="0"` například k vrácení 0 pro pole s nulovým sdělovým číselně.|  
|**_throw**|Vyvolat výjimku. Toto nastavení je výchozí.|  
|**_null**|Vrátí nulový odkaz nebo vyvolat výjimku, pokud je zjištěn primitivní typ.|  
|**_empty**|Pro řetězce vrátí **String.Empty**, jinak vrátí objekt vytvořený z prázdného konstruktoru. Pokud dojde k primitivní typ, vyvolat výjimku.|  
  
 V následující tabulce jsou uvedeny výchozí hodnoty pro objekty v zadané **datové sadě** a dostupné poznámky.  
  
|Objekt/Metoda/událost|Výchozí|Poznámka|  
|---------------------------|-------------|----------------|  
|**DataTable**|TableNameDataTable|typedPlural|  
|**Tabulka dat** Metody|NewTableNameRow<br /><br /> AddTableNameRow<br /><br /> Odstranitnázev_řádku|typedName|  
|**Datarowcollection**|TableName|typedPlural|  
|**Datarow**|Název_tabulky|typedName|  
|**Datacolumn**|Sloupec Název_sloupce DataTable.Column<br /><br /> Název_řádku_data|typedName|  
|**Vlastnost**|PropertyName|typedName|  
|**Dítě** Přístupové|GetChildTableNameRows|typedChildren|  
|**Nadřazená** Přístupové|Název_tabulky|typedParent|  
|**Datová sada** Události|TableNameRowChangeEvent<br /><br /> Obslužná rutina_události TableNameRowChangeEventHandler|typedName|  
  
 Chcete-li použít zadané poznámky **DataSet,** musíte do schématu jazyka Xml Schema (XSD) zahrnout následující odkaz **xmlns.** Chcete-li vytvořit xsd z <xref:System.Data.DataSet.WriteXmlSchema%2A> databázových tabulek, přečtěte si další informace nebo [práce s datovými sadami v sadě Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
```xml  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 Následuje ukázkové schéma s anotovanými notami, které zpřístupňuje tabulku **Zákazníci** databáze **Northwind** s vztahem k tabulce **Objednávky.**  
  
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
  
 Následující příklad kódu používá silně zadaný **DataSet** vytvořený z ukázkového schématu. Používá jeden <xref:System.Data.SqlClient.SqlDataAdapter> k naplnění tabulky <xref:System.Data.SqlClient.SqlDataAdapter> **Zákazníci** a jiný k naplnění tabulky **Objednávky.** Silně zadaný **dataset** definuje **DataRelations**.  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [Typové datové sady](typed-datasets.md)
- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [Přehled ADO.NET](../ado-net-overview.md)
