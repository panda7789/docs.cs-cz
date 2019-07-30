---
title: 'Smyčky: Výraz for...in'
description: Podívejte se, F# jak pro... v konstruktoru smyčky výrazů se používá k iteraci přes shody vzoru ve vyčíslitelné kolekci.
ms.date: 05/16/2016
ms.openlocfilehash: 640b0f91f6c641f3b49a99dc67abe7e4c31911ea
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630724"
---
# <a name="loops-forin-expression"></a>Smyčky: Výraz for...in

Tato konstrukce smyčky se používá k iteraci přes shody vzoru ve vyčíslitelné kolekci, jako je například výraz rozsahu, sekvence, seznam, pole nebo jiná konstrukce, která podporuje výčet.

## <a name="syntax"></a>Syntaxe

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a>Poznámky

Výraz může být porovnán `for each` s příkazem v jiných jazycích .NET, protože se používá k překonání hodnot ve vyčíslitelné kolekci. `for...in` Nicméně podporuje `for...in` také porovnávání vzorů přes kolekci namísto pouze iterace v celé kolekci.

Vyčíslitelné výrazy lze zadat jako vyčíslitelné kolekce nebo pomocí `..` operátoru jako rozsahu pro celočíselný typ. Vyčíslitelné kolekce obsahují seznamy, sekvence, pole, sady, mapy a tak dále. Lze použít jakýkoli typ `System.Collections.IEnumerable` , který implementuje implementaci.

Při vyjádření rozsahu pomocí `..` operátoru můžete použít následující syntaxi.

*Spustit* ... *skončit*

Můžete také použít verzi, která obsahuje přírůstek s názvem *Skip*, jak je uvedeno v následujícím kódu.

*Spustit* ... *Přeskočit* ... *skončit*

Když použijete celočíselné rozsahy a jednoduchou proměnnou čítače jako vzor, typické chování je zvýšit proměnnou čítače o 1 u každé iterace, ale pokud rozsah obsahuje hodnotu Skip, čítač se zvýší o hodnotu přeskočení.

Hodnoty odpovídající vzoru lze také použít ve výrazu body.

Následující příklady kódu ilustrují použití `for...in` výrazu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

Výstup je následující.

```
1
5
100
450
788
```

Následující příklad ukazuje, jak vytvořit smyčku přes sekvenci a jak použít vzor řazené kolekce členů namísto jednoduché proměnné.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

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

Následující příklad ukazuje, jak vytvořit smyčku přes jednoduchý celočíselný rozsah.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

Výstup Function1 je následující.

```
1 2 3 4 5 6 7 8 9 10
```

Následující příklad ukazuje, jak vytvořit smyčku v rámci rozsahu s vynecháním 2, který obsahuje všechny ostatní prvky rozsahu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

Výstup `function2` je následující:

```
1 3 5 7 9
```

Následující příklad ukazuje, jak použít rozsah znaků.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

Výstup `function3` je následující:

```
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

Následující příklad ukazuje, jak použít pro reverzní iteraci zápornou hodnotu Skip.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

Výstup `function4` je následující:

```
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

Začátek a konec rozsahu může být také výrazy, například funkce, jako v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

Výstup `function5` tohoto vstupu je následující.

```
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

Následující příklad ukazuje použití zástupného znaku (\_), pokud element není ve smyčce potřeba.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

Výstup je následující.

```
Number of elements in list1: 5
```

`Note`Můžete použít `for...in` ve výrazech pořadí a dalších výrazech výpočtu. v takovém případě se používá přizpůsobená verze `for...in` výrazu. Další informace najdete v tématu [sekvence](sequences.md), [asynchronní pracovní postupy](asynchronous-workflows.md)a [výpočetní výrazy](computation-expressions.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Smyčky `for...to`Vyjádření](loops-for-to-expression.md)
- [Smyčky `while...do`Vyjádření](loops-while-do-expression.md)
