---
title: "Porovnání DataRows (LINQ na DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9f17a73d2d6349d4fc35668d7251877034e5e29f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="comparing-datarows-linq-to-dataset"></a><span data-ttu-id="07888-102">Porovnání DataRows (LINQ na DataSet)</span><span class="sxs-lookup"><span data-stu-id="07888-102">Comparing DataRows (LINQ to DataSet)</span></span>
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]<span data-ttu-id="07888-103">definuje různé operátory set k porovnání zdrojové elementy, které chcete zobrazit, pokud jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="07888-103"> defines various set operators to compare source elements to see if they are equal.</span></span> [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]<span data-ttu-id="07888-104">poskytuje následující sadu operátory:</span><span class="sxs-lookup"><span data-stu-id="07888-104"> provides the following set operators:</span></span>  
  
-   <xref:System.Linq.Enumerable.Distinct%2A>  
  
-   <xref:System.Linq.Enumerable.Union%2A>  
  
-   <xref:System.Linq.Enumerable.Intersect%2A>  
  
-   <xref:System.Linq.Enumerable.Except%2A>  
  
 <span data-ttu-id="07888-105">Tyto operátory porovnání zdrojové elementy voláním <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> a <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> metody pro každou kolekci elementů.</span><span class="sxs-lookup"><span data-stu-id="07888-105">These operators compare source elements by calling the <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> and <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> methods on each collection of elements.</span></span> <span data-ttu-id="07888-106">U <xref:System.Data.DataRow>, proveďte tyto operátory porovnání odkaz, který není obecně ideální chování množinové operace přes tabulková data.</span><span class="sxs-lookup"><span data-stu-id="07888-106">In the case of a <xref:System.Data.DataRow>, these operators perform a reference comparison, which is generally not the ideal behavior for set operations over tabular data.</span></span> <span data-ttu-id="07888-107">Pro sadu operací obvykle chcete určit, jestli jsou stejné hodnoty elementu a není odkazuje element.</span><span class="sxs-lookup"><span data-stu-id="07888-107">For set operations, you usually want to determine whether the element values are equal and not the element references.</span></span> <span data-ttu-id="07888-108">Proto <xref:System.Data.DataRowComparer> třída byla přidána do [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="07888-108">Therefore, the <xref:System.Data.DataRowComparer> class has been added to [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="07888-109">Tato třída slouží k porovnání hodnot řádků.</span><span class="sxs-lookup"><span data-stu-id="07888-109">This class can be used to compare row values.</span></span>  
  
 <span data-ttu-id="07888-110"><xref:System.Data.DataRowComparer> Třída obsahuje implementace porovnání hodnota <xref:System.Data.DataRow>, takže tato třída slouží pro sadu operací, jako <xref:System.Linq.Enumerable.Distinct%2A>.</span><span class="sxs-lookup"><span data-stu-id="07888-110">The <xref:System.Data.DataRowComparer> class contains a value comparison implementation for <xref:System.Data.DataRow>, so this class can be used for set operations such as <xref:System.Linq.Enumerable.Distinct%2A>.</span></span> <span data-ttu-id="07888-111">Tato třída nemůže být přímo vytvořeny instance; Místo toho <xref:System.Data.DataRowComparer.Default%2A> vlastnost je nutné použít vrátit instanci <xref:System.Data.DataRowComparer%601>.</span><span class="sxs-lookup"><span data-stu-id="07888-111">This class cannot be directly instantiated; instead, the <xref:System.Data.DataRowComparer.Default%2A> property must be used to return an instance of the <xref:System.Data.DataRowComparer%601>.</span></span> <span data-ttu-id="07888-112"><xref:System.Data.DataRowComparer%601.Equals%2A> Metoda je volána poté a dvě <xref:System.Data.DataRow> předávání objektů, který se má porovnat v jako vstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="07888-112">The <xref:System.Data.DataRowComparer%601.Equals%2A> method is then called and the two <xref:System.Data.DataRow> objects to be compared are passed in as input parameters.</span></span> <span data-ttu-id="07888-113"><xref:System.Data.DataRowComparer%601.Equals%2A> Metoda vrátí `true` Pokud sadu seřazený sloupec hodnoty v obou <xref:System.Data.DataRow> objekty jsou stejné, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="07888-113">The <xref:System.Data.DataRowComparer%601.Equals%2A> method returns `true` if the ordered set of column values in both <xref:System.Data.DataRow> objects are equal; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07888-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="07888-114">Example</span></span>  
 <span data-ttu-id="07888-115">Tento příklad používá `Intersect` vrátit kontakty, které se zobrazují v obou tabulkách.</span><span class="sxs-lookup"><span data-stu-id="07888-115">This example uses `Intersect` to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
### <a name="example"></a><span data-ttu-id="07888-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="07888-116">Example</span></span>  
 <span data-ttu-id="07888-117">Následující příklad porovná dva řádky a získá jejich hash.</span><span class="sxs-lookup"><span data-stu-id="07888-117">The following example compares two rows and gets their hash codes.</span></span>  
  
 [!code-vb[DP LINQ to DataSet Examples#CompareDifferentRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#comparedifferentrows)]  
  
## <a name="see-also"></a><span data-ttu-id="07888-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="07888-118">See Also</span></span>  
 <xref:System.Data.DataRowComparer>  
 [<span data-ttu-id="07888-119">Načítání dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="07888-119">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="07888-120">LINQ na DataSet příklady</span><span class="sxs-lookup"><span data-stu-id="07888-120">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
