---
title: "Postupy: Implementace vlastních přístupových objektů událostí (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
caps.latest.revision: "7"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3ff5fedeeaa427bb62991f9b406c167647dc376d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a>Postupy: Implementace vlastních přístupových objektů událostí (Průvodce programováním v C#)
Událost je zvláštní druh vícesměrového vysílání delegáta, který jde volat jenom z v rámci třídy, která je definována v. Kód klienta jako odběratel u události tím, že poskytuje odkaz na metodu, která by měla být volána, když je aktivována událost. Tyto metody jsou přidány do seznamu vyvolání tohoto delegáta prostřednictvím přístupových objektů událostí, které se podobají vlastnost přístupové objekty, s tím rozdílem, že jsou pojmenované přístupových objektů událostí `add` a `remove`. Ve většině případů není nutné k poskytování vlastních přístupových objektů událostí. Pokud ve vašem kódu jsou zadány žádné vlastních přístupových objektů událostí, kompilátor je přidá automaticky. V některých případech ale může mít poskytnout vlastní chování. V tomto tématu se zobrazí jeden takový případ [postupy: implementace událostí rozhraní](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak implementovat vlastní přidávat a odebírat přístupových objektů událostí. I když můžete nahradit žádný kód uvnitř přístupy, doporučujeme vám, že zamknete událostí, než přidáte nebo odeberete nové metody obslužné rutiny událostí.  
  
```  
event EventHandler IDrawingObject.OnDraw  
        {  
            add  
            {  
                lock (PreDrawEvent)  
                {  
                    PreDrawEvent += value;  
                }  
            }  
            remove  
            {  
                lock (PreDrawEvent)  
                {  
                    PreDrawEvent -= value;  
                }  
            }  
        }  
```  
  
## <a name="see-also"></a>Viz také  
 [Události](../../../csharp/programming-guide/events/index.md)  
 [události](../../../csharp/language-reference/keywords/event.md)
