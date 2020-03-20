---
title: Definování události v ovládacích prvcích
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- events [Windows Forms], defining within Windows Forms custom controls
- custom controls [Windows Forms], events using code
ms.assetid: d89f1096-8061-42e2-a855-a1f053f1940a
ms.openlocfilehash: 6799b229de8e8eb49dd3b8bbaffe0d08a32b7208
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142287"
---
# <a name="defining-an-event-in-windows-forms-controls"></a>Definování události v ovládacím prvku Windows Forms
Podrobnosti o definování vlastních událostí naleznete v [tématu Události](../../../standard/events/index.md). Pokud definujete událost, která nemá žádná přidružená data, použijte <xref:System.EventArgs>základní <xref:System.EventHandler> typ pro data události a použijte jako delegát události. Vše, co zbývá udělat, je definovat `On`člen události a chráněnou metodu *EventName,* která vyvolává událost.  
  
 Následující fragment kódu ukazuje, `FlashTrackBar` jak vlastní ovládací `ValueChanged`prvek definuje vlastní událost . Úplný kód ukázky `FlashTrackBar` naleznete v tématu [Postup: Vytvoření ovládacího prvku formulářů systému Windows, který ukazuje průběh](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
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
  
## <a name="see-also"></a>Viz také

- [Události v ovládacích prvcích Windows Forms](events-in-windows-forms-controls.md)
- [Akce](../../../standard/events/index.md)
