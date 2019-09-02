---
title: Správa zobrazení dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b67fab5-1722-4d2b-bfc1-247a75f0f1ee
ms.openlocfilehash: c6dcc206775866fd9136e4f6f5f038d021d11433
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204685"
---
# <a name="managing-dataviews"></a><span data-ttu-id="5a324-102">Správa zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="5a324-102">Managing DataViews</span></span>
<span data-ttu-id="5a324-103">Můžete použít <xref:System.Data.DataViewManager> ke správě nastavení zobrazení pro všechny tabulky <xref:System.Data.DataView>v.</span><span class="sxs-lookup"><span data-stu-id="5a324-103">You can use a <xref:System.Data.DataViewManager> to manage view settings for all the tables in a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="5a324-104">Pokud máte ovládací prvek, který chcete vytvořit z více tabulek, jako je například mřížka, která naviguje mezi relacemi, je objekt **DataViewManager** ideální.</span><span class="sxs-lookup"><span data-stu-id="5a324-104">If you have a control that you want to bind to multiple tables, such as a grid that navigates relationships, a **DataViewManager** is ideal.</span></span>  
  
 <span data-ttu-id="5a324-105"><xref:System.Data.DataViewSetting> Objekt **DataViewManager** obsahuje kolekci objektů, které se používají k nastavení nastavení zobrazení tabulek v <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="5a324-105">The **DataViewManager** contains a collection of <xref:System.Data.DataViewSetting> objects that are used to set the view setting of the tables in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="5a324-106">Obsahuje jeden <xref:System.Data.DataViewSetting> objekt pro každou tabulku v **datové sadě.** <xref:System.Data.DataViewSettingCollection></span><span class="sxs-lookup"><span data-stu-id="5a324-106">The <xref:System.Data.DataViewSettingCollection> contains one <xref:System.Data.DataViewSetting> object for each table in a **DataSet**.</span></span> <span data-ttu-id="5a324-107">Můžete nastavit výchozí vlastnosti **ApplyDefaultSort**, **Sort**, **RowFilter vyžaduje hodnotu**a **vlastnost RowStateFilter** odkazované tabulky pomocí jejího **DataViewSetting**.</span><span class="sxs-lookup"><span data-stu-id="5a324-107">You can set the default **ApplyDefaultSort**, **Sort**, **RowFilter**, and **RowStateFilter** properties of the referenced table by using its **DataViewSetting**.</span></span> <span data-ttu-id="5a324-108">Můžete odkazovat na **DataViewSetting** pro konkrétní tabulku podle názvu nebo ordinálního odkazu nebo předáním odkazu na tento konkrétní objekt tabulky.</span><span class="sxs-lookup"><span data-stu-id="5a324-108">You can reference the **DataViewSetting** for a particular table by name or ordinal reference, or by passing a reference to that specific table object.</span></span> <span data-ttu-id="5a324-109">Ke kolekci objektů **DataViewSetting** můžete přistupovat v objektu **DataViewManager** pomocí vlastnosti **DataViewSettings** .</span><span class="sxs-lookup"><span data-stu-id="5a324-109">You can access the collection of **DataViewSetting** objects in a **DataViewManager** by using the **DataViewSettings** property.</span></span>  
  
 <span data-ttu-id="5a324-110">Následující příklad kódu vyplní **datovou sadu** pomocí SQL Server **Northwind** databáze tabulky **zákazníci**, **objednávky**a **Podrobnosti objednávky**, vytvoří vztahy mezi tabulkami, používá objekt **DataViewManager** k Nastavte výchozí nastavení **DataView** a naváže objekt **DataGrid** k objektu **DataViewManager**.</span><span class="sxs-lookup"><span data-stu-id="5a324-110">The following code example fills a **DataSet** with the SQL Server **Northwind** database tables **Customers**, **Orders**, and **Order Details**, creates the relationships between the tables, uses a **DataViewManager** to set default **DataView** settings, and binds a **DataGrid** to the **DataViewManager**.</span></span> <span data-ttu-id="5a324-111">Příklad nastaví výchozí nastavení zobrazení pro všechny tabulky v **datové sadě** pro řazení podle primárního klíče tabulky (**ApplyDefaultSort** = **true**) a pak upraví pořadí řazení tabulky **Customers** na Seřadit podle **CompanyName**.</span><span class="sxs-lookup"><span data-stu-id="5a324-111">The example sets the default **DataView** settings for all tables in the **DataSet** to sort by the primary key of the table (**ApplyDefaultSort** = **true**), and then modifies the sort order of the **Customers** table to sort by **CompanyName**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5a324-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a324-112">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Data.DataViewManager>
- <xref:System.Data.DataViewSetting>
- <xref:System.Data.DataViewSettingCollection>
- [<span data-ttu-id="5a324-113">Zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="5a324-113">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="5a324-114">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="5a324-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
