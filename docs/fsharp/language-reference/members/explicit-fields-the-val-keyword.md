---
title: 'Explicitní pole: klíčové slovo Val'
description: Přečtěte si F# o klíčovém slově Val, který se používá k deklaraci umístění pro uložení hodnoty v typu třídy nebo struktury bez inicializace typu.
ms.date: 05/16/2016
ms.openlocfilehash: 2703d9a2734cfda1614a401ec24c6630ec31b2f1
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736837"
---
# <a name="explicit-fields-the-val-keyword"></a>Explicitní pole: klíčové slovo Val

Klíčové slovo `val` slouží k deklaraci umístění pro uložení hodnoty v typu třídy nebo struktury, aniž by bylo nutné ji inicializovat. Umístění úložiště deklarovaná tímto způsobem se nazývají *explicitní pole*. Jiné použití klíčového slova `val` je ve spojení s klíčovým slovem `member` pro deklaraci automaticky implementované vlastnosti. Další informace o automaticky implementovaných vlastnostech naleznete v tématu [Properties](properties.md).

## <a name="syntax"></a>Syntaxe

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a>Poznámky

Obvyklým způsobem, jak definovat pole v typu třídy nebo struktury, je použití vazby `let`. Vazby `let` však musí být inicializovány jako součást konstruktoru třídy, který není vždy možný, nutný nebo žádoucí. Klíčové slovo `val` můžete použít, pokud chcete pole, které není inicializováno.

Explicitní pole mohou být statická nebo nestatická. *Modifikátor přístupu* může být `public`, `private` nebo `internal`. Ve výchozím nastavení jsou explicitní pole veřejná. To se liší od vazeb `let` ve třídách, které jsou vždy soukromé.

Atribut [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) je vyžadován v explicitních polích typu třídy, které mají primární konstruktor. Tento atribut určuje, že pole je inicializováno na nulu. Typ pole musí podporovat nulovou inicializaci. Typ podporuje nulovou inicializaci, pokud se jedná o jednu z následujících možností:

- Primitivní typ, který má nulovou hodnotu.
- Typ, který podporuje hodnotu null buď jako normální hodnotu, jako neobvyklou hodnotu, nebo jako reprezentace hodnoty. To zahrnuje třídy, řazené kolekce členů, záznamy, funkce, rozhraní, typy odkazů .NET, typ `unit` a typy rozlišených sjednocení.
- Typ hodnoty .NET.
- Struktura, jejíž pole všechny podporují výchozí nulovou hodnotu.

Například neměnné pole s názvem `someField` má v kompilované reprezentaci .NET název `someField@` a přístup k uložené hodnotě pomocí vlastnosti s názvem `someField`.

V případě proměnlivého pole je kompilovaná reprezentace rozhraní .NET pole rozhraní .NET.

> [!WARNING]
> Obor názvů .NET Framework `System.ComponentModel` obsahuje atribut, který má stejný název. Informace o tomto atributu naleznete v tématu <xref:System.ComponentModel.DefaultValueAttribute>.

Následující kód ukazuje použití explicitních polí a pro porovnání, vázání `let` ve třídě, která má primární konstruktor. Všimněte si, že pole @no__t vázané na -0 `myInt1` je soukromé. Pokud @no__t pole vázané na -0 `myInt1` je odkazováno z členské metody, není identifikátor autoidentifier `this` vyžadován. Pokud však odkazujete na explicitní pole `myInt2` a `myString`, je identifikátor autoidentifier požadován.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

Výstup je následující:

```console
11 12 abc
30 def
```

Následující kód ukazuje použití explicitních polí ve třídě, která nemá primární konstruktor. V tomto případě není požadován atribut `DefaultValue`, ale všechna pole musí být inicializována v konstruktorech, které jsou definovány pro daný typ.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

Výstup je `35 22`.

Následující kód ukazuje použití explicitních polí ve struktuře. Vzhledem k tomu, že struktura je hodnotový typ, má automaticky konstruktor bez parametrů, který nastaví hodnoty jejich polí na nulu. Proto není požadován atribut `DefaultValue`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

Výstup je `11 xyz`.

Pokud se chystáte inicializovat svou strukturu pomocí `mutable` pole bez klíčového slova `mutable`, budou vaše přiřazení fungovat na kopii struktury, která se po přiřazení zahodí hned. Proto se vaše struktura nemění.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6704.fs)]

Explicitní pole nejsou určena pro rutinové použití. Obecně platí, že pokud je to možné, měli byste použít vazbu `let` ve třídě namísto explicitního pole. Explicitní pole jsou užitečná v některých scénářích interoperability, například když potřebujete definovat strukturu, která bude použita v volání metody Invoke do nativního rozhraní API nebo ve scénářích komunikace s objekty COM. Další informace najdete v tématu věnovaném [externím funkcím](../functions/external-functions.md). Další situací, kdy může být explicitní pole nutné, je při práci s generátorem F# kódu, který generuje třídy bez primárního konstruktoru. Explicitní pole jsou také užitečná pro proměnné vlákn-static nebo podobné konstrukce. Další informace najdete v tématu `System.ThreadStaticAttribute`.

Když jsou klíčová slova `member val` uvedena v definici typu společně, jedná se o definici automaticky implementované vlastnosti. Další informace najdete v tématu [vlastnosti](properties.md).

## <a name="see-also"></a>Další informace najdete v tématech

- [Vlastnosti](properties.md)
- [Pedagog](index.md)
- [Vazby `let` ve třídách](let-bindings-in-classes.md)
