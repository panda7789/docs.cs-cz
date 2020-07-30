---
title: Indexery – Průvodce programováním v C#
description: Indexery v jazyce C# umožňují, aby instance třídy nebo struktury byly indexovány jako pole. Můžete nastavit nebo získat indexovanou hodnotu bez určení typu nebo členu instance.
ms.date: 03/10/2017
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
ms.openlocfilehash: 07e0ae4294373817e10bb79920c73ec1e275d169
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303111"
---
# <a name="indexers-c-programming-guide"></a><span data-ttu-id="dc723-104">Indexery (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="dc723-104">Indexers (C# Programming Guide)</span></span>

<span data-ttu-id="dc723-105">Indexery umožňují, aby byly instance třídy nebo struktury indexovány stejně jako pole.</span><span class="sxs-lookup"><span data-stu-id="dc723-105">Indexers allow instances of a class or struct to be indexed just like arrays.</span></span> <span data-ttu-id="dc723-106">Indexovaná hodnota může být nastavena nebo načtena bez explicitního určení typu nebo členu instance.</span><span class="sxs-lookup"><span data-stu-id="dc723-106">The indexed value can be set or retrieved without explicitly specifying a type or instance member.</span></span> <span data-ttu-id="dc723-107">Indexery připomínají [vlastnosti](../classes-and-structs/properties.md) s tím rozdílem, že jejich přístupové objekty přijímají parametry.</span><span class="sxs-lookup"><span data-stu-id="dc723-107">Indexers resemble [properties](../classes-and-structs/properties.md) except that their accessors take parameters.</span></span>  

 <span data-ttu-id="dc723-108">Následující příklad definuje obecnou třídu pomocí jednoduchých přístupových metod [Get](../../language-reference/keywords/get.md) a [set](../../language-reference/keywords/set.md) pro přiřazení a načtení hodnot.</span><span class="sxs-lookup"><span data-stu-id="dc723-108">The following example defines a generic class with simple [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) accessor methods to assign and retrieve values.</span></span> <span data-ttu-id="dc723-109">`Program`Třída vytvoří instanci této třídy pro ukládání řetězců.</span><span class="sxs-lookup"><span data-stu-id="dc723-109">The `Program` class creates an instance of this class for storing strings.</span></span>  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
