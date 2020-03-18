---
title: Indexery – programovací příručka Jazyka C#
ms.date: 03/10/2017
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
ms.openlocfilehash: 539b2861e975c0c758c43c8a5d4cca86e3d2bb2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79167535"
---
# <a name="indexers-c-programming-guide"></a><span data-ttu-id="f2d07-102">Indexery (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="f2d07-102">Indexers (C# Programming Guide)</span></span>

<span data-ttu-id="f2d07-103">Indexery umožňují indexovat instance třídy nebo struktury stejně jako pole.</span><span class="sxs-lookup"><span data-stu-id="f2d07-103">Indexers allow instances of a class or struct to be indexed just like arrays.</span></span> <span data-ttu-id="f2d07-104">Indexovnou hodnotu lze nastavit nebo načíst bez explicitního zadání typu nebo člena instance.</span><span class="sxs-lookup"><span data-stu-id="f2d07-104">The indexed value can be set or retrieved without explicitly specifying a type or instance member.</span></span> <span data-ttu-id="f2d07-105">Indexery se podobají [vlastnostem](../classes-and-structs/properties.md) s tím rozdílem, že jejich přístupové objekty přebírají parametry.</span><span class="sxs-lookup"><span data-stu-id="f2d07-105">Indexers resemble [properties](../classes-and-structs/properties.md) except that their accessors take parameters.</span></span>  

 <span data-ttu-id="f2d07-106">Následující příklad definuje obecnou třídu s jednoduchými metodami přístupového přístupu [get](../../language-reference/keywords/get.md) a [set](../../language-reference/keywords/set.md) pro přiřazení a načtení hodnot.</span><span class="sxs-lookup"><span data-stu-id="f2d07-106">The following example defines a generic class with simple [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) accessor methods to assign and retrieve values.</span></span> <span data-ttu-id="f2d07-107">Třída `Program` vytvoří instanci této třídy pro ukládání řetězců.</span><span class="sxs-lookup"><span data-stu-id="f2d07-107">The `Program` class creates an instance of this class for storing strings.</span></span>  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
