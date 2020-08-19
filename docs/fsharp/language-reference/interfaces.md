---
title: Rozhraní
description: 'Přečtěte si, jak rozhraní F # určují sady souvisejících členů, které implementují jiné třídy.'
ms.date: 08/15/2020
ms.openlocfilehash: 36272b52fcff83e8e8a54ccc4e6ecd1252a91819
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558124"
---
# <a name="interfaces"></a>Rozhraní

*Rozhraní* určují sady souvisejících členů, které implementují jiné třídy.

## <a name="syntax"></a>Syntax

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

Deklarace rozhraní se podobají deklaracím třídy s tím rozdílem, že žádné členy nejsou implementovány. Místo toho jsou všichni členové abstrakcí, jak je uvedeno v klíčovém slově `abstract` . Pro abstraktní metody neposkytujete tělo metody. Můžete však zadat výchozí implementaci zahrnutím samostatné definice člena jako metody společně s `default` klíčovým slovem. To je ekvivalentní vytvoření virtuální metody v základní třídě v jiných jazycích .NET. Taková virtuální metoda může být přepsána ve třídách, které implementují rozhraní.

Výchozí přístupnost rozhraní je `public` .

Volitelně můžete každému parametru metody poskytnout název pomocí normální syntaxe F #:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

V předchozím `ISprintable` příkladu `Print` má metoda jeden parametr typu `string` s názvem `format` .

Existují dva způsoby, jak implementovat rozhraní: pomocí výrazů objektů a pomocí typů tříd. V obou případech typ třídy nebo výraz objektu poskytuje tělo metody pro abstraktní metody rozhraní. Implementace jsou specifické pro každý typ, který implementuje rozhraní. Proto se metody rozhraní u různých typů mohou lišit od sebe navzájem.

Klíčová slova `interface` a `end` , která označují začátek a konec definice, jsou volitelná při použití zjednodušené syntaxe. Pokud tato klíčová slova nepoužíváte, kompilátor se pokusí odvodit, zda je typ třídou nebo rozhraním analýzou konstrukcí, které používáte. Pokud definujete člena nebo použijete jinou syntaxi třídy, je typ interpretován jako třída.

Styl kódování .NET je začít všechna rozhraní s velkým písmenem `I` .

Více parametrů lze zadat dvěma způsoby: F #-Style a. Typ sítě. Obě budou kompilovat stejným způsobem pro příjemce .NET, ale styl F # Vynutí, aby volající F # používali parametr F # Style a. NET-Style vynutí, aby volající F # používali aplikaci argumentu s řazenou kolekcí členů.

```fsharp
type INumeric1 =
    abstract Add: x: int -> y: int -> int

type INumeric2 =
    abstract Add: x: int * y: int -> int
```

## <a name="implementing-interfaces-by-using-class-types"></a>Implementace rozhraní pomocí typů tříd

Můžete implementovat jedno nebo více rozhraní v typu třídy pomocí `interface` klíčového slova, názvu rozhraní a `with` klíčového slova následovaných definicemi člena rozhraní, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

Implementace rozhraní jsou zděděny, takže jakékoli odvozené třídy není nutné je znovu implementovat.

## <a name="calling-interface-methods"></a>Volání metod rozhraní

Metody rozhraní lze volat pouze prostřednictvím rozhraní, nikoli prostřednictvím libovolného objektu typu, který implementuje rozhraní. Proto může být nutné přetypování na typ rozhraní pomocí `:>` operátoru nebo operátoru, aby bylo možné `upcast` tyto metody volat.

Chcete-li volat metodu rozhraní, když máte objekt typu `SomeClass` , je nutné přetypování objektu na typ rozhraní, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

Alternativou je deklarovat metodu pro objekt, který přechází a volá metodu rozhraní, jak je uvedeno v následujícím příkladu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a>Implementace rozhraní pomocí objektových výrazů

Výrazy objektu představují krátký způsob, jak implementovat rozhraní. Jsou užitečné v případě, že nemusíte vytvářet pojmenovaný typ a vy chcete pouze objekt, který podporuje metody rozhraní bez jakýchkoli dalších metod. Výraz objektu je znázorněn v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a>Dědičnost rozhraní

Rozhraní mohou dědit z jednoho nebo více základních rozhraní.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka F #](index.md)
- [Objektové výrazy](object-expressions.md)
- [Třídy](classes.md)
