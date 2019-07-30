---
title: Delegáty
description: Naučte se pracovat s delegáty F#v.
ms.date: 05/16/2016
ms.openlocfilehash: 65875897d5fc4b2ac66f1dfbe913f29fb74137cd
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630367"
---
# <a name="delegates"></a>Delegáty

Delegát představuje volání funkce jako objekt. V F#aplikaci je obvykle vhodné použít hodnoty funkcí k reprezentování funkcí jako hodnot první třídy; Delegáti se ale používají v .NET Framework, takže je potřeba, když pracujete s rozhraními API, která je očekávají. Můžou se používat taky při vytváření knihoven určených pro použití z jiných .NET Frameworkch jazyků.

## <a name="syntax"></a>Syntaxe

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi `type1` představuje typ argumentu nebo typy a `type2` představuje návratový typ. Typy argumentů, které jsou reprezentovány `type1` , jsou automaticky curryfikované. To naznačuje, že pro tento typ použijete formulář řazené kolekce členů, pokud jsou argumenty cílové funkce curryfikované a řazená kolekce členů v závorkách pro argumenty, které jsou již ve formuláři řazené kolekce členů. Automatický procesu curryfikace odebere sadu závorek a ponechává argument řazené kolekce členů, který odpovídá cílové metodě. Podívejte se na příklad kódu pro syntaxi, kterou byste měli použít v každém případě.

Delegáty lze připojit k F# hodnotám funkcí a statickým nebo instančním metodám. F#hodnoty funkcí lze předat přímo jako argumenty pro konstruktory Delegate. Pro statickou metodu sestavíte delegáty pomocí názvu třídy a metody. V případě metody instance poskytujete instanci objektu a metodu v jednom argumentu. V obou případech je použit operátor přístupu ke členu (`.`).

`Invoke` Metoda na typu delegáta volá zapouzdřenou funkci. Delegáty lze také předat jako hodnoty funkcí odkazem na název metody Invoke bez závorek.

Následující kód ukazuje syntaxi pro vytváření delegátů, kteří reprezentují různé metody ve třídě. V závislosti na tom, zda je metoda statickou metodou nebo metodou instance a zda má argumenty ve formuláři řazené kolekce členů nebo ve formuláři curryfikované, syntaxe pro deklaraci a přiřazení delegáta je trochu odlišná.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

Následující kód ukazuje některé z různých způsobů, jak můžete s delegáty pracovat.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

Výstup předchozího příkladu kódu je následující.

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Parametry a argumenty](parameters-and-arguments.md)
- [Události](./members/events.md)
