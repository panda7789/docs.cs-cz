---
description: částečný způsob – reference jazyka C#
title: částečný způsob – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: d6c433fd30f6ec51355bdefee90d815783487c1b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134377"
---
# <a name="partial-method-c-reference"></a>Partial – metoda (Referenční dokumentace jazyka C#)

Částečná metoda má svou signaturu definovanou v jedné části částečného typu a implementaci definovanou v jiné části typu. Částečné metody umožňují návrhářům tříd poskytovat háky metod, podobně jako obslužné rutiny událostí, u kterých se mohou vývojáři rozhodnout, zda je chtějí implementovat nebo ne. Pokud vývojář neposkytne implementaci, kompilátor v době kompilace odebere signaturu. Na částečné metody se uplatňují tyto podmínky:

- Podpisy v obou částech částečného typu se musí shodovat.

- Metoda musí vracet typ void.

- Nejsou povoleny žádné modifikátory přístupu. Částečné metody jsou implicitně soukromé.

Následující příklad ukazuje částečnou metodu definovanou ve dvou částech částečné třídy:

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

Další informace naleznete v tématu [částečné třídy a metody](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [částečný typ](partial-type.md)
