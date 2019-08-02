---
title: 'Explicitní pole: Klíčové slovo Val'
description: Přečtěte si F# o klíčovém slově Val, který se používá k deklaraci umístění pro uložení hodnoty v typu třídy nebo struktury bez inicializace typu.
ms.date: 05/16/2016
ms.openlocfilehash: 13e0ba2875e8accfd1c0da0e1c6fef4973309f9b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627530"
---
# <a name="explicit-fields-the-val-keyword"></a>Explicitní pole: Klíčové slovo Val

`val` Klíčové slovo slouží k deklaraci umístění pro uložení hodnoty v typu třídy nebo struktury, aniž by bylo nutné ji inicializovat. Umístění úložiště deklarovaná tímto způsobem se nazývají *explicitní pole*. Jiné použití `val` klíčového slova je ve spojení `member` s klíčovým slovem pro deklaraci automaticky implementované vlastnosti. Další informace o automaticky implementovaných vlastnostech naleznete v tématu [Properties](properties.md).

## <a name="syntax"></a>Syntaxe

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a>Poznámky

Obvyklým způsobem, jak definovat pole v typu třídy nebo struktury, je použití `let` vazby. `let` Vazby je však nutné inicializovat jako součást konstruktoru třídy, který není vždy možný, nutný nebo žádoucí. `val` Klíčové slovo lze použít, pokud chcete pole, které není inicializováno.

Explicitní pole mohou být statická nebo nestatická. *Modifikátor přístupu* může být `public`, `private`, nebo `internal`. Ve výchozím nastavení jsou explicitní pole veřejná. To se liší od `let` vazeb ve třídách, které jsou vždy soukromé.

Atribut [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) je vyžadován v explicitních polích typu třídy, které mají primární konstruktor. Tento atribut určuje, že pole je inicializováno na nulu. Typ pole musí podporovat nulovou inicializaci. Typ podporuje nulovou inicializaci, pokud se jedná o jednu z následujících možností:

- Primitivní typ, který má nulovou hodnotu.

- Typ, který podporuje hodnotu null buď jako normální hodnotu, jako neobvyklou hodnotu, nebo jako reprezentace hodnoty. To zahrnuje třídy, řazené kolekce členů, záznamy, funkce, rozhraní, typy odkazů .NET `unit` , typ a rozlišené typy sjednocení.

- Typ hodnoty .NET.

- Struktura, jejíž pole všechny podporují výchozí nulovou hodnotu.

Například neměnné pole `someField` s názvem má v kompilované reprezentaci .NET s názvem `someField@`pole zálohování a přístup k uložené hodnotě pomocí vlastnosti s názvem `someField`.

V případě proměnlivého pole je kompilovaná reprezentace rozhraní .NET pole rozhraní .NET.

>[!WARNING]
>Obor názvů `System.ComponentModel` .NET Framework obsahuje atribut, který má stejný název. Informace o tomto atributu naleznete v tématu `System.ComponentModel.DefaultValueAttribute`.

Následující kód ukazuje použití explicitních polí a pro porovnání, `let` vazby ve třídě, která má primární konstruktor. Všimněte si, `let`že pole `myInt1` svázané je soukromé. Při odkazování na `let`pole `myInt1` vázané z členské metody není identifikátor `this` držitele vyžadován. Ale když odkazujete na explicitní pole `myInt2` a `myString`, je požadován identifikátor autotest.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

Výstup je následující:

```
11 12 abc
30 def
```

Následující kód ukazuje použití explicitních polí ve třídě, která nemá primární konstruktor. V tomto případě `DefaultValue` není atribut vyžadován, ale všechna pole musí být inicializována v konstruktorech, které jsou definovány pro daný typ.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

Výstup je `35 22`.

Následující kód ukazuje použití explicitních polí ve struktuře. Vzhledem k tomu, že struktura je hodnotový typ, má automaticky výchozí konstruktor, který nastaví hodnoty jejich polí na nulu. `DefaultValue` Proto atribut není požadován.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

Výstup je `11 xyz`.

Pokud se chystáte inicializovat strukturu s `mutable` poli bez `mutable` klíčového slova, budou vaše přiřazení fungovat na kopii struktury, která se po přiřazení zahodí hned. Proto se vaše struktura nemění.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6704.fs)]

Explicitní pole nejsou určena pro rutinové použití. Obecně platí, že pokud je to možné, `let` měli byste použít vazbu ve třídě namísto explicitního pole. Explicitní pole jsou užitečná v některých scénářích interoperability, například když potřebujete definovat strukturu, která bude použita v volání metody Invoke do nativního rozhraní API nebo ve scénářích komunikace s objekty COM. Další informace najdete v tématu [](../functions/external-functions.md)věnovaném externím funkcím. Další situací, kdy může být explicitní pole nutné, je při práci s generátorem F# kódu, který generuje třídy bez primárního konstruktoru. Explicitní pole jsou také užitečná pro proměnné vlákn-static nebo podobné konstrukce. Další informace naleznete v tématu `System.ThreadStaticAttribute`.

Když se klíčová slova `member val` zobrazí v definici typu společně, jedná se o definici automaticky implementované vlastnosti. Další informace najdete v tématu [vlastnosti](properties.md).

## <a name="see-also"></a>Viz také:

- [Vlastnosti](properties.md)
- [Členové](index.md)
- [`let`Vazby ve třídách](let-bindings-in-classes.md)
