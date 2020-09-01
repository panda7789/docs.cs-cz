---
description: ':::no-loc text=interface::: (Referenční dokumentace jazyka C#)'
title: rozhraní – reference jazyka C#
ms.date: 01/17/2020
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 24f95e828522f467c519c0c8a7ba9410aa97af4e
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134585"
---
# <a name="no-loc-textinterface-c-reference"></a><span data-ttu-id="540a7-103">:::no-loc text="interface"::: (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="540a7-103">:::no-loc text="interface"::: (C# Reference)</span></span>

<span data-ttu-id="540a7-104">Rozhraní definuje kontrakt.</span><span class="sxs-lookup"><span data-stu-id="540a7-104">An interface defines a contract.</span></span> <span data-ttu-id="540a7-105">Jakýkoli [`class`](class.md) nebo [`struct`](../builtin-types/struct.md) , který implementuje daný kontrakt, musí poskytnout implementaci členů definovaných v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="540a7-105">Any [`class`](class.md) or [`struct`](../builtin-types/struct.md) that implements that contract must provide an implementation of the members defined in the interface.</span></span> <span data-ttu-id="540a7-106">Počínaje jazykem C# 8,0 může rozhraní definovat výchozí implementaci pro členy.</span><span class="sxs-lookup"><span data-stu-id="540a7-106">Beginning with C# 8.0, an interface may define a default implementation for members.</span></span> <span data-ttu-id="540a7-107">Může také definovat členy, aby [`static`](static.md) poskytovaly jednu implementaci pro běžné funkce.</span><span class="sxs-lookup"><span data-stu-id="540a7-107">It may also define [`static`](static.md) members in order to provide a single implementation for common functionality.</span></span>

<span data-ttu-id="540a7-108">V následujícím příkladu musí třída `ImplementationClass` implementovat metodu s názvem `SampleMethod`, která nemá žádné parametry a vrací `void`.</span><span class="sxs-lookup"><span data-stu-id="540a7-108">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>

