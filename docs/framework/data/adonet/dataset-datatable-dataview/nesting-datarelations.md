---
title: DataRelations vnoření
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
ms.openlocfilehash: 3f17d81ac41c90e7f1c48523a4ced91bc788a962
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761893"
---
# <a name="nesting-datarelations"></a>DataRelations vnoření
Jednotlivé tabulky v znázornění relační data obsahují řádky, které se vztahují na sebe navzájem pomocí sloupec nebo sadu sloupců. V technologie ADO.NET <xref:System.Data.DataSet>, relace mezi tabulkami je implementovaná pomocí <xref:System.Data.DataRelation>. Při vytváření **DataRelation**, vztahy podřízenosti sloupců, které lze spravovat pouze prostřednictvím vztah. Tabulky a sloupce jsou samostatné entity. V hierarchické reprezentace dat, který obsahuje XML vztahů nadřazenosti a podřízenosti reprezentována nadřazené elementy, které obsahují vnořené podřízené elementy.  
  
 Pro usnadnění vnoření podřízených objektů při **datovou sadu** je synchronizován se službou <xref:System.Xml.XmlDataDocument> nebo zapsat jako data XML pomocí **WriteXml**, **DataRelation** zpřístupní **vnořené** vlastnost. Nastavení **vnořené** vlastnost **DataRelation** k **true** způsobí, že podřízená řádky vztah k začlenit do nadřazeného sloupce, když se zapisují jako XML data nebo synchronizovat se službou **XmlDataDocument**. **Vnořené** vlastnost **DataRelation** je **false**, ve výchozím nastavení.  
  
 Například vezměte v úvahu následující **datovou sadu**.  
  
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
  
 Protože **vnořené** vlastnost **DataRelation** objekt není nastavený na **true** pro tento **datovou sadu**, nejsou vnořené podřízené objekty v rámci nadřazené elementy při to **datovou sadu** je reprezentována jako XML data. Převod reprezentace XML **datovou sadu** obsahující související **datovou sadu**s s-nested datové relace může způsobit snížení výkonu. Doporučujeme vám, že je vnořovat datové relace. Chcete-li to provést, nastavte **vnořené** vlastnost **true**. Potom napište kód v Styl XSLT používající vertikální hierarchické výrazy dotazů XPath pro vyhledání a transformovat data.  
  
 Následující příklad kódu ukazuje výsledek z volání **WriteXml** na **datovou sadu**.  
  
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
  
 Všimněte si, že **zákazníci** element a **objednávky** elementy se zobrazují jako podřízené prvky. Pokud jste chtěli **objednávky** elementy objeví jako podřízené objekty jejich příslušné nadřazené elementy, **vnořené** vlastnost **DataRelation** by bylo potřeba nastavit na **true** a by přidejte následující:  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 Následující kód ukazuje, jak výsledný výstup bude vypadat, s **objednávky** vnořených elementů v rámci jejich příslušné nadřazené elementy.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Přidání datových relací](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
