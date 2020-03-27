---
title: Typy struktur – odkaz jazyka C#
ms.date: 03/26/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 6a2c97b93a8f6d1d62bd8a96865a4fe6587f55d3
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345133"
---
# <a name="structure-types-c-reference"></a>Typy struktur (odkaz C#

*Typ struktury* (nebo *typ struktury*) je [typ hodnoty,](value-types.md) který může zapouzdřit data a související funkce. `struct` Klíčové slovo slouží k definování typu struktury:

[!code-csharp[struct example](snippets/StructType.cs#StructExample)]

Typy struktur mají *hodnotu sémantiku*. To znamená, že proměnná typu struktury obsahuje instanci typu. Ve výchozím nastavení jsou hodnoty proměnných zkopírovány při přiřazení, předání argumentu metodě a vrácení výsledku metody. V případě proměnné typu struktura je zkopírována instance typu. Další informace naleznete v [tématu Value types](value-types.md).

Obvykle se používají typy struktury k návrhu malé typy zaměřené na data, které poskytují malé nebo žádné chování. Například .NET používá typy struktury představují číslo [(celé číslo](integral-numeric-types.md) i [skutečné](floating-point-numeric-types.md)), [logická hodnota](bool.md), [znak Unicode](char.md), [instance time](xref:System.DateTime). Pokud se zaměřujete na chování typu, zvažte definování [třídy](../keywords/class.md). Typy tříd mají *referenční sémantiku*. To znamená, že proměnná typu třídy obsahuje odkaz na instanci typu, nikoli samotnou instanci.

Vzhledem k tomu, že typy struktur mají hodnotovou sémantiku, doporučujeme definovat *neměnné* typy struktur.

## <a name="readonly-struct"></a>`readonly`Struct

Počínaje C# 7.2, pomocí `readonly` modifikátoru deklarovat, že typ struktury je neměnný:

[!code-csharp[readonly struct](snippets/StructType.cs#ReadonlyStruct)]

Všechny datové členy `readonly` struktury musí být jen pro čtení takto:

- Každá deklarace pole musí mít [ `readonly` modifikátor.](../keywords/readonly.md)
- Každá vlastnost, včetně automaticky implementovaných, musí být jen pro čtení

To zaručuje, že žádný `readonly` člen struktury modifikuje stav struktury.

> [!NOTE]
> Ve `readonly` struktuře může datový člen proměnlivého typu odkazu stále zmutovat svůj vlastní stav. Například nelze nahradit <xref:System.Collections.Generic.List%601> instanci, ale můžete do ní přidat nové prvky.

## <a name="limitations-with-the-design-of-a-structure-type"></a>Omezení s návrhem typu konstrukce

Při návrhu typu struktury máte stejné možnosti jako u typu [třídy,](../keywords/class.md) s následujícími výjimkami:

- Nelze deklarovat konstruktor bez parametrů. Každý typ struktury již poskytuje implicitní konstruktor bez parametrů, který vytváří [výchozí hodnotu](default-values.md) typu.

- Pole nebo vlastnost instance nelze inicializovat v jeho deklaraci. Můžete však inicializovat [statické](../keywords/static.md) nebo [const](../keywords/const.md) pole nebo statické vlastnosti na jeho deklaraci.

- Konstruktor typu struktury musí inicializovat všechna pole instance typu.

- Typ struktury nemůže dědit z jiné třídy nebo typu struktury a nemůže být základem třídy. Typ struktury však může implementovat [rozhraní](../keywords/interface.md).

- Finizarant [finalizer](../../programming-guide/classes-and-structs/destructors.md) nelze deklarovat v rámci typu struktury.

## <a name="instantiation-of-a-structure-type"></a>Vytvoření instance typu struktury

V C# je nutné inicializovat deklarované proměnné před ji lze použít. Vzhledem k tomu, `null` že proměnná typu struktury nemůže být (pokud se nejedná o proměnnou [typu hodnoty s možnou hodnotou s možnou hodnotou),](nullable-value-types.md)je nutné vytvořit instanci odpovídajícího typu. Existuje několik způsobů, jak to udělat.

Obvykle konsitujete typ struktury voláním příslušného [`new`](../operators/new-operator.md) konstruktoru s operátorem. Každý typ struktury má alespoň jeden konstruktor. To je implicitní konstruktor bez parametrů, který vytváří [výchozí hodnotu](default-values.md) typu. Výchozí [výraz hodnoty](../operators/default.md) můžete také použít k vytvoření výchozí hodnoty typu.

Pokud jsou přístupná všechna pole instance typu struktury, můžete ji `new` také vytvořit bez operátora. V takovém případě je nutné inicializovat všechna pole instance před prvním použitím instance. Následující příklad ukazuje, jak to udělat:

[!code-csharp[without new](snippets/StructType.cs#WithoutNew)]

V případě [předdefinovaných typů hodnot](value-types.md#built-in-value-types)použijte odpovídající literály k určení hodnoty typu.

## <a name="passing-structure-type-variables-by-reference"></a>Předávání proměnných typu struktury odkazem

Když předáte proměnnou typu struktury metodě jako argument nebo vrátíte hodnotu typu struktury z metody, zkopíruje se celá instance typu struktury. To může ovlivnit výkon kódu ve scénářích s vysokým výkonem, které zahrnují velké typy struktur. Kopírování hodnot se můžete vyhnout předáním proměnné typu struktury odkazem. Modifikátory parametrů [`ref`](../keywords/ref.md#passing-an-argument-by-reference), [`out`](../keywords/out-parameter-modifier.md)nebo [`in`](../keywords/in-parameter-modifier.md) metody označují, že argument musí být předán odkazem. Použijte [ref vrátí](../../programming-guide/classes-and-structs/ref-returns.md) výsledek metody odkazem. Další informace naleznete v [tématu Zápis bezpečné a efektivní kód jazyka C#](../../write-safe-efficient-code.md).

## <a name="conversions"></a>Převody

Pro všechny typy struktury existují [převody zabalení a rozbalení](../../programming-guide/types/boxing-and-unboxing.md) do a z <xref:System.ValueType?displayProperty=nameWithType> <xref:System.Object?displayProperty=nameWithType> a typy. Existují také zabalení a rozbalení převody mezi typ struktury a rozhraní, které implementuje.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [Structs](~/_csharplang/spec/structs.md) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

Další informace `readonly` o strukturách naleznete v [poznámce k návrhu funkce](~/_csharplang/proposals/csharp-7.2/readonly-ref.md#readonly-structs).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Pokyny pro návrh - Výběr mezi třídou a strukturou](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [Pokyny pro návrh - Design Struct](../../../standard/design-guidelines/struct.md)
- [Třídy a struktury](../../programming-guide/classes-and-structs/index.md)
