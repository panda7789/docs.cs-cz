---
title: 'Postupy: Kombinování delegátů (vícesměroví delegáti) (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: e3cc3f9082bd86004a7821b64c01253408c07641
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44083274"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a>Postupy: Kombinování delegátů (vícesměroví delegáti) (Průvodce programováním v C#)
Tento příklad ukazuje, jak vytvořit vícesměroví delegáti. Užitečné vlastnost [delegovat](../../../csharp/language-reference/keywords/delegate.md) objekty je, že více objektů lze přiřadit instanci jednoho delegáta pomocí `+` operátor. Vícesměrového vysílání delegát obsahuje seznam přiřazenou delegáti. Při volání vícesměrového vysílání delegáta vyvolá Delegáti v seznamu, v pořadí. Můžete kombinovat pouze delegáti stejného typu.  
  
 `-` Operátor slouží k odebrání delegáta součásti vícesměrového vysílání delegáta.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.MulticastDelegate>  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Události](../../../csharp/programming-guide/events/index.md)
