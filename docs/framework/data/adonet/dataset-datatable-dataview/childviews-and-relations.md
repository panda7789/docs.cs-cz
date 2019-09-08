---
title: ChildViews a relace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d475d356-6abb-4701-8fd1-2906fb93dfba
ms.openlocfilehash: d208b0796a072cda2873678ba184bc9793a1688a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786582"
---
# <a name="childviews-and-relations"></a><span data-ttu-id="86cd2-102">ChildViews a relace</span><span class="sxs-lookup"><span data-stu-id="86cd2-102">ChildViews and Relations</span></span>
<span data-ttu-id="86cd2-103">Pokud existuje relace mezi <xref:System.Data.DataSet>tabulkami v, můžete <xref:System.Data.DataView> vytvořit obsahující řádky z související <xref:System.Data.DataRowView.CreateChildView%2A> podřízené tabulky <xref:System.Data.DataRowView> pomocí metody pro řádky v nadřazené tabulce.</span><span class="sxs-lookup"><span data-stu-id="86cd2-103">If a relationship exists between tables in a <xref:System.Data.DataSet>, you can create a <xref:System.Data.DataView> containing rows from the related child table by using the <xref:System.Data.DataRowView.CreateChildView%2A> method of the <xref:System.Data.DataRowView> for the rows in the parent table.</span></span> <span data-ttu-id="86cd2-104">Například následující kód zobrazuje **kategorie** a jejich související **produkty** v abecedním pořadí seřazené podle **CategoryName** a **ProductName**.</span><span class="sxs-lookup"><span data-stu-id="86cd2-104">For example, the following code displays **Categories** and their related **Products** in alphabetical order sorted by **CategoryName** and **ProductName**.</span></span>  
  
```vb  
Dim catTable As DataTable = catDS.Tables("Categories")  
Dim prodTable As DataTable = catDS.Tables("Products")  
  
' Create a relation between the Categories and Products tables.  
Dim relation As DataRelation = catDS.Relations.Add("CatProdRel", _  
  catTable.Columns("CategoryID"), _  
  prodTable.Columns("CategoryID"))  
  
' Create DataViews for the Categories and Products tables.  
Dim catView As DataView = New DataView(catTable, "", _  
  "CategoryName", DataViewRowState.CurrentRows)  
Dim prodView As DataView  
  
' Iterate through the Categories table.  
Dim catDRV, prodDRV As DataRowView  
  
For Each catDRV In catView  
  Console.WriteLine(catDRV("CategoryName"))  
  
  ' Create a DataView of the child product records.  
  prodView = catDRV.CreateChildView(relation)  
  prodView.Sort = "ProductName"  
  
  For Each prodDRV In prodView  
    Console.WriteLine(vbTab & prodDRV("ProductName"))  
  Next  
Next  
```  
  
```csharp  
DataTable catTable = catDS.Tables["Categories"];  
DataTable prodTable = catDS.Tables["Products"];  
  
// Create a relation between the Categories and Products tables.  
DataRelation relation = catDS.Relations.Add("CatProdRel",   
  catTable.Columns["CategoryID"],  
                                                            prodTable.Columns["CategoryID"]);  
  
// Create DataViews for the Categories and Products tables.  
DataView catView = new DataView(catTable, "", "CategoryName",   
  DataViewRowState.CurrentRows);  
DataView prodView;  
  
// Iterate through the Categories table.  
foreach (DataRowView catDRV in catView)  
{  
  Console.WriteLine(catDRV["CategoryName"]);  
  
  // Create a DataView of the child product records.  
  prodView = catDRV.CreateChildView(relation);  
  prodView.Sort = "ProductName";  
  
  foreach (DataRowView prodDRV in prodView)  
    Console.WriteLine("\t" + prodDRV["ProductName"]);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="86cd2-105">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86cd2-105">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [<span data-ttu-id="86cd2-106">Zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="86cd2-106">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="86cd2-107">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="86cd2-107">ADO.NET Overview</span></span>](../ado-net-overview.md)
