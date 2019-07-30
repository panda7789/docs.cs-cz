---
title: Možnosti
description: Naučte se používat F# typy možností, když skutečná hodnota nemusí existovat pro pojmenovanou hodnotu nebo proměnnou.
ms.date: 05/16/2016
ms.openlocfilehash: 9326cf04f53adac7422c09a49a59c4eecd49486d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627348"
---
# <a name="options"></a>Možnosti

Typ možnosti v se F# používá v případě, že skutečná hodnota nemusí existovat pro pojmenovanou hodnotu nebo proměnnou. Možnost má podkladový typ a může obsahovat hodnotu tohoto typu, nebo nemusí mít hodnotu.

## <a name="remarks"></a>Poznámky

Následující kód ilustruje funkci, která generuje typ možnosti.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1404.fs)]

Jak vidíte, pokud je vstup `a` větší než 0, `Some(a)` je vygenerována.  V opačném případě se vygeneruje. `None`

Hodnota `None` se používá, pokud možnost nemá skutečnou hodnotu. V opačném případě `Some( ... )` výraz poskytuje možnost hodnotu. Hodnoty `Some` `true` a `None` jsou užitečné v porovnávání vzorů, jako v následující funkci `exists`, která vrátí, pokud má možnost hodnotu, a `false` Pokud není.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1401.fs)]

## <a name="using-options"></a>Použití možností

Možnosti jsou běžně používány, pokud hledání nevrátí výsledek odpovídajícího výsledku, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1403.fs)]

V předchozím kódu se seznam rekurzivně prohledává. Funkce `tryFindMatch` přebírá funkci `pred` predikátu, která vrací logickou hodnotu, a seznam pro hledání. Pokud je nalezen element, který splňuje predikát, rekurze skončí a funkce vrátí hodnotu jako možnost ve výrazu `Some(head)`. Rekurze skončí po porovnání prázdného seznamu. V tomto okamžiku se hodnota `head` nenajde a `None` vrátí se.

Mnoho F# funkcí knihovny, které v kolekci hledají hodnotu, která může nebo nemusí existovat, vrátí `option` typ. Podle konvence tyto funkce začínají `try` předponou, [`Seq.tryFindIndex`](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a)například.

Možnosti mohou být užitečné také v případě, že hodnota nemusí existovat, například pokud je možné, že při pokusu o vytvoření hodnoty dojde k výjimce. Následující příklad kódu to dokládá.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1402.fs)]

Funkce v předchozím příkladu má typ `string -> File option` , protože vrátí `File` objekt, pokud se soubor otevře úspěšně a `None` Pokud dojde k výjimce. `openFile` V závislosti na situaci nemusí být vhodná volba pro vlastní návrh, aby bylo možné zachytit výjimku místo toho, aby bylo možné ji rozšířit.

Kromě toho je stále možné předat `null` nebo hodnotu, která má hodnotu null, `Some` pro případ možnosti. Obecně se to vyhnete a obvykle je běžné F# programování, ale je možné v důsledku povahy odkazových typů v rozhraní .NET.

## <a name="option-properties-and-methods"></a>Vlastnosti a metody možnosti

Typ možnosti podporuje následující vlastnosti a metody.

|Vlastnost nebo metoda|type|Popis|
|------------------|----|-----------|
|[Žádné](https://msdn.microsoft.com/library/83ef260a-aa33-4e6f-aee6-b9bf0a461476)|`'T option`|Statická vlastnost, která umožňuje vytvořit hodnotu možnosti, která má `None` hodnotu.|
|[IsNone –](https://msdn.microsoft.com/library/f08532ca-1716-4f60-ae59-8ef6256df234)|`bool`|Vrátí `true` , zda `None` má možnost hodnotu.|
|[Issome –](https://msdn.microsoft.com/library/c5088d51-c5d7-425f-a77f-12c379bb356f)|`bool`|Vrátí `true` , zda má možnost hodnotu, která `None`není.|
|[Některé](https://msdn.microsoft.com/library/12f048d2-e293-4596-accb-de036ecd63fc)|`'T option`|Statický člen, který vytvoří možnost, která má hodnotu, která `None`není.|
|[Hodnota](https://msdn.microsoft.com/library/c79f68e8-11fd-45b1-a053-e8fc38b56df7)|`'T`|Vrátí podkladovou hodnotu nebo vyvolá výjimku `System.NullReferenceException` , pokud je `None`hodnota.|

## <a name="option-module"></a>Modul možností

Existuje [modul, který](https://msdn.microsoft.com/library/e615e4d3-bbbb-49ba-addc-6061ea2e2f4c)obsahuje užitečné funkce, které provádějí operace s možnostmi. Některé funkce opakují funkci vlastností, ale jsou užitečné v kontextech, kde je funkce potřebná. [Option...](https://msdn.microsoft.com/library/41ad0857-5672-4326-84b5-c33dc43dcf79) je [funkce](https://msdn.microsoft.com/library/73db6a53-15e7-40a6-94f9-a0049e5f4819) modulu, které testují, zda má parametr hodnotu. [Možnost. Get](https://msdn.microsoft.com/library/803e9fcb-6edd-4910-808c-25f08cbc55ea) Získá hodnotu, pokud je nějaká. Pokud není žádná hodnota, vyvolá `System.ArgumentException`se.

Funkce [Option. Bind](https://msdn.microsoft.com/library/c3406192-24ac-49b5-bc3b-8f805187f1c0) spustí funkci na hodnotu, pokud existuje hodnota. Funkce musí přijmout přesně jeden argument a její typ parametru musí být typ možnosti. Návratová hodnota funkce je další typ možnosti.

Modul možností obsahuje také funkce, které odpovídají funkcím, které jsou k dispozici pro seznamy, pole, sekvence a jiné typy kolekcí. Mezi tyto funkce [`Option.map`](https://msdn.microsoft.com/library/91a20385-7e73-40c2-9adc-635e86d6a622)patří [`Option.iter`](https://msdn.microsoft.com/library/83389eef-3dff-4074-b4cc-f69581c25191), [`Option.forall`](https://msdn.microsoft.com/library/ba884586-5eae-49c5-9e36-05481c1c3428), [`Option.exists`](https://msdn.microsoft.com/library/a606d2d4-fddc-4eab-ab37-c6138fb7ad99) [,,`Option.fold`](https://msdn.microsoft.com/library/af896794-3d53-406c-9411-316cd5c33ad8), a [.`Option.count`](https://msdn.microsoft.com/library/2dac83a9-684e-4d0f-b50e-ff722a8bb876) [`Option.foldBack`](https://msdn.microsoft.com/library/a882fbaf-c019-46f0-b4f5-b8c2b8b90ffb) Tyto funkce umožňují použít možnosti jako kolekci nula nebo jeden prvek. Další informace a příklady najdete v diskuzi o funkcích kolekce v [seznamech](lists.md).

## <a name="converting-to-other-types"></a>Převod na jiné typy

Možnosti lze převést na seznamy nebo pole. Když je možnost převedena na některou z těchto datových struktur, výsledná struktura dat má žádný nebo jeden element. Chcete-li převést možnost na pole, použijte [`Option.toArray`](https://msdn.microsoft.com/library/c8044873-ba17-4b52-8231-eb1a28318c64). Chcete-li převést možnost na seznam, použijte [`Option.toList`](https://msdn.microsoft.com/library/5f1af295-9fa9-40ad-b4a1-3578d94d44e1).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Typy F#](fsharp-types.md)
