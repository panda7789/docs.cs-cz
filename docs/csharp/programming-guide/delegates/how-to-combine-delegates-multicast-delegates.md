---
title: 'Postupy: Kombinování delegátů (vícesměroví delegáti) (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: e1214a4d281dbcb9d8186770b68510d3d9a4b15f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a>Postupy: Kombinování delegátů (vícesměroví delegáti) (Průvodce programováním v C#)
Tento příklad ukazuje, jak vytvořit vícesměroví delegáti. Užitečné vlastnost [delegovat](../../../csharp/language-reference/keywords/delegate.md) objektů je, že může být přiřazen více objektů do instance jednoho delegáta pomocí `+` operátor. Delegát vícesměrového vysílání obsahuje seznam přiřazené delegáti. Když vícesměrového vysílání delegáta je zavolána, vyvolá delegáty v seznamu, v pořadí. Lze spojit pouze delegáti stejného typu.  
  
 `-` Operátor slouží k odebrání delegáta součásti vícesměrového vysílání delegáta.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.MulticastDelegate>  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Události](../../../csharp/programming-guide/events/index.md)
