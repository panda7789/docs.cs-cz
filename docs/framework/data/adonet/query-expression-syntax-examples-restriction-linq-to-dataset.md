---
title: 'Příklady syntaxe výrazů dotazů: Omezení (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1daf42c2-c9f4-4cda-b291-7641b9c6d3fe
ms.openlocfilehash: 04a7b2027ac956d14086f94527b10d253749949d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794663"
---
# <a name="query-expression-syntax-examples-restriction-linq-to-dataset"></a><span data-ttu-id="12c1a-102">Příklady syntaxe výrazů dotazů: Omezení (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="12c1a-102">Query Expression Syntax Examples: Restriction (LINQ to DataSet)</span></span>
<span data-ttu-id="12c1a-103">Příklady v tomto tématu ukazují, jak použít <xref:System.Linq.Enumerable.Where%2A> metodu pro <xref:System.Data.DataSet> dotazování pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="12c1a-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Where%2A> method to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="12c1a-104">Metoda použitá v těchto příkladech je určena při [načítání dat do datové sady.](loading-data-into-a-dataset.md) `FillDataSet`</span><span class="sxs-lookup"><span data-stu-id="12c1a-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="12c1a-105">V příkladech v tomto tématu se používá tabulka Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="12c1a-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="12c1a-106">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="12c1a-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
[!code-csharp[DP LINQ to DataSetExamples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]        
  
 <span data-ttu-id="12c1a-107">Další informace najdete v tématu [jak: Vytvoření projektu LINQ to DataSet v aplikaci Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="12c1a-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="where"></a><span data-ttu-id="12c1a-108">Where</span><span class="sxs-lookup"><span data-stu-id="12c1a-108">Where</span></span>  
  
### <a name="example"></a><span data-ttu-id="12c1a-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="12c1a-109">Example</span></span>  
 <span data-ttu-id="12c1a-110">Tento příklad vrátí všechny online objednávky.</span><span class="sxs-lookup"><span data-stu-id="12c1a-110">This example returns all online orders.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)]     
  
### <a name="example"></a><span data-ttu-id="12c1a-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="12c1a-111">Example</span></span>  
 <span data-ttu-id="12c1a-112">Tento příklad vrátí objednávky, kde je množství objednávky větší než 2 a menší než 6.</span><span class="sxs-lookup"><span data-stu-id="12c1a-112">This example returns the orders where the order quantity is greater than 2 and less than 6.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where2)]  
 [!code-vb[DP LINQ to DataSet Examples#Where2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where2)]     
  
### <a name="example"></a><span data-ttu-id="12c1a-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="12c1a-113">Example</span></span>  
 <span data-ttu-id="12c1a-114">Tento příklad vrátí všechny červené barevné produkty.</span><span class="sxs-lookup"><span data-stu-id="12c1a-114">This example returns all red colored products.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]  
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]     
  
### <a name="example"></a><span data-ttu-id="12c1a-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="12c1a-115">Example</span></span>  
 <span data-ttu-id="12c1a-116">Tento příklad používá <xref:System.Linq.Enumerable.Where%2A> metodu k vyhledání objednávek, které byly provedeny po 1. prosinci 2002 a poté <xref:System.Data.DataRow.GetChildRows%2A> používá metodu k získání podrobností pro každou objednávku.</span><span class="sxs-lookup"><span data-stu-id="12c1a-116">This example uses the <xref:System.Linq.Enumerable.Where%2A> method to find orders that were made after December 1, 2002 and then uses the <xref:System.Data.DataRow.GetChildRows%2A> method to get the details for each order.</span></span>  
  
 [!code-csharp[DP LINQ to DataSetExamples#WhereDrillDown](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#wheredrilldown)]       
 [!code-vb[DP LINQ to DataSet Examples#WhereDrillDown](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#wheredrilldown)]  
  
## <a name="see-also"></a><span data-ttu-id="12c1a-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12c1a-117">See also</span></span>

- [<span data-ttu-id="12c1a-118">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="12c1a-118">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="12c1a-119">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="12c1a-119">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="12c1a-120">Přehled standardních operátorů dotazůC#()</span><span class="sxs-lookup"><span data-stu-id="12c1a-120">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="12c1a-121">Přehled standardních operátorů dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12c1a-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
