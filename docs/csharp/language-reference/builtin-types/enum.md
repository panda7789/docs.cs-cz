---
title: Výčtové typy C# – referenční informace
description: Seznamte C# se s typy výčtu, které reprezentují volbu nebo kombinaci voleb.
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
ms.openlocfilehash: 77c7b7bd7f3e59fbe782755c829f18cf1cefc725
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239817"
---
# <a name="enumeration-types-c-reference"></a><span data-ttu-id="6b9ce-103">Výčtové typyC# (referenční)</span><span class="sxs-lookup"><span data-stu-id="6b9ce-103">Enumeration types (C# reference)</span></span>

<span data-ttu-id="6b9ce-104">*Výčtový typ* (nebo *typ výčtu*) je [typ hodnoty](value-types.md) definovaný sadou pojmenovaných konstant základního [integrálního číselného](integral-numeric-types.md) typu.</span><span class="sxs-lookup"><span data-stu-id="6b9ce-104">An *enumeration type* (or *enum type*) is a [value type](value-types.md) defined by a set of named constants of the underlying [integral numeric](integral-numeric-types.md) type.</span></span> <span data-ttu-id="6b9ce-105">Chcete-li definovat typ výčtu, použijte klíčové slovo `enum` a zadejte názvy *členů výčtu*:</span><span class="sxs-lookup"><span data-stu-id="6b9ce-105">To define an enumeration type, use the `enum` keyword and specify the names of *enum members*:</span></span>

```csharp
enum Season
{
    Spring,
    Summer,
    Autumn,
    Winter
}
```

<span data-ttu-id="6b9ce-106">Ve výchozím nastavení jsou přidružené konstantní hodnoty členů výčtu typu `int`; začínají nulou a zvyšují se o jednu z následujících hodnot podle pořadí textu definice.</span><span class="sxs-lookup"><span data-stu-id="6b9ce-106">By default, the associated constant values of enum members are of type `int`; they start with zero and increase by one following the definition text order.</span></span> <span data-ttu-id="6b9ce-107">Můžete explicitně zadat jakýkoli jiný [integrální číselný](integral-numeric-types.md) typ jako nadřízený typ výčtového typu.</span><span class="sxs-lookup"><span data-stu-id="6b9ce-107">You can explicitly specify any other [integral numeric](integral-numeric-types.md) type as an underlying type of an enumeration type.</span></span> <span data-ttu-id="6b9ce-108">Můžete také explicitně zadat přidružené konstantní hodnoty, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="6b9ce-108">You also can explicitly specify the associated constant values, as the following example shows:</span></span>

```csharp
enum ErrorCode : ushort
{
    None = 0,
    Unknown = 1,
    ConnectionLost = 100,
    OutlierReading = 200
}
```

