---
title: "Postupy: Kombinování delegátů (vícesměroví delegáti) (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ddb4ecbbf456179e91aa0003c2dc5653f153411f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a>Postupy: Kombinování delegátů (vícesměroví delegáti) (Průvodce programováním v C#)
Tento příklad ukazuje, jak vytvořit vícesměroví delegáti. Užitečné vlastnost [delegovat](../../../csharp/language-reference/keywords/delegate.md) objektů je, že může být přiřazen více objektů do instance jednoho delegáta pomocí `+` operátor. Delegát vícesměrového vysílání obsahuje seznam přiřazené delegáti. Když vícesměrového vysílání delegáta je zavolána, vyvolá delegáty v seznamu, v pořadí. Lze spojit pouze delegáti stejného typu.  
  
 `-` Operátor slouží k odebrání delegáta součásti vícesměrového vysílání delegáta.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.MulticastDelegate>  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Události](../../../csharp/programming-guide/events/index.md)
