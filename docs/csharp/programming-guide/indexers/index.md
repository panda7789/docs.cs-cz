---
title: Indexery – C# Průvodce programováním
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
ms.openlocfilehash: f0df3170289d780852ee14232e92c3b71412c548
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392376"
---
# <a name="indexers-c-programming-guide"></a><span data-ttu-id="86ced-102">Indexery (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="86ced-102">Indexers (C# Programming Guide)</span></span>

<span data-ttu-id="86ced-103">Indexery umožňují, aby byly instance třídy nebo struktury indexovány stejně jako pole.</span><span class="sxs-lookup"><span data-stu-id="86ced-103">Indexers allow instances of a class or struct to be indexed just like arrays.</span></span> <span data-ttu-id="86ced-104">Indexovaná hodnota může být nastavena nebo načtena bez explicitního určení typu nebo členu instance.</span><span class="sxs-lookup"><span data-stu-id="86ced-104">The indexed value can be set or retrieved without explicitly specifying a type or instance member.</span></span> <span data-ttu-id="86ced-105">Indexery připomínají [vlastnosti](../classes-and-structs/properties.md) s tím rozdílem, že jejich přístupové objekty přijímají parametry.</span><span class="sxs-lookup"><span data-stu-id="86ced-105">Indexers resemble [properties](../classes-and-structs/properties.md) except that their accessors take parameters.</span></span>  

 <span data-ttu-id="86ced-106">Následující příklad definuje obecnou třídu pomocí jednoduchých přístupových metod [Get](../../language-reference/keywords/get.md) a [set](../../language-reference/keywords/set.md) pro přiřazení a načtení hodnot.</span><span class="sxs-lookup"><span data-stu-id="86ced-106">The following example defines a generic class with simple [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) accessor methods to assign and retrieve values.</span></span> <span data-ttu-id="86ced-107">Třída `Program` vytvoří instanci této třídy pro ukládání řetězců.</span><span class="sxs-lookup"><span data-stu-id="86ced-107">The `Program` class creates an instance of this class for storing strings.</span></span>  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
