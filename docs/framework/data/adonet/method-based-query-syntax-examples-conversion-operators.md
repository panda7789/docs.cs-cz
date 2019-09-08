---
title: 'Příklady syntaxe dotazů založených na volání metody: Operátory převodu (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a084c16b-9b55-4690-aefd-f8e0810a92c3
ms.openlocfilehash: 3e2a72a2bb0921828bdd90fe437987fddfc995b5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783695"
---
# <a name="method-based-query-syntax-examples-conversion-operators-linq-to-dataset"></a><span data-ttu-id="b69dc-102">Příklady syntaxe dotazů založených na volání metody: Operátory převodu (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="b69dc-102">Method-Based Query Syntax Examples: Conversion Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="b69dc-103">Příklady v tomto tématu ukazují <xref:System.Linq.Enumerable.ToArray%2A>, jak použít metody, <xref:System.Linq.Enumerable.ToDictionary%2A>a <xref:System.Linq.Enumerable.ToList%2A> k okamžitému provedení výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="b69dc-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, and <xref:System.Linq.Enumerable.ToList%2A> methods to immediately execute a query expression.</span></span>  
  
 <span data-ttu-id="b69dc-104">Metoda použitá v těchto příkladech je určena při [načítání dat do datové sady.](loading-data-into-a-dataset.md) `FillDataSet`</span><span class="sxs-lookup"><span data-stu-id="b69dc-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="b69dc-105">V příkladech v tomto tématu se používá tabulka Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b69dc-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="b69dc-106">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="b69dc-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="b69dc-107">Další informace najdete v tématu [jak: Vytvoření projektu LINQ to DataSet v aplikaci Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="b69dc-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="toarray"></a><span data-ttu-id="b69dc-108">ToArray –</span><span class="sxs-lookup"><span data-stu-id="b69dc-108">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="b69dc-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="b69dc-109">Example</span></span>  
 <span data-ttu-id="b69dc-110">Tento příklad používá <xref:System.Linq.Enumerable.ToArray%2A> metodu k okamžitému vyhodnocení sekvence do pole.</span><span class="sxs-lookup"><span data-stu-id="b69dc-110">This example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="b69dc-111">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="b69dc-111">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="b69dc-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="b69dc-112">Example</span></span>  
 <span data-ttu-id="b69dc-113">Tento příklad používá <xref:System.Linq.Enumerable.ToDictionary%2A> metodu k okamžitému vyhodnocení sekvence a souvisejícího výrazu klíče do slovníku.</span><span class="sxs-lookup"><span data-stu-id="b69dc-113">This example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="b69dc-114">ToList –</span><span class="sxs-lookup"><span data-stu-id="b69dc-114">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="b69dc-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="b69dc-115">Example</span></span>  
 <span data-ttu-id="b69dc-116">Tento příklad používá <xref:System.Linq.Enumerable.ToList%2A> metodu pro okamžité vyhodnocení sekvence <xref:System.Collections.Generic.List%601>do, kde `T` je typu <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="b69dc-116">This example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#tolist)]
 [!code-vb[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="b69dc-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b69dc-117">See also</span></span>

- [<span data-ttu-id="b69dc-118">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="b69dc-118">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="b69dc-119">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="b69dc-119">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="b69dc-120">Přehled standardních operátorů dotazůC#()</span><span class="sxs-lookup"><span data-stu-id="b69dc-120">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="b69dc-121">Přehled standardních operátorů dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b69dc-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
