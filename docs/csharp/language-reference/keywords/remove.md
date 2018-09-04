---
title: odebrat kontextové klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- remove_CSharpKeyword
helpviewer_keywords:
- remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
ms.openlocfilehash: 70b324b8bca09701ead398eb6586ad181826e5f4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527228"
---
# <a name="remove-c-reference"></a>remove (Referenční dokumentace jazyka C#)

`remove` Kontextové klíčové slovo se používá k definování přístupový objekt vlastní událost, která je volána, když kód klienta ruší registraci z vaší [události](event.md). Pokud zadáte vlastní `remove` přístupový objekt, je třeba zadat také [přidat](add.md) přistupujícího objektu.

## <a name="example"></a>Příklad

Následující příklad ukazuje událost s vlastní [přidat](add.md) a `remove` přistupující objekty. Úplný příklad naleznete v tématu [postupy: implementace událostí rozhraní](../../programming-guide/events/how-to-implement-interface-events.md).

 [!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]

Obvykle není potřeba poskytovat vlastní vlastních přístupových objektů událostí. Přístupové objekty, které jsou automaticky generovány v kompilátoru při deklaraci události postačí pro většinu scénářů.

## <a name="see-also"></a>Viz také:

- [Události](../../programming-guide/events/index.md)