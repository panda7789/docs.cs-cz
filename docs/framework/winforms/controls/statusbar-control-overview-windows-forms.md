---
title: Přehled ovládacího prvku StatusBar
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: b0b97bc3cb0291871e1fd113d82d0b480b53cdba
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742874"
---
# <a name="statusbar-control-overview-windows-forms"></a><span data-ttu-id="b9a9b-102">StatusBar – přehled ovládacího prvku (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="b9a9b-102">StatusBar Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="b9a9b-103">Ovládací prvky <xref:System.Windows.Forms.StatusStrip> a <xref:System.Windows.Forms.ToolStripStatusLabel> nahrazují a přidávají funkce ovládacím prvkům <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel>; ovládací prvky <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> se však uchovávají pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.</span><span class="sxs-lookup"><span data-stu-id="b9a9b-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="b9a9b-104">[Ovládací prvek](statusbar-control-windows-forms.md) model Windows Forms stavový řádek se používá ve formulářích jako oblast, obvykle se zobrazuje v dolní části okna, kde aplikace může zobrazit různé druhy informací o stavu.</span><span class="sxs-lookup"><span data-stu-id="b9a9b-104">The Windows Forms [StatusBar Control](statusbar-control-windows-forms.md) is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="b9a9b-105">ovládací prvky <xref:System.Windows.Forms.StatusBar> mohou mít panely na stavovém řádku, které zobrazují text nebo ikony k označení stavu, nebo řadu ikon v animaci, která indikuje, že proces pracuje. například Microsoft Word značí, že se dokument ukládá.</span><span class="sxs-lookup"><span data-stu-id="b9a9b-105"><xref:System.Windows.Forms.StatusBar> controls can have status bar panels on them that display text or icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, Microsoft Word indicating that the document is being saved.</span></span>  
  
## <a name="using-the-statusbar-control"></a><span data-ttu-id="b9a9b-106">Použití ovládacího prvku stavový řádek</span><span class="sxs-lookup"><span data-stu-id="b9a9b-106">Using the StatusBar Control</span></span>  
 <span data-ttu-id="b9a9b-107">Internet Explorer používá stavový řádek k označení adresy URL stránky, když se ukazatel myši přesune na hypertextový odkaz. V aplikaci Microsoft Word získáte informace o umístění stránky, umístění oddílu a režimech úprav, například přepisu a sledování revizí. a Visual Studio používá stavový řádek k poskytnutí kontextově citlivých informací, jako je například oznámení, jak pracovat s ukotvit okny buď jako docked, nebo float.</span><span class="sxs-lookup"><span data-stu-id="b9a9b-107">Internet Explorer uses a status bar to indicate the URL of a page when the mouse rolls over the hyperlink; Microsoft Word gives you information on page location, section location, and editing modes such as overtype and revision tracking; and Visual Studio uses the status bar to give context-sensitive information, such as telling you how to manipulate dockable windows as either docked or floating.</span></span>  
  
 <span data-ttu-id="b9a9b-108">Můžete zobrazit jednu zprávu na stavovém řádku nastavením vlastnosti <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> na `false` (výchozí nastavení) a nastavením vlastnosti <xref:System.Windows.Forms.StatusBar.Text%2A> stavového řádku na text, který se má zobrazit ve stavovém řádku.</span><span class="sxs-lookup"><span data-stu-id="b9a9b-108">You can display a single message on the status bar by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `false` (the default) and setting the <xref:System.Windows.Forms.StatusBar.Text%2A> property of the status bar to the text you want to appear in the status bar.</span></span> <span data-ttu-id="b9a9b-109">Stavový řádek můžete rozdělit na panely a zobrazit tak více než jeden typ informací nastavením vlastnosti <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> na `true` a pomocí metody <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span><span class="sxs-lookup"><span data-stu-id="b9a9b-109">You can divide the status bar into panels to display more than one type of information by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true` and using the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> method of <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9a9b-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9a9b-110">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="b9a9b-111">Postupy: Určení panelu v ovládacím prvku Windows Forms StatusBar označeného kliknutím</span><span class="sxs-lookup"><span data-stu-id="b9a9b-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
