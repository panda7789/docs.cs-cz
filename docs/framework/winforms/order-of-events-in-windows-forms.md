---
title: "Řazení událostí ve Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [Windows Forms], order of
- focus event order
- application shutdown event order
- sequence [Windows Forms], of events
- validation events [Windows Forms], order of
- application startup event order
ms.assetid: e81db09b-4453-437f-b78a-62d7cd5c9829
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f822133b44f0f32224402463b4332811f8cd52b5
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="order-of-events-in-windows-forms"></a>Řazení událostí ve Windows Forms
Pořadí, ve kterém události jsou vyvolány v aplikacích Windows Forms je zajímají hlavně o vývojáři nevadí, každá z těchto událostí zase zpracování. Když stav vyžaduje pečlivou zpracování události, například když jsou překreslování části formuláře, je nutné je třeba znát přesné pořadí, ve kterém jsou vyvolány události za běhu. Toto téma obsahuje některé podrobnosti v řádu události během několika fázích důležité v životního cyklu aplikací a ovládací prvky. Konkrétní podrobnosti o pořadí vstupních událostech myši najdete v tématu [události myši ve Windows Forms](../../../docs/framework/winforms/mouse-events-in-windows-forms.md). Přehled událostí ve Windows Forms najdete v tématu [Přehled událostí](../../../docs/framework/winforms/events-overview-windows-forms.md). Podrobnosti o způsob vytvoření obslužných rutin událostí najdete v tématu [Přehled obslužných rutin událostí](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).  
  
## <a name="application-startup-and-shutdown-events"></a>Spuštění aplikace a událostí vypnutí  
 <xref:System.Windows.Forms.Form> a <xref:System.Windows.Forms.Control> třídy poskytují sadu události související s aplikací spuštění a vypnutí. Při spuštění aplikace Windows Forms události spuštění hlavního formuláře jsou vyvolány v následujícím pořadí:  
  
-   <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Activated?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Shown?displayProperty=nameWithType>  
  
 Až se aplikace zavře, události vypnutí hlavního formuláře jsou vyvolány v následujícím pořadí:  
  
-   <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Closed?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.FormClosed?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.Form.Deactivate?displayProperty=nameWithType>  
  
 <xref:System.Windows.Forms.Application.ApplicationExit> Události <xref:System.Windows.Forms.Application> třída je vyvolána po události vypnutí hlavního formuláře.  
  
> [!NOTE]
>  Visual Basic 2005 zahrnuje další události aplikace, jako například <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> a <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.  
  
## <a name="focus-and-validation-events"></a>Fokus a události ověření  
 Pokud změníte fokus pomocí klávesnice (karta, SHIFT + TAB a tak dále), pomocí volání metody <xref:System.Windows.Forms.Control.Select%2A> nebo <xref:System.Windows.Forms.Control.SelectNextControl%2A> metody, nebo nastavením <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> vlastnost aktuálního formuláře, události fokus <xref:System.Windows.Forms.Control> třídy, ke kterým došlo v následujícím pořadí :  
  
-   <xref:System.Windows.Forms.Control.Enter>  
  
-   <xref:System.Windows.Forms.Control.GotFocus>  
  
-   <xref:System.Windows.Forms.Control.Leave>  
  
-   <xref:System.Windows.Forms.Control.Validating>  
  
-   <xref:System.Windows.Forms.Control.Validated>  
  
-   <xref:System.Windows.Forms.Control.LostFocus>  
  
 Pokud změníte fokus pomocí myši nebo volání <xref:System.Windows.Forms.Control.Focus%2A> metoda, události fokus <xref:System.Windows.Forms.Control> třídy, ke kterým došlo v následujícím pořadí:  
  
-   <xref:System.Windows.Forms.Control.Enter>  
  
-   <xref:System.Windows.Forms.Control.GotFocus>  
  
-   <xref:System.Windows.Forms.Control.LostFocus>  
  
-   <xref:System.Windows.Forms.Control.Leave>  
  
-   <xref:System.Windows.Forms.Control.Validating>  
  
-   <xref:System.Windows.Forms.Control.Validated>  
  
## <a name="see-also"></a>Viz také  
 [Vytváření obslužných rutin událostí v systému Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
