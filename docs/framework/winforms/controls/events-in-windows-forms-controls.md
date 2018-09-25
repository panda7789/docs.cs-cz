---
title: Události v ovládacích prvcích Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: d18938565c302be085b7ac51f878d83ae5ab533d
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2018
ms.locfileid: "47027895"
---
# <a name="events-in-windows-forms-controls"></a><span data-ttu-id="a1d7d-102">Události v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a1d7d-102">Events in Windows Forms Controls</span></span>
<span data-ttu-id="a1d7d-103">Dědí z více než 60 události ovládacího prvku Windows Forms <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a1d7d-103">A Windows Forms control inherits more than sixty events from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a1d7d-104">Patří mezi ně <xref:System.Windows.Forms.Control.Paint> událost, což způsobí, že ovládací prvek chcete kreslit, události související s zobrazení okna, například <xref:System.Windows.Forms.Control.Resize> a <xref:System.Windows.Forms.Control.Layout> události a nízké úrovně události myši a klávesnice.</span><span class="sxs-lookup"><span data-stu-id="a1d7d-104">These include the <xref:System.Windows.Forms.Control.Paint> event, which causes a control to be drawn, events related to displaying a window, such as the <xref:System.Windows.Forms.Control.Resize> and <xref:System.Windows.Forms.Control.Layout> events, and low-level mouse and keyboard events.</span></span> <span data-ttu-id="a1d7d-105">Některé události nízké úrovně jsou syntetizovat podle <xref:System.Windows.Forms.Control> do sémantického událostech, například <xref:System.Windows.Forms.Control.Click> a <xref:System.Windows.Forms.Control.DoubleClick>.</span><span class="sxs-lookup"><span data-stu-id="a1d7d-105">Some low-level events are synthesized by <xref:System.Windows.Forms.Control> into semantic events such as <xref:System.Windows.Forms.Control.Click> and <xref:System.Windows.Forms.Control.DoubleClick>.</span></span> <span data-ttu-id="a1d7d-106">Podrobnosti o zděděné události najdete v tématu <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="a1d7d-106">For details about inherited events, see <xref:System.Windows.Forms.Control>.</span></span>  
  
 <span data-ttu-id="a1d7d-107">Pokud vaše vlastní ovládací prvek musí přepsat funkci zděděných událostí, přepsat zděděnou `On` *EventName* metoda místo připojením delegáta.</span><span class="sxs-lookup"><span data-stu-id="a1d7d-107">If your custom control needs to override inherited event functionality, override the inherited `On`*EventName* method instead of attaching a delegate.</span></span> <span data-ttu-id="a1d7d-108">Pokud nejste obeznámeni s modelem události v rozhraní .NET Framework, přečtěte si téma [vyvolávání událostí z komponenty](https://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).</span><span class="sxs-lookup"><span data-stu-id="a1d7d-108">If you are not familiar with the event model in the .NET Framework, see [Raising Events from a Component](https://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1d7d-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1d7d-109">See Also</span></span>  
 [<span data-ttu-id="a1d7d-110">Přepsání metody OnPaint</span><span class="sxs-lookup"><span data-stu-id="a1d7d-110">Overriding the OnPaint Method</span></span>](../../../../docs/framework/winforms/controls/overriding-the-onpaint-method.md)  
 [<span data-ttu-id="a1d7d-111">Zpracování uživatelského vstupu</span><span class="sxs-lookup"><span data-stu-id="a1d7d-111">Handling User Input</span></span>](../../../../docs/framework/winforms/controls/handling-user-input.md)  
 [<span data-ttu-id="a1d7d-112">Definování události</span><span class="sxs-lookup"><span data-stu-id="a1d7d-112">Defining an Event</span></span>](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [<span data-ttu-id="a1d7d-113">Události</span><span class="sxs-lookup"><span data-stu-id="a1d7d-113">Events</span></span>](../../../../docs/standard/events/index.md)
