---
title: 'Příklady syntaxe výrazů dotazů: Operátory elementu (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ca392dda-16e3-45c7-8d87-12d8d4ee0578
ms.openlocfilehash: ae29ed3d61489b9da24a34e2e99ee32bd67c6d5c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783027"
---
# <a name="query-expression-syntax-examples-element-operators-linq-to-dataset"></a><span data-ttu-id="3c441-102">Příklady syntaxe výrazů dotazů: Operátory elementu (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="3c441-102">Query Expression Syntax Examples: Element Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="3c441-103">Příklady v tomto tématu ukazují <xref:System.Linq.Enumerable.First%2A> , jak použít metody a <xref:System.Linq.Enumerable.ElementAt%2A> <xref:System.Data.DataSet> k získání <xref:System.Data.DataRow> prvků z pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="3c441-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="3c441-104">Metoda použitá v těchto příkladech je určena při [načítání dat do datové sady.](loading-data-into-a-dataset.md) `FillDataSet`</span><span class="sxs-lookup"><span data-stu-id="3c441-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="3c441-105">V příkladech v tomto tématu se používá tabulka Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="3c441-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="3c441-106">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="3c441-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="3c441-107">Další informace najdete v tématu [jak: Vytvoření projektu LINQ to DataSet v aplikaci Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="3c441-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="elementat"></a><span data-ttu-id="3c441-108">ElementAt</span><span class="sxs-lookup"><span data-stu-id="3c441-108">ElementAt</span></span>  
  
### <a name="example"></a><span data-ttu-id="3c441-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="3c441-109">Example</span></span>  
 <span data-ttu-id="3c441-110">Tento příklad používá <xref:System.Linq.Enumerable.ElementAt%2A> metodu k načtení páté adresy, kde `PostalCode` = = "M4B 1V7".</span><span class="sxs-lookup"><span data-stu-id="3c441-110">This example uses the <xref:System.Linq.Enumerable.ElementAt%2A> method to retrieve the fifth address where `PostalCode` == "M4B 1V7".</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#elementat)]
 [!code-vb[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#elementat)]  
  
## <a name="first"></a><span data-ttu-id="3c441-111">První</span><span class="sxs-lookup"><span data-stu-id="3c441-111">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="3c441-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="3c441-112">Example</span></span>  
 <span data-ttu-id="3c441-113">Tento příklad používá <xref:System.Linq.Enumerable.First%2A> metodu k vrácení prvního kontaktu, jehož křestní jméno je ' Brooke '.</span><span class="sxs-lookup"><span data-stu-id="3c441-113">This example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is 'Brooke'.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#firstsimple)]
 [!code-vb[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#firstsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="3c441-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3c441-114">See also</span></span>

- [<span data-ttu-id="3c441-115">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="3c441-115">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="3c441-116">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="3c441-116">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="3c441-117">Přehled standardních operátorů dotazůC#()</span><span class="sxs-lookup"><span data-stu-id="3c441-117">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="3c441-118">Přehled standardních operátorů dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c441-118">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
