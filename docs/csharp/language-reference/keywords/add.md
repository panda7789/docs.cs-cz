---
title: add (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
ms.openlocfilehash: c1fa8c130475a67ac175205fe3491a32654ea475
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216010"
---
# <a name="add-c-reference"></a>add (Referenční dokumentace jazyka C#)
`add` Kontextové klíčové slovo se používá k definování vlastní události přistupujícího objektu, která je volána, když kód klienta jako odběratel u vaší [událostí](../../../csharp/language-reference/keywords/event.md). Pokud zadáte vlastní `add` přistupujícího objektu, musíte také zadat [odebrat](../../../csharp/language-reference/keywords/remove.md) přistupujícího objektu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje událost, která má vlastní `add` a [odebrat](../../../csharp/language-reference/keywords/remove.md) přistupující objekty. Úplný příklad najdete v tématu [postupy: implementace událostí rozhraní](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
 [!code-csharp[csrefKeywordsContextual#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/add_1.cs)]  
  
 Obvykle není potřeba zadat vlastní vlastních přístupových objektů událostí. Přístupové objekty, které automaticky generuje služba kompilátor po deklarování událost postačí pro většinu scénářů.  
  
## <a name="see-also"></a>Viz také  
 [Události](../../../csharp/programming-guide/events/index.md)
