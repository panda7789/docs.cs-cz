---
title: Vytváření sloupců výrazů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
ms.openlocfilehash: 6e19e4e7cc0ea92e9d93e45c2a50d009e46b78c5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175497"
---
# <a name="creating-expression-columns"></a><span data-ttu-id="30ef5-102">Vytváření sloupců výrazů</span><span class="sxs-lookup"><span data-stu-id="30ef5-102">Creating Expression Columns</span></span>
<span data-ttu-id="30ef5-103">Výraz pro sloupec můžete definovat, díky tomu se může obsahovat hodnotu počítá z jiných hodnot sloupců na stejném řádku nebo z hodnoty ve sloupcích více řádků v tabulce.</span><span class="sxs-lookup"><span data-stu-id="30ef5-103">You can define an expression for a column, enabling it to contain a value calculated from other column values in the same row or from the column values of multiple rows in the table.</span></span> <span data-ttu-id="30ef5-104">Chcete-li definovat výraz, který má být vyhodnocen, použijte <xref:System.Data.DataColumn.Expression%2A> vlastnost cílového sloupce a jeho používání <xref:System.Data.DataColumn.ColumnName%2A> vlastnost k odkazování na ostatní sloupce ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="30ef5-104">To define the expression to be evaluated, use the <xref:System.Data.DataColumn.Expression%2A> property of the target column, and use the <xref:System.Data.DataColumn.ColumnName%2A> property to refer to other columns in the expression.</span></span> <span data-ttu-id="30ef5-105"><xref:System.Data.DataColumn.DataType%2A> Sloupec musí být výraz odpovídající hodnotu, která vrací výraz.</span><span class="sxs-lookup"><span data-stu-id="30ef5-105">The <xref:System.Data.DataColumn.DataType%2A> for the expression column must be appropriate for the value that the expression returns.</span></span>  
  
 <span data-ttu-id="30ef5-106">Následující tabulka uvádí několik možných použití výrazu sloupce v tabulce.</span><span class="sxs-lookup"><span data-stu-id="30ef5-106">The following table lists several possible uses for expression columns in a table.</span></span>  
  
|<span data-ttu-id="30ef5-107">Typ výrazu</span><span class="sxs-lookup"><span data-stu-id="30ef5-107">Expression type</span></span>|<span data-ttu-id="30ef5-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="30ef5-108">Example</span></span>|  
|---------------------|-------------|  
|<span data-ttu-id="30ef5-109">Srovnání</span><span class="sxs-lookup"><span data-stu-id="30ef5-109">Comparison</span></span>|<span data-ttu-id="30ef5-110">"Celkový > = 500"</span><span class="sxs-lookup"><span data-stu-id="30ef5-110">"Total >= 500"</span></span>|  
|<span data-ttu-id="30ef5-111">Výpočet</span><span class="sxs-lookup"><span data-stu-id="30ef5-111">Computation</span></span>|<span data-ttu-id="30ef5-112">"UnitPrice \* Quantity"</span><span class="sxs-lookup"><span data-stu-id="30ef5-112">"UnitPrice \* Quantity"</span></span>|  
|<span data-ttu-id="30ef5-113">Aggregation</span><span class="sxs-lookup"><span data-stu-id="30ef5-113">Aggregation</span></span>|<span data-ttu-id="30ef5-114">Výraz sum(price)</span><span class="sxs-lookup"><span data-stu-id="30ef5-114">Sum(Price)</span></span>|  
  
 <span data-ttu-id="30ef5-115">Můžete nastavit **výraz** vlastnost na existující **DataColumn** objektu, nebo můžete zahrnout vlastnost jako třetí argument předaný do <xref:System.Data.DataColumn> konstruktoru, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="30ef5-115">You can set the **Expression** property on an existing **DataColumn** object, or you can include the property as the third argument passed to the <xref:System.Data.DataColumn> constructor, as shown in the following example.</span></span>  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 <span data-ttu-id="30ef5-116">Výrazy mohou odkazovat na jiné sloupce výrazu; Cyklický odkaz, ve kterém dvou výrazů odkazovat na sebe navzájem, ale bude generovat výjimku.</span><span class="sxs-lookup"><span data-stu-id="30ef5-116">Expressions can reference other expression columns; however, a circular reference, in which two expressions reference each other, will generate an exception.</span></span> <span data-ttu-id="30ef5-117">Pravidla týkající se vytváření výrazů, najdete v článku <xref:System.Data.DataColumn.Expression%2A> vlastnost **DataColumn** třídy.</span><span class="sxs-lookup"><span data-stu-id="30ef5-117">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30ef5-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30ef5-118">See also</span></span>

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="30ef5-119">Definice schématu datové tabulky</span><span class="sxs-lookup"><span data-stu-id="30ef5-119">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [<span data-ttu-id="30ef5-120">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="30ef5-120">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [<span data-ttu-id="30ef5-121">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="30ef5-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
