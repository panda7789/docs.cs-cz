---
title: Indexery - C# Průvodce programováním
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
ms.openlocfilehash: 5ab0a5e524979110c355391cf800cc82e6d6244f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61680154"
---
# <a name="indexers-c-programming-guide"></a><span data-ttu-id="795f0-102">Indexery (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="795f0-102">Indexers (C# Programming Guide)</span></span>

<span data-ttu-id="795f0-103">Indexery povolit instance třídy nebo struktury indexovaných stejně jako pole.</span><span class="sxs-lookup"><span data-stu-id="795f0-103">Indexers allow instances of a class or struct to be indexed just like arrays.</span></span> <span data-ttu-id="795f0-104">Indexovanou hodnotu můžete nastavit nebo načíst bez explicitního určení typu nebo instance člena.</span><span class="sxs-lookup"><span data-stu-id="795f0-104">The indexed value can be set or retrieved without explicitly specifying a type or instance member.</span></span> <span data-ttu-id="795f0-105">Indexery se podobají [vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md) s tím rozdílem, že jejich přístupových objektů přijímají parametry.</span><span class="sxs-lookup"><span data-stu-id="795f0-105">Indexers resemble [properties](../../../csharp/programming-guide/classes-and-structs/properties.md) except that their accessors take parameters.</span></span>  
 
 <span data-ttu-id="795f0-106">Následující příklad definuje obecné třídy s jednoduchou [získat](../../../csharp/language-reference/keywords/get.md) a [nastavit](../../../csharp/language-reference/keywords/set.md) přístupové metody pro přiřazení a načítat hodnoty.</span><span class="sxs-lookup"><span data-stu-id="795f0-106">The following example defines a generic class with simple [get](../../../csharp/language-reference/keywords/get.md) and [set](../../../csharp/language-reference/keywords/set.md) accessor methods to assign and retrieve values.</span></span> <span data-ttu-id="795f0-107">`Program` Třídy vytvoří instanci této třídy pro uložení řetězce.</span><span class="sxs-lookup"><span data-stu-id="795f0-107">The `Program` class creates an instance of this class for storing strings.</span></span>  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
>  <span data-ttu-id="795f0-108">Další příklady najdete v tématu [související oddíly](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections).</span><span class="sxs-lookup"><span data-stu-id="795f0-108">For more examples, see [Related Sections](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections).</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="795f0-109">Definice textu výrazu</span><span class="sxs-lookup"><span data-stu-id="795f0-109">Expression Body Definitions</span></span>  
 
<span data-ttu-id="795f0-110">Je běžné, že indexování get nebo přístupový objekt set spočívají jediném příkazu, který vrátí nebo nastaví hodnotu.</span><span class="sxs-lookup"><span data-stu-id="795f0-110">It is common for an indexer's get or set accessor to consist of a single statement that either returns or sets a value.</span></span> <span data-ttu-id="795f0-111">Členové tvoření poskytují zjednodušenou syntaxi pro podporu tohoto scénáře.</span><span class="sxs-lookup"><span data-stu-id="795f0-111">Expression-bodied members provide a simplified syntax to support this scenario.</span></span> <span data-ttu-id="795f0-112">Od verze C# 6, je možné implementovat jako člena s výrazem v těle, jak ukazuje následující příklad indexer jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="795f0-112">Starting with C# 6, a read-only indexer can be implemented as an expression-bodied member, as the following example shows.</span></span>

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

<span data-ttu-id="795f0-113">Všimněte si, že `=>` představuje text výrazu a, který `get` – klíčové slovo se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="795f0-113">Note that `=>` introduces the expression body, and that the `get` keyword is not used.</span></span> 

