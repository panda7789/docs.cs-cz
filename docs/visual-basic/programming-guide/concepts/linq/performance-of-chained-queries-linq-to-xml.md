---
title: Výkon zřetězené dotazů (technologie LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
ms.openlocfilehash: d390fc0e45967cd98697320eb6f61a51cb1c19da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645704"
---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a><span data-ttu-id="d742d-102">Výkon zřetězené dotazů (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d742d-102">Performance of Chained Queries (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="d742d-103">Jednou z nejdůležitějších výhod LINQ (a technologie LINQ to XML) je, že zřetězené dotazy můžete provést i jediný rozsáhlejších, složitějších dotaz.</span><span class="sxs-lookup"><span data-stu-id="d742d-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>  
  
 <span data-ttu-id="d742d-104">Zřetězené dotaz je dotaz, který používá jiný dotaz jako zdroj.</span><span class="sxs-lookup"><span data-stu-id="d742d-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="d742d-105">Například v následujícím kódu jednoduchý `query2` má `query1` jako svůj zdroj:</span><span class="sxs-lookup"><span data-stu-id="d742d-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>  
  
```vb  
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))  
  
Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x  
  
Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e  
  
For Each i As var In query2  
    Console.WriteLine("{0}", CInt(i))  
Next  
```  
  
 <span data-ttu-id="d742d-106">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d742d-106">This example produces the following output:</span></span>  
  
```  
4  
```  
  
 <span data-ttu-id="d742d-107">Tento dotaz zřetězené poskytuje stejný profil výkonu jako iterace v rámci odkazovaného seznamu.</span><span class="sxs-lookup"><span data-stu-id="d742d-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>  
  
-   <span data-ttu-id="d742d-108"><xref:System.Xml.Linq.XContainer.Elements%2A> Má osa v podstatě stejný výkon jako iterace v rámci odkazovaného seznamu.</span><span class="sxs-lookup"><span data-stu-id="d742d-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="d742d-109"><xref:System.Xml.Linq.XContainer.Elements%2A> je implementovaný jako iterace s odložené provedení.</span><span class="sxs-lookup"><span data-stu-id="d742d-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="d742d-110">To znamená, že některé činnosti provede kromě iterace v rámci odkazovaného seznamu, jako například přidělování objekt iterator a udržování přehledu o stavu spuštění.</span><span class="sxs-lookup"><span data-stu-id="d742d-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="d742d-111">Tato práce je možné rozdělit do dvou kategorií: práce, kterou je provést v době je nastavený iterator a práci, kterou se provádí při každé iteraci.</span><span class="sxs-lookup"><span data-stu-id="d742d-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="d742d-112">Instalační program práce malé, pevné množství práce, a práci při každé iteraci je úměrná počet položek ve zdrojové kolekci.</span><span class="sxs-lookup"><span data-stu-id="d742d-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>  
  
-   <span data-ttu-id="d742d-113">V `query1`, `Where` klauzule způsobí, že dotaz pro volání <xref:System.Linq.Enumerable.Where%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="d742d-113">In `query1`, the `Where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="d742d-114">Tato metoda je také implementovaný jako iterace.</span><span class="sxs-lookup"><span data-stu-id="d742d-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="d742d-115">Instalační program pracovní se skládá z vytvoření instance delegáta, který bude odkazovat výrazu lambda, plus normální instalace pro iterace.</span><span class="sxs-lookup"><span data-stu-id="d742d-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="d742d-116">Přičemž při každém opakování se nazývá delegát provést predikátu.</span><span class="sxs-lookup"><span data-stu-id="d742d-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="d742d-117">Instalační program práci a práci při každé iteraci je podobná objem práce při iterace v rámci ose.</span><span class="sxs-lookup"><span data-stu-id="d742d-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>  
  
-   <span data-ttu-id="d742d-118">V `query1`, klauzule select způsobí, že dotaz pro volání <xref:System.Linq.Enumerable.Select%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="d742d-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="d742d-119">Tato metoda má stejný profil výkonu jako <xref:System.Linq.Enumerable.Where%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="d742d-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>  
  
-   <span data-ttu-id="d742d-120">V `query2`, i `Where` klauzule a `Select` klauzule mají stejný profil výkonu jako v `query1`.</span><span class="sxs-lookup"><span data-stu-id="d742d-120">In `query2`, both the `Where` clause and the `Select` clause have the same performance profile as in `query1`.</span></span>  
  
 <span data-ttu-id="d742d-121">Iterace prostřednictvím `query2` je proto přímo úměrné k počet položek ve zdroji prvního, jinými slovy, lineární doba dotazu.</span><span class="sxs-lookup"><span data-stu-id="d742d-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d742d-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="d742d-122">See Also</span></span>  
 [<span data-ttu-id="d742d-123">Výkon (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d742d-123">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
