---
title: partial (metoda) (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 69e16dd8b0fe0055124aca90fea65a36d9e413f3
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42933682"
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

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [partial (typ)](../../../csharp/language-reference/keywords/partial-type.md)
