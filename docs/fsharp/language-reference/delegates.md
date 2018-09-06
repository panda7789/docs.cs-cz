---
title: Delegáti (F#)
description: 'Zjistěte, jak pracovat s Delegáti v jazyce F #.'
ms.date: 05/16/2016
ms.openlocfilehash: be58997dffe8fcd949bbc2d47d86ffccc157d43e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43801519"
---
# <a name="delegates"></a>Delegáty

Delegát představuje volání funkce, jako objekt. V jazyce F # obvykle používejte funkce hodnoty k reprezentaci funkce jako hodnoty první třídy; ale delegáty se používají v rozhraní .NET Framework a proto jsou potřeba při spolupráci s rozhraní API, která je. Může také používají při vytváření knihovny určená pro použití z jiných jazycích rozhraní .NET Framework.

## <a name="syntax"></a>Syntaxe

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi `type1` reprezentuje typ argumentu nebo typy a `type2` představuje návratovým typem. Typy argumentů, které jsou reprezentovány `type1` jsou automaticky curryfikované. To naznačuje, který pro tento typ použít formulář řazené kolekce členů, pokud jsou curryfikované argumenty cílová funkce a řazené kolekce členů v závorkách pro argumenty, které jsou již v podobě řazené kolekce členů. Automatické curryfikace odebere závorka, byste museli opustit argumentem řazené kolekce členů, která odpovídá cílové metody. Naleznete v příkladu kódu pro syntaxi, kterou byste měli použít ve všech případech.

Delegáty lze připojit k F # hodnoty funkcí a statické nebo instanci metody. Hodnoty funkcí F # je možné předat přímo jako argumenty pro delegování konstruktorů. Pro statické metody vytvoříte pomocí názvu třídy a metody delegáta. Pro metodu instance zadejte instanci objektu a metoda v jeden argument. V obou případech se člen přístup – operátor (`.`) se používá.

`Invoke` Metodu na typ delegáta volá funkci zapouzdřený objekt. Také delegáty lze předat jako hodnoty funkcí odkazem název metody Invoke bez závorek.

Následující kód ukazuje syntaxi pro vytvoření delegáty, které představují různé metody ve třídě. V závislosti na tom, jestli je metoda statickou metodu nebo metodu instance a určuje, zda má argumenty v podobě řazené kolekce členů nebo curryfikované formuláře syntaxi pro deklaraci a přiřazení delegáta se mírně liší.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

Následující kód ukazuje některé z různými způsoby, kterými můžete pracovat s delegátů.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

Výstup z předchozího příkladu kódu vypadá takto.

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Parametry a argumenty](parameters-and-arguments.md)
- [Události](members/events.md)
