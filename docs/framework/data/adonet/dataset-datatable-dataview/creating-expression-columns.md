---
title: "Vytváření výraz sloupce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 315944262136e5db453ea01eae64fff6cb0d534d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="creating-expression-columns"></a><span data-ttu-id="ebc18-102">Vytváření výraz sloupce</span><span class="sxs-lookup"><span data-stu-id="ebc18-102">Creating Expression Columns</span></span>
<span data-ttu-id="ebc18-103">Můžete definovat výraz pro sloupec, mu umožní obsahovat hodnotu vypočítat z jiné hodnoty sloupců na stejném řádku nebo z hodnoty ve sloupcích více řádků v tabulce.</span><span class="sxs-lookup"><span data-stu-id="ebc18-103">You can define an expression for a column, enabling it to contain a value calculated from other column values in the same row or from the column values of multiple rows in the table.</span></span> <span data-ttu-id="ebc18-104">Chcete-li definovat výraz, který se vyhodnotí, použijte <xref:System.Data.DataColumn.Expression%2A> vlastnost cílového sloupce použijte <xref:System.Data.DataColumn.ColumnName%2A> vlastnost, která má odkazovat na jiné sloupce ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="ebc18-104">To define the expression to be evaluated, use the <xref:System.Data.DataColumn.Expression%2A> property of the target column, and use the <xref:System.Data.DataColumn.ColumnName%2A> property to refer to other columns in the expression.</span></span> <span data-ttu-id="ebc18-105"><xref:System.Data.DataColumn.DataType%2A> Sloupec musí být výraz odpovídající hodnotu, která vrací výraz.</span><span class="sxs-lookup"><span data-stu-id="ebc18-105">The <xref:System.Data.DataColumn.DataType%2A> for the expression column must be appropriate for the value that the expression returns.</span></span>  
  
 <span data-ttu-id="ebc18-106">Následující tabulka uvádí několik možných používá pro výraz sloupce v tabulce.</span><span class="sxs-lookup"><span data-stu-id="ebc18-106">The following table lists several possible uses for expression columns in a table.</span></span>  
  
|<span data-ttu-id="ebc18-107">Typ výrazu</span><span class="sxs-lookup"><span data-stu-id="ebc18-107">Expression type</span></span>|<span data-ttu-id="ebc18-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="ebc18-108">Example</span></span>|  
|---------------------|-------------|  
|<span data-ttu-id="ebc18-109">Srovnání</span><span class="sxs-lookup"><span data-stu-id="ebc18-109">Comparison</span></span>|<span data-ttu-id="ebc18-110">"Celkový > = 500"</span><span class="sxs-lookup"><span data-stu-id="ebc18-110">"Total >= 500"</span></span>|  
|<span data-ttu-id="ebc18-111">Výpočet</span><span class="sxs-lookup"><span data-stu-id="ebc18-111">Computation</span></span>|<span data-ttu-id="ebc18-112">"UnitPrice * množství"</span><span class="sxs-lookup"><span data-stu-id="ebc18-112">"UnitPrice * Quantity"</span></span>|  
|<span data-ttu-id="ebc18-113">Agregace</span><span class="sxs-lookup"><span data-stu-id="ebc18-113">Aggregation</span></span>|<span data-ttu-id="ebc18-114">Výraz sum(price)</span><span class="sxs-lookup"><span data-stu-id="ebc18-114">Sum(Price)</span></span>|  
  
 <span data-ttu-id="ebc18-115">Můžete nastavit **výraz** vlastnost na existujícím **DataColumn** objekt, nebo můžete zahrnout vlastnost jako třetí argument předaný <xref:System.Data.DataColumn> konstruktoru, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ebc18-115">You can set the **Expression** property on an existing **DataColumn** object, or you can include the property as the third argument passed to the <xref:System.Data.DataColumn> constructor, as shown in the following example.</span></span>  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 <span data-ttu-id="ebc18-116">Výrazy mohou odkazovat na jiné výrazu sloupce; Cyklický odkaz, ve kterém dvou výrazů odkazovat na sebe, ale vygeneruje výjimku.</span><span class="sxs-lookup"><span data-stu-id="ebc18-116">Expressions can reference other expression columns; however, a circular reference, in which two expressions reference each other, will generate an exception.</span></span> <span data-ttu-id="ebc18-117">Pravidla o zapisují se výrazy, najdete v článku <xref:System.Data.DataColumn.Expression%2A> vlastnost **DataColumn** třídy.</span><span class="sxs-lookup"><span data-stu-id="ebc18-117">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebc18-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ebc18-118">See Also</span></span>  
 <xref:System.Data.DataColumn>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="ebc18-119">Definice schématu DataTable</span><span class="sxs-lookup"><span data-stu-id="ebc18-119">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="ebc18-120">DataTables</span><span class="sxs-lookup"><span data-stu-id="ebc18-120">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="ebc18-121">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="ebc18-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
