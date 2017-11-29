---
title: "remove (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: remove_CSharpKeyword
helpviewer_keywords: remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
caps.latest.revision: "8"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 66647dee0c4cc728ae5e19457a4a5ef0e7f72248
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
---
# <a name="remove-c-reference"></a>remove (Referenční dokumentace jazyka C#)
`remove` Kontextové klíčové slovo se používá k definování vlastní události přistupujícího objektu, která je volána, když kód klienta odhlásí vaše [událostí](../../../csharp/language-reference/keywords/event.md). Pokud zadáte vlastní `remove` přistupující objekt, je třeba zadat také [přidat](../../../csharp/language-reference/keywords/add.md) přistupujícího objektu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje událost s vlastní [přidat](../../../csharp/language-reference/keywords/add.md) a `remove` přistupující objekty. Úplný příklad najdete v tématu [postupy: implementace událostí rozhraní](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
 [!code-csharp[csrefKeywordsContextual#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/remove_1.cs)]  
  
 Obvykle není potřeba zadat vlastní vlastních přístupových objektů událostí. Přístupové objekty, které automaticky generuje služba kompilátor po deklarování událost postačí pro většinu scénářů.  
  
## <a name="see-also"></a>Viz také  
 [Události](../../../csharp/programming-guide/events/index.md)