<span data-ttu-id="540a7-109">Další informace a příklady naleznete v tématu [rozhraní](../../programming-guide/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="540a7-109">For more information and examples, see [Interfaces](../../programming-guide/interfaces/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="540a7-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="540a7-110">Example</span></span>

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

<span data-ttu-id="540a7-111">Rozhraní může být členem oboru názvů nebo třídy.</span><span class="sxs-lookup"><span data-stu-id="540a7-111">An interface can be a member of a namespace or a class.</span></span> <span data-ttu-id="540a7-112">Deklarace rozhraní může obsahovat deklarace (signatury bez implementace) následujících členů:</span><span class="sxs-lookup"><span data-stu-id="540a7-112">An interface declaration can contain declarations (signatures without any implementation) of the following members:</span></span>

- [<span data-ttu-id="540a7-113">Metody</span><span class="sxs-lookup"><span data-stu-id="540a7-113">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="540a7-114">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="540a7-114">Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="540a7-115">Indexery</span><span class="sxs-lookup"><span data-stu-id="540a7-115">Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
- [<span data-ttu-id="540a7-116">Události</span><span class="sxs-lookup"><span data-stu-id="540a7-116">Events</span></span>](event.md)

<span data-ttu-id="540a7-117">Předchozí deklarace členů obvykle neobsahují tělo.</span><span class="sxs-lookup"><span data-stu-id="540a7-117">These preceding member declarations typically do not contain a body.</span></span> <span data-ttu-id="540a7-118">Počínaje jazykem C# 8,0 může člen rozhraní deklarovat tělo.</span><span class="sxs-lookup"><span data-stu-id="540a7-118">Beginning with C# 8.0, an interface member may declare a body.</span></span> <span data-ttu-id="540a7-119">Tato metoda se nazývá *Výchozí implementace*.</span><span class="sxs-lookup"><span data-stu-id="540a7-119">This is called a *default implementation*.</span></span> <span data-ttu-id="540a7-120">Členové s orgány umožňují, aby rozhraní poskytovalo "výchozí" implementaci pro třídy a struktury, které neposkytují přepisující implementaci.</span><span class="sxs-lookup"><span data-stu-id="540a7-120">Members with bodies permit the interface to provide a "default" implementation for classes and structs that don't provide an overriding implementation.</span></span> <span data-ttu-id="540a7-121">Kromě toho, počínaje C# 8,0, může rozhraní zahrnovat:</span><span class="sxs-lookup"><span data-stu-id="540a7-121">In addition, beginning with C# 8.0, an interface may include:</span></span>

- [<span data-ttu-id="540a7-122">Konstanty</span><span class="sxs-lookup"><span data-stu-id="540a7-122">Constants</span></span>](const.md)
- [<span data-ttu-id="540a7-123">Operátory</span><span class="sxs-lookup"><span data-stu-id="540a7-123">Operators</span></span>](../operators/operator-overloading.md)
- <span data-ttu-id="540a7-124">[Statický konstruktor](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span><span class="sxs-lookup"><span data-stu-id="540a7-124">[Static constructor](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span></span>
- [<span data-ttu-id="540a7-125">Vnořené typy</span><span class="sxs-lookup"><span data-stu-id="540a7-125">Nested types</span></span>](../../programming-guide/classes-and-structs/nested-types.md)
- [<span data-ttu-id="540a7-126">Statická pole, metody, vlastnosti, indexery a události</span><span class="sxs-lookup"><span data-stu-id="540a7-126">Static fields, methods, properties, indexers, and events</span></span>](static.md)
- <span data-ttu-id="540a7-127">Deklarace členů pomocí explicitní syntaxe implementace rozhraní.</span><span class="sxs-lookup"><span data-stu-id="540a7-127">Member declarations using the explicit interface implementation syntax.</span></span>
- <span data-ttu-id="540a7-128">Explicitní modifikátory přístupu (výchozí přístup je [`public`](access-modifiers.md) ).</span><span class="sxs-lookup"><span data-stu-id="540a7-128">Explicit access modifiers (the default access is [`public`](access-modifiers.md)).</span></span>

<span data-ttu-id="540a7-129">Rozhraní nemůžou obsahovat stav instance.</span><span class="sxs-lookup"><span data-stu-id="540a7-129">Interfaces may not contain instance state.</span></span> <span data-ttu-id="540a7-130">Zatímco statická pole jsou nyní povolena, pole instance nejsou v rozhraních povolena.</span><span class="sxs-lookup"><span data-stu-id="540a7-130">While static fields are now permitted, instance fields are not permitted in interfaces.</span></span> <span data-ttu-id="540a7-131">[Automatické vlastnosti instance](../../programming-guide/classes-and-structs/auto-implemented-properties.md) nejsou v rozhraních podporované, protože by implicitně deklarovaly skryté pole.</span><span class="sxs-lookup"><span data-stu-id="540a7-131">[Instance auto-properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) are not supported in interfaces, as they would implicitly declare a hidden field.</span></span> <span data-ttu-id="540a7-132">Toto pravidlo má jemný efekt pro deklarace vlastností.</span><span class="sxs-lookup"><span data-stu-id="540a7-132">This rule has a subtle effect on property declarations.</span></span> <span data-ttu-id="540a7-133">V deklaraci rozhraní následující kód nedeklaruje automaticky implementovanou vlastnost, která je v `class` nebo `struct` .</span><span class="sxs-lookup"><span data-stu-id="540a7-133">In an interface declaration, the following code does not declare an auto-implemented property as it does in a `class` or `struct`.</span></span> <span data-ttu-id="540a7-134">Místo toho deklaruje vlastnost, která nemá výchozí implementaci, ale musí být implementována v jakémkoli typu, který implementuje rozhraní:</span><span class="sxs-lookup"><span data-stu-id="540a7-134">Instead, it declares a property that doesn't have a default implementation but must be implemented in any type that implements the interface:</span></span>

```csharp
public interface INamed
{
  public string Name {get; set;}
}
```

<span data-ttu-id="540a7-135">Rozhraní může dědit z jednoho nebo více základních rozhraní.</span><span class="sxs-lookup"><span data-stu-id="540a7-135">An interface can inherit from one or more base interfaces.</span></span> <span data-ttu-id="540a7-136">Když rozhraní [přepisuje metodu](override.md) implementovanou v základním rozhraní, musí použít [explicitní syntaxi implementace rozhraní](../../programming-guide/interfaces/explicit-interface-implementation.md) .</span><span class="sxs-lookup"><span data-stu-id="540a7-136">When an interface [overrides a method](override.md) implemented in a base interface, it must use the [explicit interface implementation](../../programming-guide/interfaces/explicit-interface-implementation.md) syntax.</span></span>

<span data-ttu-id="540a7-137">Jestliže seznam základních typů obsahuje základní třídu a rozhraní, musí se základní třída nacházet v seznamu jako první.</span><span class="sxs-lookup"><span data-stu-id="540a7-137">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>

<span data-ttu-id="540a7-138">Třída, která implementuje rozhraní, může explicitně implementovat členy rozhraní.</span><span class="sxs-lookup"><span data-stu-id="540a7-138">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="540a7-139">Explicitně implementovaný člen není přístupný prostřednictvím instance třídy, ale pouze prostřednictvím instance rozhraní.</span><span class="sxs-lookup"><span data-stu-id="540a7-139">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span> <span data-ttu-id="540a7-140">Kromě toho mohou být k výchozím členům rozhraní přicházet pouze prostřednictvím instance rozhraní.</span><span class="sxs-lookup"><span data-stu-id="540a7-140">In addition, default interface members can only be accessed through an instance of the interface.</span></span>

<span data-ttu-id="540a7-141">Další informace o explicitní implementaci rozhraní naleznete v tématu [explicitní implementace rozhraní](../../programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="540a7-141">For more information about explicit interface implementation, see [Explicit Interface Implementation](../../programming-guide/interfaces/explicit-interface-implementation.md).</span></span>

## <a name="example"></a><span data-ttu-id="540a7-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="540a7-142">Example</span></span>

<span data-ttu-id="540a7-143">Následující příklad ukazuje implementaci rozhraní.</span><span class="sxs-lookup"><span data-stu-id="540a7-143">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="540a7-144">V tomto příkladu obsahuje rozhraní deklaraci vlastnosti a třída obsahuje implementaci.</span><span class="sxs-lookup"><span data-stu-id="540a7-144">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="540a7-145">Jakákoli instance třídy, která implementuje rozhraní `IPoint`, má celočíselné vlastnosti `x` a `y`.</span><span class="sxs-lookup"><span data-stu-id="540a7-145">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="540a7-146">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="540a7-146">C# language specification</span></span>

<span data-ttu-id="540a7-147">Další informace naleznete v části [rozhraní](~/_csharplang/spec/interfaces.md) [specifikace jazyka C#](~/_csharplang/spec/introduction.md) a specifikace funkce pro [výchozí členy rozhraní – C# 8,0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span><span class="sxs-lookup"><span data-stu-id="540a7-147">For more information, see the [Interfaces](~/_csharplang/spec/interfaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the feature specification for [Default interface members - C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="540a7-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="540a7-148">See also</span></span>

- [<span data-ttu-id="540a7-149">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="540a7-149">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="540a7-150">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="540a7-150">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="540a7-151">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="540a7-151">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="540a7-152">Typy odkazů</span><span class="sxs-lookup"><span data-stu-id="540a7-152">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="540a7-153">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="540a7-153">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
- [<span data-ttu-id="540a7-154">Použití vlastností</span><span class="sxs-lookup"><span data-stu-id="540a7-154">Using Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="540a7-155">Použití indexerů</span><span class="sxs-lookup"><span data-stu-id="540a7-155">Using Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
