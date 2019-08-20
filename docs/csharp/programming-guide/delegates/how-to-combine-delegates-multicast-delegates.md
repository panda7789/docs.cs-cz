---
title: 'Postupy: Kombinování delegátů (delegáti C# vícesměrového vysílání) – Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: d9430021e6a9b438822f1a6dc201f64adf4fdb0f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590661"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a>Postupy: Kombinování delegátů (vícesměroví delegáti) (Průvodce programováním v C#)
Tento příklad ukazuje, jak vytvořit delegáty vícesměrového vysílání. Užitečnou vlastností objektů [delegáta](../../language-reference/keywords/delegate.md) je, že více objektů lze přiřadit k jedné instanci delegáta pomocí `+` operátoru. Delegát vícesměrového vysílání obsahuje seznam přiřazených delegátů. Při volání delegáta vícesměrového vysílání vyvolá delegáty v seznamu v pořadí. Kombinovat lze pouze delegáty stejného typu.  
  
 `-` Operátor lze použít k odebrání delegáta komponenty z delegáta vícesměrového vysílání.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.MulticastDelegate>
- [Průvodce programováním v jazyce C#](../index.md)
- [Události](../events/index.md)
