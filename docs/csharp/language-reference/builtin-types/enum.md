---
title: Typy výčtu – odkaz jazyka C#
description: Informace o typech výčtu jazyka C#, které představují volbu nebo kombinaci možností
ms.date: 12/13/2019
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
- enum type [C#]
- enumeration type [C#]
- bit flags [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: 617c5ec037ad7a47b43cca2c13da4a77aa682997
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739088"
---
# <a name="enumeration-types-c-reference"></a><span data-ttu-id="0c781-103">Typy výčtu (odkaz Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="0c781-103">Enumeration types (C# reference)</span></span>

<span data-ttu-id="0c781-104">*Typ výčtu* (nebo *typ výčtu*) je typ [hodnoty](value-types.md) definovaný sadou pojmenovaných konstant základního [integrálního číselného](integral-numeric-types.md) typu.</span><span class="sxs-lookup"><span data-stu-id="0c781-104">An *enumeration type* (or *enum type*) is a [value type](value-types.md) defined by a set of named constants of the underlying [integral numeric](integral-numeric-types.md) type.</span></span> <span data-ttu-id="0c781-105">Chcete-li definovat typ výčtu, použijte `enum` klíčové slovo a zadejte názvy členů *výčtu*:</span><span class="sxs-lookup"><span data-stu-id="0c781-105">To define an enumeration type, use the `enum` keyword and specify the names of *enum members*:</span></span>

```csharp
enum Season
{
    Spring,
    Summer,
    Autumn,
    Winter
}
```

<span data-ttu-id="0c781-106">Ve výchozím nastavení jsou přidružené konstantní hodnoty `int`členů výčtu typu ; začínají nulou a zvyšují se o jednu po pořadí definičního textu.</span><span class="sxs-lookup"><span data-stu-id="0c781-106">By default, the associated constant values of enum members are of type `int`; they start with zero and increase by one following the definition text order.</span></span> <span data-ttu-id="0c781-107">Jako základní typ typu výčtu můžete explicitně zadat jakýkoli jiný [integrální číselný](integral-numeric-types.md) typ.</span><span class="sxs-lookup"><span data-stu-id="0c781-107">You can explicitly specify any other [integral numeric](integral-numeric-types.md) type as an underlying type of an enumeration type.</span></span> <span data-ttu-id="0c781-108">Můžete také explicitně zadat přidružené konstantní hodnoty, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="0c781-108">You can also explicitly specify the associated constant values, as the following example shows:</span></span>

```csharp
enum ErrorCode : ushort
{
    None = 0,
    Unknown = 1,
    ConnectionLost = 100,
    OutlierReading = 200
}
```

<span data-ttu-id="0c781-109">Metodu nelze definovat uvnitř definice typu výčtu.</span><span class="sxs-lookup"><span data-stu-id="0c781-109">You cannot define a method inside the definition of an enumeration type.</span></span> <span data-ttu-id="0c781-110">Chcete-li přidat funkce do typu výčtu, vytvořte [metodu rozšíření](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="0c781-110">To add functionality to an enumeration type, create an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

<span data-ttu-id="0c781-111">Výchozí hodnota typu `E` výčtu je hodnota vytvořená výrazem `(E)0`, i když nula nemá odpovídající výčtový člen.</span><span class="sxs-lookup"><span data-stu-id="0c781-111">The default value of an enumeration type `E` is the value produced by expression `(E)0`, even if zero doesn't have the corresponding enum member.</span></span>

<span data-ttu-id="0c781-112">Typ výčtu slouží k reprezentaci volby ze sady vzájemně se vylučujících hodnot nebo kombinace voleb.</span><span class="sxs-lookup"><span data-stu-id="0c781-112">You use an enumeration type to represent a choice from a set of mutually exclusive values or a combination of choices.</span></span> <span data-ttu-id="0c781-113">Chcete-li představovat kombinaci voleb, definujte typ výčtu jako bitové příznaky.</span><span class="sxs-lookup"><span data-stu-id="0c781-113">To represent a combination of choices, define an enumeration type as bit flags.</span></span>

## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="0c781-114">Typy výčtu jako bitové příznaky</span><span class="sxs-lookup"><span data-stu-id="0c781-114">Enumeration types as bit flags</span></span>

<span data-ttu-id="0c781-115">Pokud chcete, aby typ výčtu představoval kombinaci voleb, definujte členy výčtu pro tyto volby tak, aby individuální volba byla bitové pole.</span><span class="sxs-lookup"><span data-stu-id="0c781-115">If you want an enumeration type to represent a combination of choices, define enum members for those choices such that an individual choice is a bit field.</span></span> <span data-ttu-id="0c781-116">To znamená, že přidružené hodnoty těchto členů výčtu by měly být pravomoci dvou.</span><span class="sxs-lookup"><span data-stu-id="0c781-116">That is, the associated values of those enum members should be the powers of two.</span></span> <span data-ttu-id="0c781-117">Potom můžete použít [bitové logické `|` `&` operátory nebo](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) kombinovat volby nebo protínat kombinace voleb, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="0c781-117">Then, you can use the [bitwise logical operators `|` or `&`](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) to combine choices or intersect combinations of choices, respectively.</span></span> <span data-ttu-id="0c781-118">Chcete-li označit, že typ výčtu deklaruje bitová pole, použijte atribut [Flags.](xref:System.FlagsAttribute)</span><span class="sxs-lookup"><span data-stu-id="0c781-118">To indicate that an enumeration type declares bit fields, apply the [Flags](xref:System.FlagsAttribute) attribute to it.</span></span> <span data-ttu-id="0c781-119">Jak ukazuje následující příklad, můžete také zahrnout některé typické kombinace v definici typu výčtu.</span><span class="sxs-lookup"><span data-stu-id="0c781-119">As the following example shows, you can also include some typical combinations in the definition of an enumeration type.</span></span>

[!code-csharp[enum flags](snippets/EnumType.cs#Flags)]

<span data-ttu-id="0c781-120">Další informace a příklady <xref:System.FlagsAttribute?displayProperty=nameWithType> naleznete na referenční stránce rozhraní API a v části [Nevýhradní členy a Atribut příznaky](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) na stránce reference <xref:System.Enum?displayProperty=nameWithType> rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="0c781-120">For more information and examples, see the <xref:System.FlagsAttribute?displayProperty=nameWithType> API reference page and the [Non-exclusive members and the Flags attribute](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) section of the <xref:System.Enum?displayProperty=nameWithType> API reference page.</span></span>

## <a name="the-systemenum-type-and-enum-constraint"></a><span data-ttu-id="0c781-121">Typ System.Enum a omezení výčtu</span><span class="sxs-lookup"><span data-stu-id="0c781-121">The System.Enum type and enum constraint</span></span>

<span data-ttu-id="0c781-122">Typ <xref:System.Enum?displayProperty=nameWithType> je abstraktní základní třída všech typů výčtu.</span><span class="sxs-lookup"><span data-stu-id="0c781-122">The <xref:System.Enum?displayProperty=nameWithType> type is the abstract base class of all enumeration types.</span></span> <span data-ttu-id="0c781-123">Poskytuje řadu metod pro získání informací o typu výčtu a jeho hodnotách.</span><span class="sxs-lookup"><span data-stu-id="0c781-123">It provides a number of methods to get information about an enumeration type and its values.</span></span> <span data-ttu-id="0c781-124">Další informace a příklady <xref:System.Enum?displayProperty=nameWithType> naleznete na referenční stránce rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="0c781-124">For more information and examples, see the <xref:System.Enum?displayProperty=nameWithType> API reference page.</span></span>

<span data-ttu-id="0c781-125">Počínaje C# 7.3, můžete `System.Enum` použít v omezení základní třídy (který je známý jako [omezení výčtu)](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)určit, že parametr typu je typ výčtu.</span><span class="sxs-lookup"><span data-stu-id="0c781-125">Beginning with C# 7.3, you can use `System.Enum` in a base class constraint (that is known as the [enum constraint](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)) to specify that a type parameter is an enumeration type.</span></span>

## <a name="conversions"></a><span data-ttu-id="0c781-126">Převody</span><span class="sxs-lookup"><span data-stu-id="0c781-126">Conversions</span></span>

<span data-ttu-id="0c781-127">Pro libovolný typ výčtu existují explicitní převody mezi typem výčtu a jeho základním integrálním typem.</span><span class="sxs-lookup"><span data-stu-id="0c781-127">For any enumeration type, there exist explicit conversions between the enumeration type and its underlying integral type.</span></span> <span data-ttu-id="0c781-128">Pokud [přetypovat](../operators/type-testing-and-cast.md#cast-expression) hodnotu výčtu na jeho základní typ, výsledkem je přidružená integrální hodnota člena výčtu.</span><span class="sxs-lookup"><span data-stu-id="0c781-128">If you [cast](../operators/type-testing-and-cast.md#cast-expression) an enum value to its underlying type, the result is the associated integral value of an enum member.</span></span>

[!code-csharp[enum conversions](snippets/EnumType.cs#Conversions)]

<span data-ttu-id="0c781-129">Pomocí <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> metody určete, zda typ výčtu obsahuje člen výčtu s určitou přidruženou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="0c781-129">Use the <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> method to determine whether an enumeration type contains an enum member with the certain associated value.</span></span>

<span data-ttu-id="0c781-130">Pro libovolný typ výčtu existují převody [zabalení a rozbalení](../../programming-guide/types/boxing-and-unboxing.md) do a z <xref:System.Enum?displayProperty=nameWithType> typu, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="0c781-130">For any enumeration type, there exist [boxing and unboxing](../../programming-guide/types/boxing-and-unboxing.md) conversions to and from the <xref:System.Enum?displayProperty=nameWithType> type, respectively.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0c781-131">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0c781-131">C# language specification</span></span>

<span data-ttu-id="0c781-132">Další informace naleznete v následujících částech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="0c781-132">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="0c781-133">Výčty</span><span class="sxs-lookup"><span data-stu-id="0c781-133">Enums</span></span>](~/_csharplang/spec/enums.md)
- [<span data-ttu-id="0c781-134">Hodnoty a operace výčtu</span><span class="sxs-lookup"><span data-stu-id="0c781-134">Enum values and operations</span></span>](~/_csharplang/spec/enums.md#enum-values-and-operations)
- [<span data-ttu-id="0c781-135">Logické operátory výčtu</span><span class="sxs-lookup"><span data-stu-id="0c781-135">Enumeration logical operators</span></span>](~/_csharplang/spec/expressions.md#enumeration-logical-operators)
- [<span data-ttu-id="0c781-136">Operátory porovnání výčtu</span><span class="sxs-lookup"><span data-stu-id="0c781-136">Enumeration comparison operators</span></span>](~/_csharplang/spec/expressions.md#enumeration-comparison-operators)
- [<span data-ttu-id="0c781-137">Explicitní převody výčtu</span><span class="sxs-lookup"><span data-stu-id="0c781-137">Explicit enumeration conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-enumeration-conversions)
- [<span data-ttu-id="0c781-138">Převody implicitního výčtu</span><span class="sxs-lookup"><span data-stu-id="0c781-138">Implicit enumeration conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-enumeration-conversions)

## <a name="see-also"></a><span data-ttu-id="0c781-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="0c781-139">See also</span></span>

- [<span data-ttu-id="0c781-140">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="0c781-140">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0c781-141">Vytvoření výčtu řetězců formátu</span><span class="sxs-lookup"><span data-stu-id="0c781-141">Enumeration format strings</span></span>](../../../standard/base-types/enumeration-format-strings.md)
- [<span data-ttu-id="0c781-142">Pokyny pro návrh - Výčet</span><span class="sxs-lookup"><span data-stu-id="0c781-142">Design guidelines - Enum design</span></span>](../../../standard/design-guidelines/enum.md)
- [<span data-ttu-id="0c781-143">Pokyny pro návrh – konvence pojmenování výčtu</span><span class="sxs-lookup"><span data-stu-id="0c781-143">Design guidelines - Enum naming conventions</span></span>](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
- [<span data-ttu-id="0c781-144">příkaz switch</span><span class="sxs-lookup"><span data-stu-id="0c781-144">switch statement</span></span>](../keywords/switch.md)
