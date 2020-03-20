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
# <a name="defining-an-event-in-windows-forms-controls"></a><span data-ttu-id="8ea03-102">Definování události v ovládacím prvku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8ea03-102">Defining an Event in Windows Forms Controls</span></span>
<span data-ttu-id="8ea03-103">Podrobnosti o definování vlastních událostí naleznete v [tématu Události](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="8ea03-103">For details about defining custom events, see [Events](../../../standard/events/index.md).</span></span> <span data-ttu-id="8ea03-104">Pokud definujete událost, která nemá žádná přidružená data, použijte <xref:System.EventArgs>základní <xref:System.EventHandler> typ pro data události a použijte jako delegát události.</span><span class="sxs-lookup"><span data-stu-id="8ea03-104">If you define an event that does not have any associated data, use the base type for event data, <xref:System.EventArgs>, and use <xref:System.EventHandler> as the event delegate.</span></span> <span data-ttu-id="8ea03-105">Vše, co zbývá udělat, je definovat `On`člen události a chráněnou metodu *EventName,* která vyvolává událost.</span><span class="sxs-lookup"><span data-stu-id="8ea03-105">All that remains to do is to define an event member and a protected `On`*EventName* method that raises the event.</span></span>  
  
 <span data-ttu-id="8ea03-106">Následující fragment kódu ukazuje, `FlashTrackBar` jak vlastní ovládací `ValueChanged`prvek definuje vlastní událost .</span><span class="sxs-lookup"><span data-stu-id="8ea03-106">The following code fragment shows how the `FlashTrackBar` custom control defines a custom event, `ValueChanged`.</span></span> <span data-ttu-id="8ea03-107">Úplný kód ukázky `FlashTrackBar` naleznete v tématu [Postup: Vytvoření ovládacího prvku formulářů systému Windows, který ukazuje průběh](how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="8ea03-107">For the complete code for the `FlashTrackBar` sample, see the [How to: Create a Windows Forms Control That Shows Progress](how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8ea03-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ea03-108">See also</span></span>

- [<span data-ttu-id="8ea03-109">Události v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8ea03-109">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)
- [<span data-ttu-id="8ea03-110">Akce</span><span class="sxs-lookup"><span data-stu-id="8ea03-110">Events</span></span>](../../../standard/events/index.md)
