---
title: Vytváření sloupců výrazů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
ms.openlocfilehash: 1c4e0b368a8eb154207382ae70b9767f5a5fe64d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785433"
---
# <a name="creating-expression-columns"></a><span data-ttu-id="fb458-102">Vytváření sloupců výrazů</span><span class="sxs-lookup"><span data-stu-id="fb458-102">Creating Expression Columns</span></span>
<span data-ttu-id="fb458-103">Můžete definovat výraz pro sloupec, který umožňuje, aby obsahoval hodnotu vypočítanou z jiných hodnot sloupce ve stejném řádku nebo z hodnot sloupců s více řádky v tabulce.</span><span class="sxs-lookup"><span data-stu-id="fb458-103">You can define an expression for a column, enabling it to contain a value calculated from other column values in the same row or from the column values of multiple rows in the table.</span></span> <span data-ttu-id="fb458-104">Chcete-li definovat výraz, který má být vyhodnocen, použijte <xref:System.Data.DataColumn.Expression%2A> vlastnost cílového sloupce a <xref:System.Data.DataColumn.ColumnName%2A> použijte vlastnost pro odkaz na jiné sloupce ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="fb458-104">To define the expression to be evaluated, use the <xref:System.Data.DataColumn.Expression%2A> property of the target column, and use the <xref:System.Data.DataColumn.ColumnName%2A> property to refer to other columns in the expression.</span></span> <span data-ttu-id="fb458-105"><xref:System.Data.DataColumn.DataType%2A> Hodnota sloupce Expression musí být vhodná pro hodnotu, kterou výraz vrátí.</span><span class="sxs-lookup"><span data-stu-id="fb458-105">The <xref:System.Data.DataColumn.DataType%2A> for the expression column must be appropriate for the value that the expression returns.</span></span>  
  
 <span data-ttu-id="fb458-106">Následující tabulka uvádí několik možných použití pro sloupce výrazů v tabulce.</span><span class="sxs-lookup"><span data-stu-id="fb458-106">The following table lists several possible uses for expression columns in a table.</span></span>  
  
|<span data-ttu-id="fb458-107">Typ výrazu</span><span class="sxs-lookup"><span data-stu-id="fb458-107">Expression type</span></span>|<span data-ttu-id="fb458-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="fb458-108">Example</span></span>|  
|---------------------|-------------|  
|<span data-ttu-id="fb458-109">Srovnání</span><span class="sxs-lookup"><span data-stu-id="fb458-109">Comparison</span></span>|<span data-ttu-id="fb458-110">"Total > = 500"</span><span class="sxs-lookup"><span data-stu-id="fb458-110">"Total >= 500"</span></span>|  
|<span data-ttu-id="fb458-111">Běhu</span><span class="sxs-lookup"><span data-stu-id="fb458-111">Computation</span></span>|<span data-ttu-id="fb458-112">"JednotkováCena \* množství"</span><span class="sxs-lookup"><span data-stu-id="fb458-112">"UnitPrice \* Quantity"</span></span>|  
|<span data-ttu-id="fb458-113">Agregace</span><span class="sxs-lookup"><span data-stu-id="fb458-113">Aggregation</span></span>|<span data-ttu-id="fb458-114">Sum (price)</span><span class="sxs-lookup"><span data-stu-id="fb458-114">Sum(Price)</span></span>|  
  
 <span data-ttu-id="fb458-115">Můžete nastavit vlastnost **Expression** pro existující objekt **DataColumn** nebo můžete vlastnost zahrnout jako třetí argument <xref:System.Data.DataColumn> předaný konstruktoru, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="fb458-115">You can set the **Expression** property on an existing **DataColumn** object, or you can include the property as the third argument passed to the <xref:System.Data.DataColumn> constructor, as shown in the following example.</span></span>  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 <span data-ttu-id="fb458-116">Výrazy můžou odkazovat na jiné sloupce výrazu; Nicméně cyklický odkaz, ve kterém dva výrazy odkazují na sebe navzájem, vygenerují výjimku.</span><span class="sxs-lookup"><span data-stu-id="fb458-116">Expressions can reference other expression columns; however, a circular reference, in which two expressions reference each other, will generate an exception.</span></span> <span data-ttu-id="fb458-117">Pravidla týkající se psaní výrazů naleznete v tématu <xref:System.Data.DataColumn.Expression%2A> vlastnost třídy **DataColumn** .</span><span class="sxs-lookup"><span data-stu-id="fb458-117">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb458-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb458-118">See also</span></span>

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="fb458-119">Definice schématu datové tabulky</span><span class="sxs-lookup"><span data-stu-id="fb458-119">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="fb458-120">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="fb458-120">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="fb458-121">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fb458-121">ADO.NET Overview</span></span>](../ado-net-overview.md)
