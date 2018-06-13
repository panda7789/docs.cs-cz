---
title: Události v ovládacích prvcích Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: 5d51b6a71bffb546c85ba253181453f6deecfa64
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525880"
---
# <a name="events-in-windows-forms-controls"></a><span data-ttu-id="7cdbe-102">Události v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7cdbe-102">Events in Windows Forms Controls</span></span>
<span data-ttu-id="7cdbe-103">Ovládacího prvku Windows Forms dědí více než 60 události z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7cdbe-103">A Windows Forms control inherits more than sixty events from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7cdbe-104">Patří mezi ně <xref:System.Windows.Forms.Control.Paint> událost, což způsobí, že řízení, které se mají vykreslovat, události související s zobrazení časového období, jako <xref:System.Windows.Forms.Control.Resize> a <xref:System.Windows.Forms.Control.Layout> události a nízké úrovně události myši a klávesnice.</span><span class="sxs-lookup"><span data-stu-id="7cdbe-104">These include the <xref:System.Windows.Forms.Control.Paint> event, which causes a control to be drawn, events related to displaying a window, such as the <xref:System.Windows.Forms.Control.Resize> and <xref:System.Windows.Forms.Control.Layout> events, and low-level mouse and keyboard events.</span></span> <span data-ttu-id="7cdbe-105">Některé nízké úrovně události jsou syntetizován podle <xref:System.Windows.Forms.Control> do sémantického událostí jako <xref:System.Windows.Forms.Control.Click> a <xref:System.Windows.Forms.Control.DoubleClick>.</span><span class="sxs-lookup"><span data-stu-id="7cdbe-105">Some low-level events are synthesized by <xref:System.Windows.Forms.Control> into semantic events such as <xref:System.Windows.Forms.Control.Click> and <xref:System.Windows.Forms.Control.DoubleClick>.</span></span> <span data-ttu-id="7cdbe-106">Podrobnosti o zděděné události najdete v tématu <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="7cdbe-106">For details about inherited events, see <xref:System.Windows.Forms.Control>.</span></span>  
  
 <span data-ttu-id="7cdbe-107">Pokud vaše vlastní ovládací prvek musí přepsat funkci zděděné událostí, mají přednost před zděděnou `On` *EventName* metody místo připojení delegáta.</span><span class="sxs-lookup"><span data-stu-id="7cdbe-107">If your custom control needs to override inherited event functionality, override the inherited `On`*EventName* method instead of attaching a delegate.</span></span> <span data-ttu-id="7cdbe-108">Pokud nejste obeznámeni s modelem události v rozhraní .NET Framework, přečtěte si téma [vyvolání události ze součásti](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).</span><span class="sxs-lookup"><span data-stu-id="7cdbe-108">If you are not familiar with the event model in the .NET Framework, see [Raising Events from a Component](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cdbe-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="7cdbe-109">See Also</span></span>  
 [<span data-ttu-id="7cdbe-110">Přepsání metody OnPaint</span><span class="sxs-lookup"><span data-stu-id="7cdbe-110">Overriding the OnPaint Method</span></span>](../../../../docs/framework/winforms/controls/overriding-the-onpaint-method.md)  
 [<span data-ttu-id="7cdbe-111">Zpracování uživatelského vstupu</span><span class="sxs-lookup"><span data-stu-id="7cdbe-111">Handling User Input</span></span>](../../../../docs/framework/winforms/controls/handling-user-input.md)  
 [<span data-ttu-id="7cdbe-112">Definování události</span><span class="sxs-lookup"><span data-stu-id="7cdbe-112">Defining an Event</span></span>](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [<span data-ttu-id="7cdbe-113">Události</span><span class="sxs-lookup"><span data-stu-id="7cdbe-113">Events</span></span>](../../../../docs/standard/events/index.md)
