---
title: Porovnání datových řádků (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
ms.openlocfilehash: 2b45a4629474c394c8e49c41a7a98fc1181e124b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077170"
---
# <a name="comparing-datarows-linq-to-dataset"></a><span data-ttu-id="50dba-102">Porovnání datových řádků (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="50dba-102">Comparing DataRows (LINQ to DataSet)</span></span>
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] <span data-ttu-id="50dba-103">definuje různé sady operátory porovnání zdrojové elementy, pokud chcete zobrazit, pokud jsou shodné.</span><span class="sxs-lookup"><span data-stu-id="50dba-103">defines various set operators to compare source elements to see if they are equal.</span></span> [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] <span data-ttu-id="50dba-104">poskytuje následující sadu operátorů:</span><span class="sxs-lookup"><span data-stu-id="50dba-104">provides the following set operators:</span></span>  
  
-   <xref:System.Linq.Enumerable.Distinct%2A>  
  
-   <xref:System.Linq.Enumerable.Union%2A>  
  
-   <xref:System.Linq.Enumerable.Intersect%2A>  
  
-   <xref:System.Linq.Enumerable.Except%2A>  
  
 <span data-ttu-id="50dba-105">Tyto operátory porovnávají zdrojové prvky pomocí volání <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> a <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> v každé kolekci prvků metody.</span><span class="sxs-lookup"><span data-stu-id="50dba-105">These operators compare source elements by calling the <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> and <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> methods on each collection of elements.</span></span> <span data-ttu-id="50dba-106">V případě třídy <xref:System.Data.DataRow>, proveďte tyto operátory porovnání odkaz, který není obecně ideální chování množinové operace přes tabulková data.</span><span class="sxs-lookup"><span data-stu-id="50dba-106">In the case of a <xref:System.Data.DataRow>, these operators perform a reference comparison, which is generally not the ideal behavior for set operations over tabular data.</span></span> <span data-ttu-id="50dba-107">Pro sadu operací obvykle chcete určit, zda jsou stejné hodnoty prvků a není element odkazy.</span><span class="sxs-lookup"><span data-stu-id="50dba-107">For set operations, you usually want to determine whether the element values are equal and not the element references.</span></span> <span data-ttu-id="50dba-108">Proto <xref:System.Data.DataRowComparer> třídy je přidaný do [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="50dba-108">Therefore, the <xref:System.Data.DataRowComparer> class has been added to [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="50dba-109">Tato třída slouží k porovnání hodnoty řádků.</span><span class="sxs-lookup"><span data-stu-id="50dba-109">This class can be used to compare row values.</span></span>  
  
 <span data-ttu-id="50dba-110"><xref:System.Data.DataRowComparer> Třída obsahuje implementaci porovnání hodnoty <xref:System.Data.DataRow>, takže tuto třídu můžete použít sadu operací, jako <xref:System.Linq.Enumerable.Distinct%2A>.</span><span class="sxs-lookup"><span data-stu-id="50dba-110">The <xref:System.Data.DataRowComparer> class contains a value comparison implementation for <xref:System.Data.DataRow>, so this class can be used for set operations such as <xref:System.Linq.Enumerable.Distinct%2A>.</span></span> <span data-ttu-id="50dba-111">Tato třída nemůže být přímo vytvořeny instance; Místo toho <xref:System.Data.DataRowComparer.Default%2A> vlastnost je nutné použít k vrácení instance <xref:System.Data.DataRowComparer%601>.</span><span class="sxs-lookup"><span data-stu-id="50dba-111">This class cannot be directly instantiated; instead, the <xref:System.Data.DataRowComparer.Default%2A> property must be used to return an instance of the <xref:System.Data.DataRowComparer%601>.</span></span> <span data-ttu-id="50dba-112"><xref:System.Data.DataRowComparer%601.Equals%2A> Metoda je volána poté a dva <xref:System.Data.DataRow> jsou objekty, který se má porovnat předaný jako vstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="50dba-112">The <xref:System.Data.DataRowComparer%601.Equals%2A> method is then called and the two <xref:System.Data.DataRow> objects to be compared are passed in as input parameters.</span></span> <span data-ttu-id="50dba-113"><xref:System.Data.DataRowComparer%601.Equals%2A> Vrátí metoda `true` Pokud uspořádané sady sloupec hodnoty v obou <xref:System.Data.DataRow> jsou objekty stejné; jinak `false`.</span><span class="sxs-lookup"><span data-stu-id="50dba-113">The <xref:System.Data.DataRowComparer%601.Equals%2A> method returns `true` if the ordered set of column values in both <xref:System.Data.DataRow> objects are equal; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50dba-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="50dba-114">Example</span></span>  
 <span data-ttu-id="50dba-115">Tento příklad používá `Intersect` vrátit kontakty, které se zobrazují v obou tabulkách.</span><span class="sxs-lookup"><span data-stu-id="50dba-115">This example uses `Intersect` to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
### <a name="example"></a><span data-ttu-id="50dba-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="50dba-116">Example</span></span>  
 <span data-ttu-id="50dba-117">Následující příklad porovná dva řádky a získá jejich kódů hash.</span><span class="sxs-lookup"><span data-stu-id="50dba-117">The following example compares two rows and gets their hash codes.</span></span>  
  
 [!code-vb[DP LINQ to DataSet Examples#CompareDifferentRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#comparedifferentrows)]  
  
## <a name="see-also"></a><span data-ttu-id="50dba-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50dba-118">See also</span></span>

- <xref:System.Data.DataRowComparer>
- [<span data-ttu-id="50dba-119">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="50dba-119">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="50dba-120">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="50dba-120">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
