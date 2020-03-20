---
title: 'Příklady syntaxe dotazu založené na metodách: Operátory elementů (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eedf2fbd-f407-4f62-bb1a-c00eb001b1dd
ms.openlocfilehash: e43208d6ae524a1370b936d42508e9c7a7d196e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149504"
---
# <a name="method-based-query-syntax-examples-element-operators-linq-to-dataset"></a><span data-ttu-id="aff7b-102">Příklady syntaxe dotazu založené na metodách: Operátory elementů (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="aff7b-102">Method-Based Query Syntax Examples: Element Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="aff7b-103">Příklady v tomto tématu ukazují, <xref:System.Linq.Enumerable.ElementAt%2A> jak <xref:System.Data.DataRow> používat metody <xref:System.Data.DataSet> <xref:System.Linq.Enumerable.First%2A> a získat prvky z pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="aff7b-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="aff7b-104">Metoda `FillDataSet` použitá v těchto příkladech je určena v [načtení dat do datové sady](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="aff7b-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="aff7b-105">Příklady v tomto tématu používají tabulky Kontakt, Adresa, Produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="aff7b-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="aff7b-106">Příklady v tomto tématu `using` / `Imports` používají následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="aff7b-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
[!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
[!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]

 <span data-ttu-id="aff7b-107">Další informace naleznete v [tématu How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="aff7b-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="elementat"></a><span data-ttu-id="aff7b-108">Elementat</span><span class="sxs-lookup"><span data-stu-id="aff7b-108">ElementAt</span></span>  
  
### <a name="example"></a><span data-ttu-id="aff7b-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="aff7b-109">Example</span></span>  
 <span data-ttu-id="aff7b-110">Tento příklad <xref:System.Linq.Enumerable.ElementAt%2A> používá metodu k `PostalCode` načtení páté adresy, kde == "M4B 1V7".</span><span class="sxs-lookup"><span data-stu-id="aff7b-110">This example uses the <xref:System.Linq.Enumerable.ElementAt%2A> method to retrieve the fifth address where `PostalCode` == "M4B 1V7".</span></span>  
  
[!code-csharp[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#elementat)]
[!code-vb[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#elementat)]
  
## <a name="first"></a><span data-ttu-id="aff7b-111">První</span><span class="sxs-lookup"><span data-stu-id="aff7b-111">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="aff7b-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="aff7b-112">Example</span></span>  
 <span data-ttu-id="aff7b-113">Tento příklad <xref:System.Linq.Enumerable.First%2A> používá metodu k vrácení první kontakt, jehož křestní jméno je "Brooke".</span><span class="sxs-lookup"><span data-stu-id="aff7b-113">This example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is 'Brooke'.</span></span>  
  
[!code-csharp[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#firstsimple)]
[!code-vb[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#firstsimple)]
  
## <a name="see-also"></a><span data-ttu-id="aff7b-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="aff7b-114">See also</span></span>

- [<span data-ttu-id="aff7b-115">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="aff7b-115">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="aff7b-116">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="aff7b-116">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="aff7b-117">Standardní operátory dotazů – přehled (C#)</span><span class="sxs-lookup"><span data-stu-id="aff7b-117">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="aff7b-118">Standardní operátory dotazů – přehled (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aff7b-118">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
