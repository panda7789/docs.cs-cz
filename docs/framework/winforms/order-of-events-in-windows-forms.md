---
title: Řazení událostí ve Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], order of
- focus event order
- application shutdown event order
- sequence [Windows Forms], of events
- validation events [Windows Forms], order of
- application startup event order
ms.assetid: e81db09b-4453-437f-b78a-62d7cd5c9829
ms.openlocfilehash: 10a6451827a16605ba738cf74b7f684b69adb5dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538467"
---
# <a name="order-of-events-in-windows-forms"></a><span data-ttu-id="165a7-102">Řazení událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="165a7-102">Order of Events in Windows Forms</span></span>
<span data-ttu-id="165a7-103">Pořadí, ve kterém události jsou vyvolány v aplikacích Windows Forms je zajímají hlavně o vývojáři nevadí, každá z těchto událostí zase zpracování.</span><span class="sxs-lookup"><span data-stu-id="165a7-103">The order in which events are raised in Windows Forms applications is of particular interest to developers concerned with handling each of these events in turn.</span></span> <span data-ttu-id="165a7-104">Když stav vyžaduje pečlivou zpracování události, například když jsou překreslování části formuláře, je nutné je třeba znát přesné pořadí, ve kterém jsou vyvolány události za běhu.</span><span class="sxs-lookup"><span data-stu-id="165a7-104">When a situation calls for meticulous handling of events, such as when you are redrawing parts of the form, an awareness of the precise order in which events are raised at run time is necessary.</span></span> <span data-ttu-id="165a7-105">Toto téma obsahuje některé podrobnosti v řádu události během několika fázích důležité v životního cyklu aplikací a ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="165a7-105">This topic provides some details on the order of events during several important stages in the lifetime of applications and controls.</span></span> <span data-ttu-id="165a7-106">Konkrétní podrobnosti o pořadí vstupních událostech myši najdete v tématu [události myši ve Windows Forms](../../../docs/framework/winforms/mouse-events-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="165a7-106">For specific details about the order of mouse input events, see [Mouse Events in Windows Forms](../../../docs/framework/winforms/mouse-events-in-windows-forms.md).</span></span> <span data-ttu-id="165a7-107">Přehled událostí ve Windows Forms najdete v tématu [Přehled událostí](../../../docs/framework/winforms/events-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="165a7-107">For an overview of events in Windows Forms, see [Events Overview](../../../docs/framework/winforms/events-overview-windows-forms.md).</span></span> <span data-ttu-id="165a7-108">Podrobnosti o způsob vytvoření obslužných rutin událostí najdete v tématu [Přehled obslužných rutin událostí](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="165a7-108">For details about the makeup of event handlers, see [Event Handlers Overview](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span></span>  
  
## <a name="application-startup-and-shutdown-events"></a><span data-ttu-id="165a7-109">Spuštění aplikace a událostí vypnutí</span><span class="sxs-lookup"><span data-stu-id="165a7-109">Application Startup and Shutdown Events</span></span>  
 <span data-ttu-id="165a7-110"><xref:System.Windows.Forms.Form> a <xref:System.Windows.Forms.Control> třídy poskytují sadu události související s aplikací spuštění a vypnutí.</span><span class="sxs-lookup"><span data-stu-id="165a7-110">The <xref:System.Windows.Forms.Form> and <xref:System.Windows.Forms.Control> classes expose a set of events related to application startup and shutdown.</span></span> <span data-ttu-id="165a7-111">Při spuštění aplikace Windows Forms události spuštění hlavního formuláře jsou vyvolány v následujícím pořadí:</span><span class="sxs-lookup"><span data-stu-id="165a7-111">When a Windows Forms application starts, the startup events of the main form are raised in the following order:</span></span>  
  
-   <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Activated?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Shown?displayProperty=nameWithType>  
  
 <span data-ttu-id="165a7-112">Až se aplikace zavře, události vypnutí hlavního formuláře jsou vyvolány v následujícím pořadí:</span><span class="sxs-lookup"><span data-stu-id="165a7-112">When an application closes, the shutdown events of the main form are raised in the following order:</span></span>  
  
-   <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Closed?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.FormClosed?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Deactivate?displayProperty=nameWithType>  
  
 <span data-ttu-id="165a7-113"><xref:System.Windows.Forms.Application.ApplicationExit> Události <xref:System.Windows.Forms.Application> třída je vyvolána po události vypnutí hlavního formuláře.</span><span class="sxs-lookup"><span data-stu-id="165a7-113">The <xref:System.Windows.Forms.Application.ApplicationExit> event of the <xref:System.Windows.Forms.Application> class is raised after the shutdown events of the main form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="165a7-114">Visual Basic 2005 zahrnuje další události aplikace, jako například <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> a <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="165a7-114">Visual Basic 2005 includes additional application events, such as <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> and <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.</span></span>  
  
## <a name="focus-and-validation-events"></a><span data-ttu-id="165a7-115">Fokus a události ověření</span><span class="sxs-lookup"><span data-stu-id="165a7-115">Focus and Validation Events</span></span>  
 <span data-ttu-id="165a7-116">Pokud změníte fokus pomocí klávesnice (karta, SHIFT + TAB a tak dále), pomocí volání metody <xref:System.Windows.Forms.Control.Select%2A> nebo <xref:System.Windows.Forms.Control.SelectNextControl%2A> metody, nebo nastavením <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> vlastnost aktuálního formuláře, události fokus <xref:System.Windows.Forms.Control> třídy, ke kterým došlo v následujícím pořadí :</span><span class="sxs-lookup"><span data-stu-id="165a7-116">When you change the focus by using the keyboard (TAB, SHIFT+TAB, and so on), by calling the <xref:System.Windows.Forms.Control.Select%2A> or <xref:System.Windows.Forms.Control.SelectNextControl%2A> methods, or by setting the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property to the current form, focus events of the <xref:System.Windows.Forms.Control> class occur in the following order:</span></span>  
  
-   <xref:System.Windows.Forms.Control.Enter>  
  
-   <xref:System.Windows.Forms.Control.GotFocus>  
  
-   <xref:System.Windows.Forms.Control.Leave>  
  
-   <xref:System.Windows.Forms.Control.Validating>  
  
-   <xref:System.Windows.Forms.Control.Validated>  
  
-   <xref:System.Windows.Forms.Control.LostFocus>  
  
 <span data-ttu-id="165a7-117">Pokud změníte fokus pomocí myši nebo volání <xref:System.Windows.Forms.Control.Focus%2A> metoda, události fokus <xref:System.Windows.Forms.Control> třídy, ke kterým došlo v následujícím pořadí:</span><span class="sxs-lookup"><span data-stu-id="165a7-117">When you change the focus by using the mouse or by calling the <xref:System.Windows.Forms.Control.Focus%2A> method, focus events of the <xref:System.Windows.Forms.Control> class occur in the following order:</span></span>  
  
-   <xref:System.Windows.Forms.Control.Enter>  
  
-   <xref:System.Windows.Forms.Control.GotFocus>  
  
-   <xref:System.Windows.Forms.Control.LostFocus>  
  
-   <xref:System.Windows.Forms.Control.Leave>  
  
-   <xref:System.Windows.Forms.Control.Validating>  
  
-   <xref:System.Windows.Forms.Control.Validated>  
  
## <a name="see-also"></a><span data-ttu-id="165a7-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="165a7-118">See Also</span></span>  
 [<span data-ttu-id="165a7-119">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="165a7-119">Creating Event Handlers in Windows Forms</span></span>](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
