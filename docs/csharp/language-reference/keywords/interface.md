---
title: odkaz na C# rozhraní
ms.date: 07/20/2015
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 19ca4b8a490dc85de0d0e2be6d3ca8fa7982fc14
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713442"
---
# <a name="interface-c-reference"></a><span data-ttu-id="06511-102">interface (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="06511-102">interface (C# Reference)</span></span>

<span data-ttu-id="06511-103">Rozhraní obsahuje pouze signatury [metod](../../programming-guide/classes-and-structs/methods.md), [vlastností](../../programming-guide/classes-and-structs/properties.md), [událostí](../../programming-guide/events/index.md) nebo [indexerů](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="06511-103">An interface contains only the signatures of [methods](../../programming-guide/classes-and-structs/methods.md), [properties](../../programming-guide/classes-and-structs/properties.md), [events](../../programming-guide/events/index.md) or [indexers](../../programming-guide/indexers/index.md).</span></span> <span data-ttu-id="06511-104">Třída nebo struktura, která implementuje rozhraní, musí implementovat členy rozhraní zadané v definici rozhraní.</span><span class="sxs-lookup"><span data-stu-id="06511-104">A class or struct that implements the interface must implement the members of the interface that are specified in the interface definition.</span></span> <span data-ttu-id="06511-105">V následujícím příkladu musí třída `ImplementationClass` implementovat metodu s názvem `SampleMethod`, která nemá žádné parametry a vrací `void`.</span><span class="sxs-lookup"><span data-stu-id="06511-105">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>

<span data-ttu-id="06511-106">Další informace a příklady naleznete v tématu [rozhraní](../../programming-guide/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="06511-106">For more information and examples, see [Interfaces](../../programming-guide/interfaces/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="06511-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="06511-107">Example</span></span>

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

<span data-ttu-id="06511-108">Rozhraní může být členem oboru názvů nebo třídy a může obsahovat podpisy následujících členů:</span><span class="sxs-lookup"><span data-stu-id="06511-108">An interface can be a member of a namespace or a class and can contain signatures of the following members:</span></span>

- [<span data-ttu-id="06511-109">Metody</span><span class="sxs-lookup"><span data-stu-id="06511-109">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="06511-110">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="06511-110">Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)

- [<span data-ttu-id="06511-111">Indexery</span><span class="sxs-lookup"><span data-stu-id="06511-111">Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)

- [<span data-ttu-id="06511-112">Události</span><span class="sxs-lookup"><span data-stu-id="06511-112">Events</span></span>](event.md)

<span data-ttu-id="06511-113">Rozhraní může dědit z jednoho nebo více základních rozhraní.</span><span class="sxs-lookup"><span data-stu-id="06511-113">An interface can inherit from one or more base interfaces.</span></span>

<span data-ttu-id="06511-114">Jestliže seznam základních typů obsahuje základní třídu a rozhraní, musí se základní třída nacházet v seznamu jako první.</span><span class="sxs-lookup"><span data-stu-id="06511-114">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>

<span data-ttu-id="06511-115">Třída, která implementuje rozhraní, může explicitně implementovat členy rozhraní.</span><span class="sxs-lookup"><span data-stu-id="06511-115">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="06511-116">Explicitně implementovaný člen není přístupný prostřednictvím instance třídy, ale pouze prostřednictvím instance rozhraní.</span><span class="sxs-lookup"><span data-stu-id="06511-116">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span>

<span data-ttu-id="06511-117">Další podrobnosti a příklady kódu v explicitní implementaci rozhraní naleznete v tématu [explicitní implementace rozhraní](../../programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="06511-117">For more details and code examples on explicit interface implementation, see [Explicit Interface Implementation](../../programming-guide/interfaces/explicit-interface-implementation.md).</span></span>

## <a name="example"></a><span data-ttu-id="06511-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="06511-118">Example</span></span>

<span data-ttu-id="06511-119">Následující příklad ukazuje implementaci rozhraní.</span><span class="sxs-lookup"><span data-stu-id="06511-119">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="06511-120">V tomto příkladu obsahuje rozhraní deklaraci vlastnosti a třída obsahuje implementaci.</span><span class="sxs-lookup"><span data-stu-id="06511-120">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="06511-121">Jakákoli instance třídy, která implementuje rozhraní `IPoint`, má celočíselné vlastnosti `x` a `y`.</span><span class="sxs-lookup"><span data-stu-id="06511-121">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="06511-122">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="06511-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="06511-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="06511-123">See also</span></span>

- [<span data-ttu-id="06511-124">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="06511-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="06511-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="06511-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="06511-126">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="06511-126">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="06511-127">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="06511-127">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="06511-128">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="06511-128">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
- [<span data-ttu-id="06511-129">Použití vlastností</span><span class="sxs-lookup"><span data-stu-id="06511-129">Using Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="06511-130">Použití indexerů</span><span class="sxs-lookup"><span data-stu-id="06511-130">Using Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
- [<span data-ttu-id="06511-131">class</span><span class="sxs-lookup"><span data-stu-id="06511-131">class</span></span>](class.md)
- [<span data-ttu-id="06511-132">struct</span><span class="sxs-lookup"><span data-stu-id="06511-132">struct</span></span>](struct.md)
- [<span data-ttu-id="06511-133">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="06511-133">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
