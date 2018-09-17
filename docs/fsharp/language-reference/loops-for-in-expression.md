---
title: 'Smyčky: Výraz for...in (F#)'
description: 'V tématu Jak F # for... ve výrazu konstrukce opakování ve smyčce se používá k iteraci přes odpovídá vzoru v vyčíslitelné kolekce.'
ms.date: 05/16/2016
ms.openlocfilehash: c4fba1f1dea3993cafa2e37ad0f32d9fb2eed85a
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45746258"
---
# <a name="loops-forin-expression"></a>Smyčky: Výraz for...in

Tato uvozuje konstruktor cyklu se používá k iteraci přes odpovídá vzoru v vyčíslitelné kolekce jako výraz rozsahu, pořadí, seznam, pole nebo jiné konstrukce, která podporuje výčtu.

## <a name="syntax"></a>Syntaxe

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a>Poznámky

`for...in` Výrazu je možné porovnat s `for each` příkaz v jiných jazycích rozhraní .NET protože se používá k vytvoření smyčky přes hodnoty v vyčíslitelné kolekce. Ale `for...in` také podporuje porovnávání vzorů přes kolekce místo pouze iterace v celé kolekci.

Vyčíslitelná výraz se dá nastavit jako vyčíslitelné kolekce nebo pomocí `..` operátor jako oblast celočíselného typu. Vyčíslitelné kolekce zahrnout seznamy, pořadí, pole, sady, mapy a tak dále. Libovolný typ, který implementuje `System.Collections.IEnumerable` lze použít.

Když vyjádřit rozsahu pomocí `..` operátoru, můžete použít následující syntaxi.

*Spustit* ... *Dokončit*

Můžete také použít verzi, která zahrnuje přírůstek volána *přeskočit*, jako v následujícím kódu.

*Spustit* ... *Přeskočit* ... *Dokončit*

Při použití integrální rozsahy a jednoduchý čítač proměnné jako vzor je obvyklé chování se zvýší o 1 při každé iteraci proměnná čítače, ale pokud rozsahu obsahuje hodnotu, přeskočit, hodnota čítače se zvýší místo toho podle hodnoty přeskočit.

Hodnoty odpovídající vzoru můžete použít také v těle výrazu.

Následující příklady kódu znázorňují použití `for...in` výrazu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

Výstup je následující.

```
1
5
100
450
788
```

Následující příklad ukazuje, jak k vytvoření smyčky přes sekvenci a způsob použití vzoru n-tice místo jednoduchá proměnná.

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

Následující příklad ukazuje, jak ve smyčce rozsah jednoduché celých čísel.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

Výstup function1 vypadá takto.

```
1 2 3 4 5 6 7 8 9 10
```

Následující příklad ukazuje, jak ve smyčce rozsah s přeskočením 2, který obsahuje každý jiného elementu rozsahu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

Výstup `function2` vypadá takto.

```
1 3 5 7 9
```

Následující příklad ukazuje, jak použít rozsah znaků.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

Výstup `function3` vypadá takto.

```
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

Následující příklad ukazuje, jak použít zápornou přeskočit hodnotu pro reverzní iteraci.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

Výstup `function4` vypadá takto.

```
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

Na začátek a konec rozsahu může být také výrazy, jako je například funkce, jako v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

Výstup `function5` tento vstup je následujícím způsobem.

```
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

Následující příklad ukazuje použití zástupných znaků (\_) Pokud prvek není nutná ve smyčce.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

Výstup je následující.

```
Number of elements in list1: 5
```

`Note` Můžete použít `for...in` ve výrazech pořadí a jiných výrazech výpočtu se v takovém případě přizpůsobenou verzi `for...in` výraz je použit. Další informace najdete v tématu [pořadí](sequences.md), [asynchronní pracovní postupy](asynchronous-workflows.md), a [výrazech výpočtu](computation-expressions.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Smyčky: `for...to` výraz](loops-for-to-expression.md)
- [Smyčky: `while...do` výraz](loops-while-do-expression.md)
