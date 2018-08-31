---
title: += – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: bd0997ec5b7d79a41e01f9c2b17533293e412c1e
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2018
ms.locfileid: "43257328"
---
# <a name="-operator-c-reference"></a>+= – operátor (Referenční dokumentace jazyka C#)
Operátor přiřazení sčítání.  
  
## <a name="remarks"></a>Poznámky  
 Pomocí výrazu `+=` operátor přiřazení, jako například  
  
```csharp  
x += y  
```  
  
 je ekvivalentem  
  
```csharp  
x = x + y  
```  
  
 s tím rozdílem, že `x` se jenom vyhodnotí jednou. Význam [+ – operátor](../../../csharp/language-reference/operators/addition-operator.md) závisí na typech `x` a `y` (součet číselného operandy, zřetězení pro řetězec operandy a tak dále).  
  
 `+=` Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [+ – operátor](../../../csharp/language-reference/operators/addition-operator.md) (viz [operátor](../../../csharp/language-reference/keywords/operator.md)).  
  
 `+=` Operátor se používá také k určení metodu, která bude volána v reakci na události; tyto metody jsou volány obslužné rutiny událostí. Použití `+=` operátoru v tomto kontextu se označuje jako *přihlášení k odběru události*. Další informace najdete v tématu [postupy: přihlášení k odběru a zrušit její odběr události](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md) a [delegáti](../../../csharp/programming-guide/delegates/index.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#35](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
