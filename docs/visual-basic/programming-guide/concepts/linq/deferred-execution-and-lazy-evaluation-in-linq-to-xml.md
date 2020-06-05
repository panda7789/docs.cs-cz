---
title: Odložené provedení a opožděné vyhodnocení v LINQ to XML
ms.date: 07/20/2015
ms.assetid: 31998eed-b95e-47fb-a865-9de1f337d1fb
ms.openlocfilehash: 98a5010de6ea7ef46d845c6a921c54d4e7692370
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410809"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-visual-basic"></a><span data-ttu-id="7dcaf-102">Odložené provádění a opožděné vyhodnocení v LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7dcaf-102">Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)</span></span>
<span data-ttu-id="7dcaf-103">Operace dotazů a OS se často implementují pro použití odloženého provedení.</span><span class="sxs-lookup"><span data-stu-id="7dcaf-103">Query and axis operations are often implemented to use deferred execution.</span></span> <span data-ttu-id="7dcaf-104">V tomto tématu najdete vysvětlení požadavků a výhod odloženého provedení a některých důležitých implementací.</span><span class="sxs-lookup"><span data-stu-id="7dcaf-104">This topic explains the requirements and advantages of deferred execution, and some implementation considerations.</span></span>  
  
## <a name="deferred-execution"></a><span data-ttu-id="7dcaf-105">Odložené provedení</span><span class="sxs-lookup"><span data-stu-id="7dcaf-105">Deferred Execution</span></span>  
 <span data-ttu-id="7dcaf-106">Odložené spuštění znamená, že vyhodnocení výrazu je zpožděno, dokud není skutečně vyžadováno jeho *realizovaná* hodnota.</span><span class="sxs-lookup"><span data-stu-id="7dcaf-106">Deferred execution means that the evaluation of an expression is delayed until its *realized* value is actually required.</span></span> <span data-ttu-id="7dcaf-107">Odložené provádění může významně zlepšit výkon, pokud je třeba manipulovat s velkými datovými kolekcemi, zejména v programech, které obsahují sérii zřetězených dotazů nebo manipulace.</span><span class="sxs-lookup"><span data-stu-id="7dcaf-107">Deferred execution can greatly improve performance when you have to manipulate large data collections, especially in programs that contain a series of chained queries or manipulations.</span></span> <span data-ttu-id="7dcaf-108">V nejlepším případě se odložené spouštění povoluje pouze jedna iterace prostřednictvím zdrojové kolekce.</span><span class="sxs-lookup"><span data-stu-id="7dcaf-108">In the best case, deferred execution enables only a single iteration through the source collection.</span></span>  
  
 <span data-ttu-id="7dcaf-109">Technologie LINQ využívají odložené spouštění jak v rámci členů základních <xref:System.Linq?displayProperty=nameWithType> tříd, tak v metodách rozšíření v různých oborech názvů LINQ, jako je například <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7dcaf-109">The LINQ technologies make extensive use of deferred execution in both the members of core <xref:System.Linq?displayProperty=nameWithType> classes and in the extension methods in the various LINQ namespaces, such as <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="eager-vs-lazy-evaluation"></a><span data-ttu-id="7dcaf-110">Eager vs. opožděné hodnocení</span><span class="sxs-lookup"><span data-stu-id="7dcaf-110">Eager vs. Lazy Evaluation</span></span>  
 <span data-ttu-id="7dcaf-111">Když napíšete metodu, která implementuje odložené vykonání, je také nutné rozhodnout, zda implementovat metodu pomocí opožděného vyhodnocení nebo vyhodnocení Eager.</span><span class="sxs-lookup"><span data-stu-id="7dcaf-111">When you write a method that implements deferred execution, you also have to decide whether to implement the method using lazy evaluation or eager evaluation.</span></span>  
  
- <span data-ttu-id="7dcaf-112">V *opožděném vyhodnocení*je během každého volání iterátoru zpracován jediný element zdrojové kolekce.</span><span class="sxs-lookup"><span data-stu-id="7dcaf-112">In *lazy evaluation*, a single element of the source collection is processed during each call to the iterator.</span></span> <span data-ttu-id="7dcaf-113">Toto je typický způsob, jakým jsou implementovány iterátory.</span><span class="sxs-lookup"><span data-stu-id="7dcaf-113">This is the typical way in which iterators are implemented.</span></span>  
  
- <span data-ttu-id="7dcaf-114">Při *vyhodnocování Eager*bude první volání iterátoru mít za následek zpracování celé kolekce.</span><span class="sxs-lookup"><span data-stu-id="7dcaf-114">In *eager evaluation*, the first call to the iterator will result in the entire collection being processed.</span></span> <span data-ttu-id="7dcaf-115">Může být také nutné zadat dočasnou kopii zdrojové kolekce.</span><span class="sxs-lookup"><span data-stu-id="7dcaf-115">A temporary copy of the source collection might also be required.</span></span> <span data-ttu-id="7dcaf-116">Například <xref:System.Linq.Enumerable.OrderBy%2A> Metoda musí seřadit celou kolekci před tím, než vrátí první prvek.</span><span class="sxs-lookup"><span data-stu-id="7dcaf-116">For example, the <xref:System.Linq.Enumerable.OrderBy%2A> method has to sort the entire collection before it returns the first element.</span></span>  
  
 <span data-ttu-id="7dcaf-117">Opožděné hodnocení obvykle poskytuje lepší výkon, protože distribuuje režijní náklady rovnoměrně během hodnocení kolekce a minimalizuje používání dočasných dat.</span><span class="sxs-lookup"><span data-stu-id="7dcaf-117">Lazy evaluation usually yields better performance because it distributes overhead processing evenly throughout the evaluation of the collection and minimizes the use of temporary data.</span></span> <span data-ttu-id="7dcaf-118">Samozřejmě není pro některé operace žádná jiná možnost než vyhodnotit mezilehlé výsledky.</span><span class="sxs-lookup"><span data-stu-id="7dcaf-118">Of course, for some operations, there is no other option than to materialize intermediate results.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7dcaf-119">Další kroky</span><span class="sxs-lookup"><span data-stu-id="7dcaf-119">Next Steps</span></span>  
 <span data-ttu-id="7dcaf-120">Další téma v tomto kurzu znázorňuje odložené provádění:</span><span class="sxs-lookup"><span data-stu-id="7dcaf-120">The next topic in this tutorial illustrates deferred execution:</span></span>  
  
- [<span data-ttu-id="7dcaf-121">Příklad odloženého provedení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7dcaf-121">Deferred Execution Example (Visual Basic)</span></span>](deferred-execution-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="7dcaf-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="7dcaf-122">See also</span></span>

- [<span data-ttu-id="7dcaf-123">Kurz: odložené provádění (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7dcaf-123">Tutorial: Deferred Execution (Visual Basic)</span></span>](tutorial-deferred-execution.md)
- [<span data-ttu-id="7dcaf-124">Koncepty a terminologie (funkce Transformation) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7dcaf-124">Concepts and Terminology (Functional Transformation) (Visual Basic)</span></span>](concepts-and-terminology-functional-transformation.md)
- [<span data-ttu-id="7dcaf-125">Agregační operace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7dcaf-125">Aggregation Operations (Visual Basic)</span></span>](aggregation-operations.md)
