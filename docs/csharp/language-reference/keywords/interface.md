---
title: rozhraní - C# Reference
ms.date: 01/17/2020
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 473f5f8e226f0a144746ac943afcffdccd4777c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77625849"
---
# <a name="no-loc-textinterface-c-reference"></a><span data-ttu-id="decd5-102">:::no-loc text="interface":::(Odkaz na C#)</span><span class="sxs-lookup"><span data-stu-id="decd5-102">:::no-loc text="interface"::: (C# Reference)</span></span>

<span data-ttu-id="decd5-103">Rozhraní definuje smlouvu.</span><span class="sxs-lookup"><span data-stu-id="decd5-103">An interface defines a contract.</span></span> <span data-ttu-id="decd5-104">Každý [`class`](class.md) [`struct`](../builtin-types/struct.md) nebo, který implementuje tuto smlouvu musí poskytnout implementaci členů definovaných v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="decd5-104">Any [`class`](class.md) or [`struct`](../builtin-types/struct.md) that implements that contract must provide an implementation of the members defined in the interface.</span></span> <span data-ttu-id="decd5-105">Počínaje C# 8.0 rozhraní může definovat výchozí implementaci pro členy.</span><span class="sxs-lookup"><span data-stu-id="decd5-105">Beginning with C# 8.0, an interface may define a default implementation for members.</span></span> <span data-ttu-id="decd5-106">Může také [`static`](static.md) definovat členy za účelem poskytnutí jediné implementace pro společné funkce.</span><span class="sxs-lookup"><span data-stu-id="decd5-106">It may also define [`static`](static.md) members in order to provide a single implementation for common functionality.</span></span>

<span data-ttu-id="decd5-107">V následujícím příkladu musí třída `ImplementationClass` implementovat metodu s názvem `SampleMethod`, která nemá žádné parametry a vrací `void`.</span><span class="sxs-lookup"><span data-stu-id="decd5-107">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>

