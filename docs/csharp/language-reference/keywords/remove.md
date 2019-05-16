---
title: odebrat kontextové klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- remove_CSharpKeyword
helpviewer_keywords:
- remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
ms.openlocfilehash: b5c604cbb0fef158750b0fa487374ab293795fc7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633725"
---
# <a name="remove-c-reference"></a>remove (Referenční dokumentace jazyka C#)

`remove` Kontextové klíčové slovo se používá k definování přístupový objekt vlastní událost, která je volána, když kód klienta ruší registraci z vaší [události](event.md). Pokud zadáte vlastní `remove` přístupový objekt, je třeba zadat také [přidat](add.md) přistupujícího objektu.

## <a name="example"></a>Příklad

Následující příklad ukazuje událost s vlastní [přidat](add.md) a `remove` přistupující objekty. Úplný příklad naleznete v tématu [jak:  Implementace událostí rozhraní](../../programming-guide/events/how-to-implement-interface-events.md).

 [!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]

Obvykle není potřeba poskytovat vlastní vlastních přístupových objektů událostí. Přístupové objekty, které jsou automaticky generovány v kompilátoru při deklaraci události postačí pro většinu scénářů.

## <a name="see-also"></a>Viz také:

- [Události](../../programming-guide/events/index.md)
