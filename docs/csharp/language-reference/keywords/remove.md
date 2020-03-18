---
title: odebrání kontextového klíčového slova – odkaz jazyka C#
ms.date: 07/20/2015
f1_keywords:
- remove_CSharpKeyword
helpviewer_keywords:
- remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
ms.openlocfilehash: 8ea3ea1910e28c03b2a894c64415cb2ccff942d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713141"
---
# <a name="remove-c-reference"></a>remove (Referenční dokumentace jazyka C#)

Kontextové `remove` klíčové slovo se používá k definování vlastního přistupujícího objektu události, který je vyvolán při odhlášení klientského kódu z [vaší události](event.md). Pokud zadáte vlastní `remove` přistupující objekt, musíte také zadat [přistupující](add.md) objekt.

## <a name="example"></a>Příklad

Následující příklad ukazuje událost s `remove` vlastní [mise add](add.md) a accessors. Úplný příklad naleznete v tématu [Jak implementovat události rozhraní](../../programming-guide/events/how-to-implement-interface-events.md).

 [!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]

Obvykle není nutné zadat vlastní přístupové objekty událostí. Přístupové objekty, které jsou automaticky generovány kompilátoru při deklarování události jsou dostatečné pro většinu scénářů.

## <a name="see-also"></a>Viz také

- [Akce](../../programming-guide/events/index.md)
