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
ms.openlocfilehash: 24d48a9dfdf10601099333e52073bb7fa3579beb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61800769"
---
# <a name="order-of-events-in-windows-forms"></a>Řazení událostí ve Windows Forms
Pořadí, ve kterém jsou vyvolány události v aplikacích Windows Forms je zajímavé především pro vývojáře se každá z těchto událostí zase zpracování. Když situace vyžaduje pečlivou zpracování událostí, například když jsou překreslování části formuláře, je nezbytné povědomí o přesné pořadí, ve kterém jsou vyvolány události v době běhu. Toto téma obsahuje některé podrobnosti pořadí událostí během několik důležitých fází životního cyklu aplikací a ovládací prvky. Konkrétní podrobnosti o pořadí vstupních událostí myši najdete v tématu [události myši ve Windows Forms](mouse-events-in-windows-forms.md). Přehled událostí ve Windows Forms, naleznete v tématu [Přehled událostí](events-overview-windows-forms.md). Podrobnosti o strukturu obslužné rutiny událostí najdete v tématu [Přehled obslužných rutin událostí](event-handlers-overview-windows-forms.md).  
  
## <a name="application-startup-and-shutdown-events"></a>Události ukončení a spuštění aplikace  
 <xref:System.Windows.Forms.Form> a <xref:System.Windows.Forms.Control> třídy poskytují sadu události související s aplikací při spuštění a ukončení. Při spuštění aplikace modelu Windows Forms jsou vyvolány události spuštění hlavního formuláře v tomto pořadí:  
  
- <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Activated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Shown?displayProperty=nameWithType>  
  
 Po zavření aplikace jsou vyvolány události vypnutí hlavního formuláře v následujícím pořadí:  
  
- <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Closed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Deactivate?displayProperty=nameWithType>  
  
 <xref:System.Windows.Forms.Application.ApplicationExit> Událost <xref:System.Windows.Forms.Application> třídy je vyvolán po vypnutí události hlavního formuláře.  
  
> [!NOTE]
>  Visual Basic 2005 zahrnuje další události aplikace, jako například <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> a <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>.  
  
## <a name="focus-and-validation-events"></a>Fokus a události ověřování  
 Při změně fokusu pomocí klávesnice (TAB, SHIFT + TAB a podobně), voláním <xref:System.Windows.Forms.Control.Select%2A> nebo <xref:System.Windows.Forms.Control.SelectNextControl%2A> metod, nebo nastavením <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> vlastnost pro aktuální formulář se události fokusu z <xref:System.Windows.Forms.Control> třídy dojít v uvedeném pořadí :  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
 Při změně fokusu pomocí myší nebo voláním <xref:System.Windows.Forms.Control.Focus%2A> metody, události fokusu <xref:System.Windows.Forms.Control> třídy vyskytují v následujícím pořadí:  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
## <a name="see-also"></a>Viz také:

- [Vytváření obslužných rutin událostí ve Windows Forms](creating-event-handlers-in-windows-forms.md)
