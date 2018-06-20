---
title: add (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
ms.openlocfilehash: 143acc0d6e1989232f80ee74bf748d6c600b9741
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208352"
---
# <a name="add-c-reference"></a>add (Referenční dokumentace jazyka C#)
`add` Kontextové klíčové slovo se používá k definování vlastní události přistupujícího objektu, která je volána, když kód klienta jako odběratel u vaší [událostí](../../../csharp/language-reference/keywords/event.md). Pokud zadáte vlastní `add` přistupujícího objektu, musíte také zadat [odebrat](../../../csharp/language-reference/keywords/remove.md) přistupujícího objektu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje událost, která má vlastní `add` a [odebrat](../../../csharp/language-reference/keywords/remove.md) přistupující objekty. Úplný příklad najdete v tématu [postupy: implementace událostí rozhraní](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
[!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]
  
 Obvykle není potřeba zadat vlastní vlastních přístupových objektů událostí. Přístupové objekty, které automaticky generuje služba kompilátor po deklarování událost postačí pro většinu scénářů.  
  
## <a name="see-also"></a>Viz také  
 [Události](../../../csharp/programming-guide/events/index.md)
