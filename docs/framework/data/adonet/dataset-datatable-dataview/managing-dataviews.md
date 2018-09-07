---
title: Správa zobrazení dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b67fab5-1722-4d2b-bfc1-247a75f0f1ee
ms.openlocfilehash: 76cf9eb70094dfe8bb760490c42503e08f4b1649
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44082266"
---
# <a name="managing-dataviews"></a><span data-ttu-id="4b52f-102">Správa zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="4b52f-102">Managing DataViews</span></span>
<span data-ttu-id="4b52f-103">Můžete použít <xref:System.Data.DataViewManager> ke správě nastavení zobrazení pro všechny tabulky v <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="4b52f-103">You can use a <xref:System.Data.DataViewManager> to manage view settings for all the tables in a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="4b52f-104">Pokud máte ovládací prvek, který chcete vytvořit vazbu k několika tabulkám, jako je například mřížka, který naviguje relací, **objekt DataViewManager** je ideální.</span><span class="sxs-lookup"><span data-stu-id="4b52f-104">If you have a control that you want to bind to multiple tables, such as a grid that navigates relationships, a **DataViewManager** is ideal.</span></span>  
  
 <span data-ttu-id="4b52f-105">**Objekt DataViewManager** obsahuje kolekci <xref:System.Data.DataViewSetting> objekty, které se používají k nastavení zobrazení tabulek v <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="4b52f-105">The **DataViewManager** contains a collection of <xref:System.Data.DataViewSetting> objects that are used to set the view setting of the tables in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="4b52f-106"><xref:System.Data.DataViewSettingCollection> Obsahuje jeden <xref:System.Data.DataViewSetting> objekt pro každou tabulku **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="4b52f-106">The <xref:System.Data.DataViewSettingCollection> contains one <xref:System.Data.DataViewSetting> object for each table in a **DataSet**.</span></span> <span data-ttu-id="4b52f-107">Můžete nastavit jako výchozí **ApplyDefaultSort**, **řazení**, **RowFilter**, a **Vlastnost RowStateFilter** odkazované tabulky pomocí vlastnosti pomocí jeho **DataViewSetting**.</span><span class="sxs-lookup"><span data-stu-id="4b52f-107">You can set the default **ApplyDefaultSort**, **Sort**, **RowFilter**, and **RowStateFilter** properties of the referenced table by using its **DataViewSetting**.</span></span> <span data-ttu-id="4b52f-108">Můžete odkazovat **DataViewSetting** pro konkrétní tabulku podle názvu nebo odkaz na pořadovém místě nebo předáním odkazu na tento objekt určité tabulky.</span><span class="sxs-lookup"><span data-stu-id="4b52f-108">You can reference the **DataViewSetting** for a particular table by name or ordinal reference, or by passing a reference to that specific table object.</span></span> <span data-ttu-id="4b52f-109">Můžete přístup ke kolekci **DataViewSetting** objekty v **objekt DataViewManager** pomocí **DataViewSettings** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4b52f-109">You can access the collection of **DataViewSetting** objects in a **DataViewManager** by using the **DataViewSettings** property.</span></span>  
  
 <span data-ttu-id="4b52f-110">Následující příklad výplně kódu **datovou sadu** s SQL serverem **Northwind** databázových tabulek **zákazníkům**, **objednávky**a  **Podrobnosti objednávky**, vytváření relací mezi tabulkami, používá **objekt DataViewManager** nastavit výchozí **DataView** nastavení a vytvoří vazbu **ovládacího prvku DataGrid**  k **objekt DataViewManager**.</span><span class="sxs-lookup"><span data-stu-id="4b52f-110">The following code example fills a **DataSet** with the SQL Server **Northwind** database tables **Customers**, **Orders**, and **Order Details**, creates the relationships between the tables, uses a **DataViewManager** to set default **DataView** settings, and binds a **DataGrid** to the **DataViewManager**.</span></span> <span data-ttu-id="4b52f-111">Příklad nastaví výchozí **DataView** nastavení pro všechny tabulky v **datovou sadu** seřadit podle primárního klíče tabulky (**ApplyDefaultSort**  =  **true**) a pak změní pořadí řazení **zákazníkům** tabulku seřaďte **CompanyName**.</span><span class="sxs-lookup"><span data-stu-id="4b52f-111">The example sets the default **DataView** settings for all tables in the **DataSet** to sort by the primary key of the table (**ApplyDefaultSort** = **true**), and then modifies the sort order of the **Customers** table to sort by **CompanyName**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4b52f-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b52f-112">See Also</span></span>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataViewManager>  
 <xref:System.Data.DataViewSetting>  
 <xref:System.Data.DataViewSettingCollection>  
 [<span data-ttu-id="4b52f-113">Zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="4b52f-113">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="4b52f-114">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="4b52f-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