<span data-ttu-id="6b9ce-109">V definici typu výčtu nelze definovat metodu.</span><span class="sxs-lookup"><span data-stu-id="6b9ce-109">You cannot define a method inside the definition of an enumeration type.</span></span> <span data-ttu-id="6b9ce-110">Chcete-li přidat funkci do výčtového typu, vytvořte [metodu rozšíření](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="6b9ce-110">To add functionality to an enumeration type, create an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

<span data-ttu-id="6b9ce-111">Výchozí hodnota typu výčtu `E` je hodnota vytvořená výrazem `(E)0`, i když nula nemá odpovídajícího člena výčtu.</span><span class="sxs-lookup"><span data-stu-id="6b9ce-111">The default value of an enumeration type `E` is the value produced by expression `(E)0`, even if zero doesn't have the corresponding enum member.</span></span>

<span data-ttu-id="6b9ce-112">Typ výčtu můžete použít k reprezentaci výběru ze sady vzájemně se vylučujících hodnot nebo kombinací možností.</span><span class="sxs-lookup"><span data-stu-id="6b9ce-112">You use an enumeration type to represent a choice from a set of mutually exclusive values or a combination of choices.</span></span> <span data-ttu-id="6b9ce-113">Pro reprezentaci kombinace voleb Definujte typ výčtu jako bitové příznaky.</span><span class="sxs-lookup"><span data-stu-id="6b9ce-113">To represent a combination of choices, define an enumeration type as bit flags.</span></span>

## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="6b9ce-114">Výčtové typy jako bitové příznaky</span><span class="sxs-lookup"><span data-stu-id="6b9ce-114">Enumeration types as bit flags</span></span>

<span data-ttu-id="6b9ce-115">Chcete-li, aby typ výčtu představoval kombinaci možností, definujte členy výčtu pro tyto možnosti tak, aby jednotlivá volba byla bitového pole.</span><span class="sxs-lookup"><span data-stu-id="6b9ce-115">If you want an enumeration type to represent a combination of choices, define enum members for those choices such that an individual choice is a bit field.</span></span> <span data-ttu-id="6b9ce-116">To znamená, že přidružené hodnoty těchto členů výčtu by měly být mocninou dvou.</span><span class="sxs-lookup"><span data-stu-id="6b9ce-116">That is, the associated values of those enum members should be the powers of two.</span></span> <span data-ttu-id="6b9ce-117">Pak můžete použít [bitové logické operátory `|` nebo `&`](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) k kombinování voleb nebo průsečíku kombinací voleb v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="6b9ce-117">Then, you can use the [bitwise logical operators `|` or `&`](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) to combine choices or intersect combinations of choices, respectively.</span></span> <span data-ttu-id="6b9ce-118">Chcete-li označit, že typ výčtu deklaruje bitová pole, použijte atribut [Flags](xref:System.FlagsAttribute) na něj.</span><span class="sxs-lookup"><span data-stu-id="6b9ce-118">To indicate that an enumeration type declares bit fields, apply the [Flags](xref:System.FlagsAttribute) attribute to it.</span></span> <span data-ttu-id="6b9ce-119">Jak ukazuje následující příklad, můžete také zahrnout některé typické kombinace v definici výčtového typu.</span><span class="sxs-lookup"><span data-stu-id="6b9ce-119">As the following example shows, you also can include some typical combinations in the definition of an enumeration type.</span></span>

[!code-csharp[enum flags](~/samples/snippets/csharp/language-reference/builtin-types/EnumType.cs#Flags)]

<span data-ttu-id="6b9ce-120">Další informace a příklady najdete na stránce s referenčními informacemi k rozhraní <xref:System.FlagsAttribute?displayProperty=nameWithType> API a v části [atributu flags](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) na referenční stránce rozhraní API <xref:System.Enum?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6b9ce-120">For more information and examples, see the <xref:System.FlagsAttribute?displayProperty=nameWithType> API reference page and the [Non-exclusive members and the Flags attribute](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) section of the <xref:System.Enum?displayProperty=nameWithType> API reference page.</span></span>

## <a name="the-systemenum-type-and-enum-constraint"></a><span data-ttu-id="6b9ce-121">Typ System. Enum a omezení výčtu</span><span class="sxs-lookup"><span data-stu-id="6b9ce-121">The System.Enum type and enum constraint</span></span>

<span data-ttu-id="6b9ce-122">Typ <xref:System.Enum?displayProperty=nameWithType> je abstraktní základní třída všech typů výčtu.</span><span class="sxs-lookup"><span data-stu-id="6b9ce-122">The <xref:System.Enum?displayProperty=nameWithType> type is the abstract base class of all enumeration types.</span></span> <span data-ttu-id="6b9ce-123">Poskytuje několik metod pro získání informací o typu výčtu a jeho hodnotách.</span><span class="sxs-lookup"><span data-stu-id="6b9ce-123">It provides a number of methods to get information about an enumeration type and its values.</span></span> <span data-ttu-id="6b9ce-124">Další informace a příklady najdete na stránce s referenčními informacemi k rozhraní <xref:System.Enum?displayProperty=nameWithType> API.</span><span class="sxs-lookup"><span data-stu-id="6b9ce-124">For more information and examples, see the <xref:System.Enum?displayProperty=nameWithType> API reference page.</span></span>

<span data-ttu-id="6b9ce-125">Počínaje C# 7,3 můžete použít `System.Enum` v omezení základní třídy (označované jako [omezení výčtu](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)), chcete-li určit, že parametr typu je výčtový typ.</span><span class="sxs-lookup"><span data-stu-id="6b9ce-125">Beginning with C# 7.3, you can use `System.Enum` in a base class constraint (that is known as the [enum constraint](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)) to specify that a type parameter is an enumeration type.</span></span>

## <a name="conversions"></a><span data-ttu-id="6b9ce-126">Převody</span><span class="sxs-lookup"><span data-stu-id="6b9ce-126">Conversions</span></span>

<span data-ttu-id="6b9ce-127">Pro jakýkoliv typ výčtu existují explicitní převody mezi výčtovým typem a jeho základním integrálním typem.</span><span class="sxs-lookup"><span data-stu-id="6b9ce-127">For any enumeration type, there exist explicit conversions between the enumeration type and its underlying integral type.</span></span> <span data-ttu-id="6b9ce-128">Pokud [přetypování](../operators/type-testing-and-cast.md#cast-operator-) hodnoty výčtu na svůj nadřízený typ, je výsledkem přidružená celočíselná hodnota člena výčtu.</span><span class="sxs-lookup"><span data-stu-id="6b9ce-128">If you [cast](../operators/type-testing-and-cast.md#cast-operator-) an enum value to its underlying type, the result is the associated integral value of an enum member.</span></span>

[!code-csharp[enum conversions](~/samples/snippets/csharp/language-reference/builtin-types/EnumType.cs#Conversions)]

<span data-ttu-id="6b9ce-129">Použijte metodu <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> k určení, zda typ výčtu obsahuje člena výčtu s určitou přidruženou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="6b9ce-129">Use the <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> method to determine whether an enumeration type contains an enum member with the certain associated value.</span></span>

<span data-ttu-id="6b9ce-130">Pro jakýkoliv typ výčtu existují převody [zabalení a rozbalení](../../programming-guide/types/boxing-and-unboxing.md) do a z typu <xref:System.Enum?displayProperty=nameWithType> v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="6b9ce-130">For any enumeration type, there exist [boxing and unboxing](../../programming-guide/types/boxing-and-unboxing.md) conversions to and from the <xref:System.Enum?displayProperty=nameWithType> type, respectively.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6b9ce-131">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6b9ce-131">C# language specification</span></span>

<span data-ttu-id="6b9ce-132">Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="6b9ce-132">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="6b9ce-133">Výčty</span><span class="sxs-lookup"><span data-stu-id="6b9ce-133">Enums</span></span>](~/_csharplang/spec/enums.md)
- [<span data-ttu-id="6b9ce-134">Výčtové hodnoty a operace</span><span class="sxs-lookup"><span data-stu-id="6b9ce-134">Enum values and operations</span></span>](~/_csharplang/spec/enums.md#enum-values-and-operations)
- [<span data-ttu-id="6b9ce-135">Logické operátory výčtu</span><span class="sxs-lookup"><span data-stu-id="6b9ce-135">Enumeration logical operators</span></span>](~/_csharplang/spec/expressions.md#enumeration-logical-operators)
- [<span data-ttu-id="6b9ce-136">Operátory porovnání výčtu</span><span class="sxs-lookup"><span data-stu-id="6b9ce-136">Enumeration comparison operators</span></span>](~/_csharplang/spec/expressions.md#enumeration-comparison-operators)
- [<span data-ttu-id="6b9ce-137">Explicitní převody výčtu</span><span class="sxs-lookup"><span data-stu-id="6b9ce-137">Explicit enumeration conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-enumeration-conversions)
- [<span data-ttu-id="6b9ce-138">Implicitní převody výčtu</span><span class="sxs-lookup"><span data-stu-id="6b9ce-138">Implicit enumeration conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-enumeration-conversions)

## <a name="see-also"></a><span data-ttu-id="6b9ce-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b9ce-139">See also</span></span>

- [<span data-ttu-id="6b9ce-140">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="6b9ce-140">C# reference</span></span>](../index.md)
- [<span data-ttu-id="6b9ce-141">Řetězce formátu výčtu</span><span class="sxs-lookup"><span data-stu-id="6b9ce-141">Enumeration format strings</span></span>](../../../standard/base-types/enumeration-format-strings.md)
- [<span data-ttu-id="6b9ce-142">Pokyny pro návrh – návrh výčtu</span><span class="sxs-lookup"><span data-stu-id="6b9ce-142">Design guidelines - Enum design</span></span>](../../../standard/design-guidelines/enum.md)
- [<span data-ttu-id="6b9ce-143">Pokyny pro návrh – zásady vytváření názvů výčtu</span><span class="sxs-lookup"><span data-stu-id="6b9ce-143">Design guidelines - Enum naming conventions</span></span>](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
- [<span data-ttu-id="6b9ce-144">příkaz switch</span><span class="sxs-lookup"><span data-stu-id="6b9ce-144">switch statement</span></span>](../keywords/switch.md)
