---
title: StatusBar – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: 4e1816ef221641f5ad54fb429442ed43289b592a
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505421"
---
# <a name="statusbar-control-overview-windows-forms"></a><span data-ttu-id="83341-102">StatusBar – přehled ovládacího prvku (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="83341-102">StatusBar Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="83341-103"><xref:System.Windows.Forms.StatusStrip> a <xref:System.Windows.Forms.ToolStripStatusLabel> ovládací prvky nahradit a přidání funkce, které <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> řídí; však <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> ovládací prvky se zachovají pro zpětnou kompatibilitu a budoucí použití, pokud jste Zvolte.</span><span class="sxs-lookup"><span data-stu-id="83341-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="83341-104">Windows Forms [ovládacího prvku StatusBar](statusbar-control-windows-forms.md) se používá ve formulářích jako oblast, obvykle se zobrazí v dolní části okna, ve kterém může aplikace zobrazit různé druhy informací o stavu.</span><span class="sxs-lookup"><span data-stu-id="83341-104">The Windows Forms [StatusBar Control](statusbar-control-windows-forms.md) is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="83341-105"><xref:System.Windows.Forms.StatusBar> ovládací prvky můžete mít stav panelu na nich zobrazit panely text nebo ikony k označení stavu nebo řady ikony animace, který indikuje, že proces funguje; například Microsoft Word označující, že dokument se ukládá.</span><span class="sxs-lookup"><span data-stu-id="83341-105"><xref:System.Windows.Forms.StatusBar> controls can have status bar panels on them that display text or icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, Microsoft Word indicating that the document is being saved.</span></span>  
  
## <a name="using-the-statusbar-control"></a><span data-ttu-id="83341-106">Použití ovládacího prvku StatusBar</span><span class="sxs-lookup"><span data-stu-id="83341-106">Using the StatusBar Control</span></span>  
 <span data-ttu-id="83341-107">Aplikace Internet Explorer stavový řádek používá k označení adresy URL stránky při umístění ukazatele myši nad hypertextový odkaz. Aplikace Microsoft Word získáte informace o umístění stránky, umístění oddílu a úpravy režimech, např. přepisování a sledování; revizí a Visual Studio využívá stavového řádku, abychom zajistili kontextové informace, například o tom, jak k práci s jako ukotvené nebo plovoucí ukotvitelných oken.</span><span class="sxs-lookup"><span data-stu-id="83341-107">Internet Explorer uses a status bar to indicate the URL of a page when the mouse rolls over the hyperlink; Microsoft Word gives you information on page location, section location, and editing modes such as overtype and revision tracking; and Visual Studio uses the status bar to give context-sensitive information, such as telling you how to manipulate dockable windows as either docked or floating.</span></span>  
  
 <span data-ttu-id="83341-108">Do jedné zprávy ve stavovém řádku můžete zobrazit tak, že nastavíte <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> vlastnost `false` (výchozí) a nastavení <xref:System.Windows.Forms.StatusBar.Text%2A> vlastnost stavový řádek textu, které se mají zobrazit ve stavovém řádku.</span><span class="sxs-lookup"><span data-stu-id="83341-108">You can display a single message on the status bar by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `false` (the default) and setting the <xref:System.Windows.Forms.StatusBar.Text%2A> property of the status bar to the text you want to appear in the status bar.</span></span> <span data-ttu-id="83341-109">Stavový řádek lze rozdělit do panelů k zobrazení více než jeden typ informací tak, že nastavíte <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> vlastnost `true` a použití <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> metoda <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span><span class="sxs-lookup"><span data-stu-id="83341-109">You can divide the status bar into panels to display more than one type of information by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true` and using the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> method of <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83341-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="83341-110">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="83341-111">Postupy: Určení panelu v ovládacím prvku Windows Forms StatusBar označeného kliknutím</span><span class="sxs-lookup"><span data-stu-id="83341-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
