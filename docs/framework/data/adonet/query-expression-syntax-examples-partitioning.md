---
title: 'Příklady syntaxe výrazů dotazů: Dělení (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: beb5f361-1ac8-44fb-afa1-2aacea15f166
ms.openlocfilehash: 6a00c5d49acc02c476895c999687aa944ba26aff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795097"
---
# <a name="query-expression-syntax-examples-partitioning-linq-to-dataset"></a><span data-ttu-id="e8e7b-102">Příklady syntaxe výrazů dotazů: Dělení (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="e8e7b-102">Query Expression Syntax Examples: Partitioning (LINQ to DataSet)</span></span>
<span data-ttu-id="e8e7b-103">Příklady v tomto tématu ukazují, jak použít <xref:System.Linq.Enumerable.Skip%2A> metody a <xref:System.Linq.Enumerable.Take%2A> k dotazování <xref:System.Data.DataSet> pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="e8e7b-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="e8e7b-104">Metoda použitá v těchto příkladech je určena při [načítání dat do datové sady.](loading-data-into-a-dataset.md) `FillDataSet`</span><span class="sxs-lookup"><span data-stu-id="e8e7b-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="e8e7b-105">V příkladech v tomto tématu se používá tabulka Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e8e7b-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="e8e7b-106">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="e8e7b-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="e8e7b-107">Další informace najdete v tématu [jak: Vytvoření projektu LINQ to DataSet v aplikaci Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="e8e7b-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="skip"></a><span data-ttu-id="e8e7b-108">Skip</span><span class="sxs-lookup"><span data-stu-id="e8e7b-108">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="e8e7b-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8e7b-109">Example</span></span>  
 <span data-ttu-id="e8e7b-110">Tento příklad používá <xref:System.Linq.Enumerable.Skip%2A> metodu k získání všech kromě prvních dvou adres v Praze.</span><span class="sxs-lookup"><span data-stu-id="e8e7b-110">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="e8e7b-111">Take</span><span class="sxs-lookup"><span data-stu-id="e8e7b-111">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="e8e7b-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8e7b-112">Example</span></span>  
 <span data-ttu-id="e8e7b-113">Tento příklad používá <xref:System.Linq.Enumerable.Take%2A> metodu k získání prvních tří adres v Praze.</span><span class="sxs-lookup"><span data-stu-id="e8e7b-113">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takenested)]
 [!code-vb[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="e8e7b-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8e7b-114">See also</span></span>

- [<span data-ttu-id="e8e7b-115">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="e8e7b-115">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="e8e7b-116">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="e8e7b-116">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="e8e7b-117">Přehled standardních operátorů dotazůC#()</span><span class="sxs-lookup"><span data-stu-id="e8e7b-117">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="e8e7b-118">Přehled standardních operátorů dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8e7b-118">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
