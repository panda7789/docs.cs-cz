---
title: 'Příklady syntaxe výrazů dotazů: Operátory elementů (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ca392dda-16e3-45c7-8d87-12d8d4ee0578
ms.openlocfilehash: 62c2a1737c6c253effc496f2569c42812732946b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43392953"
---
# <a name="query-expression-syntax-examples-element-operators-linq-to-dataset"></a><span data-ttu-id="f33ba-102">Příklady syntaxe výrazů dotazů: Operátory elementů (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="f33ba-102">Query Expression Syntax Examples: Element Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="f33ba-103">Příklady v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.First%2A> a <xref:System.Linq.Enumerable.ElementAt%2A> metody k získání <xref:System.Data.DataRow> elementy ze <xref:System.Data.DataSet> pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="f33ba-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="f33ba-104">`FillDataSet` Metodu použitou v těchto příkladech je zadán v [načítání dat do datová sada](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="f33ba-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="f33ba-105">Příklady v tomto tématu použijte tabulky Kontakt, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f33ba-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="f33ba-106">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="f33ba-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="f33ba-107">Další informace najdete v tématu [postupy: vytvoření LINQ to DataSet projektu v sadě Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="f33ba-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="elementat"></a><span data-ttu-id="f33ba-108">ElementAt</span><span class="sxs-lookup"><span data-stu-id="f33ba-108">ElementAt</span></span>  
  
### <a name="example"></a><span data-ttu-id="f33ba-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="f33ba-109">Example</span></span>  
 <span data-ttu-id="f33ba-110">V tomto příkladu <xref:System.Linq.Enumerable.ElementAt%2A> metody k získání páté adresu kde `PostalCode` == "M4B 1V7".</span><span class="sxs-lookup"><span data-stu-id="f33ba-110">This example uses the <xref:System.Linq.Enumerable.ElementAt%2A> method to retrieve the fifth address where `PostalCode` == "M4B 1V7".</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#elementat)]
 [!code-vb[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#elementat)]  
  
## <a name="first"></a><span data-ttu-id="f33ba-111">první</span><span class="sxs-lookup"><span data-stu-id="f33ba-111">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="f33ba-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="f33ba-112">Example</span></span>  
 <span data-ttu-id="f33ba-113">V tomto příkladu <xref:System.Linq.Enumerable.First%2A> metoda vrátí první kontakt jejichž křestní jméno je "Brooke".</span><span class="sxs-lookup"><span data-stu-id="f33ba-113">This example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is 'Brooke'.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#firstsimple)]
 [!code-vb[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#firstsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="f33ba-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="f33ba-114">See Also</span></span>  
 [<span data-ttu-id="f33ba-115">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="f33ba-115">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="f33ba-116">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="f33ba-116">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="f33ba-117">Přehled standardních operátorů dotazu</span><span class="sxs-lookup"><span data-stu-id="f33ba-117">Standard Query Operators Overview</span></span>](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
