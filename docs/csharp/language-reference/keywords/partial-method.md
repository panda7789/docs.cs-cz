---
title: částečné metody (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: f859506ef59f4fc709e9942d86130fc222c14faf
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516366"
---
# <a name="partial-method-c-reference"></a>částečné metody (referenční dokumentace jazyka C#)

Částečná metoda má svou signaturu definovanou v jedné části částečného typu a implementaci definovanou v jiné části typu. Částečné metody umožňují návrhářům tříd poskytovat háky metod, podobně jako obslužné rutiny událostí, u kterých se mohou vývojáři rozhodnout, zda je chtějí implementovat nebo ne. Pokud vývojář neposkytne implementaci, kompilátor v době kompilace odebere signaturu. Na částečné metody se uplatňují tyto podmínky:

- Podpisy v obou částech částečného typu se musí shodovat.

- Metoda musí vracet typ void.

- Nejsou povoleny žádné modifikátory přístupu. Částečné metody jsou implicitně soukromé.

Následující příklad ukazuje částečnou metodu definovanou ve dvou částech částečné třídy:

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

Další informace najdete v tématu [částečné třídy a metody](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [částečný typ](partial-type.md)