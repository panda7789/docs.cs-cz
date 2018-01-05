---
title: "Definování události v ovládacím prvku Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- events [Windows Forms], defining within Windows Forms custom controls
- custom controls [Windows Forms], events using code
ms.assetid: d89f1096-8061-42e2-a855-a1f053f1940a
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 900d4d402c905f10ec7db98421adcb0bc7f46048
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="defining-an-event-in-windows-forms-controls"></a><span data-ttu-id="ce534-102">Definování události v ovládacím prvku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ce534-102">Defining an Event in Windows Forms Controls</span></span>
<span data-ttu-id="ce534-103">Podrobnosti o definování vlastních událostí najdete v tématu [události](../../../../docs/standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="ce534-103">For details about defining custom events, see [Events](../../../../docs/standard/events/index.md).</span></span> <span data-ttu-id="ce534-104">Pokud definujete událost, která nemá žádné přidružená data, použijte základní typ pro data události <xref:System.EventArgs>a použijte <xref:System.EventHandler> jako delegát události.</span><span class="sxs-lookup"><span data-stu-id="ce534-104">If you define an event that does not have any associated data, use the base type for event data, <xref:System.EventArgs>, and use <xref:System.EventHandler> as the event delegate.</span></span> <span data-ttu-id="ce534-105">Uděláte to zbývá určit člen události a s chráněným `On` *EventName* metoda, která vyvolává událost.</span><span class="sxs-lookup"><span data-stu-id="ce534-105">All that remains to do is to define an event member and a protected `On`*EventName* method that raises the event.</span></span>  
  
 <span data-ttu-id="ce534-106">Následující kód fragmentovat ukazuje jak `FlashTrackBar` vlastního ovládacího prvku definuje vlastní události `ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="ce534-106">The following code fragment shows how the `FlashTrackBar` custom control defines a custom event, `ValueChanged`.</span></span> <span data-ttu-id="ce534-107">Pro kompletní kód `FlashTrackBar` ukázkové najdete v tématu [postupy: vytvoření Windows Forms ovládací prvek, zobrazuje průběh](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="ce534-107">For the complete code for the `FlashTrackBar` sample, see the [How to: Create a Windows Forms Control That Shows Progress](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
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
   protected virtual void OnValueChanged(EventArgs e) {  
      if (ValueChanged != null) {  
         ValueChanged(this, e);  
      }  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce534-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce534-108">See Also</span></span>  
 [<span data-ttu-id="ce534-109">Události v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ce534-109">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 [<span data-ttu-id="ce534-110">Události</span><span class="sxs-lookup"><span data-stu-id="ce534-110">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="ce534-111">Události</span><span class="sxs-lookup"><span data-stu-id="ce534-111">Events</span></span>](../../../../docs/standard/events/index.md)
