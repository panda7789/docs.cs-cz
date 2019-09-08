---
title: Správa zobrazení dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b67fab5-1722-4d2b-bfc1-247a75f0f1ee
ms.openlocfilehash: 5e85fccddf6359791ea702667a36b44f611815dc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784502"
---
# <a name="managing-dataviews"></a>Správa zobrazení dat
Můžete použít <xref:System.Data.DataViewManager> ke správě nastavení zobrazení pro všechny tabulky <xref:System.Data.DataView>v. Pokud máte ovládací prvek, který chcete vytvořit z více tabulek, jako je například mřížka, která naviguje mezi relacemi, je objekt **DataViewManager** ideální.  
  
 <xref:System.Data.DataViewSetting> Objekt **DataViewManager** obsahuje kolekci objektů, které se používají k nastavení nastavení zobrazení tabulek v <xref:System.Data.DataSet>. Obsahuje jeden <xref:System.Data.DataViewSetting> objekt pro každou tabulku v **datové sadě.** <xref:System.Data.DataViewSettingCollection> Můžete nastavit výchozí vlastnosti **ApplyDefaultSort**, **Sort**, **RowFilter vyžaduje hodnotu**a **vlastnost RowStateFilter** odkazované tabulky pomocí jejího **DataViewSetting**. Můžete odkazovat na **DataViewSetting** pro konkrétní tabulku podle názvu nebo ordinálního odkazu nebo předáním odkazu na tento konkrétní objekt tabulky. Ke kolekci objektů **DataViewSetting** můžete přistupovat v objektu **DataViewManager** pomocí vlastnosti **DataViewSettings** .  
  
 Následující příklad kódu vyplní **datovou sadu** pomocí SQL Server **Northwind** databáze tabulky **zákazníci**, **objednávky**a **Podrobnosti objednávky**, vytvoří vztahy mezi tabulkami, používá objekt **DataViewManager** k Nastavte výchozí nastavení **DataView** a naváže objekt **DataGrid** k objektu **DataViewManager**. Příklad **Nastaví výchozí nastavení** zobrazení pro všechny tabulky v **datové sadě** pro řazení podle primárního klíče tabulky (**ApplyDefaultSort** = **true**) a pak upraví pořadí řazení tabulky **Customers** na Seřadit podle **CompanyName**.  
  
```vb  
' Assumes connection is a valid SqlConnection to Northwind.  
' Create a Connection, DataAdapters, and a DataSet.  
Dim custDA As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
Dim orderDA As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, CustomerID FROM Orders", connection)  
Dim ordDetDA As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, ProductID, Quantity FROM [Order Details]", connection)  
  
Dim custDS As DataSet = New DataSet()  
  
' Open the Connection.  
connection.Open()  
  
    ' Fill the DataSet with schema information and data.  
    custDA.MissingSchemaAction = MissingSchemaAction.AddWithKey  
    orderDA.MissingSchemaAction = MissingSchemaAction.AddWithKey  
    ordDetDA.MissingSchemaAction = MissingSchemaAction.AddWithKey  
  
    custDA.Fill(custDS, "Customers")  
    orderDA.Fill(custDS, "Orders")  
    ordDetDA.Fill(custDS, "OrderDetails")  
  
    ' Close the Connection.  
    connection.Close()  
  
    ' Create relationships.  
    custDS.Relations.Add("CustomerOrders", _  
          custDS.Tables("Customers").Columns("CustomerID"), _  
          custDS.Tables("Orders").Columns("CustomerID"))  
  
    custDS.Relations.Add("OrderDetails", _  
          custDS.Tables("Orders").Columns("OrderID"), _  
          custDS.Tables("OrderDetails").Columns("OrderID"))  
  
' Create default DataView settings.  
Dim viewManager As DataViewManager = New DataViewManager(custDS)  
  
Dim viewSetting As DataViewSetting  
For Each viewSetting In viewManager.DataViewSettings  
  viewSetting.ApplyDefaultSort = True  
Next  
  
viewManager.DataViewSettings("Customers").Sort = "CompanyName"  
  
' Bind to a DataGrid.  
Dim grid As System.Windows.Forms.DataGrid = New System.Windows.Forms.DataGrid()  
grid.SetDataBinding(viewManager, "Customers")  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection to Northwind.  
// Create a Connection, DataAdapters, and a DataSet.  
SqlDataAdapter custDA = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
SqlDataAdapter orderDA = new SqlDataAdapter(  
  "SELECT OrderID, CustomerID FROM Orders", connection);  
SqlDataAdapter ordDetDA = new SqlDataAdapter(  
  "SELECT OrderID, ProductID, Quantity FROM [Order Details]", connection);  
  
DataSet custDS = new DataSet();  
  
// Open the Connection.  
connection.Open();  
  
    // Fill the DataSet with schema information and data.  
    custDA.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
    orderDA.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
    ordDetDA.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
  
    custDA.Fill(custDS, "Customers");  
    orderDA.Fill(custDS, "Orders");  
    ordDetDA.Fill(custDS, "OrderDetails");  
  
    // Close the Connection.  
    connection.Close();  
  
    // Create relationships.  
    custDS.Relations.Add("CustomerOrders",  
          custDS.Tables["Customers"].Columns["CustomerID"],  
          custDS.Tables["Orders"].Columns["CustomerID"]);  
  
    custDS.Relations.Add("OrderDetails",  
          custDS.Tables["Orders"].Columns["OrderID"],  
          custDS.Tables["OrderDetails"].Columns["OrderID"]);  
  
// Create default DataView settings.  
DataViewManager viewManager = new DataViewManager(custDS);  
  
foreach (DataViewSetting viewSetting in viewManager.DataViewSettings)  
  viewSetting.ApplyDefaultSort = true;  
  
viewManager.DataViewSettings["Customers"].Sort = "CompanyName";  
  
// Bind to a DataGrid.  
System.Windows.Forms.DataGrid grid = new System.Windows.Forms.DataGrid();  
grid.SetDataBinding(viewManager, "Customers");  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataSet>
- <xref:System.Data.DataViewManager>
- <xref:System.Data.DataViewSetting>
- <xref:System.Data.DataViewSettingCollection>
- [Zobrazení dat](dataviews.md)
- [Přehled ADO.NET](../ado-net-overview.md)
