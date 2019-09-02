---
title: Vytváření sloupců s automatickým navyšováním
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 2548ad9382b406978dac0a3d366207626278f501
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205128"
---
# <a name="creating-autoincrement-columns"></a><span data-ttu-id="c0a25-102">Vytváření sloupců s automatickým navyšováním</span><span class="sxs-lookup"><span data-stu-id="c0a25-102">Creating AutoIncrement Columns</span></span>
<span data-ttu-id="c0a25-103">Chcete-li zajistit jedinečné hodnoty sloupce, můžete nastavit hodnoty sloupce tak, aby byly automaticky zvyšovány při přidání nových řádků do tabulky.</span><span class="sxs-lookup"><span data-stu-id="c0a25-103">To ensure unique column values, you can set the column values to increment automatically when new rows are added to the table.</span></span> <span data-ttu-id="c0a25-104">Chcete-li vytvořit automatické přičítání <xref:System.Data.DataColumn>, <xref:System.Data.DataColumn.AutoIncrement%2A> nastavte vlastnost sloupce na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="c0a25-104">To create an auto-incrementing <xref:System.Data.DataColumn>, set the <xref:System.Data.DataColumn.AutoIncrement%2A> property of the column to **true**.</span></span> <span data-ttu-id="c0a25-105">Pak začíná <xref:System.Data.DataColumn.AutoIncrementSeed%2A> hodnotou definovanou ve vlastnosti a každým řádkem přidaným do sloupce <xref:System.Data.DataColumn.AutoIncrementStep%2A> autoincrements se zvyšuje hodnota definovaná ve vlastnosti sloupce. <xref:System.Data.DataColumn></span><span class="sxs-lookup"><span data-stu-id="c0a25-105">The <xref:System.Data.DataColumn> then starts with the value defined in the <xref:System.Data.DataColumn.AutoIncrementSeed%2A> property, and with each row added the value of the **AutoIncrement** column increases by the value defined in the <xref:System.Data.DataColumn.AutoIncrementStep%2A> property of the column.</span></span>  
  
 <span data-ttu-id="c0a25-106">Pro sloupce AutoIncrement doporučujeme, aby <xref:System.Data.DataColumn.ReadOnly%2A> vlastnost DataColumn byla nastavena na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="c0a25-106">For **AutoIncrement** columns, we recommend that the <xref:System.Data.DataColumn.ReadOnly%2A> property of the **DataColumn** be set to **true**.</span></span>  
  
 <span data-ttu-id="c0a25-107">Následující příklad ukazuje, jak vytvořit sloupec, který začíná hodnotou 200 a postupně se přidá do kroků 3.</span><span class="sxs-lookup"><span data-stu-id="c0a25-107">The following example demonstrates how to create a column that starts with a value of 200 and adds incrementally in steps of 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c0a25-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c0a25-108">See also</span></span>

- <xref:System.Data.DataColumn>
- [<span data-ttu-id="c0a25-109">Definice schématu datové tabulky</span><span class="sxs-lookup"><span data-stu-id="c0a25-109">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="c0a25-110">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="c0a25-110">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="c0a25-111">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="c0a25-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
