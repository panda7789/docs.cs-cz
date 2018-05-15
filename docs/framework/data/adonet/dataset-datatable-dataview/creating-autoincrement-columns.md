---
title: Vytváření AutoIncrement sloupců
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 5972d9e3d84a236104e85e17d8df1e9ee7f56122
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="creating-autoincrement-columns"></a><span data-ttu-id="2e4a2-102">Vytváření AutoIncrement sloupců</span><span class="sxs-lookup"><span data-stu-id="2e4a2-102">Creating AutoIncrement Columns</span></span>
<span data-ttu-id="2e4a2-103">Aby jedinečný sloupec hodnoty, můžete nastavit hodnoty ve sloupcích se zvýší automaticky při přidávání řádků do tabulky.</span><span class="sxs-lookup"><span data-stu-id="2e4a2-103">To ensure unique column values, you can set the column values to increment automatically when new rows are added to the table.</span></span> <span data-ttu-id="2e4a2-104">Chcete-li vytvořit automaticky rostoucí <xref:System.Data.DataColumn>, nastavte <xref:System.Data.DataColumn.AutoIncrement%2A> vlastnost sloupce, který se **true**.</span><span class="sxs-lookup"><span data-stu-id="2e4a2-104">To create an auto-incrementing <xref:System.Data.DataColumn>, set the <xref:System.Data.DataColumn.AutoIncrement%2A> property of the column to **true**.</span></span> <span data-ttu-id="2e4a2-105"><xref:System.Data.DataColumn> Pak začíná hodnota definovaná v <xref:System.Data.DataColumn.AutoIncrementSeed%2A> vlastnost a s každým řádkem přidat hodnotu **AutoIncrement** sloupec zvyšuje úroveň hodnota definovaná v <xref:System.Data.DataColumn.AutoIncrementStep%2A> vlastnost sloupce.</span><span class="sxs-lookup"><span data-stu-id="2e4a2-105">The <xref:System.Data.DataColumn> then starts with the value defined in the <xref:System.Data.DataColumn.AutoIncrementSeed%2A> property, and with each row added the value of the **AutoIncrement** column increases by the value defined in the <xref:System.Data.DataColumn.AutoIncrementStep%2A> property of the column.</span></span>  
  
 <span data-ttu-id="2e4a2-106">Pro **AutoIncrement** sloupců, doporučujeme, aby <xref:System.Data.DataColumn.ReadOnly%2A> vlastnost **DataColumn** nastavit na **true**.</span><span class="sxs-lookup"><span data-stu-id="2e4a2-106">For **AutoIncrement** columns, we recommend that the <xref:System.Data.DataColumn.ReadOnly%2A> property of the **DataColumn** be set to **true**.</span></span>  
  
 <span data-ttu-id="2e4a2-107">Následující příklad ukazuje, jak vytvořit sloupec, který začíná hodnota 200 a přidá postupně v krocích 3.</span><span class="sxs-lookup"><span data-stu-id="2e4a2-107">The following example demonstrates how to create a column that starts with a value of 200 and adds incrementally in steps of 3.</span></span>  
  
```vb  
Dim workColumn As DataColumn = workTable.Columns.Add( _  
    "CustomerID", typeof(Int32))  
workColumn.AutoIncrement = true  
workColumn.AutoIncrementSeed = 200  
workColumn.AutoIncrementStep = 3  
```  
  
```csharp  
DataColumn workColumn = workTable.Columns.Add(  
    "CustomerID", typeof(Int32));  
workColumn.AutoIncrement = true;  
workColumn.AutoIncrementSeed = 200;  
workColumn.AutoIncrementStep = 3;  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e4a2-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e4a2-108">See Also</span></span>  
 <xref:System.Data.DataColumn>  
 [<span data-ttu-id="2e4a2-109">Definice schématu datové tabulky</span><span class="sxs-lookup"><span data-stu-id="2e4a2-109">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="2e4a2-110">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="2e4a2-110">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="2e4a2-111">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="2e4a2-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
