---
title: "StatusBar – přehled ovládacího prvku (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: df8e6b8484cf3b35c684445445ddc41adc358698
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="statusbar-control-overview-windows-forms"></a><span data-ttu-id="00289-102">StatusBar – přehled ovládacího prvku (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="00289-102">StatusBar Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="00289-103"><xref:System.Windows.Forms.StatusStrip> a <xref:System.Windows.Forms.ToolStripStatusLabel> ovládací prvky nahradit a přidání funkcí do <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> řídí; však <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> ovládací prvky jsou uchovány pro zpětnou kompatibilitu a budoucí použití, pokud jste Vyberte.</span><span class="sxs-lookup"><span data-stu-id="00289-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="00289-104">Windows Forms [StatusBar – ovládací prvek](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) se používá ve formulářích jako oblast, obvykle zobrazují v dolní části okna, ve kterém aplikace můžete zobrazit různé typy informací o stavu.</span><span class="sxs-lookup"><span data-stu-id="00289-104">The Windows Forms [StatusBar Control](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="00289-105"><xref:System.Windows.Forms.StatusBar>ovládací prvky může mít stav panely panelu na nich, které zobrazení textu nebo ikony, které označují stav nebo řadu ikony v animace, který indikuje, že proces je v provozu. například [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] označující, že dokument je uložen.</span><span class="sxs-lookup"><span data-stu-id="00289-105"><xref:System.Windows.Forms.StatusBar> controls can have status bar panels on them that display text or icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] indicating that the document is being saved.</span></span>  
  
## <a name="using-the-statusbar-control"></a><span data-ttu-id="00289-106">Použití ovládacího prvku StatusBar</span><span class="sxs-lookup"><span data-stu-id="00289-106">Using the StatusBar Control</span></span>  
 <span data-ttu-id="00289-107">Internet Explorer pomocí stavového řádku označuje adresu URL stránky při umístění ukazatele myši na hypertextový odkaz; [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] získáte informace na stránce umístění, část umístění a úpravy v režimu například přepisování a revize sledování; a [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] používá stavový řádek umožnit kontextové informace, například o tom, jak pracovat s lze ukotvit Windows jako ukotveného nebo plovoucí.</span><span class="sxs-lookup"><span data-stu-id="00289-107">Internet Explorer uses a status bar to indicate the URL of a page when the mouse rolls over the hyperlink; [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] gives you information on page location, section location, and editing modes such as overtype and revision tracking; and [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] uses the status bar to give context-sensitive information, such as telling you how to manipulate dockable windows as either docked or floating.</span></span>  
  
 <span data-ttu-id="00289-108">Do jedné zprávy můžete zobrazit na stavovém řádku nastavením <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> vlastnost `false` (výchozí) a nastavení <xref:System.Windows.Forms.StatusBar.Text%2A> vlastnost stavový řádek na text, který se má zobrazit ve stavovém řádku.</span><span class="sxs-lookup"><span data-stu-id="00289-108">You can display a single message on the status bar by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `false` (the default) and setting the <xref:System.Windows.Forms.StatusBar.Text%2A> property of the status bar to the text you want to appear in the status bar.</span></span> <span data-ttu-id="00289-109">Stavový řádek lze rozdělit do panelů zobrazíte víc než jeden typ informací nastavením <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> vlastnost, která má `true` a pomocí <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> metodu <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span><span class="sxs-lookup"><span data-stu-id="00289-109">You can divide the status bar into panels to display more than one type of information by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true` and using the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> method of <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00289-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="00289-110">See Also</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [<span data-ttu-id="00289-111">Postupy: Určení panelu v ovládacím prvku Windows Forms StatusBar označeného kliknutím</span><span class="sxs-lookup"><span data-stu-id="00289-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)
