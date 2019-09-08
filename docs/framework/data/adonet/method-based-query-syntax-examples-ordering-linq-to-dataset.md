---
title: 'Příklady syntaxe dotazů založených na volání metody: Řazení (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f9ce4fd-e84f-48c0-bb64-89e217236d3e
ms.openlocfilehash: 16a37cb0bc36741ad816d2aa038a1390e3282d9b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794974"
---
# <a name="method-based-query-syntax-examples-ordering-linq-to-dataset"></a><span data-ttu-id="24a7f-102">Příklady syntaxe dotazů založených na volání metody: Řazení (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="24a7f-102">Method-Based Query Syntax Examples: Ordering (LINQ to DataSet)</span></span>
<span data-ttu-id="24a7f-103">Příklady v tomto <xref:System.Linq.Enumerable.OrderBy%2A>tématu ukazují, jak použít <xref:System.Linq.Enumerable.ThenBy%2A> metody, <xref:System.Linq.Enumerable.Reverse%2A>a k dotazování <xref:System.Data.DataSet> a seřazení výsledků pomocí syntaxe dotazu metody.</span><span class="sxs-lookup"><span data-stu-id="24a7f-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>,  <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenBy%2A> methods to query a <xref:System.Data.DataSet> and order the results using the method query syntax.</span></span>  
  
 <span data-ttu-id="24a7f-104">Metoda použitá v těchto příkladech je určena při [načítání dat do datové sady.](loading-data-into-a-dataset.md) `FillDataSet`</span><span class="sxs-lookup"><span data-stu-id="24a7f-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="24a7f-105">V příkladech v tomto tématu se používá tabulka Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="24a7f-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="24a7f-106">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="24a7f-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="24a7f-107">Další informace najdete v tématu [jak: Vytvoření projektu LINQ to DataSet v aplikaci Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="24a7f-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="orderby"></a><span data-ttu-id="24a7f-108">OrderBy</span><span class="sxs-lookup"><span data-stu-id="24a7f-108">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="24a7f-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="24a7f-109">Example</span></span>  
 <span data-ttu-id="24a7f-110">V <xref:System.Linq.Enumerable.OrderBy%2A> tomto příkladu se používá metoda s vlastní porovnávací metodou pro řazení příjmení bez rozlišování velkých a malých písmen.</span><span class="sxs-lookup"><span data-stu-id="24a7f-110">This example uses the <xref:System.Linq.Enumerable.OrderBy%2A> method with a custom comparer to do a case-insensitive sort of last names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbycomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbycomparer_mq)]  
  
## <a name="reverse"></a><span data-ttu-id="24a7f-111">Zpět</span><span class="sxs-lookup"><span data-stu-id="24a7f-111">Reverse</span></span>  
  
### <a name="example"></a><span data-ttu-id="24a7f-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="24a7f-112">Example</span></span>  
 <span data-ttu-id="24a7f-113">Tento příklad používá <xref:System.Linq.Enumerable.Reverse%2A> metodu k vytvoření seznamu objednávek, kde `OrderDate` je dřívější než 20. února 2002.</span><span class="sxs-lookup"><span data-stu-id="24a7f-113">This example uses the <xref:System.Linq.Enumerable.Reverse%2A> method to create a list of orders where `OrderDate` is earlier than Feb 20, 2002.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenby"></a><span data-ttu-id="24a7f-114">ThenBy</span><span class="sxs-lookup"><span data-stu-id="24a7f-114">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="24a7f-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="24a7f-115">Example</span></span>  
 <span data-ttu-id="24a7f-116">Tento příklad používá <xref:System.Linq.Enumerable.OrderBy%2A> metody <xref:System.Linq.Enumerable.ThenBy%2A> a s vlastními porovnávacími k prvnímu řazení podle ceníkové ceny a pak provede sestupné řazení názvů produktů bez rozlišování velkých a malých písmen.</span><span class="sxs-lookup"><span data-stu-id="24a7f-116">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.ThenBy%2A> methods with a custom comparer to first sort by list price, and then perform a case-insensitive descending sort of the product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingcomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingcomparer_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="24a7f-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="24a7f-117">See also</span></span>

- [<span data-ttu-id="24a7f-118">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="24a7f-118">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="24a7f-119">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="24a7f-119">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="24a7f-120">Přehled standardních operátorů dotazůC#()</span><span class="sxs-lookup"><span data-stu-id="24a7f-120">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="24a7f-121">Přehled standardních operátorů dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24a7f-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
