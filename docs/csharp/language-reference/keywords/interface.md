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
# <a name="no-loc-textinterface-c-reference"></a>:::no-loc text="interface"::: (Referenční dokumentace jazyka C#)

Rozhraní definuje kontrakt. Jakýkoli [`class`](class.md) nebo [`struct`](../builtin-types/struct.md) , který implementuje daný kontrakt, musí poskytnout implementaci členů definovaných v rozhraní. Počínaje jazykem C# 8,0 může rozhraní definovat výchozí implementaci pro členy. Může také definovat členy, aby [`static`](static.md) poskytovaly jednu implementaci pro běžné funkce.

V následujícím příkladu musí třída `ImplementationClass` implementovat metodu s názvem `SampleMethod`, která nemá žádné parametry a vrací `void`.

Další informace a příklady naleznete v tématu [rozhraní](../../programming-guide/interfaces/index.md).

## <a name="example"></a>Příklad

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

Rozhraní může být členem oboru názvů nebo třídy. Deklarace rozhraní může obsahovat deklarace (signatury bez implementace) následujících členů:

- [Metody](../../programming-guide/classes-and-structs/methods.md)
- [Vlastnosti](../../programming-guide/classes-and-structs/using-properties.md)
- [Indexery](../../programming-guide/indexers/using-indexers.md)
- [Události](event.md)

Předchozí deklarace členů obvykle neobsahují tělo. Počínaje jazykem C# 8,0 může člen rozhraní deklarovat tělo. Tato metoda se nazývá *Výchozí implementace*. Členové s orgány umožňují, aby rozhraní poskytovalo "výchozí" implementaci pro třídy a struktury, které neposkytují přepisující implementaci. Kromě toho, počínaje C# 8,0, může rozhraní zahrnovat:

- [Konstanty](const.md)
- [Operátory](../operators/operator-overloading.md)
- [Statický konstruktor](../../programming-guide/classes-and-structs/constructors.md#static-constructors).
- [Vnořené typy](../../programming-guide/classes-and-structs/nested-types.md)
- [Statická pole, metody, vlastnosti, indexery a události](static.md)
- Deklarace členů pomocí explicitní syntaxe implementace rozhraní.
- Explicitní modifikátory přístupu (výchozí přístup je [`public`](access-modifiers.md) ).

Rozhraní nemůžou obsahovat stav instance. Zatímco statická pole jsou nyní povolena, pole instance nejsou v rozhraních povolena. [Automatické vlastnosti instance](../../programming-guide/classes-and-structs/auto-implemented-properties.md) nejsou v rozhraních podporované, protože by implicitně deklarovaly skryté pole. Toto pravidlo má jemný efekt pro deklarace vlastností. V deklaraci rozhraní následující kód nedeklaruje automaticky implementovanou vlastnost, která je v `class` nebo `struct` . Místo toho deklaruje vlastnost, která nemá výchozí implementaci, ale musí být implementována v jakémkoli typu, který implementuje rozhraní:

```csharp
public interface INamed
{
  public string Name {get; set;}
}
```

Rozhraní může dědit z jednoho nebo více základních rozhraní. Když rozhraní [přepisuje metodu](override.md) implementovanou v základním rozhraní, musí použít [explicitní syntaxi implementace rozhraní](../../programming-guide/interfaces/explicit-interface-implementation.md) .

Jestliže seznam základních typů obsahuje základní třídu a rozhraní, musí se základní třída nacházet v seznamu jako první.

Třída, která implementuje rozhraní, může explicitně implementovat členy rozhraní. Explicitně implementovaný člen není přístupný prostřednictvím instance třídy, ale pouze prostřednictvím instance rozhraní. Kromě toho mohou být k výchozím členům rozhraní přicházet pouze prostřednictvím instance rozhraní.

Další informace o explicitní implementaci rozhraní naleznete v tématu [explicitní implementace rozhraní](../../programming-guide/interfaces/explicit-interface-implementation.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje implementaci rozhraní. V tomto příkladu obsahuje rozhraní deklaraci vlastnosti a třída obsahuje implementaci. Jakákoli instance třídy, která implementuje rozhraní `IPoint`, má celočíselné vlastnosti `x` a `y`.

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [rozhraní](~/_csharplang/spec/interfaces.md) [specifikace jazyka C#](~/_csharplang/spec/introduction.md) a specifikace funkce pro [výchozí členy rozhraní – C# 8,0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Typy odkazů](reference-types.md)
- [Rozhraní](../../programming-guide/interfaces/index.md)
- [Použití vlastností](../../programming-guide/classes-and-structs/using-properties.md)
- [Použití indexerů](../../programming-guide/indexers/using-indexers.md)
