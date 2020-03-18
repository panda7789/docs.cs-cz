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
# <a name="no-loc-textinterface-c-reference"></a>:::no-loc text="interface":::(Odkaz na C#)

Rozhraní definuje smlouvu. Každý [`class`](class.md) [`struct`](../builtin-types/struct.md) nebo, který implementuje tuto smlouvu musí poskytnout implementaci členů definovaných v rozhraní. Počínaje C# 8.0 rozhraní může definovat výchozí implementaci pro členy. Může také [`static`](static.md) definovat členy za účelem poskytnutí jediné implementace pro společné funkce.

V následujícím příkladu musí třída `ImplementationClass` implementovat metodu s názvem `SampleMethod`, která nemá žádné parametry a vrací `void`.

Další informace a příklady naleznete v [tématu Rozhraní](../../programming-guide/interfaces/index.md).

## <a name="example"></a>Příklad

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

Rozhraní může být členem oboru názvů nebo třídy. Deklarace rozhraní může obsahovat deklarace (podpisy bez jakékoli implementace) následujících členů:

- [Metody](../../programming-guide/classes-and-structs/methods.md)
- [Vlastnosti](../../programming-guide/classes-and-structs/using-properties.md)
- [Indexery](../../programming-guide/indexers/using-indexers.md)
- [Akce](event.md)

Tyto předchozí deklarace členů obvykle neobsahují tělo. Počínaje C# 8.0, člen rozhraní může deklarovat tělo. To se nazývá *výchozí implementace*. Členové s orgány povolit rozhraní poskytnout "výchozí" implementace pro třídy a struktury, které neposkytují přepsání implementace. Kromě toho počínaje C# 8.0 rozhraní může zahrnovat:

- [Konstanty](const.md)
- [Operátory](../operators/operator-overloading.md)
- [Statický konstruktor](../../programming-guide/classes-and-structs/constructors.md#static-constructors).
- [Vnořené typy](../../programming-guide/classes-and-structs/nested-types.md)
- [Statická pole, metody, vlastnosti, indexery a události](static.md)
- Deklarace členů pomocí syntaxe implementace explicitnírozhraní.
- Explicitní modifikátory přístupu [`public`](access-modifiers.md)(výchozí přístup je ).

Rozhraní nesmí obsahovat stav instance. Zatímco statická pole jsou nyní povolena, pole instancí nejsou povolena v rozhraních. [Automatické vlastnosti instance](../../programming-guide/classes-and-structs/auto-implemented-properties.md) nejsou v rozhraních podporovány, protože by implicitně deklarovaly skryté pole. Toto pravidlo má jemný vliv na deklarace vlastností. V deklaraci rozhraní následující kód nedeklaruje automaticky implementované `class` `struct`vlastnosti, jak to dělá v nebo . Místo toho deklaruje vlastnost, která nemá výchozí implementaci, ale musí být implementována v libovolném typu, který implementuje rozhraní:

```csharp
public interface INamed
{
  public string Name {get; set;}
}
```

Rozhraní může dědit z jednoho nebo více základních rozhraní. Když rozhraní [přepíše metodu](override.md) implementovanou v základním rozhraní, musí použít syntaxi [implementace explicitní rozhraní.](../../programming-guide/interfaces/explicit-interface-implementation.md)

Jestliže seznam základních typů obsahuje základní třídu a rozhraní, musí se základní třída nacházet v seznamu jako první.

Třída, která implementuje rozhraní, může explicitně implementovat členy rozhraní. Explicitně implementovaný člen není přístupný prostřednictvím instance třídy, ale pouze prostřednictvím instance rozhraní. Kromě toho výchozí členy rozhraní lze přistupovat pouze prostřednictvím instance rozhraní.

Další informace o explicitní implementaci rozhraní naleznete [v tématu Explicitní implementace rozhraní](../../programming-guide/interfaces/explicit-interface-implementation.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje implementaci rozhraní. V tomto příkladu obsahuje rozhraní deklaraci vlastnosti a třída obsahuje implementaci. Jakákoli instance třídy, která implementuje rozhraní `IPoint`, má celočíselné vlastnosti `x` a `y`.

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [Rozhraní](~/_csharplang/spec/interfaces.md) [specifikace jazyka C#](~/_csharplang/spec/introduction.md) a specifikace funkce pro výchozí členy rozhraní - [C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [Odkazové typy](reference-types.md)
- [Rozhraní](../../programming-guide/interfaces/index.md)
- [Použití vlastností](../../programming-guide/classes-and-structs/using-properties.md)
- [Použití indexerů](../../programming-guide/indexers/using-indexers.md)
- [Rozhraní](../../programming-guide/interfaces/index.md)
