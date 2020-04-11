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
ms.openlocfilehash: 15f5e9ccb1396277229ba935381812700f63ece8
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121159"
---
# <a name="enumeration-types-c-reference"></a>Typy výčtu (odkaz Jazyka C#)

*Typ výčtu* (nebo *typ výčtu*) je typ [hodnoty](value-types.md) definovaný sadou pojmenovaných konstant základního [integrálního číselného](integral-numeric-types.md) typu. Chcete-li definovat typ výčtu, použijte `enum` klíčové slovo a zadejte názvy členů *výčtu*:

```csharp
enum Season
{
    Spring,
    Summer,
    Autumn,
    Winter
}
```

Ve výchozím nastavení jsou přidružené konstantní hodnoty `int`členů výčtu typu ; začínají nulou a zvyšují se o jednu po pořadí definičního textu. Jako základní typ typu výčtu můžete explicitně zadat jakýkoli jiný [integrální číselný](integral-numeric-types.md) typ. Můžete také explicitně zadat přidružené konstantní hodnoty, jak ukazuje následující příklad:

```csharp
enum ErrorCode : ushort
{
    None = 0,
    Unknown = 1,
    ConnectionLost = 100,
    OutlierReading = 200
}
```

Metodu nelze definovat uvnitř definice typu výčtu. Chcete-li přidat funkce do typu výčtu, vytvořte [metodu rozšíření](../../programming-guide/classes-and-structs/extension-methods.md).

Výchozí hodnota typu `E` výčtu je hodnota vytvořená výrazem `(E)0`, i když nula nemá odpovídající výčtový člen.

Typ výčtu slouží k reprezentaci volby ze sady vzájemně se vylučujících hodnot nebo kombinace voleb. Chcete-li představovat kombinaci voleb, definujte typ výčtu jako bitové příznaky.

## <a name="enumeration-types-as-bit-flags"></a>Typy výčtu jako bitové příznaky

Pokud chcete, aby typ výčtu představoval kombinaci voleb, definujte členy výčtu pro tyto volby tak, aby individuální volba byla bitové pole. To znamená, že přidružené hodnoty těchto členů výčtu by měly být pravomoci dvou. Potom můžete použít [bitové logické `|` `&` operátory nebo](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) kombinovat volby nebo protínat kombinace voleb, v uvedeném pořadí. Chcete-li označit, že typ výčtu deklaruje bitová pole, použijte atribut [Flags.](xref:System.FlagsAttribute) Jak ukazuje následující příklad, můžete také zahrnout některé typické kombinace v definici typu výčtu.

[!code-csharp[enum flags](snippets/EnumType.cs#Flags)]

Další informace a příklady <xref:System.FlagsAttribute?displayProperty=nameWithType> naleznete na referenční stránce rozhraní API a v části [Nevýhradní členy a Atribut příznaky](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) na stránce reference <xref:System.Enum?displayProperty=nameWithType> rozhraní API.

## <a name="the-systemenum-type-and-enum-constraint"></a>Typ System.Enum a omezení výčtu

Typ <xref:System.Enum?displayProperty=nameWithType> je abstraktní základní třída všech typů výčtu. Poskytuje řadu metod pro získání informací o typu výčtu a jeho hodnotách. Další informace a příklady <xref:System.Enum?displayProperty=nameWithType> naleznete na referenční stránce rozhraní API.

Počínaje C# 7.3, můžete `System.Enum` použít v omezení základní třídy (který je známý jako [omezení výčtu)](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)určit, že parametr typu je typ výčtu.

## <a name="conversions"></a>Převody

Pro libovolný typ výčtu existují explicitní převody mezi typem výčtu a jeho základním integrálním typem. Pokud [přetypovat](../operators/type-testing-and-cast.md#cast-expression) hodnotu výčtu na jeho základní typ, výsledkem je přidružená integrální hodnota člena výčtu.

[!code-csharp[enum conversions](snippets/EnumType.cs#Conversions)]

Pomocí <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> metody určete, zda typ výčtu obsahuje člen výčtu s určitou přidruženou hodnotou.

Pro libovolný typ výčtu existují převody [zabalení a rozbalení](../../programming-guide/types/boxing-and-unboxing.md) do a z <xref:System.Enum?displayProperty=nameWithType> typu, v uvedeném pořadí.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v následujících částech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):

- [Výčty](~/_csharplang/spec/enums.md)
- [Hodnoty a operace výčtu](~/_csharplang/spec/enums.md#enum-values-and-operations)
- [Logické operátory výčtu](~/_csharplang/spec/expressions.md#enumeration-logical-operators)
- [Operátory porovnání výčtu](~/_csharplang/spec/expressions.md#enumeration-comparison-operators)
- [Explicitní převody výčtu](~/_csharplang/spec/conversions.md#explicit-enumeration-conversions)
- [Převody implicitního výčtu](~/_csharplang/spec/conversions.md#implicit-enumeration-conversions)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Vytvoření výčtu řetězců formátu](../../../standard/base-types/enumeration-format-strings.md)
- [Pokyny pro návrh - Výčet](../../../standard/design-guidelines/enum.md)
- [Pokyny pro návrh – konvence pojmenování výčtu](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
- [příkaz switch](../keywords/switch.md)