> <span data-ttu-id="f2d07-108">Další příklady naleznete [v tématu Související oddíly](./index.md#BKMK_RelatedSections).</span><span class="sxs-lookup"><span data-stu-id="f2d07-108">For more examples, see [Related Sections](./index.md#BKMK_RelatedSections).</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="f2d07-109">Definice textu výrazu</span><span class="sxs-lookup"><span data-stu-id="f2d07-109">Expression Body Definitions</span></span>  

<span data-ttu-id="f2d07-110">Je běžné pro indexeru získat nebo nastavit přistupující objekt se skládá z jednoho příkazu, který vrátí nebo nastaví hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f2d07-110">It is common for an indexer's get or set accessor to consist of a single statement that either returns or sets a value.</span></span> <span data-ttu-id="f2d07-111">Členové s výrazem poskytují zjednodušenou syntaxi pro podporu tohoto scénáře.</span><span class="sxs-lookup"><span data-stu-id="f2d07-111">Expression-bodied members provide a simplified syntax to support this scenario.</span></span> <span data-ttu-id="f2d07-112">Počínaje C# 6, indexer jen pro čtení lze implementovat jako člen s výrazem, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="f2d07-112">Starting with C# 6, a read-only indexer can be implemented as an expression-bodied member, as the following example shows.</span></span>

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

<span data-ttu-id="f2d07-113">Všimněte `=>` si, že zavádí tělo `get` výrazu a klíčové slovo se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="f2d07-113">Note that `=>` introduces the expression body, and that the `get` keyword is not used.</span></span>

<span data-ttu-id="f2d07-114">Počínaje C# 7.0, jak získat a nastavit přistupující objekt může být implementována jako členy s výrazem.</span><span class="sxs-lookup"><span data-stu-id="f2d07-114">Starting with C# 7.0, both the get and set accessor can be an implemented as expression-bodied members.</span></span> <span data-ttu-id="f2d07-115">V tomto případě `get` `set` musí být použita klíčová slova i klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="f2d07-115">In this case, both `get` and `set` keywords must be used.</span></span> <span data-ttu-id="f2d07-116">Například:</span><span class="sxs-lookup"><span data-stu-id="f2d07-116">For example:</span></span>

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a><span data-ttu-id="f2d07-117">Přehled indexerů</span><span class="sxs-lookup"><span data-stu-id="f2d07-117">Indexers Overview</span></span>  
  
- <span data-ttu-id="f2d07-118">Indexery umožňují objekty, které mají být indexovány podobným způsobem jako pole.</span><span class="sxs-lookup"><span data-stu-id="f2d07-118">Indexers enable objects to be indexed in a similar manner to arrays.</span></span>  
  
- <span data-ttu-id="f2d07-119">Přistupující `get` pole vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f2d07-119">A `get` accessor returns a value.</span></span> <span data-ttu-id="f2d07-120">Přistupující `set` pole přiřadí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f2d07-120">A `set` accessor assigns a value.</span></span>  
  
- <span data-ttu-id="f2d07-121">[Toto](../../language-reference/keywords/this.md) klíčové slovo se používá k definování indexeru.</span><span class="sxs-lookup"><span data-stu-id="f2d07-121">The [this](../../language-reference/keywords/this.md) keyword is used to define the indexer.</span></span>  
  
- <span data-ttu-id="f2d07-122">Klíčové slovo [value](../../language-reference/keywords/value.md) se používá k definování `set` hodnoty přiřazené indexerem.</span><span class="sxs-lookup"><span data-stu-id="f2d07-122">The [value](../../language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` indexer.</span></span>  
  
- <span data-ttu-id="f2d07-123">Indexery nemusí být indexovány podle celé hodnoty; je jen na vás, jak definovat konkrétní vyhledávací mechanismus.</span><span class="sxs-lookup"><span data-stu-id="f2d07-123">Indexers do not have to be indexed by an integer value; it is up to you how to define the specific look-up mechanism.</span></span>  
  
- <span data-ttu-id="f2d07-124">Indexery mohou být přetížené.</span><span class="sxs-lookup"><span data-stu-id="f2d07-124">Indexers can be overloaded.</span></span>  
  
- <span data-ttu-id="f2d07-125">Indexery mohou mít více než jeden formální parametr, například při přístupu k dvojrozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="f2d07-125">Indexers can have more than one formal parameter, for example, when accessing a two-dimensional array.</span></span>  
  
## <a name="BKMK_RelatedSections"></a><span data-ttu-id="f2d07-126">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="f2d07-126">Related Sections</span></span>  
  
- [<span data-ttu-id="f2d07-127">Použití indexerů</span><span class="sxs-lookup"><span data-stu-id="f2d07-127">Using Indexers</span></span>](./using-indexers.md)  
  
- [<span data-ttu-id="f2d07-128">Indexery v rozhraních</span><span class="sxs-lookup"><span data-stu-id="f2d07-128">Indexers in Interfaces</span></span>](./indexers-in-interfaces.md)  
  
- [<span data-ttu-id="f2d07-129">Porovnání vlastností a indexerů</span><span class="sxs-lookup"><span data-stu-id="f2d07-129">Comparison Between Properties and Indexers</span></span>](./comparison-between-properties-and-indexers.md)  
  
- [<span data-ttu-id="f2d07-130">Omezení přístupnosti přístupového objektu</span><span class="sxs-lookup"><span data-stu-id="f2d07-130">Restricting Accessor Accessibility</span></span>](../classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="f2d07-131">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f2d07-131">C# Language Specification</span></span>  

<span data-ttu-id="f2d07-132">Další informace naleznete v tématu [Indexery](~/_csharplang/spec/classes.md#indexers) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="f2d07-132">For more information, see [Indexers](~/_csharplang/spec/classes.md#indexers) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="f2d07-133">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="f2d07-133">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f2d07-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2d07-134">See also</span></span>

- [<span data-ttu-id="f2d07-135">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f2d07-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f2d07-136">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f2d07-136">Properties</span></span>](../classes-and-structs/properties.md)
