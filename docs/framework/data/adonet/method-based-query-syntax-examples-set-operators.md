---
title: 'Příklady syntaxe dotazů založených na volání metody: Nastavit operátory (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa93af15-28af-4b5e-846b-897308410edb
ms.openlocfilehash: 481c0ed7e39b8f958ccdae01e4589d54b3ff2446
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783576"
---
# <a name="method-based-query-syntax-examples-set-operators-linq-to-dataset"></a><span data-ttu-id="92b6e-102">Příklady syntaxe dotazů založených na volání metody: Nastavit operátory (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="92b6e-102">Method-Based Query Syntax Examples: Set Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="92b6e-103">Příklady v tomto <xref:System.Linq.Enumerable.Distinct%2A>tématu ukazují, jak použít <xref:System.Linq.Enumerable.Union%2A> operátory, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>a k provádění operací porovnání na základě hodnoty na sadách datových řádků.[ Načítají se data do datové sady](loading-data-into-a-dataset.md) . Další informace najdete v <xref:System.Data.DataRowComparer>tématu [porovnání datových řádků](comparing-datarows-linq-to-dataset.md) .</span><span class="sxs-lookup"><span data-stu-id="92b6e-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, and <xref:System.Linq.Enumerable.Union%2A> operators to perform value-based comparison operations on sets of data rows.[Loading Data Into a DataSet](loading-data-into-a-dataset.md) See [Comparing DataRows](comparing-datarows-linq-to-dataset.md) for more information on <xref:System.Data.DataRowComparer>.</span></span>  
  
 <span data-ttu-id="92b6e-104">Metoda použitá v těchto příkladech je určena při [načítání dat do datové sady.](loading-data-into-a-dataset.md) `FillDataSet`</span><span class="sxs-lookup"><span data-stu-id="92b6e-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="92b6e-105">V příkladech v tomto tématu se používá tabulka Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="92b6e-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="92b6e-106">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="92b6e-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="92b6e-107">Další informace najdete v tématu [jak: Vytvoření projektu LINQ to DataSet v aplikaci Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="92b6e-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="distinct"></a><span data-ttu-id="92b6e-108">Distinct</span><span class="sxs-lookup"><span data-stu-id="92b6e-108">Distinct</span></span>  
  
### <a name="example"></a><span data-ttu-id="92b6e-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="92b6e-109">Example</span></span>  
 <span data-ttu-id="92b6e-110">Tento příklad používá <xref:System.Linq.Enumerable.Distinct%2A> metodu pro odebrání duplicitních prvků v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="92b6e-110">This example uses the <xref:System.Linq.Enumerable.Distinct%2A> method to remove duplicate elements in a sequence.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#distinctrows)]
 [!code-vb[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#distinctrows)]  
  
## <a name="except"></a><span data-ttu-id="92b6e-111">Výjimk</span><span class="sxs-lookup"><span data-stu-id="92b6e-111">Except</span></span>  
  
### <a name="example"></a><span data-ttu-id="92b6e-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="92b6e-112">Example</span></span>  
 <span data-ttu-id="92b6e-113">Tento příklad používá <xref:System.Linq.Enumerable.Except%2A> metodu k vrácení kontaktů, které se zobrazí v první tabulce, ale ne v druhé.</span><span class="sxs-lookup"><span data-stu-id="92b6e-113">This example uses the <xref:System.Linq.Enumerable.Except%2A> method to return contacts that appear in the first table but not in the second.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#except2)]
 [!code-vb[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#except2)]  
  
## <a name="intersect"></a><span data-ttu-id="92b6e-114">Krývají</span><span class="sxs-lookup"><span data-stu-id="92b6e-114">Intersect</span></span>  
  
### <a name="example"></a><span data-ttu-id="92b6e-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="92b6e-115">Example</span></span>  
 <span data-ttu-id="92b6e-116">Tento příklad používá <xref:System.Linq.Enumerable.Intersect%2A> metodu k vrácení kontaktů, které se zobrazí v obou tabulkách.</span><span class="sxs-lookup"><span data-stu-id="92b6e-116">This example uses the <xref:System.Linq.Enumerable.Intersect%2A> method to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
## <a name="union"></a><span data-ttu-id="92b6e-117">Unie</span><span class="sxs-lookup"><span data-stu-id="92b6e-117">Union</span></span>  
  
### <a name="example"></a><span data-ttu-id="92b6e-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="92b6e-118">Example</span></span>  
 <span data-ttu-id="92b6e-119">Tento příklad používá <xref:System.Linq.Enumerable.Union%2A> metodu k vrácení jedinečných kontaktů z obou tabulek.</span><span class="sxs-lookup"><span data-stu-id="92b6e-119">This example uses the <xref:System.Linq.Enumerable.Union%2A> method to return unique contacts from either of the two tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#union2)]
 [!code-vb[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#union2)]  
  
## <a name="see-also"></a><span data-ttu-id="92b6e-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="92b6e-120">See also</span></span>

- [<span data-ttu-id="92b6e-121">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="92b6e-121">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="92b6e-122">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="92b6e-122">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="92b6e-123">Přehled standardních operátorů dotazůC#()</span><span class="sxs-lookup"><span data-stu-id="92b6e-123">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="92b6e-124">Přehled standardních operátorů dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92b6e-124">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