<span data-ttu-id="decd5-108">Další informace a příklady naleznete v [tématu Rozhraní](../../programming-guide/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="decd5-108">For more information and examples, see [Interfaces](../../programming-guide/interfaces/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="decd5-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="decd5-109">Example</span></span>

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

<span data-ttu-id="decd5-110">Rozhraní může být členem oboru názvů nebo třídy.</span><span class="sxs-lookup"><span data-stu-id="decd5-110">An interface can be a member of a namespace or a class.</span></span> <span data-ttu-id="decd5-111">Deklarace rozhraní může obsahovat deklarace (podpisy bez jakékoli implementace) následujících členů:</span><span class="sxs-lookup"><span data-stu-id="decd5-111">An interface declaration can contain declarations (signatures without any implementation) of the following members:</span></span>

- [<span data-ttu-id="decd5-112">Metody</span><span class="sxs-lookup"><span data-stu-id="decd5-112">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="decd5-113">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="decd5-113">Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="decd5-114">Indexery</span><span class="sxs-lookup"><span data-stu-id="decd5-114">Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
- [<span data-ttu-id="decd5-115">Akce</span><span class="sxs-lookup"><span data-stu-id="decd5-115">Events</span></span>](event.md)

<span data-ttu-id="decd5-116">Tyto předchozí deklarace členů obvykle neobsahují tělo.</span><span class="sxs-lookup"><span data-stu-id="decd5-116">These preceding member declarations typically do not contain a body.</span></span> <span data-ttu-id="decd5-117">Počínaje C# 8.0, člen rozhraní může deklarovat tělo.</span><span class="sxs-lookup"><span data-stu-id="decd5-117">Beginning with C# 8.0, an interface member may declare a body.</span></span> <span data-ttu-id="decd5-118">To se nazývá *výchozí implementace*.</span><span class="sxs-lookup"><span data-stu-id="decd5-118">This is called a *default implementation*.</span></span> <span data-ttu-id="decd5-119">Členové s orgány povolit rozhraní poskytnout "výchozí" implementace pro třídy a struktury, které neposkytují přepsání implementace.</span><span class="sxs-lookup"><span data-stu-id="decd5-119">Members with bodies permit the interface to provide a "default" implementation for classes and structs that don't provide an overriding implementation.</span></span> <span data-ttu-id="decd5-120">Kromě toho počínaje C# 8.0 rozhraní může zahrnovat:</span><span class="sxs-lookup"><span data-stu-id="decd5-120">In addition, beginning with C# 8.0, an interface may include:</span></span>

- [<span data-ttu-id="decd5-121">Konstanty</span><span class="sxs-lookup"><span data-stu-id="decd5-121">Constants</span></span>](const.md)
- [<span data-ttu-id="decd5-122">Operátory</span><span class="sxs-lookup"><span data-stu-id="decd5-122">Operators</span></span>](../operators/operator-overloading.md)
- <span data-ttu-id="decd5-123">[Statický konstruktor](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span><span class="sxs-lookup"><span data-stu-id="decd5-123">[Static constructor](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span></span>
- [<span data-ttu-id="decd5-124">Vnořené typy</span><span class="sxs-lookup"><span data-stu-id="decd5-124">Nested types</span></span>](../../programming-guide/classes-and-structs/nested-types.md)
- [<span data-ttu-id="decd5-125">Statická pole, metody, vlastnosti, indexery a události</span><span class="sxs-lookup"><span data-stu-id="decd5-125">Static fields, methods, properties, indexers, and events</span></span>](static.md)
- <span data-ttu-id="decd5-126">Deklarace členů pomocí syntaxe implementace explicitnírozhraní.</span><span class="sxs-lookup"><span data-stu-id="decd5-126">Member declarations using the explicit interface implementation syntax.</span></span>
- <span data-ttu-id="decd5-127">Explicitní modifikátory přístupu [`public`](access-modifiers.md)(výchozí přístup je ).</span><span class="sxs-lookup"><span data-stu-id="decd5-127">Explicit access modifiers (the default access is [`public`](access-modifiers.md)).</span></span>

<span data-ttu-id="decd5-128">Rozhraní nesmí obsahovat stav instance.</span><span class="sxs-lookup"><span data-stu-id="decd5-128">Interfaces may not contain instance state.</span></span> <span data-ttu-id="decd5-129">Zatímco statická pole jsou nyní povolena, pole instancí nejsou povolena v rozhraních.</span><span class="sxs-lookup"><span data-stu-id="decd5-129">While static fields are now permitted, instance fields are not permitted in interfaces.</span></span> <span data-ttu-id="decd5-130">[Automatické vlastnosti instance](../../programming-guide/classes-and-structs/auto-implemented-properties.md) nejsou v rozhraních podporovány, protože by implicitně deklarovaly skryté pole.</span><span class="sxs-lookup"><span data-stu-id="decd5-130">[Instance auto-properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) are not supported in interfaces, as they would implicitly declare a hidden field.</span></span> <span data-ttu-id="decd5-131">Toto pravidlo má jemný vliv na deklarace vlastností.</span><span class="sxs-lookup"><span data-stu-id="decd5-131">This rule has a subtle effect on property declarations.</span></span> <span data-ttu-id="decd5-132">V deklaraci rozhraní následující kód nedeklaruje automaticky implementované `class` `struct`vlastnosti, jak to dělá v nebo .</span><span class="sxs-lookup"><span data-stu-id="decd5-132">In an interface declaration, the following code does not declare an auto-implemented property as it does in a `class` or `struct`.</span></span> <span data-ttu-id="decd5-133">Místo toho deklaruje vlastnost, která nemá výchozí implementaci, ale musí být implementována v libovolném typu, který implementuje rozhraní:</span><span class="sxs-lookup"><span data-stu-id="decd5-133">Instead, it declares a property that doesn't have a default implementation but must be implemented in any type that implements the interface:</span></span>

```csharp
public interface INamed
{
  public string Name {get; set;}
}
```

<span data-ttu-id="decd5-134">Rozhraní může dědit z jednoho nebo více základních rozhraní.</span><span class="sxs-lookup"><span data-stu-id="decd5-134">An interface can inherit from one or more base interfaces.</span></span> <span data-ttu-id="decd5-135">Když rozhraní [přepíše metodu](override.md) implementovanou v základním rozhraní, musí použít syntaxi [implementace explicitní rozhraní.](../../programming-guide/interfaces/explicit-interface-implementation.md)</span><span class="sxs-lookup"><span data-stu-id="decd5-135">When an interface [overrides a method](override.md) implemented in a base interface, it must use the [explicit interface implementation](../../programming-guide/interfaces/explicit-interface-implementation.md) syntax.</span></span>

<span data-ttu-id="decd5-136">Jestliže seznam základních typů obsahuje základní třídu a rozhraní, musí se základní třída nacházet v seznamu jako první.</span><span class="sxs-lookup"><span data-stu-id="decd5-136">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>

<span data-ttu-id="decd5-137">Třída, která implementuje rozhraní, může explicitně implementovat členy rozhraní.</span><span class="sxs-lookup"><span data-stu-id="decd5-137">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="decd5-138">Explicitně implementovaný člen není přístupný prostřednictvím instance třídy, ale pouze prostřednictvím instance rozhraní.</span><span class="sxs-lookup"><span data-stu-id="decd5-138">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span> <span data-ttu-id="decd5-139">Kromě toho výchozí členy rozhraní lze přistupovat pouze prostřednictvím instance rozhraní.</span><span class="sxs-lookup"><span data-stu-id="decd5-139">In addition, default interface members can only be accessed through an instance of the interface.</span></span>

<span data-ttu-id="decd5-140">Další informace o explicitní implementaci rozhraní naleznete [v tématu Explicitní implementace rozhraní](../../programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="decd5-140">For more information about explicit interface implementation, see [Explicit Interface Implementation](../../programming-guide/interfaces/explicit-interface-implementation.md).</span></span>

## <a name="example"></a><span data-ttu-id="decd5-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="decd5-141">Example</span></span>

<span data-ttu-id="decd5-142">Následující příklad ukazuje implementaci rozhraní.</span><span class="sxs-lookup"><span data-stu-id="decd5-142">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="decd5-143">V tomto příkladu obsahuje rozhraní deklaraci vlastnosti a třída obsahuje implementaci.</span><span class="sxs-lookup"><span data-stu-id="decd5-143">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="decd5-144">Jakákoli instance třídy, která implementuje rozhraní `IPoint`, má celočíselné vlastnosti `x` a `y`.</span><span class="sxs-lookup"><span data-stu-id="decd5-144">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="decd5-145">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="decd5-145">C# language specification</span></span>

<span data-ttu-id="decd5-146">Další informace naleznete v části [Rozhraní](~/_csharplang/spec/interfaces.md) [specifikace jazyka C#](~/_csharplang/spec/introduction.md) a specifikace funkce pro výchozí členy rozhraní - [C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span><span class="sxs-lookup"><span data-stu-id="decd5-146">For more information, see the [Interfaces](~/_csharplang/spec/interfaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the feature specification for [Default interface members - C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="decd5-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="decd5-147">See also</span></span>

- [<span data-ttu-id="decd5-148">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="decd5-148">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="decd5-149">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="decd5-149">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="decd5-150">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="decd5-150">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="decd5-151">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="decd5-151">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="decd5-152">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="decd5-152">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
- [<span data-ttu-id="decd5-153">Použití vlastností</span><span class="sxs-lookup"><span data-stu-id="decd5-153">Using Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="decd5-154">Použití indexerů</span><span class="sxs-lookup"><span data-stu-id="decd5-154">Using Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
- [<span data-ttu-id="decd5-155">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="decd5-155">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
