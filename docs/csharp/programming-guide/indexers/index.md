---
title: "Indexery (Průvodce programováním v C#)"
ms.date: 03/10/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
caps.latest.revision: "29"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: db49a602b83940cab3f87dea17accb92a2be825d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="indexers-c-programming-guide"></a><span data-ttu-id="e8e6b-102">Indexery (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="e8e6b-102">Indexers (C# Programming Guide)</span></span>

<span data-ttu-id="e8e6b-103">Indexery povolit instancí třídě nebo struktuře indexovaných stejně jako pole.</span><span class="sxs-lookup"><span data-stu-id="e8e6b-103">Indexers allow instances of a class or struct to be indexed just like arrays.</span></span> <span data-ttu-id="e8e6b-104">Indexované hodnotu můžete nastavit nebo načíst bez zadání explicitně členem typ, nebo instance.</span><span class="sxs-lookup"><span data-stu-id="e8e6b-104">The indexed value can be set or retrieved without explicitly specifying a type or instance member.</span></span> <span data-ttu-id="e8e6b-105">Indexery vypadat [vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md) s tím rozdílem, že jejich přístupových objektů trvat parametry.</span><span class="sxs-lookup"><span data-stu-id="e8e6b-105">Indexers resemble [properties](../../../csharp/programming-guide/classes-and-structs/properties.md) except that their accessors take parameters.</span></span>  
 
 <span data-ttu-id="e8e6b-106">Následující příklad definuje třídu obecné s jednoduchou [získat](../../../csharp/language-reference/keywords/get.md) a [nastavit](../../../csharp/language-reference/keywords/set.md) přístupových metod a přiřadit k získávání hodnot.</span><span class="sxs-lookup"><span data-stu-id="e8e6b-106">The following example defines a generic class with simple [get](../../../csharp/language-reference/keywords/get.md) and [set](../../../csharp/language-reference/keywords/set.md) accessor methods to assign and retrieve values.</span></span> <span data-ttu-id="e8e6b-107">`Program` Třída vytvoří instance této třídy pro ukládání řetězců.</span><span class="sxs-lookup"><span data-stu-id="e8e6b-107">The `Program` class creates an instance of this class for storing strings.</span></span>  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
>  <span data-ttu-id="e8e6b-108">Další příklady najdete v tématu [související oddíly](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections).</span><span class="sxs-lookup"><span data-stu-id="e8e6b-108">For more examples, see [Related Sections](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections).</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="e8e6b-109">Výraz definice textu</span><span class="sxs-lookup"><span data-stu-id="e8e6b-109">Expression Body Definitions</span></span>  
 
<span data-ttu-id="e8e6b-110">Je běžné pro get indexer nebo přistupující objekt set sestává z jedné příkaz, který vrátí nebo nastaví hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e8e6b-110">It is common for an indexer's get or set accessor to consist of a single statement that either returns or sets a value.</span></span> <span data-ttu-id="e8e6b-111">Výraz vozidlo členy poskytují zjednodušenou syntaxi pro podporu tohoto scénáře.</span><span class="sxs-lookup"><span data-stu-id="e8e6b-111">Expression-bodied members provide a simplified syntax to support this scenario.</span></span> <span data-ttu-id="e8e6b-112">Od verze jazyka C# 6, indexer jen pro čtení se dá implementovat jako výraz vozidlo člena, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="e8e6b-112">Starting with C# 6, a read-only indexer can be implemented as an expression-bodied member, as the following example shows.</span></span>

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

<span data-ttu-id="e8e6b-113">Všimněte si, že `=>` představuje výraz text a který `get` – klíčové slovo nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="e8e6b-113">Note that `=>` introduces the expression body, and that the `get` keyword is not used.</span></span> 

<span data-ttu-id="e8e6b-114">Od verze jazyka C# 7, i get a přistupující objekt set může být implementovaná jako výraz vozidlo členy.</span><span class="sxs-lookup"><span data-stu-id="e8e6b-114">Starting with C# 7, both the get and set accessor can be an implemented as expression-bodied members.</span></span> <span data-ttu-id="e8e6b-115">V takovém případě obě `get` a `set` klíčová slova se musí použít.</span><span class="sxs-lookup"><span data-stu-id="e8e6b-115">In this case, both `get` and `set` keywords must be used.</span></span> <span data-ttu-id="e8e6b-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e8e6b-116">For example:</span></span>

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a><span data-ttu-id="e8e6b-117">Přehled indexerů</span><span class="sxs-lookup"><span data-stu-id="e8e6b-117">Indexers Overview</span></span>  
  
-   <span data-ttu-id="e8e6b-118">Indexery povolit objekty indexovaných podobným způsobem jako na pole.</span><span class="sxs-lookup"><span data-stu-id="e8e6b-118">Indexers enable objects to be indexed in a similar manner to arrays.</span></span>  
  
-   <span data-ttu-id="e8e6b-119">A `get` přistupujícího objektu vrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e8e6b-119">A `get` accessor returns a value.</span></span> <span data-ttu-id="e8e6b-120">A `set` přistupujícího objektu přiřazuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e8e6b-120">A `set` accessor assigns a value.</span></span>  
  
-   <span data-ttu-id="e8e6b-121">[To](../../../csharp/language-reference/keywords/this.md) – klíčové slovo se používá k definování indexeru.</span><span class="sxs-lookup"><span data-stu-id="e8e6b-121">The [this](../../../csharp/language-reference/keywords/this.md) keyword is used to define the indexer.</span></span>  
  
-   <span data-ttu-id="e8e6b-122">[Hodnotu](../../../csharp/language-reference/keywords/value.md) – klíčové slovo se používá k definování přiřazené podle `set` indexer.</span><span class="sxs-lookup"><span data-stu-id="e8e6b-122">The [value](../../../csharp/language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` indexer.</span></span>  
  
-   <span data-ttu-id="e8e6b-123">Indexery nemusíte indexovat pomocí celočíselnou hodnotu; Můžete se rozhodnout, jak definovat mechanismus konkrétní hledání.</span><span class="sxs-lookup"><span data-stu-id="e8e6b-123">Indexers do not have to be indexed by an integer value; it is up to you how to define the specific look-up mechanism.</span></span>  
  
-   <span data-ttu-id="e8e6b-124">Indexery může být přetížený.</span><span class="sxs-lookup"><span data-stu-id="e8e6b-124">Indexers can be overloaded.</span></span>  
  
-   <span data-ttu-id="e8e6b-125">Indexery může mít více než jeden formální parametr, například při přístupu k dvourozměrná pole.</span><span class="sxs-lookup"><span data-stu-id="e8e6b-125">Indexers can have more than one formal parameter, for example, when accessing a two-dimensional array.</span></span>  
  
##  <a name="BKMK_RelatedSections"></a><span data-ttu-id="e8e6b-126">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="e8e6b-126">Related Sections</span></span>  
  
-   [<span data-ttu-id="e8e6b-127">Použití indexerů</span><span class="sxs-lookup"><span data-stu-id="e8e6b-127">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [<span data-ttu-id="e8e6b-128">Indexery v rozhraní</span><span class="sxs-lookup"><span data-stu-id="e8e6b-128">Indexers in Interfaces</span></span>](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [<span data-ttu-id="e8e6b-129">Porovnání mezi vlastnostmi a indexery</span><span class="sxs-lookup"><span data-stu-id="e8e6b-129">Comparison Between Properties and Indexers</span></span>](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [<span data-ttu-id="e8e6b-130">Omezení přístupnosti přistupujícího objektu</span><span class="sxs-lookup"><span data-stu-id="e8e6b-130">Restricting Accessor Accessibility</span></span>](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="e8e6b-131">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e8e6b-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e8e6b-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8e6b-132">See Also</span></span>  
 [<span data-ttu-id="e8e6b-133">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="e8e6b-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e8e6b-134">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e8e6b-134">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
