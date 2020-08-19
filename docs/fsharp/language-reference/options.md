---
title: Možnosti
description: 'Naučte se používat typy možností jazyka F #, pokud skutečná hodnota nemusí existovat pro pojmenovanou hodnotu nebo proměnnou.'
ms.date: 08/13/2020
ms.openlocfilehash: 0618590c10f6ecac51a23483ca0ab6cd66f2df4f
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557565"
---
# <a name="options"></a>Možnosti

Typ možnosti v jazyce F # se používá v případě, že skutečná hodnota nemusí existovat pro pojmenovanou hodnotu nebo proměnnou. Možnost má podkladový typ a může obsahovat hodnotu tohoto typu, nebo nemusí mít hodnotu.

## <a name="remarks"></a>Poznámky

Následující kód ilustruje funkci, která generuje typ možnosti.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1404.fs)]

Jak vidíte, pokud `a` je vstup větší než 0, `Some(a)` je vygenerována.  V opačném případě `None` se vygeneruje.

Hodnota `None` se používá, pokud možnost nemá skutečnou hodnotu. V opačném případě výraz `Some( ... )` poskytuje možnost hodnotu. Hodnoty `Some` a `None` jsou užitečné v porovnávání vzorů, jako v následující funkci `exists` , která vrátí, `true` Pokud má možnost hodnotu, a `false` Pokud není.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1401.fs)]

## <a name="using-options"></a>Použití možností

Možnosti jsou běžně používány, pokud hledání nevrátí výsledek odpovídajícího výsledku, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1403.fs)]

V předchozím kódu se seznam rekurzivně prohledává. Funkce `tryFindMatch` přebírá funkci predikátu `pred` , která vrací logickou hodnotu, a seznam pro hledání. Pokud je nalezen element, který splňuje predikát, rekurze skončí a funkce vrátí hodnotu jako možnost ve výrazu `Some(head)` . Rekurze skončí po porovnání prázdného seznamu. V tomto okamžiku se hodnota nenajde `head` a `None` vrátí se.

Mnoho funkcí knihovny jazyka F #, které hledají kolekci pro hodnotu, která může nebo nemusí existovat, vrátí `option` typ. Podle konvence tyto funkce začínají `try` předponou, například [`Seq.tryFindIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#tryFindIndex) .

Možnosti mohou být užitečné také v případě, že hodnota nemusí existovat, například pokud je možné, že při pokusu o vytvoření hodnoty dojde k výjimce. Následující příklad kódu to dokládá.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1402.fs)]

`openFile`Funkce v předchozím příkladu má typ, `string -> File option` protože vrátí `File` objekt, pokud se soubor otevře úspěšně a `None` Pokud dojde k výjimce. V závislosti na situaci nemusí být vhodná volba pro vlastní návrh, aby bylo možné zachytit výjimku místo toho, aby bylo možné ji rozšířit.

Kromě toho je stále možné předat `null` nebo hodnotu, která má hodnotu null, pro `Some` případ možnosti. Obecně se to vyhnete a obvykle je běžné programování F #, ale je možné z důvodu povahy odkazových typů v rozhraní .NET.

## <a name="option-properties-and-methods"></a>Vlastnosti a metody možnosti

Typ možnosti podporuje následující vlastnosti a metody.

|Vlastnost nebo metoda|Typ|Popis|
|------------------|----|-----------|
|[Žádný](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-fsharpoption-1.html#None)|`'T option`|Statická vlastnost, která umožňuje vytvořit hodnotu možnosti, která má `None` hodnotu.|
|[IsNone –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-fsharpoption-1.html#IsNone)|`bool`|Vrátí, `true` zda má možnost `None` hodnotu.|
|[Issome –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-fsharpoption-1.html#IsSome)|`bool`|Vrátí `true` , zda má možnost hodnotu, která není `None` .|
|[Některé](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-fsharpoption-1.html#Some)|`'T option`|Statický člen, který vytvoří možnost, která má hodnotu, která není `None` .|
|[Hodnota](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-fsharpoption-1.html#Value)|`'T`|Vrátí podkladovou hodnotu nebo vyvolá výjimku, `System.NullReferenceException` Pokud je hodnota `None` .|

## <a name="option-module"></a>Modul možností

Existuje modul, který obsahuje užitečné funkce, které provádějí operace [s možnostmi](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html). Některé funkce opakují funkci vlastností, ale jsou užitečné v kontextech, kde je funkce potřebná. [Option...](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#isSome) je [funkce](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#isNone) modulu, které testují, zda má parametr hodnotu. [Možnost. Get](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#get) Získá hodnotu, pokud je nějaká. Pokud není žádná hodnota, vyvolá se `System.ArgumentException` .

Funkce [Option. Bind](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#bind) spustí funkci na hodnotu, pokud existuje hodnota. Funkce musí přijmout přesně jeden argument a její typ parametru musí být typ možnosti. Návratová hodnota funkce je další typ možnosti.

Modul možností obsahuje také funkce, které odpovídají funkcím, které jsou k dispozici pro seznamy, pole, sekvence a jiné typy kolekcí. Mezi tyto funkce patří [`Option.map`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#map) ,,,, [`Option.iter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#iter) , a [`Option.forall`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#forall) [`Option.exists`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#exists) [`Option.foldBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#foldBack) [`Option.fold`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#fold) [`Option.count`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#count) . Tyto funkce umožňují použít možnosti jako kolekci nula nebo jeden prvek. Další informace a příklady najdete v diskuzi o funkcích kolekce v [seznamech](lists.md).

## <a name="converting-to-other-types"></a>Převod na jiné typy

Možnosti lze převést na seznamy nebo pole. Když je možnost převedena na některou z těchto datových struktur, výsledná struktura dat má žádný nebo jeden element. Chcete-li převést možnost na pole, použijte [`Option.toArray`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#toArray) . Chcete-li převést možnost na seznam, použijte [`Option.toList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#toList) .

## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka F #](index.md)
- [Typy F#](fsharp-types.md)
