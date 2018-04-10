---
title: partial (metoda) (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
caps.latest.revision: 26
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 03962a59d5dbe0146cad9835f81d41c06914795b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="partial-method-c-reference"></a>partial (metoda) (Referenční dokumentace jazyka C#)
Částečná metoda má svou signaturu definovanou v jedné části částečného typu a implementaci definovanou v jiné části typu. Částečné metody umožňují návrhářům tříd poskytovat háky metod, podobně jako obslužné rutiny událostí, u kterých se mohou vývojáři rozhodnout, zda je chtějí implementovat nebo ne. Pokud vývojář neposkytne implementaci, kompilátor v době kompilace odebere signaturu. Na částečné metody se uplatňují tyto podmínky:  
  
-   Podpisy v obou částech částečného typu se musí shodovat.  
  
-   Metoda musí vracet typ void.  
  
-   Nejsou povoleny žádné modifikátory přístupu. Částečné metody jsou implicitně soukromé.  
  
 Následující příklad ukazuje částečnou metodu definovanou ve dvou částech částečné třídy:  
  
 [!code-csharp[csrefKeywordsContextual#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-method_1.cs)]  
  
 Další informace najdete v tématu [částečné třídy a metody](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [partial (typ)](../../../csharp/language-reference/keywords/partial-type.md)
