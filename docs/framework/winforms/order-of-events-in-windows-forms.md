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
ms.openlocfilehash: a88fd7b912063af5961a2bb366b42b0f67411f5f
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720287"
---
# <a name="order-of-events-in-windows-forms"></a><span data-ttu-id="cd544-102">Řazení událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cd544-102">Order of Events in Windows Forms</span></span>
<span data-ttu-id="cd544-103">Pořadí, ve kterém jsou vyvolány události v aplikacích Windows Forms je zajímavé především pro vývojáře se každá z těchto událostí zase zpracování.</span><span class="sxs-lookup"><span data-stu-id="cd544-103">The order in which events are raised in Windows Forms applications is of particular interest to developers concerned with handling each of these events in turn.</span></span> <span data-ttu-id="cd544-104">Když situace vyžaduje pečlivou zpracování událostí, například když jsou překreslování části formuláře, je nezbytné povědomí o přesné pořadí, ve kterém jsou vyvolány události v době běhu.</span><span class="sxs-lookup"><span data-stu-id="cd544-104">When a situation calls for meticulous handling of events, such as when you are redrawing parts of the form, an awareness of the precise order in which events are raised at run time is necessary.</span></span> <span data-ttu-id="cd544-105">Toto téma obsahuje některé podrobnosti pořadí událostí během několik důležitých fází životního cyklu aplikací a ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="cd544-105">This topic provides some details on the order of events during several important stages in the lifetime of applications and controls.</span></span> <span data-ttu-id="cd544-106">Konkrétní podrobnosti o pořadí vstupních událostí myši najdete v tématu [události myši ve Windows Forms](mouse-events-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="cd544-106">For specific details about the order of mouse input events, see [Mouse Events in Windows Forms](mouse-events-in-windows-forms.md).</span></span> <span data-ttu-id="cd544-107">Přehled událostí ve Windows Forms, naleznete v tématu [Přehled událostí](events-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="cd544-107">For an overview of events in Windows Forms, see [Events Overview](events-overview-windows-forms.md).</span></span> <span data-ttu-id="cd544-108">Podrobnosti o strukturu obslužné rutiny událostí najdete v tématu [Přehled obslužných rutin událostí](event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="cd544-108">For details about the makeup of event handlers, see [Event Handlers Overview](event-handlers-overview-windows-forms.md).</span></span>  
  
## <a name="application-startup-and-shutdown-events"></a><span data-ttu-id="cd544-109">Události ukončení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="cd544-109">Application Startup and Shutdown Events</span></span>  
 <span data-ttu-id="cd544-110"><xref:System.Windows.Forms.Form> a <xref:System.Windows.Forms.Control> třídy poskytují sadu události související s aplikací při spuštění a ukončení.</span><span class="sxs-lookup"><span data-stu-id="cd544-110">The <xref:System.Windows.Forms.Form> and <xref:System.Windows.Forms.Control> classes expose a set of events related to application startup and shutdown.</span></span> <span data-ttu-id="cd544-111">Při spuštění aplikace modelu Windows Forms jsou vyvolány události spuštění hlavního formuláře v tomto pořadí:</span><span class="sxs-lookup"><span data-stu-id="cd544-111">When a Windows Forms application starts, the startup events of the main form are raised in the following order:</span></span>  
  
-   <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Activated?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Shown?displayProperty=nameWithType>  
  
 <span data-ttu-id="cd544-112">Po zavření aplikace jsou vyvolány události vypnutí hlavního formuláře v následujícím pořadí:</span><span class="sxs-lookup"><span data-stu-id="cd544-112">When an application closes, the shutdown events of the main form are raised in the following order:</span></span>  
  
-   <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Closed?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.FormClosed?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Deactivate?displayProperty=nameWithType>  
  
 <span data-ttu-id="cd544-113"><xref:System.Windows.Forms.Application.ApplicationExit> Událost <xref:System.Windows.Forms.Application> třídy je vyvolán po vypnutí události hlavního formuláře.</span><span class="sxs-lookup"><span data-stu-id="cd544-113">The <xref:System.Windows.Forms.Application.ApplicationExit> event of the <xref:System.Windows.Forms.Application> class is raised after the shutdown events of the main form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cd544-114">Visual Basic 2005 zahrnuje další události aplikace, jako například <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> a <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cd544-114">Visual Basic 2005 includes additional application events, such as <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> and <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.</span></span>  
  
## <a name="focus-and-validation-events"></a><span data-ttu-id="cd544-115">Fokus a události ověřování</span><span class="sxs-lookup"><span data-stu-id="cd544-115">Focus and Validation Events</span></span>  
 <span data-ttu-id="cd544-116">Při změně fokusu pomocí klávesnice (TAB, SHIFT + TAB a podobně), voláním <xref:System.Windows.Forms.Control.Select%2A> nebo <xref:System.Windows.Forms.Control.SelectNextControl%2A> metod, nebo nastavením <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> vlastnost pro aktuální formulář se události fokusu z <xref:System.Windows.Forms.Control> třídy dojít v uvedeném pořadí :</span><span class="sxs-lookup"><span data-stu-id="cd544-116">When you change the focus by using the keyboard (TAB, SHIFT+TAB, and so on), by calling the <xref:System.Windows.Forms.Control.Select%2A> or <xref:System.Windows.Forms.Control.SelectNextControl%2A> methods, or by setting the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property to the current form, focus events of the <xref:System.Windows.Forms.Control> class occur in the following order:</span></span>  
  
-   <xref:System.Windows.Forms.Control.Enter>  
  
-   <xref:System.Windows.Forms.Control.GotFocus>  
  
-   <xref:System.Windows.Forms.Control.Leave>  
  
-   <xref:System.Windows.Forms.Control.Validating>  
  
-   <xref:System.Windows.Forms.Control.Validated>  
  
-   <xref:System.Windows.Forms.Control.LostFocus>  
  
 <span data-ttu-id="cd544-117">Při změně fokusu pomocí myší nebo voláním <xref:System.Windows.Forms.Control.Focus%2A> metody, události fokusu <xref:System.Windows.Forms.Control> třídy vyskytují v následujícím pořadí:</span><span class="sxs-lookup"><span data-stu-id="cd544-117">When you change the focus by using the mouse or by calling the <xref:System.Windows.Forms.Control.Focus%2A> method, focus events of the <xref:System.Windows.Forms.Control> class occur in the following order:</span></span>  
  
-   <xref:System.Windows.Forms.Control.Enter>  
  
-   <xref:System.Windows.Forms.Control.GotFocus>  
  
-   <xref:System.Windows.Forms.Control.LostFocus>  
  
-   <xref:System.Windows.Forms.Control.Leave>  
  
-   <xref:System.Windows.Forms.Control.Validating>  
  
-   <xref:System.Windows.Forms.Control.Validated>  
  
## <a name="see-also"></a><span data-ttu-id="cd544-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd544-118">See also</span></span>
- [<span data-ttu-id="cd544-119">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cd544-119">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