> <span data-ttu-id="86ced-108">Další příklady najdete v části [související oddíly](./index.md#BKMK_RelatedSections).</span><span class="sxs-lookup"><span data-stu-id="86ced-108">For more examples, see [Related Sections](./index.md#BKMK_RelatedSections).</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="86ced-109">Definice textu výrazu</span><span class="sxs-lookup"><span data-stu-id="86ced-109">Expression Body Definitions</span></span>  
 
<span data-ttu-id="86ced-110">Je běžné, že přistupující objekt get nebo set indexeru se skládá z jednoho příkazu, který vrátí nebo nastaví hodnotu.</span><span class="sxs-lookup"><span data-stu-id="86ced-110">It is common for an indexer's get or set accessor to consist of a single statement that either returns or sets a value.</span></span> <span data-ttu-id="86ced-111">Členové Expression-těle poskytují zjednodušenou syntaxi pro podporu tohoto scénáře.</span><span class="sxs-lookup"><span data-stu-id="86ced-111">Expression-bodied members provide a simplified syntax to support this scenario.</span></span> <span data-ttu-id="86ced-112">Počínaje C# 6 se indexer jen pro čtení dá implementovat jako člen s výrazem těle, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="86ced-112">Starting with C# 6, a read-only indexer can be implemented as an expression-bodied member, as the following example shows.</span></span>

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

<span data-ttu-id="86ced-113">Všimněte si, že `=>` zavádí tělo výrazu a nepoužívá se klíčové slovo `get`.</span><span class="sxs-lookup"><span data-stu-id="86ced-113">Note that `=>` introduces the expression body, and that the `get` keyword is not used.</span></span> 

<span data-ttu-id="86ced-114">Počínaje C# 7,0 se přístupové objekty get a set můžou implementovat jako členy Expression-těle.</span><span class="sxs-lookup"><span data-stu-id="86ced-114">Starting with C# 7.0, both the get and set accessor can be an implemented as expression-bodied members.</span></span> <span data-ttu-id="86ced-115">V takovém případě musí být použita klíčová slova `get` a `set`.</span><span class="sxs-lookup"><span data-stu-id="86ced-115">In this case, both `get` and `set` keywords must be used.</span></span> <span data-ttu-id="86ced-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="86ced-116">For example:</span></span>

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a><span data-ttu-id="86ced-117">Přehled indexerů</span><span class="sxs-lookup"><span data-stu-id="86ced-117">Indexers Overview</span></span>  
  
- <span data-ttu-id="86ced-118">Indexery povolují, aby objekty byly indexovány podobným způsobem jako pole.</span><span class="sxs-lookup"><span data-stu-id="86ced-118">Indexers enable objects to be indexed in a similar manner to arrays.</span></span>  
  
- <span data-ttu-id="86ced-119">Přístupový objekt `get` vrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="86ced-119">A `get` accessor returns a value.</span></span> <span data-ttu-id="86ced-120">Přístupový objekt `set` přiřadí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="86ced-120">A `set` accessor assigns a value.</span></span>  
  
- <span data-ttu-id="86ced-121">Klíčové slovo [This](../../language-reference/keywords/this.md) slouží k definování indexeru.</span><span class="sxs-lookup"><span data-stu-id="86ced-121">The [this](../../language-reference/keywords/this.md) keyword is used to define the indexer.</span></span>  
  
- <span data-ttu-id="86ced-122">Klíčové slovo [Value](../../language-reference/keywords/value.md) slouží k definování hodnoty, kterou přiřazuje indexer `set`.</span><span class="sxs-lookup"><span data-stu-id="86ced-122">The [value](../../language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` indexer.</span></span>  
  
- <span data-ttu-id="86ced-123">Indexery nemusí být indexovány pomocí celočíselné hodnoty; je zde postup, jak definovat konkrétní vyhledávací mechanismus.</span><span class="sxs-lookup"><span data-stu-id="86ced-123">Indexers do not have to be indexed by an integer value; it is up to you how to define the specific look-up mechanism.</span></span>  
  
- <span data-ttu-id="86ced-124">Indexery mohou být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="86ced-124">Indexers can be overloaded.</span></span>  
  
- <span data-ttu-id="86ced-125">Indexery mohou mít více než jeden formální parametr, například při přístupu k dvojrozměrnému poli.</span><span class="sxs-lookup"><span data-stu-id="86ced-125">Indexers can have more than one formal parameter, for example, when accessing a two-dimensional array.</span></span>  
  
## <a name="BKMK_RelatedSections"></a><span data-ttu-id="86ced-126">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="86ced-126">Related Sections</span></span>  
  
- [<span data-ttu-id="86ced-127">Použití indexerů</span><span class="sxs-lookup"><span data-stu-id="86ced-127">Using Indexers</span></span>](./using-indexers.md)  
  
- [<span data-ttu-id="86ced-128">Indexery v rozhraní</span><span class="sxs-lookup"><span data-stu-id="86ced-128">Indexers in Interfaces</span></span>](./indexers-in-interfaces.md)  
  
- [<span data-ttu-id="86ced-129">Porovnání mezi vlastnostmi a indexery</span><span class="sxs-lookup"><span data-stu-id="86ced-129">Comparison Between Properties and Indexers</span></span>](./comparison-between-properties-and-indexers.md)  
  
- [<span data-ttu-id="86ced-130">Omezení přístupnosti přístupového objektu</span><span class="sxs-lookup"><span data-stu-id="86ced-130">Restricting Accessor Accessibility</span></span>](../classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="86ced-131">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="86ced-131">C# Language Specification</span></span>  

<span data-ttu-id="86ced-132">Další informace najdete v tématu [indexery](~/_csharplang/spec/classes.md#indexers) ve [ C# specifikaci jazyka](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="86ced-132">For more information, see [Indexers](~/_csharplang/spec/classes.md#indexers) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="86ced-133">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="86ced-133">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="86ced-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86ced-134">See also</span></span>

- [<span data-ttu-id="86ced-135">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="86ced-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="86ced-136">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="86ced-136">Properties</span></span>](../classes-and-structs/properties.md)
