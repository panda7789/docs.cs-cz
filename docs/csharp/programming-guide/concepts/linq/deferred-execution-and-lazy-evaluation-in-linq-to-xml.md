---
title: "Odložené provedení a opožděné vyhodnocení v technologii LINQ to XML (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 8683d1b4-b7ec-407b-be12-906ebe958a09
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 847d8f830c26f54521664accc4bf569f822f255a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-c"></a><span data-ttu-id="4e42e-102">Odložené provedení a opožděné vyhodnocení v technologii LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4e42e-102">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>
<span data-ttu-id="4e42e-103">Operace dotazů a osu se často implementují používat odložené provedení.</span><span class="sxs-lookup"><span data-stu-id="4e42e-103">Query and axis operations are often implemented to use deferred execution.</span></span> <span data-ttu-id="4e42e-104">Toto téma vysvětluje požadavky a výhody odložené provedení a některé aspekty implementace.</span><span class="sxs-lookup"><span data-stu-id="4e42e-104">This topic explains the requirements and advantages of deferred execution, and some implementation considerations.</span></span>  
  
## <a name="deferred-execution"></a><span data-ttu-id="4e42e-105">Odložené provedení</span><span class="sxs-lookup"><span data-stu-id="4e42e-105">Deferred Execution</span></span>  
 <span data-ttu-id="4e42e-106">Odložené provedení znamená, že je zpožděna vyhodnocení výrazu, dokud jeho *uvědomili si* je ve skutečnosti požadována hodnota.</span><span class="sxs-lookup"><span data-stu-id="4e42e-106">Deferred execution means that the evaluation of an expression is delayed until its *realized* value is actually required.</span></span> <span data-ttu-id="4e42e-107">Odložené provedení může výrazně zlepšit výkon, když máte k manipulaci s kolekcí velkého množství dat, zejména v programech, které obsahují řadu zřetězené dotazy nebo manipulace.</span><span class="sxs-lookup"><span data-stu-id="4e42e-107">Deferred execution can greatly improve performance when you have to manipulate large data collections, especially in programs that contain a series of chained queries or manipulations.</span></span> <span data-ttu-id="4e42e-108">V případě nejlepší umožňuje odložené provedení jednoho iteraci prostřednictvím kolekce zdroje.</span><span class="sxs-lookup"><span data-stu-id="4e42e-108">In the best case, deferred execution enables only a single iteration through the source collection.</span></span>  
  
 <span data-ttu-id="4e42e-109">Technologie LINQ využívají rozsáhlé odložené provedení v obou členy základní <xref:System.Linq?displayProperty=nameWithType> třídy a metody rozšíření v různých oborech názvů LINQ, jako například <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4e42e-109">The LINQ technologies make extensive use of deferred execution in both the members of core <xref:System.Linq?displayProperty=nameWithType> classes and in the extension methods in the various LINQ namespaces, such as <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="4e42e-110">Odložené provedení je podporována přímo v jazyce C# pomocí [yield](../../../../csharp/language-reference/keywords/yield.md) – klíčové slovo (ve formě `yield-return` příkaz) při použití v rámci bloku iterator.</span><span class="sxs-lookup"><span data-stu-id="4e42e-110">Deferred execution is supported directly in the C# language by the [yield](../../../../csharp/language-reference/keywords/yield.md) keyword (in the form of the `yield-return` statement) when used within an iterator block.</span></span> <span data-ttu-id="4e42e-111">Takové iterovat musí vracet kolekci typu <xref:System.Collections.IEnumerator> nebo <xref:System.Collections.Generic.IEnumerator%601> (nebo odvozený typ).</span><span class="sxs-lookup"><span data-stu-id="4e42e-111">Such an iterator must return a collection of type <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> (or a derived type).</span></span>  
  
