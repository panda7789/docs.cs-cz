---
title: remove (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- remove_CSharpKeyword
helpviewer_keywords:
- remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
ms.openlocfilehash: 245ef0a16fd2cec2f36c86dd0ac3b8838a76b02e
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2018
ms.locfileid: "42999768"
---
# <a name="remove-c-reference"></a>remove (Referenční dokumentace jazyka C#)
`remove` Kontextové klíčové slovo se používá k definování přístupový objekt vlastní událost, která je volána, když kód klienta ruší registraci z vaší [události](../../../csharp/language-reference/keywords/event.md). Pokud zadáte vlastní `remove` přístupový objekt, je třeba zadat také [přidat](../../../csharp/language-reference/keywords/add.md) přistupujícího objektu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje událost s vlastní [přidat](../../../csharp/language-reference/keywords/add.md) a `remove` přistupující objekty. Úplný příklad naleznete v tématu [postupy: implementace událostí rozhraní](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
 [!code-csharp[csrefKeywordsContextual#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/remove_1.cs)]  
  
 Obvykle není potřeba poskytovat vlastní vlastních přístupových objektů událostí. Přístupové objekty, které jsou automaticky generovány v kompilátoru při deklaraci události postačí pro většinu scénářů.  
  
## <a name="see-also"></a>Viz také

- [Události](../../../csharp/programming-guide/events/index.md)
