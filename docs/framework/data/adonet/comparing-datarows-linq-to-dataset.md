---
title: Porovnání hodnot DataRows (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
ms.openlocfilehash: fbd642fb3da6d664df9076b8d7576865d516727e
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634895"
---
# <a name="comparing-datarows-linq-to-dataset"></a><span data-ttu-id="4362b-102">Porovnání hodnot DataRows (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="4362b-102">Comparing DataRows (LINQ to DataSet)</span></span>
<span data-ttu-id="4362b-103">LINQ (Language-Integrated Query) definuje různé nastavené operátory pro porovnání zdrojových elementů, aby bylo vidět, zda jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="4362b-103">Language-Integrated Query (LINQ) defines various set operators to compare source elements to see if they are equal.</span></span> <span data-ttu-id="4362b-104">LINQ poskytuje následující operátory set:</span><span class="sxs-lookup"><span data-stu-id="4362b-104">LINQ provides the following set operators:</span></span>  
  
- <xref:System.Linq.Enumerable.Distinct%2A>  
  
- <xref:System.Linq.Enumerable.Union%2A>  
  
- <xref:System.Linq.Enumerable.Intersect%2A>  
  
- <xref:System.Linq.Enumerable.Except%2A>  
  
 <span data-ttu-id="4362b-105">Tyto operátory porovnávají zdrojové prvky voláním metody <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> a <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> v každé kolekci prvků.</span><span class="sxs-lookup"><span data-stu-id="4362b-105">These operators compare source elements by calling the <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> and <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> methods on each collection of elements.</span></span> <span data-ttu-id="4362b-106">V případě <xref:System.Data.DataRow>tyto operátory provádějí porovnání odkazů, což obecně není ideální chování pro operace set přes tabulková data.</span><span class="sxs-lookup"><span data-stu-id="4362b-106">In the case of a <xref:System.Data.DataRow>, these operators perform a reference comparison, which is generally not the ideal behavior for set operations over tabular data.</span></span> <span data-ttu-id="4362b-107">Pro operace set je obvykle vhodné určit, zda jsou hodnoty prvků stejné a nikoli odkazy na prvky.</span><span class="sxs-lookup"><span data-stu-id="4362b-107">For set operations, you usually want to determine whether the element values are equal and not the element references.</span></span> <span data-ttu-id="4362b-108">Proto byla třída <xref:System.Data.DataRowComparer> přidána do LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="4362b-108">Therefore, the <xref:System.Data.DataRowComparer> class has been added to LINQ to DataSet.</span></span> <span data-ttu-id="4362b-109">Tato třída se dá použít k porovnání hodnot řádků.</span><span class="sxs-lookup"><span data-stu-id="4362b-109">This class can be used to compare row values.</span></span>  
  
 <span data-ttu-id="4362b-110">Třída <xref:System.Data.DataRowComparer> obsahuje implementaci porovnání hodnot pro <xref:System.Data.DataRow>, takže tuto třídu lze použít pro operace set, jako je například <xref:System.Linq.Enumerable.Distinct%2A>.</span><span class="sxs-lookup"><span data-stu-id="4362b-110">The <xref:System.Data.DataRowComparer> class contains a value comparison implementation for <xref:System.Data.DataRow>, so this class can be used for set operations such as <xref:System.Linq.Enumerable.Distinct%2A>.</span></span> <span data-ttu-id="4362b-111">Tato třída nemůže být vytvořena přímo. místo toho je nutné použít vlastnost <xref:System.Data.DataRowComparer.Default%2A> k vrácení instance <xref:System.Data.DataRowComparer%601>.</span><span class="sxs-lookup"><span data-stu-id="4362b-111">This class cannot be directly instantiated; instead, the <xref:System.Data.DataRowComparer.Default%2A> property must be used to return an instance of the <xref:System.Data.DataRowComparer%601>.</span></span> <span data-ttu-id="4362b-112">Pak se zavolá metoda <xref:System.Data.DataRowComparer%601.Equals%2A> a dva objekty <xref:System.Data.DataRow>, které se mají porovnat, jsou předány jako vstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="4362b-112">The <xref:System.Data.DataRowComparer%601.Equals%2A> method is then called and the two <xref:System.Data.DataRow> objects to be compared are passed in as input parameters.</span></span> <span data-ttu-id="4362b-113">Metoda <xref:System.Data.DataRowComparer%601.Equals%2A> vrátí `true`, pokud je seřazená sada hodnot sloupců v obou <xref:System.Data.DataRow>ch objektech rovna hodnotě; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="4362b-113">The <xref:System.Data.DataRowComparer%601.Equals%2A> method returns `true` if the ordered set of column values in both <xref:System.Data.DataRow> objects are equal; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4362b-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="4362b-114">Example</span></span>  
 <span data-ttu-id="4362b-115">Tento příklad používá `Intersect` k vrácení kontaktů, které se zobrazí v obou tabulkách.</span><span class="sxs-lookup"><span data-stu-id="4362b-115">This example uses `Intersect` to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
### <a name="example"></a><span data-ttu-id="4362b-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="4362b-116">Example</span></span>  
 <span data-ttu-id="4362b-117">Následující příklad Porovná dva řádky a získá své kódy hash.</span><span class="sxs-lookup"><span data-stu-id="4362b-117">The following example compares two rows and gets their hash codes.</span></span>  
  
 [!code-vb[DP LINQ to DataSet Examples#CompareDifferentRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#comparedifferentrows)]  
  
## <a name="see-also"></a><span data-ttu-id="4362b-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4362b-118">See also</span></span>

- <xref:System.Data.DataRowComparer>
- [<span data-ttu-id="4362b-119">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="4362b-119">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="4362b-120">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="4362b-120">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
