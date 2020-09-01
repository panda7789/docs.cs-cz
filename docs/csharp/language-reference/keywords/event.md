---
description: Event – Referenční dokumentace jazyka C#
title: Event – Referenční dokumentace jazyka C#
ms.date: 07/20/2015
f1_keywords:
- event
- remove
- event_CSharpKeyword
- add
helpviewer_keywords:
- event keyword [C#]
ms.assetid: 7858fd85-153b-4259-85d0-6aa13c35f174
ms.openlocfilehash: 5e75fec12390cb694126c5bec684c40caa378915
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139096"
---
# <a name="event-c-reference"></a>Event (Referenční dokumentace jazyka C#)

`event`Klíčové slovo slouží k deklaraci události ve třídě vydavatele.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak deklarovat a vyvolat událost, která používá <xref:System.EventHandler> jako nadřízený typ delegátu. Úplný příklad kódu, který ukazuje, jak použít <xref:System.EventHandler%601> Typ obecného delegáta a jak se přihlásit k odběru události a vytvořit metodu obslužné rutiny události, najdete v tématu [Jak publikovat události, které jsou v souladu s pokyny pro .NET Framework](../../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).

[!code-csharp[csrefKeywordsModifiers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#7)]

Události jsou speciálním druhem delegáta vícesměrového vysílání, který lze volat pouze z třídy nebo struktury, kde jsou deklarovány (třída vydavatele). Pokud se jiné třídy nebo struktury přihlásí k odběru události, jejich metody obslužné rutiny události budou volány, když třída vydavatele vyvolá událost. Další informace a příklady kódu naleznete v tématu [události](../../programming-guide/events/index.md) a [Delegáti](../../programming-guide/delegates/index.md).

Události se dají označit jako [veřejné](./public.md), [privátní](./private.md), [chráněné](./protected.md), [interní](./internal.md), [chráněné interní](./protected-internal.md)nebo [soukromé chráněné](./private-protected.md). Tyto modifikátory přístupu definují, jak mohou uživatelé třídy přistupovat k události. Další informace najdete v tématu [modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md).

## <a name="keywords-and-events"></a>Klíčová slova a události

Následující klíčová slova platí pro události.

|Klíčové slovo|Popis|Další informace|
|-------------|-----------------|--------------------------|
|[static](./static.md)|Zpřístupňuje událost volajícím kdykoli, i když žádná instance třídy neexistuje.|[Statické třídy a jejich členové](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|
|[virtual](./virtual.md)|Umožňuje odvozeným třídám přepsat chování události pomocí klíčového slova [override](./override.md) .|[Dědičnost](../../programming-guide/classes-and-structs/inheritance.md)|
|[sealed](./sealed.md)|Určuje, že pro odvozené třídy už není virtuální.||
|[Výtah](./abstract.md)|Kompilátor negeneruje `add` bloky pro přístup k `remove` událostem a proto odvozené třídy musí poskytovat svou vlastní implementaci.||

Událost může být deklarována jako statická událost pomocí klíčového slova [static](./static.md) . Tím se událost zpřístupní volajícím kdykoli, i když žádná instance třídy neexistuje. Další informace naleznete v tématu [statické třídy a statické členy třídy](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).

Událost může být označena jako virtuální událost pomocí klíčového slova [Virtual](./virtual.md) . To umožňuje odvozeným třídám přepsat chování události pomocí klíčového slova [override](./override.md) . Další informace najdete v tématu [Dědičnost](../../programming-guide/classes-and-structs/inheritance.md). Událost přepsání virtuální události může být také [zapečetěna](./sealed.md), což určuje, že pro odvozené třídy již není virtuální. Nakonec může být událost deklarovaná jako [abstraktní](./abstract.md), což znamená, že kompilátor negeneruje `add` `remove` bloky přistupujícího objektu a události. Proto odvozené třídy musí poskytovat svou vlastní implementaci.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](./index.md)
- [add](./add.md)
- [odebrány](./remove.md)
- [Modifikátory](index.md)
- [Postup kombinování delegátů (Delegáti vícesměrového vysílání)](../../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
