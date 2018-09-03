---
title: Vytváření sloupců výrazů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
ms.openlocfilehash: 9c7a656e82198568c39b9bb58f8708f563d6caa2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43482312"
---
# <a name="creating-expression-columns"></a><span data-ttu-id="2e13b-102">Vytváření sloupců výrazů</span><span class="sxs-lookup"><span data-stu-id="2e13b-102">Creating Expression Columns</span></span>
<span data-ttu-id="2e13b-103">Výraz pro sloupec můžete definovat, díky tomu se může obsahovat hodnotu počítá z jiných hodnot sloupců na stejném řádku nebo z hodnoty ve sloupcích více řádků v tabulce.</span><span class="sxs-lookup"><span data-stu-id="2e13b-103">You can define an expression for a column, enabling it to contain a value calculated from other column values in the same row or from the column values of multiple rows in the table.</span></span> <span data-ttu-id="2e13b-104">Chcete-li definovat výraz, který má být vyhodnocen, použijte <xref:System.Data.DataColumn.Expression%2A> vlastnost cílového sloupce a jeho používání <xref:System.Data.DataColumn.ColumnName%2A> vlastnost k odkazování na ostatní sloupce ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="2e13b-104">To define the expression to be evaluated, use the <xref:System.Data.DataColumn.Expression%2A> property of the target column, and use the <xref:System.Data.DataColumn.ColumnName%2A> property to refer to other columns in the expression.</span></span> <span data-ttu-id="2e13b-105"><xref:System.Data.DataColumn.DataType%2A> Sloupec musí být výraz odpovídající hodnotu, která vrací výraz.</span><span class="sxs-lookup"><span data-stu-id="2e13b-105">The <xref:System.Data.DataColumn.DataType%2A> for the expression column must be appropriate for the value that the expression returns.</span></span>  
  
 <span data-ttu-id="2e13b-106">Následující tabulka uvádí několik možných použití výrazu sloupce v tabulce.</span><span class="sxs-lookup"><span data-stu-id="2e13b-106">The following table lists several possible uses for expression columns in a table.</span></span>  
  
|<span data-ttu-id="2e13b-107">Typ výrazu</span><span class="sxs-lookup"><span data-stu-id="2e13b-107">Expression type</span></span>|<span data-ttu-id="2e13b-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="2e13b-108">Example</span></span>|  
|---------------------|-------------|  
|<span data-ttu-id="2e13b-109">Srovnání</span><span class="sxs-lookup"><span data-stu-id="2e13b-109">Comparison</span></span>|<span data-ttu-id="2e13b-110">"Celkový > = 500"</span><span class="sxs-lookup"><span data-stu-id="2e13b-110">"Total >= 500"</span></span>|  
|<span data-ttu-id="2e13b-111">Výpočet</span><span class="sxs-lookup"><span data-stu-id="2e13b-111">Computation</span></span>|<span data-ttu-id="2e13b-112">"UnitPrice \* Quantity"</span><span class="sxs-lookup"><span data-stu-id="2e13b-112">"UnitPrice \* Quantity"</span></span>|  
|<span data-ttu-id="2e13b-113">Agregace</span><span class="sxs-lookup"><span data-stu-id="2e13b-113">Aggregation</span></span>|<span data-ttu-id="2e13b-114">Výraz sum(price)</span><span class="sxs-lookup"><span data-stu-id="2e13b-114">Sum(Price)</span></span>|  
  
 <span data-ttu-id="2e13b-115">Můžete nastavit **výraz** vlastnost na existující **DataColumn** objektu, nebo můžete zahrnout vlastnost jako třetí argument předaný do <xref:System.Data.DataColumn> konstruktoru, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2e13b-115">You can set the **Expression** property on an existing **DataColumn** object, or you can include the property as the third argument passed to the <xref:System.Data.DataColumn> constructor, as shown in the following example.</span></span>  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 <span data-ttu-id="2e13b-116">Výrazy mohou odkazovat na jiné sloupce výrazu; Cyklický odkaz, ve kterém dvou výrazů odkazovat na sebe navzájem, ale bude generovat výjimku.</span><span class="sxs-lookup"><span data-stu-id="2e13b-116">Expressions can reference other expression columns; however, a circular reference, in which two expressions reference each other, will generate an exception.</span></span> <span data-ttu-id="2e13b-117">Pravidla týkající se vytváření výrazů, najdete v článku <xref:System.Data.DataColumn.Expression%2A> vlastnost **DataColumn** třídy.</span><span class="sxs-lookup"><span data-stu-id="2e13b-117">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e13b-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e13b-118">See Also</span></span>  
 <xref:System.Data.DataColumn>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="2e13b-119">Definice schématu datové tabulky</span><span class="sxs-lookup"><span data-stu-id="2e13b-119">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="2e13b-120">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="2e13b-120">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="2e13b-121">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="2e13b-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
