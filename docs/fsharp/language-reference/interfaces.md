---
title: Rozhraní (F#)
description: 'Zjistěte, jak určit sadu souvisejících členů, které implementují jiné třídy rozhraní F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 6d7f8ee9ea17d2294933f88577c30a96975ae5d4
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46009346"
---
# <a name="interfaces"></a>Rozhraní

*Rozhraní* zadat sady souvisejících členů, které implementují jiné třídy.

## <a name="syntax"></a>Syntaxe

```fsharp
// Interface declaration:
[ attributes ]
type [accessibility-modifier] interface-name =
    [ interface ]     [ inherit base-interface-name ...]
    abstract member1 : [ argument-types1 -> ] return-type1
    abstract member2 : [ argument-types2 -> ] return-type2
    ...
[ end ]

// Implementing, inside a class type definition:
interface interface-name with
    member self-identifier.member1argument-list = method-body1
    member self-identifier.member2argument-list = method-body2

// Implementing, by using an object expression:
[ attributes ]
let class-name (argument-list) =
    { new interface-name with
        member self-identifier.member1argument-list = method-body1
        member self-identifier.member2argument-list = method-body2
        [ base-interface-definitions ]
    }
    member-list
```

## <a name="remarks"></a>Poznámky

Deklarace rozhraní vypadat podobně jako deklarace tříd s tím rozdílem, že jsou implementovány žádní členové. Místo toho jsou všechny členy abstract, jak je uvedeno klíčové slovo `abstract`. Tělo metody se neposkytují pro abstraktní metody. Ale může poskytovat výchozí implementace také zahrnutím samostatné definice člena jako metoda spolu s `default` – klíčové slovo. To je ekvivalentní k vytváření virtuální metodu v základní třídě v jiných jazycích rozhraní .NET. Virtuální metoda může přepsat ve třídách, které implementují rozhraní.

Výchozí dostupnost pro rozhraní je `public`.

Můžete volitelně zadejte každý parametr metody název pomocí syntaxe normální F #:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

V uvedeném `ISprintable` například `Print` metoda má jeden parametr typu `string` s názvem `format`.

Existují dva způsoby, jak implementovat rozhraní: použitím objektových výrazů a použitím typů tříd. V obou případech se výraz typu nebo objekt třídy poskytuje těla metod pro abstraktní metody rozhraní. Implementace jsou specifické pro každý typ, který implementuje rozhraní. Proto může být metody rozhraní s různými typy liší od sebe navzájem.

Klíčová slova `interface` a `end`, které označení začátku a konce definice, jsou při použití nenáročném syntaxi volitelné. Pokud použijete tato klíčová slova, kompilátor se pokusí odvodit, zda je typ třídy nebo rozhraní díky analýze konstrukce, které používáte. Pokud definujete člena nebo použijte jiné syntaxe třídy, typ je interpretován jako třídu.

Styl kódování .NET, je začít všechna rozhraní s velkým `I`.

## <a name="implementing-interfaces-by-using-class-types"></a>Implementace rozhraní pomocí třídy typů

Můžete implementovat jednu nebo více rozhraní v typu třídy pomocí `interface` – klíčové slovo, název rozhraní a `with` – klíčové slovo, za nímž následuje definice členů rozhraní, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

Implementace rozhraní se dědí, takže není potřeba znovu implementovat je všechny odvozené třídy.

## <a name="calling-interface-methods"></a>Volání metody rozhraní

Metody rozhraní lze volat pouze prostřednictvím rozhraní, ne prostřednictvím libovolného objektu typu, který implementuje rozhraní. Proto může být nutné přetypování nahoru na typ rozhraní pomocí `:>` operátor nebo `upcast` operátor pro volání těchto metod.

Volání metody rozhraní, až budete mít objekt typu `SomeClass`, je nutné přetypování nahoru objektu na typ rozhraní, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

Alternativou je deklarovat metodu na objekt této upcasts a volá metodu rozhraní, jako v následujícím příkladu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a>Implementace rozhraní s použitím objektových výrazů

Objektové výrazy poskytují krátký způsob, jak implementovat rozhraní. Jsou užitečné v případě nemusíte vytvářet pojmenované typy a chcete jenom objekt, který podporuje metody rozhraní, bez jakékoli další metody. V následujícím kódu je znázorněn objektový výraz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a>Dědičnost rozhraní

Rozhraní může dědit z jednoho nebo více základních rozhraní.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Objektové výrazy](object-expressions.md)
- [Třídy](classes.md)
