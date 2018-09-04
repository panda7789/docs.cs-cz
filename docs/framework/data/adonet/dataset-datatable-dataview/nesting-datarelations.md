---
title: Vnoření datových relací
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
ms.openlocfilehash: 9255615c7786773f1d4f453b910fdccdf191721f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43552524"
---
# <a name="nesting-datarelations"></a>Vnoření datových relací
Jednotlivé tabulky v relační znázornění dat, obsahovat řádky, které se vztahují k navzájem pomocí sloupec nebo sadu sloupců. V ADO.NET <xref:System.Data.DataSet>, relace mezi tabulkami se implementuje pomocí <xref:System.Data.DataRelation>. Když vytvoříte **DataRelation**, vztahy nadřazenosti a podřízenosti sloupce, které se spravují jenom do relace. Tabulky a sloupce jsou samostatné entity. V Hierarchická reprezentace dat, které obsahuje XML nadřazené a podřízené vztahy jsou reprezentovány nadřazené elementy, které obsahují vnořené podřízené prvky.  
  
 Pro usnadnění vnoření podřízené objekty při **datovou sadu** synchronizována s <xref:System.Xml.XmlDataDocument> nebo zapsat jako dat XML pomocí **WriteXml**, **DataRelation** Zpřístupňuje **vnořené** vlastnost. Nastavení **vnořené** vlastnost **DataRelation** k **true** způsobí, že podřízené řádky vztahu, chcete-li být vnořen v rámci nadřazeného sloupce při zápisu jako XML data nebo synchronizovat se službou **XmlDataDocument**. **Vnořené** vlastnost **DataRelation** je **false**, ve výchozím nastavení.  
  
 Představte si třeba následující **datovou sadu**.  
  
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
  
 Protože **vnořené** vlastnost **DataRelation** není nastaven na **true** pro tuto **datovou sadu**, nejsou vnořené podřízené objekty v rámci nadřazené prvky při to **datovou sadu** je vyjádřena jako XML data. Transformace reprezentace XML **datovou sadu** , který obsahuje související **datovou sadu**s s-nested datové relace může způsobit snížení výkonu. Doporučujeme vám, že byste vnořit datové relace. Chcete-li to provést, nastavte **vnořené** vlastnost **true**. Teprve pak píšete kód v šabloně stylů XSLT, který používá výrazy dotazu XPath hierarchické shora dolů k vyhledání a transformovat data.  
  
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
  
 Všimněte si, že **zákazníkům** elementu a **objednávky** prvky jsou uvedeny jako prvky na stejné úrovni. Pokud byste chtěli **objednávky** prvků, které se zobrazují jako podřízené objekty daného jejich příslušné nadřazené elementy **vnořené** vlastnost **DataRelation** by bylo potřeba nastavit na **true** a přidejte následující:  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 Následující kód ukazuje, co výsledný výstup bude vypadat, se **objednávky** vnořené elementy v rámci svých odpovídajících nadřazené prvky.  
  
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
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
