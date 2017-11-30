---
title: "Odložené provedení a opožděné vyhodnocení v technologii LINQ to XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31998eed-b95e-47fb-a865-9de1f337d1fb
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3a465c4448157505a42db57202298cb18e44a562
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-visual-basic"></a><span data-ttu-id="95324-102">Odložené provedení a opožděné vyhodnocení v technologii LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95324-102">Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)</span></span>
<span data-ttu-id="95324-103">Operace dotazů a osu se často implementují používat odložené provedení.</span><span class="sxs-lookup"><span data-stu-id="95324-103">Query and axis operations are often implemented to use deferred execution.</span></span> <span data-ttu-id="95324-104">Toto téma vysvětluje požadavky a výhody odložené provedení a některé aspekty implementace.</span><span class="sxs-lookup"><span data-stu-id="95324-104">This topic explains the requirements and advantages of deferred execution, and some implementation considerations.</span></span>  
  
## <a name="deferred-execution"></a><span data-ttu-id="95324-105">Odložené provedení</span><span class="sxs-lookup"><span data-stu-id="95324-105">Deferred Execution</span></span>  
 <span data-ttu-id="95324-106">Odložené provedení znamená, že je zpožděna vyhodnocení výrazu, dokud jeho *uvědomili si* je ve skutečnosti požadována hodnota.</span><span class="sxs-lookup"><span data-stu-id="95324-106">Deferred execution means that the evaluation of an expression is delayed until its *realized* value is actually required.</span></span> <span data-ttu-id="95324-107">Odložené provedení může výrazně zlepšit výkon, když máte k manipulaci s kolekcí velkého množství dat, zejména v programech, které obsahují řadu zřetězené dotazy nebo manipulace.</span><span class="sxs-lookup"><span data-stu-id="95324-107">Deferred execution can greatly improve performance when you have to manipulate large data collections, especially in programs that contain a series of chained queries or manipulations.</span></span> <span data-ttu-id="95324-108">V případě nejlepší umožňuje odložené provedení jednoho iteraci prostřednictvím kolekce zdroje.</span><span class="sxs-lookup"><span data-stu-id="95324-108">In the best case, deferred execution enables only a single iteration through the source collection.</span></span>  
  
 <span data-ttu-id="95324-109">Technologie LINQ využívají rozsáhlé odložené provedení v obou členy základní <xref:System.Linq?displayProperty=nameWithType> třídy a metody rozšíření v různých oborech názvů LINQ, jako například <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="95324-109">The LINQ technologies make extensive use of deferred execution in both the members of core <xref:System.Linq?displayProperty=nameWithType> classes and in the extension methods in the various LINQ namespaces, such as <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="eager-vs-lazy-evaluation"></a><span data-ttu-id="95324-110">Přes vs. Opožděné vyhodnocení</span><span class="sxs-lookup"><span data-stu-id="95324-110">Eager vs. Lazy Evaluation</span></span>  
 <span data-ttu-id="95324-111">Pokud napíšete metodu, která implementuje odložené provedení, máte také rozhodnout, zda chcete implementovat metodu pomocí opožděné vyhodnocení nebo přes hodnocení.</span><span class="sxs-lookup"><span data-stu-id="95324-111">When you write a method that implements deferred execution, you also have to decide whether to implement the method using lazy evaluation or eager evaluation.</span></span>  
  
-   <span data-ttu-id="95324-112">V *opožděné vyhodnocení*, jeden prvek zdrojové kolekci je zpracovaných za každé volání iteraci.</span><span class="sxs-lookup"><span data-stu-id="95324-112">In *lazy evaluation*, a single element of the source collection is processed during each call to the iterator.</span></span> <span data-ttu-id="95324-113">To je typické způsob, ve kterém jsou implementované iterátory.</span><span class="sxs-lookup"><span data-stu-id="95324-113">This is the typical way in which iterators are implemented.</span></span>  
  
-   <span data-ttu-id="95324-114">V *přes vyhodnocení*, první volání iteraci způsobí celou kolekci zpracovává.</span><span class="sxs-lookup"><span data-stu-id="95324-114">In *eager evaluation*, the first call to the iterator will result in the entire collection being processed.</span></span> <span data-ttu-id="95324-115">Dočasnou kopii tohoto zdrojové kolekci může být taky potřeba.</span><span class="sxs-lookup"><span data-stu-id="95324-115">A temporary copy of the source collection might also be required.</span></span> <span data-ttu-id="95324-116">Například <xref:System.Linq.Enumerable.OrderBy%2A> metoda má seřadit celou kolekci před vrátí první prvek.</span><span class="sxs-lookup"><span data-stu-id="95324-116">For example, the <xref:System.Linq.Enumerable.OrderBy%2A> method has to sort the entire collection before it returns the first element.</span></span>  
  
 <span data-ttu-id="95324-117">Opožděné vyhodnocení obvykle poskytuje lepší výkon, protože distribuuje nároky na zpracování rovnoměrně v rámci vyhodnocení kolekce a minimalizuje použití dočasná data.</span><span class="sxs-lookup"><span data-stu-id="95324-117">Lazy evaluation usually yields better performance because it distributes overhead processing evenly throughout the evaluation of the collection and minimizes the use of temporary data.</span></span> <span data-ttu-id="95324-118">Samozřejmě pro některé operace, není žádná možnost než chcete vyhodnotit mezilehlých výsledků.</span><span class="sxs-lookup"><span data-stu-id="95324-118">Of course, for some operations, there is no other option than to materialize intermediate results.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="95324-119">Další kroky</span><span class="sxs-lookup"><span data-stu-id="95324-119">Next Steps</span></span>  
 <span data-ttu-id="95324-120">Další téma v tomto kurzu znázorňuje odložené provedení:</span><span class="sxs-lookup"><span data-stu-id="95324-120">The next topic in this tutorial illustrates deferred execution:</span></span>  
  
-   [<span data-ttu-id="95324-121">Odložené provedení příklad (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95324-121">Deferred Execution Example (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="95324-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="95324-122">See Also</span></span>  
 [<span data-ttu-id="95324-123">Kurz: Odložený provádění (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95324-123">Tutorial: Deferred Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)  
 [<span data-ttu-id="95324-124">Principy a terminologií (funkční transformaci) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95324-124">Concepts and Terminology (Functional Transformation) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)  
 [<span data-ttu-id="95324-125">Agregační operace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95324-125">Aggregation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)