## <a name="eager-vs-lazy-evaluation"></a><span data-ttu-id="4e42e-112">Přes vs. Opožděné vyhodnocení</span><span class="sxs-lookup"><span data-stu-id="4e42e-112">Eager vs. Lazy Evaluation</span></span>  
 <span data-ttu-id="4e42e-113">Pokud napíšete metodu, která implementuje odložené provedení, máte také rozhodnout, zda chcete implementovat metodu pomocí opožděné vyhodnocení nebo přes hodnocení.</span><span class="sxs-lookup"><span data-stu-id="4e42e-113">When you write a method that implements deferred execution, you also have to decide whether to implement the method using lazy evaluation or eager evaluation.</span></span>  
  
-   <span data-ttu-id="4e42e-114">V *opožděné vyhodnocení*, jeden prvek zdrojové kolekci je zpracovaných za každé volání iteraci.</span><span class="sxs-lookup"><span data-stu-id="4e42e-114">In *lazy evaluation*, a single element of the source collection is processed during each call to the iterator.</span></span> <span data-ttu-id="4e42e-115">To je typické způsob, ve kterém jsou implementované iterátory.</span><span class="sxs-lookup"><span data-stu-id="4e42e-115">This is the typical way in which iterators are implemented.</span></span>  
  
-   <span data-ttu-id="4e42e-116">V *přes vyhodnocení*, první volání iteraci způsobí celou kolekci zpracovává.</span><span class="sxs-lookup"><span data-stu-id="4e42e-116">In *eager evaluation*, the first call to the iterator will result in the entire collection being processed.</span></span> <span data-ttu-id="4e42e-117">Dočasnou kopii tohoto zdrojové kolekci může být taky potřeba.</span><span class="sxs-lookup"><span data-stu-id="4e42e-117">A temporary copy of the source collection might also be required.</span></span> <span data-ttu-id="4e42e-118">Například <xref:System.Linq.Enumerable.OrderBy%2A> metoda má seřadit celou kolekci před vrátí první prvek.</span><span class="sxs-lookup"><span data-stu-id="4e42e-118">For example, the <xref:System.Linq.Enumerable.OrderBy%2A> method has to sort the entire collection before it returns the first element.</span></span>  
  
 <span data-ttu-id="4e42e-119">Opožděné vyhodnocení obvykle poskytuje lepší výkon, protože distribuuje nároky na zpracování rovnoměrně v rámci vyhodnocení kolekce a minimalizuje použití dočasná data.</span><span class="sxs-lookup"><span data-stu-id="4e42e-119">Lazy evaluation usually yields better performance because it distributes overhead processing evenly throughout the evaluation of the collection and minimizes the use of temporary data.</span></span> <span data-ttu-id="4e42e-120">Samozřejmě pro některé operace, není žádná možnost než chcete vyhodnotit mezilehlých výsledků.</span><span class="sxs-lookup"><span data-stu-id="4e42e-120">Of course, for some operations, there is no other option than to materialize intermediate results.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="4e42e-121">Další kroky</span><span class="sxs-lookup"><span data-stu-id="4e42e-121">Next Steps</span></span>  
 <span data-ttu-id="4e42e-122">Další téma v tomto kurzu znázorňuje odložené provedení:</span><span class="sxs-lookup"><span data-stu-id="4e42e-122">The next topic in this tutorial illustrates deferred execution:</span></span>  
  
-   [<span data-ttu-id="4e42e-123">Odložené provedení příklad (C#)</span><span class="sxs-lookup"><span data-stu-id="4e42e-123">Deferred Execution Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="4e42e-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e42e-124">See Also</span></span>  
 [<span data-ttu-id="4e42e-125">Kurz: Řetězení dotazy společně (C#)</span><span class="sxs-lookup"><span data-stu-id="4e42e-125">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)  
 [<span data-ttu-id="4e42e-126">Principy a terminologií (funkční transformaci) (C#)</span><span class="sxs-lookup"><span data-stu-id="4e42e-126">Concepts and Terminology (Functional Transformation) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)  
 [<span data-ttu-id="4e42e-127">Agregační operace (C#)</span><span class="sxs-lookup"><span data-stu-id="4e42e-127">Aggregation Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/aggregation-operations.md)  
 [<span data-ttu-id="4e42e-128">YIELD –</span><span class="sxs-lookup"><span data-stu-id="4e42e-128">yield</span></span>](../../../../csharp/language-reference/keywords/yield.md)