<span data-ttu-id="795f0-114">Od verze C# 7.0, jak získat a přístupový objekt set mohou být implementovaná jako členy s výrazem v těle.</span><span class="sxs-lookup"><span data-stu-id="795f0-114">Starting with C# 7.0, both the get and set accessor can be an implemented as expression-bodied members.</span></span> <span data-ttu-id="795f0-115">V takovém případě obě `get` a `set` klíčová slova musí být použita.</span><span class="sxs-lookup"><span data-stu-id="795f0-115">In this case, both `get` and `set` keywords must be used.</span></span> <span data-ttu-id="795f0-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="795f0-116">For example:</span></span>

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a><span data-ttu-id="795f0-117">Přehled indexerů</span><span class="sxs-lookup"><span data-stu-id="795f0-117">Indexers Overview</span></span>  
  
- <span data-ttu-id="795f0-118">Indexery povolují objekty, které mají být indexovány v podobným způsobem jako pole.</span><span class="sxs-lookup"><span data-stu-id="795f0-118">Indexers enable objects to be indexed in a similar manner to arrays.</span></span>  
  
- <span data-ttu-id="795f0-119">A `get` přistupující objekt vrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="795f0-119">A `get` accessor returns a value.</span></span> <span data-ttu-id="795f0-120">A `set` přístupového objektu přiřadí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="795f0-120">A `set` accessor assigns a value.</span></span>  
  
- <span data-ttu-id="795f0-121">[To](../../../csharp/language-reference/keywords/this.md) – klíčové slovo se používá k definování indexeru.</span><span class="sxs-lookup"><span data-stu-id="795f0-121">The [this](../../../csharp/language-reference/keywords/this.md) keyword is used to define the indexer.</span></span>  
  
- <span data-ttu-id="795f0-122">[Hodnotu](../../../csharp/language-reference/keywords/value.md) – klíčové slovo se používá k definování přiřazené podle hodnoty `set` indexeru.</span><span class="sxs-lookup"><span data-stu-id="795f0-122">The [value](../../../csharp/language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` indexer.</span></span>  
  
- <span data-ttu-id="795f0-123">Indexery není nutné indexovat pomocí celočíselnou hodnotu; je jenom na vás, jak definovat konkrétní vyhledávací mechanismus.</span><span class="sxs-lookup"><span data-stu-id="795f0-123">Indexers do not have to be indexed by an integer value; it is up to you how to define the specific look-up mechanism.</span></span>  
  
- <span data-ttu-id="795f0-124">Indexery můžou být přetížené.</span><span class="sxs-lookup"><span data-stu-id="795f0-124">Indexers can be overloaded.</span></span>  
  
- <span data-ttu-id="795f0-125">Indexery může mít více než jeden formální parametr, například při přístupu k dvourozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="795f0-125">Indexers can have more than one formal parameter, for example, when accessing a two-dimensional array.</span></span>  
  
## <a name="BKMK_RelatedSections"></a> <span data-ttu-id="795f0-126">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="795f0-126">Related Sections</span></span>  
  
- [<span data-ttu-id="795f0-127">Použití indexerů</span><span class="sxs-lookup"><span data-stu-id="795f0-127">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
- [<span data-ttu-id="795f0-128">Indexery v rozhraní</span><span class="sxs-lookup"><span data-stu-id="795f0-128">Indexers in Interfaces</span></span>](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
- [<span data-ttu-id="795f0-129">Porovnání mezi vlastnostmi a indexery</span><span class="sxs-lookup"><span data-stu-id="795f0-129">Comparison Between Properties and Indexers</span></span>](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
- [<span data-ttu-id="795f0-130">Omezení přístupnosti přístupového objektu</span><span class="sxs-lookup"><span data-stu-id="795f0-130">Restricting Accessor Accessibility</span></span>](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="795f0-131">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="795f0-131">C# Language Specification</span></span>  

<span data-ttu-id="795f0-132">Další informace najdete v tématu [indexery](~/_csharplang/spec/classes.md#indexers) v [ C# specifikace jazyka](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="795f0-132">For more information, see [Indexers](~/_csharplang/spec/classes.md#indexers) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="795f0-133">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="795f0-133">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="795f0-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="795f0-134">See also</span></span>

- [<span data-ttu-id="795f0-135">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="795f0-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="795f0-136">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="795f0-136">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
