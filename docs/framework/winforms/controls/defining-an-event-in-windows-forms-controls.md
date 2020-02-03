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
ms.openlocfilehash: d45c369e1fc82ee009a85b5b35fe6aa754873436
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746078"
---
# <a name="defining-an-event-in-windows-forms-controls"></a><span data-ttu-id="ba187-102">Definování události v ovládacím prvku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ba187-102">Defining an Event in Windows Forms Controls</span></span>
<span data-ttu-id="ba187-103">Podrobnosti o definování vlastních událostí najdete v tématu [události](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="ba187-103">For details about defining custom events, see [Events](../../../standard/events/index.md).</span></span> <span data-ttu-id="ba187-104">Pokud definujete událost, která nemá žádná přidružená data, použijte základní typ pro data události <xref:System.EventArgs>a jako delegáta události použijte <xref:System.EventHandler>.</span><span class="sxs-lookup"><span data-stu-id="ba187-104">If you define an event that does not have any associated data, use the base type for event data, <xref:System.EventArgs>, and use <xref:System.EventHandler> as the event delegate.</span></span> <span data-ttu-id="ba187-105">Vše, co je potřeba udělat, je definovat člena události a metodu Protected `On`*EventName* , která událost vyvolá.</span><span class="sxs-lookup"><span data-stu-id="ba187-105">All that remains to do is to define an event member and a protected `On`*EventName* method that raises the event.</span></span>  
  
 <span data-ttu-id="ba187-106">Následující fragment kódu ukazuje, jak `FlashTrackBar` vlastní ovládací prvek definuje vlastní událost, `ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="ba187-106">The following code fragment shows how the `FlashTrackBar` custom control defines a custom event, `ValueChanged`.</span></span> <span data-ttu-id="ba187-107">Úplný kód pro `FlashTrackBar` Sample naleznete v tématu [How to: Create a model Windows Forms Control, který zobrazuje průběh](how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="ba187-107">For the complete code for the `FlashTrackBar` sample, see the [How to: Create a Windows Forms Control That Shows Progress](how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ba187-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="ba187-108">See also</span></span>

- [<span data-ttu-id="ba187-109">Události v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ba187-109">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)
- [<span data-ttu-id="ba187-110">Události</span><span class="sxs-lookup"><span data-stu-id="ba187-110">Events</span></span>](../../../standard/events/index.md)
