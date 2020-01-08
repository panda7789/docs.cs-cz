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
ms.openlocfilehash: 72bc867bf0a789279da9a01f97c85d96b78684ed
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75444345"
---
# <a name="enumeration-types-c-reference"></a>Výčtové typyC# (referenční)

Výčtový typ (nebo typ výčtu) je typ hodnoty definovaný sadou pojmenovaných konstant základního [integrálního číselného](integral-numeric-types.md) typu. Chcete-li definovat typ výčtu, použijte klíčové slovo `enum` a zadejte názvy *členů výčtu*:

```csharp
enum Season
{
    Spring,
    Summer,
    Autumn,
    Winter
}
```

Ve výchozím nastavení jsou přidružené konstantní hodnoty členů výčtu typu `int`; začínají nulou a zvyšují se o jednu z následujících hodnot podle pořadí textu definice. Můžete explicitně zadat jakýkoli jiný [integrální číselný](integral-numeric-types.md) typ jako nadřízený typ výčtového typu. Můžete také explicitně zadat přidružené konstantní hodnoty, jak ukazuje následující příklad:

```csharp
enum ErrorCode : ushort
{
    None = 0,
    Unknown = 1,
    ConnectionLost = 100,
    OutlierReading = 200
}
```

V definici typu výčtu nelze definovat metodu. Chcete-li přidat funkci do výčtového typu, vytvořte [metodu rozšíření](../../programming-guide/classes-and-structs/extension-methods.md).

Výchozí hodnota typu výčtu `E` je hodnota vytvořená výrazem `(E)0`, i když nula nemá odpovídajícího člena výčtu.

Typ výčtu můžete použít k reprezentaci výběru ze sady vzájemně se vylučujících hodnot nebo kombinací možností. Pro reprezentaci kombinace voleb Definujte typ výčtu jako bitové příznaky.

## <a name="enumeration-types-as-bit-flags"></a>Výčtové typy jako bitové příznaky

Chcete-li, aby typ výčtu představoval kombinaci možností, definujte členy výčtu pro tyto možnosti tak, aby jednotlivá volba byla bitového pole. To znamená, že přidružené hodnoty těchto členů výčtu by měly být mocninou dvou. Pak můžete použít [bitové logické operátory `|` nebo `&`](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) k kombinování voleb nebo průsečíku kombinací voleb v uvedeném pořadí. Chcete-li označit, že typ výčtu deklaruje bitová pole, použijte atribut [Flags](xref:System.FlagsAttribute) na něj. Jak ukazuje následující příklad, můžete také zahrnout některé typické kombinace v definici výčtového typu.

[!code-csharp[enum flags](~/samples/csharp/language-reference/builtin-types/EnumType.cs#Flags)]

Další informace a příklady najdete na stránce s referenčními informacemi k rozhraní <xref:System.FlagsAttribute?displayProperty=nameWithType> API a v části [atributu flags](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) na referenční stránce rozhraní API <xref:System.Enum?displayProperty=nameWithType>.

## <a name="the-systemenum-type-and-enum-constraint"></a>Typ System. Enum a omezení výčtu

Typ <xref:System.Enum?displayProperty=nameWithType> je abstraktní základní třída všech typů výčtu. Poskytuje několik metod pro získání informací o typu výčtu a jeho hodnotách. Další informace a příklady najdete na stránce s referenčními informacemi k rozhraní <xref:System.Enum?displayProperty=nameWithType> API.

Počínaje C# 7,3 můžete použít `System.Enum` v omezení základní třídy (označované jako [omezení výčtu](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)), chcete-li určit, že parametr typu je výčtový typ.

## <a name="conversions"></a>Převody

Pro jakýkoliv typ výčtu existují explicitní převody mezi výčtovým typem a jeho základním integrálním typem. Pokud [přetypování](../operators/type-testing-and-cast.md#cast-operator-) hodnoty výčtu na svůj nadřízený typ, je výsledkem přidružená celočíselná hodnota člena výčtu.

[!code-csharp[enum conversions](~/samples/csharp/language-reference/builtin-types/EnumType.cs#Conversions)]

Použijte metodu <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> k určení, zda typ výčtu obsahuje člena výčtu s určitou přidruženou hodnotou.

Pro jakýkoliv typ výčtu existují převody [zabalení a rozbalení](../../programming-guide/types/boxing-and-unboxing.md) do a z typu <xref:System.Enum?displayProperty=nameWithType> v uvedeném pořadí.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):

- [Výčty](~/_csharplang/spec/enums.md)
- [Výčtové hodnoty a operace](~/_csharplang/spec/enums.md#enum-values-and-operations)
- [Logické operátory výčtu](~/_csharplang/spec/expressions.md#enumeration-logical-operators)
- [Operátory porovnání výčtu](~/_csharplang/spec/expressions.md#enumeration-comparison-operators)
- [Explicitní převody výčtu](~/_csharplang/spec/conversions.md#explicit-enumeration-conversions)
- [Implicitní převody výčtu](~/_csharplang/spec/conversions.md#implicit-enumeration-conversions)

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Řetězce formátu výčtu](../../../standard/base-types/enumeration-format-strings.md)
- [Zásady vytváření názvů výčtu](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
- [příkaz switch](../keywords/switch.md)