> <span data-ttu-id="dc723-110">Další příklady najdete v části [související oddíly](./index.md#BKMK_RelatedSections).</span><span class="sxs-lookup"><span data-stu-id="dc723-110">For more examples, see [Related Sections](./index.md#BKMK_RelatedSections).</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="dc723-111">Definice textu výrazu</span><span class="sxs-lookup"><span data-stu-id="dc723-111">Expression Body Definitions</span></span>  

<span data-ttu-id="dc723-112">Je běžné, že přistupující objekt get nebo set indexeru se skládá z jednoho příkazu, který vrátí nebo nastaví hodnotu.</span><span class="sxs-lookup"><span data-stu-id="dc723-112">It is common for an indexer's get or set accessor to consist of a single statement that either returns or sets a value.</span></span> <span data-ttu-id="dc723-113">Členové Expression-těle poskytují zjednodušenou syntaxi pro podporu tohoto scénáře.</span><span class="sxs-lookup"><span data-stu-id="dc723-113">Expression-bodied members provide a simplified syntax to support this scenario.</span></span> <span data-ttu-id="dc723-114">Počínaje jazykem C# 6 může být indexer jen pro čtení implementován jako člen výrazu těle, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="dc723-114">Starting with C# 6, a read-only indexer can be implemented as an expression-bodied member, as the following example shows.</span></span>

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

<span data-ttu-id="dc723-115">Všimněte si, že `=>` zavádí tělo výrazu a že `get` klíčové slovo se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="dc723-115">Note that `=>` introduces the expression body, and that the `get` keyword is not used.</span></span>

<span data-ttu-id="dc723-116">Počínaje jazykem C# 7,0, přístupový objekt get a set může být implementován jako členové Expression-těle.</span><span class="sxs-lookup"><span data-stu-id="dc723-116">Starting with C# 7.0, both the get and set accessor can be an implemented as expression-bodied members.</span></span> <span data-ttu-id="dc723-117">V takovém případě `get` `set` je nutné použít jak klíčová slova, tak i klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="dc723-117">In this case, both `get` and `set` keywords must be used.</span></span> <span data-ttu-id="dc723-118">Příklad:</span><span class="sxs-lookup"><span data-stu-id="dc723-118">For example:</span></span>

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a><span data-ttu-id="dc723-119">Přehled indexerů</span><span class="sxs-lookup"><span data-stu-id="dc723-119">Indexers Overview</span></span>  
  
- <span data-ttu-id="dc723-120">Indexery povolují, aby objekty byly indexovány podobným způsobem jako pole.</span><span class="sxs-lookup"><span data-stu-id="dc723-120">Indexers enable objects to be indexed in a similar manner to arrays.</span></span>  
  
- <span data-ttu-id="dc723-121">`get`Přistupující objekt vrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="dc723-121">A `get` accessor returns a value.</span></span> <span data-ttu-id="dc723-122">`set`Přístupový objekt přiřadí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="dc723-122">A `set` accessor assigns a value.</span></span>  
  
- <span data-ttu-id="dc723-123">Klíčové slovo [This](../../language-reference/keywords/this.md) slouží k definování indexeru.</span><span class="sxs-lookup"><span data-stu-id="dc723-123">The [this](../../language-reference/keywords/this.md) keyword is used to define the indexer.</span></span>  
  
- <span data-ttu-id="dc723-124">Klíčové slovo [Value](../../language-reference/keywords/value.md) slouží k definování hodnoty, kterou přiřazuje `set` indexer.</span><span class="sxs-lookup"><span data-stu-id="dc723-124">The [value](../../language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` indexer.</span></span>  
  
- <span data-ttu-id="dc723-125">Indexery nemusí být indexovány pomocí celočíselné hodnoty; je zde postup, jak definovat konkrétní vyhledávací mechanismus.</span><span class="sxs-lookup"><span data-stu-id="dc723-125">Indexers do not have to be indexed by an integer value; it is up to you how to define the specific look-up mechanism.</span></span>  
  
- <span data-ttu-id="dc723-126">Indexery mohou být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="dc723-126">Indexers can be overloaded.</span></span>  
  
- <span data-ttu-id="dc723-127">Indexery mohou mít více než jeden formální parametr, například při přístupu k dvojrozměrnému poli.</span><span class="sxs-lookup"><span data-stu-id="dc723-127">Indexers can have more than one formal parameter, for example, when accessing a two-dimensional array.</span></span>  
  
## <a name="related-sections"></a><a name="BKMK_RelatedSections"></a><span data-ttu-id="dc723-128">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="dc723-128">Related Sections</span></span>  
  
- [<span data-ttu-id="dc723-129">Použití indexerů</span><span class="sxs-lookup"><span data-stu-id="dc723-129">Using Indexers</span></span>](./using-indexers.md)  
  
- [<span data-ttu-id="dc723-130">Indexery v rozhraních</span><span class="sxs-lookup"><span data-stu-id="dc723-130">Indexers in Interfaces</span></span>](./indexers-in-interfaces.md)  
  
- [<span data-ttu-id="dc723-131">Porovnání mezi vlastnostmi a indexery</span><span class="sxs-lookup"><span data-stu-id="dc723-131">Comparison Between Properties and Indexers</span></span>](./comparison-between-properties-and-indexers.md)  
  
- [<span data-ttu-id="dc723-132">Omezení přístupnosti přístupového objektu</span><span class="sxs-lookup"><span data-stu-id="dc723-132">Restricting Accessor Accessibility</span></span>](../classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="dc723-133">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="dc723-133">C# Language Specification</span></span>  

<span data-ttu-id="dc723-134">Další informace najdete v tématu [indexery](~/_csharplang/spec/classes.md#indexers) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="dc723-134">For more information, see [Indexers](~/_csharplang/spec/classes.md#indexers) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="dc723-135">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="dc723-135">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="dc723-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dc723-136">See also</span></span>

- [<span data-ttu-id="dc723-137">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="dc723-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="dc723-138">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="dc723-138">Properties</span></span>](../classes-and-structs/properties.md)
