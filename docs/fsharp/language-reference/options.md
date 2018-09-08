---
title: Možnosti (F#)
description: 'Zjistěte, jak použít možnost F #, typy, když skutečnou hodnotu nemusí existovat pojmenovaná hodnota nebo proměnná.'
ms.date: 05/16/2016
ms.openlocfilehash: 0859cb42e72ef9e67551b884f5cf6130fb099a78
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44187819"
---
# <a name="options"></a>Možnosti

Typ možnosti v jazyce F # se používá při skutečnou hodnotu nemusí existovat pojmenovaná hodnota nebo proměnná. Použít má základní typ a můžou obsahovat hodnotu daného typu, nebo nemusí mít hodnotu.

## <a name="remarks"></a>Poznámky

Následující kód ukazuje funkci, která generuje typ možnosti.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1404.fs)]

Jak je vidět, pokud vstupní `a` je větší než 0, `Some(a)` je generován.  V opačném případě `None` je generován.

Hodnota `None` se používá, když je možnost nemá skutečnou hodnotu. V opačném případě výraz `Some( ... )` dává možnost hodnotu. Hodnoty `Some` a `None` jsou užitečné při porovnávání vzorů, jako v následující funkci `exists`, která vrací `true` Pokud možnost má hodnotu a `false` Pokud tomu tak není.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1401.fs)]

## <a name="using-options"></a>Pomocí možností

Běžně se používají možnosti při hledání nevrací odpovídající výsledek, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1403.fs)]

V předchozím kódu je seznam hledaný rekurzivně. Funkce `tryFindMatch` trvá funkce predikátu `pred` , který vrací logickou hodnotu a seznamu pro vyhledávání. Pokud je nalezen element, který splňuje predikát, elementy end rekurze a funkce vrátí hodnotu jako možnost ve výrazu `Some(head)`. Rekurze končí, když je nalezena shoda s prázdný seznam. V tomto okamžiku hodnotu `head` nebyl nalezen, a `None` je vrácena.

Mnoho F # knihovních funkcí, které vyhledání v kolekci na hodnotu, která můžou nebo nemusí existovat vrátit `option` typu. Podle konvence, tyto funkce začínat `try` předponu, například [ `Seq.tryFindIndex` ](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a).

Možnosti mohou být užitečné také při nemusí existovat hodnotu, například pokud je to možné, že při pokusu o vytvoření hodnotu bude vyvolána výjimka. Následující příklad kódu to dokládá.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1402.fs)]

`openFile` Funkce v předchozím příkladu má typ `string -> File option` vzhledem k tomu, že ji vrací `File` objektu, pokud soubor úspěšně otevřen a `None` Pokud dojde k výjimce. V závislosti na situaci nemusí být příslušné návrhu zachytit výjimku nepovolí na dokončení propagace.

## <a name="option-properties-and-methods"></a>Možnost Vlastnosti a metody

Typ možnosti podporuje následující vlastnosti a metody.

|Vlastnost nebo metoda|Typ|Popis|
|------------------|----|-----------|
|[None](https://msdn.microsoft.com/library/83ef260a-aa33-4e6f-aee6-b9bf0a461476)|`'T option`|Statická vlastnost, která vám umožní vytvořit hodnotu možnosti, která má `None` hodnotu.|
|[Isnone –](https://msdn.microsoft.com/library/f08532ca-1716-4f60-ae59-8ef6256df234)|`bool`|Vrátí `true` Pokud má možnost `None` hodnotu.|
|[Issome –](https://msdn.microsoft.com/library/c5088d51-c5d7-425f-a77f-12c379bb356f)|`bool`|Vrátí `true` Pokud parametr má hodnotu, která není `None`.|
|[Některé](https://msdn.microsoft.com/library/12f048d2-e293-4596-accb-de036ecd63fc)|`'T option`|Statický člen, který vytvoří možnost, která má hodnotu, která není `None`.|
|[Hodnota](https://msdn.microsoft.com/library/c79f68e8-11fd-45b1-a053-e8fc38b56df7)|`'T`|Vrátí zdrojovou hodnotu, nebo vyvolá výjimku `System.NullReferenceException` Pokud je hodnota `None`.|

## <a name="option-module"></a>Možnost modulu

Je-li modul [možnost](https://msdn.microsoft.com/library/e615e4d3-bbbb-49ba-addc-6061ea2e2f4c), obsahující užitečných funkcí, které provádějí operace na možnosti. Některé funkce opakujte funkci vlastností, ale jsou užitečné v kontextech, ve které je vyžadují funkce. [Option.issome –](https://msdn.microsoft.com/library/41ad0857-5672-4326-84b5-c33dc43dcf79) a [Option.isNone](https://msdn.microsoft.com/library/73db6a53-15e7-40a6-94f9-a0049e5f4819) jsou obě modulu funkce, které testují, zda možnost obsahuje hodnotu. [Option.Get](https://msdn.microsoft.com/library/803e9fcb-6edd-4910-808c-25f08cbc55ea) získá hodnotu, pokud existuje. Pokud není žádná hodnota, vyvolá `System.ArgumentException`.

[Option.bind](https://msdn.microsoft.com/library/c3406192-24ac-49b5-bc3b-8f805187f1c0) funkce spustí funkci na základě hodnoty, pokud hodnota. Funkce musí přebírat přesně jeden argument a jeho typ parametru musí být typu možnosti. Návratový typ funkce je jiný typ možnost.

Modul možnost také zahrnuje funkce, které odpovídají funkcím, které jsou k dispozici pro seznamy, polí, sekvencí a typy kolekcí. Tyto funkce patří [ `Option.map` ](https://msdn.microsoft.com/library/91a20385-7e73-40c2-9adc-635e86d6a622), [ `Option.iter` ](https://msdn.microsoft.com/library/83389eef-3dff-4074-b4cc-f69581c25191), [ `Option.forall` ](https://msdn.microsoft.com/library/ba884586-5eae-49c5-9e36-05481c1c3428), [ `Option.exists` ](https://msdn.microsoft.com/library/a606d2d4-fddc-4eab-ab37-c6138fb7ad99), [ `Option.foldBack` ](https://msdn.microsoft.com/library/a882fbaf-c019-46f0-b4f5-b8c2b8b90ffb), [ `Option.fold` ](https://msdn.microsoft.com/library/af896794-3d53-406c-9411-316cd5c33ad8), a [ `Option.count` ](https://msdn.microsoft.com/library/2dac83a9-684e-4d0f-b50e-ff722a8bb876). Tyto funkce povolit možnost použít jako kolekci elementů žádnou nebo jednou. Další informace a příklady najdete v diskuzi o kolekce funkcí v [uvádí](lists.md).

## <a name="converting-to-other-types"></a>Převádění na jiné typy.

Možnosti lze převést do seznamů nebo polí. Pokud možnost se převede na některou z těchto datových struktur, výsledná datová struktura nemá žádný nebo jeden element. Chcete-li možnost převést na pole, použijte [ `Option.toArray` ](https://msdn.microsoft.com/library/c8044873-ba17-4b52-8231-eb1a28318c64). Chcete-li možnost převést do seznamu, použijte [ `Option.toList` ](https://msdn.microsoft.com/library/5f1af295-9fa9-40ad-b4a1-3578d94d44e1).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Typy F#](fsharp-types.md)
