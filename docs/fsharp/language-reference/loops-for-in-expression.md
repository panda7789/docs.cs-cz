---
title: 'Smyčky: Výraz for...in (F#)'
description: 'V tématu Jak F # for... ve výrazu opakování ve smyčce konstrukce je použít k iteraci nad na odpovídá vzoru v kolekci vyčíslitelná.'
ms.date: 05/16/2016
ms.openlocfilehash: 926f0a9940021b3dc0deefc12ea158c35975e949
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="loops-forin-expression"></a>Smyčky: Výraz for...in

Tato opakování konstrukce se používá k iteraci nad na odpovídá vzoru v kolekci vyčíslitelná například výraz rozsahu, pořadí, seznam, pole nebo jiné konstrukce, která podporuje – výčet.


## <a name="syntax"></a>Syntaxe

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a>Poznámky
`for...in` Výraz může být ve srovnání s `for each` příkaz v jiných jazycích .NET protože se používá k vytvoření smyčky přes hodnoty v kolekci vyčíslitelná. Ale `for...in` také podporuje vzor odpovídající nad shromažďováním místo jenom iteraci přes celou kolekci.

Vyčíslitelná výraz lze zadat jako kolekci výčtové nebo pomocí `..` operátor jako rozsah celočíselných typu. Vyčíslitelná kolekce zahrnují seznamy, pořadí, pole, sady, mapy a tak dále. Žádný typ, který implementuje `System.Collections.IEnumerable` lze použít.

Když express rozsah pomocí `..` operátor, můžete použít následující syntaxi.

*Spustit* ... *Dokončit*

Můžete také na verzi, která zahrnuje přírůstek volat *přeskočit*, jako v následujícím kódu.

*Spustit* ... *Přeskočit* ... *Dokončit*

Použijete-li jako vzor integrální rozsahy a jednoduchý čítač proměnnou, je typické chování se zvýší o 1 na každé iteraci proměnnou čítače, ale pokud rozsahu obsahuje hodnotu přeskočit, hodnota čítače se zvýší místo hodnotou přeskočit.

Hodnoty shodná ve vzoru mohou sloužit také ve výrazu textu.

Následující příklady kódu ilustrují použití `for...in` výraz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

Výstup je následující.

```
1
5
100
450
788
```

Následující příklad ukazuje, jak smyčku sekvenci a způsob použití vzoru řazené kolekce členů místo jednoduché proměnné.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

Výstup je následující.

```
1 squared is 1
2 squared is 4
3 squared is 9
4 squared is 16
5 squared is 25
6 squared is 36
7 squared is 49
8 squared is 64
9 squared is 81
10 squared is 100
```

Následující příklad ukazuje, jak smyčku rozsah jednoduché celé číslo.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

Výstup function1 je následující.

```
1 2 3 4 5 6 7 8 9 10
```

Následující příklad ukazuje, jak na rozsah s přeskočením 2, která zahrnuje každý element, rozsahu opakovací smyčku.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

Výstup `function2` je následující.

```
1 3 5 7 9
```

Následující příklad ukazuje, jak používat rozsah znaků.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

Výstup `function3` je následující.

```
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

Následující příklad ukazuje, jak chcete použít hodnotu s záporné přeskočit pro zpětné iterací.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

Výstup `function4` je následující.

```
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

Na začátek a konec rozsahu může být také výrazy, jako je například funkce, jako v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

Výstup `function5` s tímto vstupem je následující.

```
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

Další příklad ukazuje použití zástupný znak (_), když element není potřeba ve smyčce.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

Výstup je následující.

```
Number of elements in list1: 5
```

`Note` Můžete použít `for...in` v pořadí výrazy a další výpočetní výrazy v takovém případě přizpůsobená verze `for...in` použit výraz. Další informace najdete v tématu [pořadí](sequences.md), [asynchronní pracovní postupy](asynchronous-workflows.md), a [výpočetní výrazy](computation-expressions.md).


## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F#](index.md)

[Smyčky: `for...to` výraz](loops-for-to-expression.md)

[Smyčky: `while...do` výraz](loops-while-do-expression.md)
