---
title: Vnoření datových relací
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
ms.openlocfilehash: 08149de9222c34928078c0ca9d88096f7a4a88d1
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203271"
---
# <a name="nesting-datarelations"></a>Vnoření datových relací
V relačních zastoupeních dat jednotlivé tabulky obsahují řádky, které jsou vzájemně propojené pomocí sloupce nebo sady sloupců. V ADO.NET <xref:System.Data.DataSet>je relace mezi tabulkami implementována <xref:System.Data.DataRelation>pomocí. Při vytváření objektu **DataRelation**jsou vztahy nadřazenosti a podřízenosti sloupců spravovány pouze prostřednictvím vztahu. Tabulky a sloupce jsou samostatné entity. V hierarchickém znázornění dat, která poskytuje XML, jsou vztahy typu nadřazený-podřízený zastoupeny nadřazenými prvky, které obsahují vnořené podřízené prvky.  
  
 Pro usnadnění vnoření podřízených objektů, pokud je **datová sada** synchronizována s <xref:System.Xml.XmlDataDocument> nebo zapsaná jako XML data pomocí funkce **WriteXml**, objekt DataRelation zpřístupňuje **vnořenou** vlastnost. Nastavení **vnořené** vlastnosti DataRelation na **hodnotu true** způsobí, že podřízené řádky relace budou vnořené do nadřazeného sloupce, pokud jsou zapsány jako data XML nebo synchronizovány pomocí **objektu XmlDataDocument**. Ve výchozím nastavení je vnořená vlastnost DataRelation nastavena na **hodnotu false**.  
  
 Zvažte například následující **datovou sadu**.  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, CustomerID, OrderDate FROM Orders", connection)  
  
connection.Open()  
  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
customerAdapter.Fill(dataSet, "Customers")  
orderAdapter.Fill(dataSet, "Orders")  
  
connection.Close()  
  
Dim customerOrders As DataRelation = dataSet.Relations.Add( _  
  "CustOrders", dataSet.Tables("Customers").Columns("CustomerID"), _  
  dataSet.Tables("Orders").Columns("CustomerID"))  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT OrderID, CustomerID, OrderDate FROM Orders", connection);  
  
connection.Open();  
  
DataSet dataSet = new DataSet("CustomerOrders");  
customerAdapter.Fill(dataSet, "Customers");  
orderAdapter.Fill(dataSet, "Orders");  
  
connection.Close();  
  
DataRelation customerOrders = dataSet.Relations.Add(  
  "CustOrders", dataSet.Tables["Customers"].Columns["CustomerID"],  
  dataSet.Tables["Orders"].Columns["CustomerID"]);  
```  
  
 Vzhledem k tomu, že vlastnost **Nested** objektu DataRelation není pro tuto **datovou sadu**nastavena na **hodnotu true** , podřízené objekty nejsou vnořené v rámci nadřazených elementů, pokud je tato **datová sada** reprezentována jako data XML. Transformace reprezentace XML pro **datovou sadu** , která obsahuje související **datovou sadu**s nevnořenými datovými relacemi, může způsobit pomalý výkon. Doporučujeme, abyste provedli vnořování datových vztahů. To provedete tak, že nastavíte vnořenou vlastnost na **hodnotu true**. Potom v šabloně stylů XSLT napíšete kód, který použije k vyhledání a transformaci dat horních hierarchické výrazy XPath.  
  
 Následující příklad kódu ukazuje výsledek volání **WriteXml** na **datovou sadu**.  
  
```xml  
<CustomerOrders>  
  <Customers>  
    <CustomerID>ALFKI</CustomerID>  
    <CompanyName>Alfreds Futterkiste</CompanyName>  
  </Customers>  
  <Customers>  
    <CustomerID>ANATR</CustomerID>  
    <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
  </Customers>  
  <Orders>  
    <OrderID>10643</OrderID>  
    <CustomerID>ALFKI</CustomerID>  
    <OrderDate>1997-08-25T00:00:00</OrderDate>  
  </Orders>  
  <Orders>  
    <OrderID>10692</OrderID>  
    <CustomerID>ALFKI</CustomerID>  
    <OrderDate>1997-10-03T00:00:00</OrderDate>  
  </Orders>  
  <Orders>  
    <OrderID>10308</OrderID>  
    <CustomerID>ANATR</CustomerID>  
    <OrderDate>1996-09-18T00:00:00</OrderDate>  
  </Orders>  
</CustomerOrders>  
```  
  
 Všimněte si, že elementy Customers a Orders se zobrazují jako elementy na stejné úrovni. Pokud jste chtěli, aby se prvky **objednávky** zobrazovaly jako podřízené objekty svých příslušných nadřazených prvků, je nutné, aby byla **vnořená** vlastnost DataRelation nastavena na **hodnotu true** a přidáte následující:  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 Následující kód ukazuje, jaký výsledný výstup by vypadal jako, s prvky **Orders** vnořené v rámci svých příslušných nadřazených prvků.  
  
```xml  
<CustomerOrders>  
  <Customers>  
    <CustomerID>ALFKI</CustomerID>  
    <Orders>  
      <OrderID>10643</OrderID>  
      <CustomerID>ALFKI</CustomerID>  
      <OrderDate>1997-08-25T00:00:00</OrderDate>  
    </Orders>  
    <Orders>  
      <OrderID>10692</OrderID>  
      <CustomerID>ALFKI</CustomerID>  
      <OrderDate>1997-10-03T00:00:00</OrderDate>  
    </Orders>  
    <CompanyName>Alfreds Futterkiste</CompanyName>  
  </Customers>  
  <Customers>  
    <CustomerID>ANATR</CustomerID>  
    <Orders>  
      <OrderID>10308</OrderID>  
      <CustomerID>ANATR</CustomerID>  
      <OrderDate>1996-09-18T00:00:00</OrderDate>  
    </Orders>  
    <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
  </Customers>  
</CustomerOrders>  
```  
  
## <a name="see-also"></a>Viz také:

- [Použití XML v datové sadě](using-xml-in-a-dataset.md)
- [Přidání datových relací](adding-datarelations.md)
- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
