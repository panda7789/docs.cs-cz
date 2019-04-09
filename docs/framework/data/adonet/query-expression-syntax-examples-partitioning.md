---
title: 'Příklady syntaxe výrazů dotazů: Dělení (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: beb5f361-1ac8-44fb-afa1-2aacea15f166
ms.openlocfilehash: 35c9c0346c84be7002800c8bf0c7e5eb8f1381e5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116698"
---
# <a name="query-expression-syntax-examples-partitioning-linq-to-dataset"></a><span data-ttu-id="f8cd7-102">Příklady syntaxe výrazů dotazů: Dělení (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="f8cd7-102">Query Expression Syntax Examples: Partitioning (LINQ to DataSet)</span></span>
<span data-ttu-id="f8cd7-103">Příklady v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Skip%2A> a <xref:System.Linq.Enumerable.Take%2A> metody pro dotazování <xref:System.Data.DataSet> pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="f8cd7-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="f8cd7-104">`FillDataSet` Metodu použitou v těchto příkladech je zadán v [načítání dat do datová sada](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="f8cd7-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="f8cd7-105">Příklady v tomto tématu použijte tabulky Kontakt, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f8cd7-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="f8cd7-106">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="f8cd7-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="f8cd7-107">Další informace najdete v tématu [jak: Vytvoření LINQ to DataSet projektu v sadě Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="f8cd7-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="skip"></a><span data-ttu-id="f8cd7-108">Skip</span><span class="sxs-lookup"><span data-stu-id="f8cd7-108">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="f8cd7-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8cd7-109">Example</span></span>  
 <span data-ttu-id="f8cd7-110">V tomto příkladu <xref:System.Linq.Enumerable.Skip%2A> metodu k získání všech, ale prvních dvou adres v Praze.</span><span class="sxs-lookup"><span data-stu-id="f8cd7-110">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="f8cd7-111">Take</span><span class="sxs-lookup"><span data-stu-id="f8cd7-111">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="f8cd7-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8cd7-112">Example</span></span>  
 <span data-ttu-id="f8cd7-113">V tomto příkladu <xref:System.Linq.Enumerable.Take%2A> metodu k získání prvními třemi adresami v Seattlu.</span><span class="sxs-lookup"><span data-stu-id="f8cd7-113">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takenested)]
 [!code-vb[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="f8cd7-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8cd7-114">See also</span></span>

- [<span data-ttu-id="f8cd7-115">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="f8cd7-115">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="f8cd7-116">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="f8cd7-116">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="f8cd7-117">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="f8cd7-117">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="f8cd7-118">Přehled standardních operátorů dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8cd7-118">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
