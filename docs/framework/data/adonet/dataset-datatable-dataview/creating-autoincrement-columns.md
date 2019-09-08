---
title: Vytváření sloupců s automatickým navyšováním
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 5e4a36829107480a44980c7210b39c21231c67f4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786451"
---
# <a name="creating-autoincrement-columns"></a><span data-ttu-id="5d298-102">Vytváření sloupců s automatickým navyšováním</span><span class="sxs-lookup"><span data-stu-id="5d298-102">Creating AutoIncrement Columns</span></span>
<span data-ttu-id="5d298-103">Chcete-li zajistit jedinečné hodnoty sloupce, můžete nastavit hodnoty sloupce tak, aby byly automaticky zvyšovány při přidání nových řádků do tabulky.</span><span class="sxs-lookup"><span data-stu-id="5d298-103">To ensure unique column values, you can set the column values to increment automatically when new rows are added to the table.</span></span> <span data-ttu-id="5d298-104">Chcete-li vytvořit automatické přičítání <xref:System.Data.DataColumn>, <xref:System.Data.DataColumn.AutoIncrement%2A> nastavte vlastnost sloupce na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="5d298-104">To create an auto-incrementing <xref:System.Data.DataColumn>, set the <xref:System.Data.DataColumn.AutoIncrement%2A> property of the column to **true**.</span></span> <span data-ttu-id="5d298-105">Pak začíná hodnotou definovanou <xref:System.Data.DataColumn.AutoIncrementSeed%2A> ve vlastnosti a každým řádkem přidaným do sloupce **autoincrements** se <xref:System.Data.DataColumn.AutoIncrementStep%2A> zvyšuje hodnota definovaná ve vlastnosti sloupce. <xref:System.Data.DataColumn></span><span class="sxs-lookup"><span data-stu-id="5d298-105">The <xref:System.Data.DataColumn> then starts with the value defined in the <xref:System.Data.DataColumn.AutoIncrementSeed%2A> property, and with each row added the value of the **AutoIncrement** column increases by the value defined in the <xref:System.Data.DataColumn.AutoIncrementStep%2A> property of the column.</span></span>  
  
 <span data-ttu-id="5d298-106">Pro sloupce **AutoIncrement** doporučujeme, aby <xref:System.Data.DataColumn.ReadOnly%2A> vlastnost **DataColumn** byla nastavena na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="5d298-106">For **AutoIncrement** columns, we recommend that the <xref:System.Data.DataColumn.ReadOnly%2A> property of the **DataColumn** be set to **true**.</span></span>  
  
 <span data-ttu-id="5d298-107">Následující příklad ukazuje, jak vytvořit sloupec, který začíná hodnotou 200 a postupně se přidá do kroků 3.</span><span class="sxs-lookup"><span data-stu-id="5d298-107">The following example demonstrates how to create a column that starts with a value of 200 and adds incrementally in steps of 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5d298-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d298-108">See also</span></span>

- <xref:System.Data.DataColumn>
- [<span data-ttu-id="5d298-109">Definice schématu datové tabulky</span><span class="sxs-lookup"><span data-stu-id="5d298-109">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="5d298-110">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="5d298-110">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="5d298-111">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5d298-111">ADO.NET Overview</span></span>](../ado-net-overview.md)
