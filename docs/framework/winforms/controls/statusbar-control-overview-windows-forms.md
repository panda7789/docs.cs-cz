---
title: StatusBar – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: 5fdefa7d7e7c7ef543f677be7beb61dfee54e077
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009683"
---
# <a name="statusbar-control-overview-windows-forms"></a><span data-ttu-id="b7d20-102">StatusBar – přehled ovládacího prvku (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="b7d20-102">StatusBar Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="b7d20-103"><xref:System.Windows.Forms.StatusStrip> a <xref:System.Windows.Forms.ToolStripStatusLabel> ovládací prvky nahradit a přidání funkce, které <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> řídí; však <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> ovládací prvky se zachovají pro zpětnou kompatibilitu a budoucí použití, pokud jste Zvolte.</span><span class="sxs-lookup"><span data-stu-id="b7d20-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="b7d20-104">Windows Forms [ovládacího prvku StatusBar](statusbar-control-windows-forms.md) se používá ve formulářích jako oblast, obvykle se zobrazí v dolní části okna, ve kterém může aplikace zobrazit různé druhy informací o stavu.</span><span class="sxs-lookup"><span data-stu-id="b7d20-104">The Windows Forms [StatusBar Control](statusbar-control-windows-forms.md) is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="b7d20-105"><xref:System.Windows.Forms.StatusBar> ovládací prvky můžete mít stav panelu na nich zobrazit panely text nebo ikony k označení stavu nebo řady ikony animace, který indikuje, že proces funguje; například [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] označující, že je dokument uložen.</span><span class="sxs-lookup"><span data-stu-id="b7d20-105"><xref:System.Windows.Forms.StatusBar> controls can have status bar panels on them that display text or icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] indicating that the document is being saved.</span></span>  
  
## <a name="using-the-statusbar-control"></a><span data-ttu-id="b7d20-106">Použití ovládacího prvku StatusBar</span><span class="sxs-lookup"><span data-stu-id="b7d20-106">Using the StatusBar Control</span></span>  
 <span data-ttu-id="b7d20-107">Aplikace Internet Explorer stavový řádek používá k označení adresy URL stránky při umístění ukazatele myši nad hypertextový odkaz. [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] poskytuje informace o umístění stránky, umístění oddílu a úpravy v režimu, jako je přepisování a sledování revizí; a sady Visual Studio využívá stavového řádku, abychom zajistili kontextové informace, například o tom, jak pracovat s ukotvitelných oken jako ukotvené nebo plovoucí.</span><span class="sxs-lookup"><span data-stu-id="b7d20-107">Internet Explorer uses a status bar to indicate the URL of a page when the mouse rolls over the hyperlink; [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] gives you information on page location, section location, and editing modes such as overtype and revision tracking; and Visual Studio uses the status bar to give context-sensitive information, such as telling you how to manipulate dockable windows as either docked or floating.</span></span>  
  
 <span data-ttu-id="b7d20-108">Do jedné zprávy ve stavovém řádku můžete zobrazit tak, že nastavíte <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> vlastnost `false` (výchozí) a nastavení <xref:System.Windows.Forms.StatusBar.Text%2A> vlastnost stavový řádek textu, které se mají zobrazit ve stavovém řádku.</span><span class="sxs-lookup"><span data-stu-id="b7d20-108">You can display a single message on the status bar by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `false` (the default) and setting the <xref:System.Windows.Forms.StatusBar.Text%2A> property of the status bar to the text you want to appear in the status bar.</span></span> <span data-ttu-id="b7d20-109">Stavový řádek lze rozdělit do panelů k zobrazení více než jeden typ informací tak, že nastavíte <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> vlastnost `true` a použití <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> metoda <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span><span class="sxs-lookup"><span data-stu-id="b7d20-109">You can divide the status bar into panels to display more than one type of information by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true` and using the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> method of <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7d20-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7d20-110">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="b7d20-111">Postupy: Určení panelu v ovládacím prvku Windows Forms StatusBar označeného kliknutím</span><span class="sxs-lookup"><span data-stu-id="b7d20-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
