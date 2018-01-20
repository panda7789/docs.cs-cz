---
title: "+= – operátor (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: de83f48fc644d8b232d9ef9e1698272f20a27d65
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="-operator-c-reference"></a>+= – operátor (Referenční dokumentace jazyka C#)
Operátor přiřazení sčítání.  
  
## <a name="remarks"></a>Poznámky  
 K pomocí výrazu `+=` operátor přiřazení, jako například  
  
```  
x += y  
```  
  
 je ekvivalentem  
  
```  
x = x + y  
```  
  
 Kromě toho, že `x` je Vyhodnocená jenom jednou. Význam [+ – operátor](../../../csharp/language-reference/operators/addition-operator.md) závisí na typech `x` a `y` (přidání pro číselné operandy, zřetězení pro operandy řetězec a tak dále).  
  
 `+=` Operátor nemohou být přetíženy přímo, ale může přetížit uživatelem definované typy [+ – operátor](../../../csharp/language-reference/operators/addition-operator.md) (viz [operátor](../../../csharp/language-reference/keywords/operator.md)).  
  
 `+=` Operátor slouží také k určení metodu, která bude volána v reakci na událost; tyto metody jsou volány obslužné rutiny událostí. Použití `+=` operátor v tomto kontextu se označuje jako *odběr pro událost*. Další informace najdete v tématu [postupy: přihlášení a odhlášení odběru událostí](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md) a [delegáti](../../../csharp/programming-guide/delegates/index.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#35](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
