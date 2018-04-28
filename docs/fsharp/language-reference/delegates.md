---
title: Delegáti (F#)
description: 'Naučte se pracovat s Delegáti v jazyce F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 56520cc631d889f390a7d4300be1cb3185306be9
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="delegates"></a>Delegáty

Delegát představuje volání funkce, jako objekt. V jazyce F # normálně měli byste použít funkce hodnoty k reprezentaci funkce jako hodnoty první třídy; Delegáti však se používají v rozhraní .NET Framework a proto je třeba při spolupráci s rozhraní API, která je očekávali. Může také používají při vytváření knihovny určená pro použití z jinými jazyky rozhraní .NET Framework.


## <a name="syntax"></a>Syntaxe

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a>Poznámky
V předchozích syntaxi `type1` reprezentuje typ argumentu nebo typy a `type2` představuje návratový typ. Typy argumentů, které jsou reprezentované pomocí `type1` jsou automaticky curryfikované. To naznačuje, že pro tento typ používat formulář řazené kolekce členů, pokud jsou argumenty funkce cíl curryfikované a řazené kolekce členů v závorkách argumenty, které jsou již v podobě řazené kolekce členů. Automatické currying odebere sadu závorky, ponechat argument řazené kolekce členů, která odpovídá cílové metody. Naleznete příklad kódu pro syntaxi, kterou byste měli použít v každém případu.

Delegáti lze připojit k F # funkce hodnoty a statické nebo instanci metody. F # funkce hodnoty lze předat přímo jako argumenty pro delegování konstruktorů. Pro statickou metodu vytvoříte pomocí názvu třídy a metody delegáta. Pro metodu instance poskytnete instance objektu a metoda v jeden argument. V obou případech člen přístup – operátor (`.`) se používá.

`Invoke` Metoda typu delegáta volání zapouzdřené funkce. Delegáti také může být předán jako funkce hodnoty pod položkou Název metody Invoke bez závorek.

Následující kód ukazuje syntaxi pro vytváření delegátů, které představují různé metody ve třídě. Syntaxe deklarace a přiřazení delegát je v závislosti na tom, zda je metoda statickou metodu nebo instanci metody a jestli má argumenty v podobě řazené kolekce členů nebo curryfikované formuláře, mírně liší.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

Následující kód ukazuje některé různými způsoby, kterými můžete pracovat s delegáti.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

Výstupem předchozího příkladu kódu je následujícím způsobem.

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F#](index.md)

[Parametry a argumenty](parameters-and-arguments.md)

[Události](members/events.md)
