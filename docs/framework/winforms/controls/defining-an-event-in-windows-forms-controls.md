---
title: Definování události v ovládacím prvku Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- events [Windows Forms], defining within Windows Forms custom controls
- custom controls [Windows Forms], events using code
ms.assetid: d89f1096-8061-42e2-a855-a1f053f1940a
ms.openlocfilehash: 60ae01ca63f895bfb1c7aabbe3337596cd13933d
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45743268"
---
# <a name="defining-an-event-in-windows-forms-controls"></a>Definování události v ovládacím prvku Windows Forms
Další informace o definování vlastních událostí, naleznete v tématu [události](../../../../docs/standard/events/index.md). Pokud definujete událost, která nemá všechna související data, použijte základní typ pro data události <xref:System.EventArgs>a použijte <xref:System.EventHandler> jako delegát události. Provedete to už jen zbývá definovat člen události a chráněnou `On` *EventName* metodu, která vyvolává událost.  
  
 Následující kód fragmentu ukazuje jak `FlashTrackBar` vlastní ovládací prvek definuje vlastní událost, `ValueChanged`. Pro kompletní kód `FlashTrackBar` ukázkový, přečtěte si téma [postupy: vytvoření Windows Forms ovládací prvek, že zobrazuje dokončeno](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.Windows.Forms  
Imports System.Drawing  
  
Public Class FlashTrackBar  
   Inherits Control  
  
   ' The event does not have any data, so EventHandler is adequate   
   ' as the event delegate.          
   ' Define the event member using the event keyword.  
   ' In this case, for efficiency, the event is defined   
   ' using the event property construct.  
   Public Event ValueChanged As EventHandler  
   ' The protected method that raises the ValueChanged   
   ' event when the value has actually   
   ' changed. Derived controls can override this method.    
   Protected Overridable Sub OnValueChanged(e As EventArgs)  
      RaiseEvent ValueChanged(Me, e)  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Windows.Forms;  
using System.Drawing;  
  
public class FlashTrackBar : Control {  
   // The event does not have any data, so EventHandler is adequate   
   // as the event delegate.  
   private EventHandler onValueChanged;  
   // Define the event member using the event keyword.  
   // In this case, for efficiency, the event is defined   
   // using the event property construct.  
   public event EventHandler ValueChanged {  
            add {  
                onValueChanged += value;  
            }  
            remove {  
                onValueChanged -= value;  
            }  
        }  
   // The protected method that raises the ValueChanged  
   // event when the value has actually   
   // changed. Derived controls can override this method.    
   protected virtual void OnValueChanged(EventArgs e) 
   {  
       ValueChanged?.Invoke(this, e);  
   }  
}  
```  
  
## <a name="see-also"></a>Viz také:

- [Události v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)
- [Události](../../../../docs/standard/events/index.md)
