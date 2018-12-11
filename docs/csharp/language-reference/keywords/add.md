---
title: Add - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
ms.openlocfilehash: 6cc1b504de383ae63284ecb3ac7d0b1b47b36bfe
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244372"
---
# <a name="add-c-reference"></a>add (Referenční dokumentace jazyka C#)
`add` Kontextové klíčové slovo se používá k definování přístupový objekt vlastní událost, která je volána, když se přihlásí k odběru kód klienta vašeho [události](../../../csharp/language-reference/keywords/event.md). Pokud zadáte vlastní `add` přístupový objekt, je třeba zadat také [odebrat](../../../csharp/language-reference/keywords/remove.md) přistupujícího objektu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje událost, která má vlastní `add` a [odebrat](../../../csharp/language-reference/keywords/remove.md) přistupující objekty. Úplný příklad naleznete v tématu [jak:  Implementace událostí rozhraní](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
[!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]
  
 Obvykle není potřeba poskytovat vlastní vlastních přístupových objektů událostí. Přístupové objekty, které jsou automaticky generovány v kompilátoru při deklaraci události postačí pro většinu scénářů.  
  
## <a name="see-also"></a>Viz také  
- [Události](../../../csharp/programming-guide/events/index.md)
