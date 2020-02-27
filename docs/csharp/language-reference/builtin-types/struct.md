---
title: Typy struktury – C# referenční informace
ms.date: 02/24/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 6113912f176d2d7b68c77ff2e78a361b373ca31a
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634867"
---
# <a name="structure-types-c-reference"></a>Typy struktury (C# Referenční dokumentace)

*Typ struktury* (nebo *typ struktury*) je [typ hodnoty](value-types.md) , který může zapouzdřit data a související funkce. Pro definování typu struktury použijte klíčové slovo `struct`:

[!code-csharp[struct example](~/samples/csharp/language-reference/builtin-types/StructType.cs#StructExample)]

Typy struktur mají *sémantiku hodnot*. To znamená, že proměnná typu struktury obsahuje instanci typu. Ve výchozím nastavení jsou proměnné hodnoty zkopírovány při přiřazení, předání argumentu metodě a vrácení výsledku metody. V případě proměnné typu struktury je zkopírována instance typu. Další informace naleznete v tématu [typy hodnot](value-types.md).

Pro návrh malých typů orientovaných na data, které poskytují pouze malé nebo žádné chování, je obvykle používán typ struktury. Například .NET používá typy struktury k reprezentaci čísla ( [Integer](integral-numeric-types.md) i [reálné](floating-point-numeric-types.md)), [logické hodnoty](bool.md), [znaku Unicode](char.md), [instance času](xref:System.DateTime). Pokud jste se zaměřili na chování typu, zvažte definování [třídy](../keywords/class.md). Typy tříd mají *sémantiku odkazů*. To znamená, že proměnná typu třídy obsahuje odkaz na instanci typu, nikoli na samotnou instanci.

## <a name="limitations-with-the-design-of-a-structure-type"></a>Omezení s návrhem typu struktury

Při návrhu typu struktury máte stejné možnosti jako u typu [třídy](../keywords/class.md) , s následujícími výjimkami:

- Nemůžete deklarovat konstruktor bez parametrů. Každý typ struktury již poskytuje implicitní konstruktor bez parametrů, který vytváří [výchozí hodnotu](default-values.md) typu.

- V deklaraci nelze inicializovat pole nebo vlastnost instance. V deklaraci ale můžete inicializovat [statické](../keywords/static.md) nebo [konstantní](../keywords/const.md) pole nebo statickou vlastnost.

- Konstruktor typu struktury musí inicializovat všechna pole instance daného typu.

- Typ struktury nemůže dědit z jiné třídy nebo typu struktury a nemůže být základem třídy. Typ struktury však může implementovat [rozhraní](../keywords/interface.md).

- Nelze deklarovat [finalizační metodu](../../programming-guide/classes-and-structs/destructors.md) v rámci typu struktury.

## <a name="instantiation-of-a-structure-type"></a>Vytvoření instance typu struktury

V C#nástroji je nutné inicializovat deklarovanou proměnnou předtím, než bude možné ji použít. Vzhledem k tomu, že proměnná typu Struktura nemůže být `null` (Pokud se nejedná o proměnnou [typu hodnoty s možnou hodnotou null](nullable-value-types.md)), je nutné vytvořit instanci odpovídajícího typu. To lze provést několika způsoby.

Obvykle vytváříte instanci typu struktury voláním vhodného konstruktoru s operátorem [`new`](../operators/new-operator.md) . Každý typ struktury má alespoň jeden konstruktor. To je implicitní konstruktor bez parametrů, který vytváří [výchozí hodnotu](default-values.md) typu. Můžete také použít [výchozí](../operators/default.md) operátor nebo literál pro vytvoření výchozí hodnoty typu.

Pokud jsou všechna pole instance typu struktury dostupná, můžete také vytvořit instanci bez operátoru `new`. V takovém případě je nutné inicializovat všechna pole instance před prvním použitím instance. Následující příklad ukazuje, jak to provést:

[!code-csharp[without new](~/samples/csharp/language-reference/builtin-types/StructType.cs#WithoutNew)]

V případě [předdefinovaných hodnotových typů](value-types.md#built-in-value-types)použijte odpovídající literály k určení hodnoty typu.

## <a name="passing-structure-type-variables-by-reference"></a>Předávání proměnných typu struktury podle odkazu

Pokud předáte proměnnou typu struktury do metody jako argument nebo vrátíte hodnotu typu struktury z metody, je zkopírována celá instance typu struktury. To může mít vliv na výkon vašeho kódu ve scénářích s vysokým výkonem, které zahrnují typy velkých struktur. Kopírování hodnot se můžete vyhnout předáním proměnné typu struktury odkazem. Použijte modifikátory parametrů [`ref`](../keywords/ref.md#passing-an-argument-by-reference), [`out`](../keywords/out-parameter-modifier.md)nebo [`in`](../keywords/in-parameter-modifier.md) , abyste označili, že argument musí být předán odkazem. Pomocí [funkce ref](../../programming-guide/classes-and-structs/ref-returns.md) Return můžete vrátit výsledek metody odkazem. Další informace najdete v tématu [Zápis bezpečného a C# efektivního kódu](../../write-safe-efficient-code.md).

## <a name="conversions"></a>Převody

Pro jakýkoliv typ struktury existují převody [zabalení a rozbalení](../../programming-guide/types/boxing-and-unboxing.md) z <xref:System.ValueType?displayProperty=nameWithType> a <xref:System.Object?displayProperty=nameWithType> typů. Existují také převody zabalení a rozbalení mezi typem struktury a jakýmkoli rozhraním, které implementuje.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v oddílu [struktury](~/_csharplang/spec/structs.md) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [C#odkaz](../index.md)
- [Pokyny pro návrh – výběr mezi třídou a strukturou](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [Pokyny pro návrh – návrh struktury](../../../standard/design-guidelines/struct.md)
- [Třídy a struktury](../../programming-guide/classes-and-structs/index.md)
