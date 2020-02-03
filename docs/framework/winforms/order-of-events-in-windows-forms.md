---
title: Pořadí událostí
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], order of
- focus event order
- application shutdown event order
- sequence [Windows Forms], of events
- validation events [Windows Forms], order of
- application startup event order
ms.assetid: e81db09b-4453-437f-b78a-62d7cd5c9829
ms.openlocfilehash: 618ac5a6a6a32ae1a53fc60ac80700d7648c81a7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734858"
---
# <a name="order-of-events-in-windows-forms"></a><span data-ttu-id="7371c-102">Řazení událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7371c-102">Order of Events in Windows Forms</span></span>
<span data-ttu-id="7371c-103">Pořadí, ve kterém jsou události vyvolány v aplikacích model Windows Forms, jsou zvláštním zájmem vývojářů, kteří mají obavy, že se jednotlivé události zpracovávají.</span><span class="sxs-lookup"><span data-stu-id="7371c-103">The order in which events are raised in Windows Forms applications is of particular interest to developers concerned with handling each of these events in turn.</span></span> <span data-ttu-id="7371c-104">Když se situace zavolá na nejpreciznější zpracování událostí, jako je třeba při překreslení částí formuláře, je nutné určit přesné pořadí, ve kterém jsou události vyvolány v době běhu.</span><span class="sxs-lookup"><span data-stu-id="7371c-104">When a situation calls for meticulous handling of events, such as when you are redrawing parts of the form, an awareness of the precise order in which events are raised at run time is necessary.</span></span> <span data-ttu-id="7371c-105">V tomto tématu jsou uvedeny některé podrobnosti o pořadí událostí během několika důležitých fází životního cyklu aplikací a ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="7371c-105">This topic provides some details on the order of events during several important stages in the lifetime of applications and controls.</span></span> <span data-ttu-id="7371c-106">Konkrétní podrobnosti o pořadí událostí vstupu myši naleznete [v tématu události myši v model Windows Forms](mouse-events-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="7371c-106">For specific details about the order of mouse input events, see [Mouse Events in Windows Forms](mouse-events-in-windows-forms.md).</span></span> <span data-ttu-id="7371c-107">Přehled událostí v model Windows Forms najdete v tématu věnovaném [událostem Overview](events-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="7371c-107">For an overview of events in Windows Forms, see [Events Overview](events-overview-windows-forms.md).</span></span> <span data-ttu-id="7371c-108">Podrobnosti o strukturu obslužných rutin událostí najdete v tématu [Přehled obslužných rutin událostí](event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="7371c-108">For details about the makeup of event handlers, see [Event Handlers Overview](event-handlers-overview-windows-forms.md).</span></span>  
  
## <a name="application-startup-and-shutdown-events"></a><span data-ttu-id="7371c-109">Události spuštění a vypnutí aplikace</span><span class="sxs-lookup"><span data-stu-id="7371c-109">Application Startup and Shutdown Events</span></span>  
 <span data-ttu-id="7371c-110">Třídy <xref:System.Windows.Forms.Form> a <xref:System.Windows.Forms.Control> zveřejňují sadu událostí souvisejících s spuštěním a vypnutím aplikace.</span><span class="sxs-lookup"><span data-stu-id="7371c-110">The <xref:System.Windows.Forms.Form> and <xref:System.Windows.Forms.Control> classes expose a set of events related to application startup and shutdown.</span></span> <span data-ttu-id="7371c-111">Při spuštění aplikace model Windows Forms se události spuštění hlavního formuláře vyvolají v tomto pořadí:</span><span class="sxs-lookup"><span data-stu-id="7371c-111">When a Windows Forms application starts, the startup events of the main form are raised in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Activated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Shown?displayProperty=nameWithType>  
  
 <span data-ttu-id="7371c-112">Po zavření aplikace se události vypnutí hlavního formuláře vyvolají v tomto pořadí:</span><span class="sxs-lookup"><span data-stu-id="7371c-112">When an application closes, the shutdown events of the main form are raised in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Closed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Deactivate?displayProperty=nameWithType>  
  
 <span data-ttu-id="7371c-113">Událost <xref:System.Windows.Forms.Application.ApplicationExit> třídy <xref:System.Windows.Forms.Application> je vyvolána po událostech vypnutí hlavního formuláře.</span><span class="sxs-lookup"><span data-stu-id="7371c-113">The <xref:System.Windows.Forms.Application.ApplicationExit> event of the <xref:System.Windows.Forms.Application> class is raised after the shutdown events of the main form.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7371c-114">Visual Basic 2005 obsahuje další události aplikace, jako je například <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> a <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7371c-114">Visual Basic 2005 includes additional application events, such as <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> and <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.</span></span>  
  
## <a name="focus-and-validation-events"></a><span data-ttu-id="7371c-115">Události fokusu a ověření</span><span class="sxs-lookup"><span data-stu-id="7371c-115">Focus and Validation Events</span></span>  
 <span data-ttu-id="7371c-116">Když změníte fokus pomocí klávesnice (karta, SHIFT + TAB atd.), zavoláním metod <xref:System.Windows.Forms.Control.Select%2A> nebo <xref:System.Windows.Forms.Control.SelectNextControl%2A> nebo nastavením vlastnosti <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> na aktuální formulář, dojde k událostem <xref:System.Windows.Forms.Control> třídy v následujícím pořadí:</span><span class="sxs-lookup"><span data-stu-id="7371c-116">When you change the focus by using the keyboard (TAB, SHIFT+TAB, and so on), by calling the <xref:System.Windows.Forms.Control.Select%2A> or <xref:System.Windows.Forms.Control.SelectNextControl%2A> methods, or by setting the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property to the current form, focus events of the <xref:System.Windows.Forms.Control> class occur in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
 <span data-ttu-id="7371c-117">Když změníte fokus pomocí myši nebo voláním metody <xref:System.Windows.Forms.Control.Focus%2A>, dojde k událostem <xref:System.Windows.Forms.Control> třídy v následujícím pořadí:</span><span class="sxs-lookup"><span data-stu-id="7371c-117">When you change the focus by using the mouse or by calling the <xref:System.Windows.Forms.Control.Focus%2A> method, focus events of the <xref:System.Windows.Forms.Control> class occur in the following order:</span></span>  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
## <a name="see-also"></a><span data-ttu-id="7371c-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="7371c-118">See also</span></span>

- [<span data-ttu-id="7371c-119">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7371c-119">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
