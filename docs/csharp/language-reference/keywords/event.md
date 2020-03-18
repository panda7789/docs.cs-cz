---
title: událost - Odkaz jazyka C#
ms.date: 07/20/2015
f1_keywords:
- event
- remove
- event_CSharpKeyword
- add
helpviewer_keywords:
- event keyword [C#]
ms.assetid: 7858fd85-153b-4259-85d0-6aa13c35f174
ms.openlocfilehash: eb1805ed55921497fea88e6b39989c876ef003d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713561"
---
# <a name="event-c-reference"></a>událost (odkaz C# )

Klíčové `event` slovo se používá k deklarování události ve třídě vydavatele.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak deklarovat <xref:System.EventHandler> a vyvolat událost, která se používá jako základní typ delegáta. Úplný příklad kódu, který také ukazuje, <xref:System.EventHandler%601> jak používat obecný typ delegáta a jak se přihlásit k odběru události a vytvořit metodu obslužné rutiny události, naleznete v [tématu Jak publikovat události, které odpovídají pokynům rozhraní .NET Framework](../../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).

[!code-csharp[csrefKeywordsModifiers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#7)]

Události jsou zvláštní druh delegáta vícesměrového vysílání, který lze vyvolat pouze z třídy nebo struktury, kde jsou deklarovány (třída vydavatele). Pokud jiné třídy nebo struktury přihlásit k odběru události, jejich metody obslužné rutiny události budou volány, když třída vydavatele vyvolá událost. Další informace a příklady kódu naleznete v [tématu Události](../../programming-guide/events/index.md) a [delegáti](../../programming-guide/delegates/index.md).

Události mohou být označeny jako [veřejné](./public.md), [soukromé](./private.md), [chráněné](./protected.md), [interní](./internal.md), [chráněné interní](./protected-internal.md)nebo soukromé [chráněné](./private-protected.md). Tyto modifikátory přístupu definují, jak mohou uživatelé třídy přistupovat k události. Další informace naleznete [v tématu Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).

## <a name="keywords-and-events"></a>Klíčová slova a události

Následující klíčová slova platí pro události.

|Klíčové slovo|Popis|Další informace|
|-------------|-----------------|--------------------------|
|[Statické](./static.md)|Zpřístupní událost volajícím kdykoli, i když neexistuje žádná instance třídy.|[Statické třídy a jejich členové](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|
|[virtual](./virtual.md)|Umožňuje odvozeným třídám přepsat chování události pomocí klíčového slova [přepsání.](./override.md)|[Dědičnost](../../programming-guide/classes-and-structs/inheritance.md)|
|[sealed](./sealed.md)|Určuje, že pro odvozené třídy již není virtuální.||
|[Abstraktní](./abstract.md)|Kompilátor nebude generovat `add` `remove` a události přistupující bloky a proto odvozené třídy musí poskytnout vlastní implementaci.||

Událost může být deklarována jako statická událost pomocí [statického](./static.md) klíčového slova. To zpřístupní událost volajícím kdykoli, i v případě, že neexistuje žádná instance třídy. Další informace naleznete [v tématu Statické třídy a statické členy třídy](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).

Událost může být označena jako virtuální událost pomocí [virtuálního](./virtual.md) klíčového slova. To umožňuje odvozené třídy přepsat chování události pomocí klíčového slova [přepsat.](./override.md) Další informace naleznete v [tématu Dědičnost](../../programming-guide/classes-and-structs/inheritance.md). Událost přepsání virtuální události může být také [zapečetěna](./sealed.md), což určuje, že pro odvozené třídy již není virtuální. Nakonec událost může být deklarována [abstraktní](./abstract.md), což `add` znamená, že kompilátor nebude generovat bloky přistupujícího objektu a `remove` události. Proto odvozené třídy musí poskytovat vlastní implementaci.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](./index.md)
- [Přidat](./add.md)
- [Odebrat](./remove.md)
- [Modifikátory](index.md)
- [Jak kombinovat delegáty (delegáti vícesměrového vysílání)](../../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
