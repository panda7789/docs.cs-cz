---
title: StatusBar – ovládací prvek (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- StatusBar control [Windows Forms]
- status bars [Windows Forms], creating
ms.assetid: 6f543e27-cf78-4b7f-b4d0-6a8030155d48
ms.openlocfilehash: 72a93fc32715596efc7fb0f8b941e62f7019d06c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964423"
---
# <a name="statusbar-control-windows-forms"></a><span data-ttu-id="d25bf-102">StatusBar – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="d25bf-102">StatusBar Control (Windows Forms)</span></span>
> [!NOTE]
> <span data-ttu-id="d25bf-103">Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBar> ovládacímu prvku. ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. <xref:System.Windows.Forms.ToolStripStatusLabel></span><span class="sxs-lookup"><span data-stu-id="d25bf-103">The <xref:System.Windows.Forms.ToolStripStatusLabel> control replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control; however, the <xref:System.Windows.Forms.StatusBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="d25bf-104">Model Windows Forms <xref:System.Windows.Forms.StatusBar> ovládací prvek se používá ve formulářích jako oblast, obvykle se zobrazuje v dolní části okna, kde aplikace může zobrazit různé druhy informací o stavu.</span><span class="sxs-lookup"><span data-stu-id="d25bf-104">The Windows Forms <xref:System.Windows.Forms.StatusBar> control is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="d25bf-105"><xref:System.Windows.Forms.StatusBar>ovládací prvky mohou mít panely na stavovém panelu, které zobrazují ikony k označení stavu, nebo řadu ikon v animaci, která indikuje, že proces pracuje. například Microsoft Word značí, že se dokument ukládá.</span><span class="sxs-lookup"><span data-stu-id="d25bf-105"><xref:System.Windows.Forms.StatusBar> controls can have status-bar panels on them that display icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, Microsoft Word indicating that the document is being saved.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d25bf-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d25bf-106">In This Section</span></span>  
 [<span data-ttu-id="d25bf-107">Přehled ovládacího prvku StatusBar</span><span class="sxs-lookup"><span data-stu-id="d25bf-107">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)  
 <span data-ttu-id="d25bf-108">Zavádí obecné koncepce <xref:System.Windows.Forms.StatusBar> ovládacího prvku, které uživatelům umožňují zobrazit relevantní informace pro ovládací prvek, který má fokus.</span><span class="sxs-lookup"><span data-stu-id="d25bf-108">Introduces the general concepts of the <xref:System.Windows.Forms.StatusBar> control, which enables users to see relevant information for the control that has focus.</span></span>  
  
 [<span data-ttu-id="d25bf-109">Postupy: Přidání panelů do ovládacího prvku stavový řádek</span><span class="sxs-lookup"><span data-stu-id="d25bf-109">How to: Add Panels to a StatusBar Control</span></span>](how-to-add-panels-to-a-statusbar-control.md)  
 <span data-ttu-id="d25bf-110">Vysvětluje, jak přidat programovatelné panely do <xref:System.Windows.Forms.StatusBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d25bf-110">Explains how to add programmable panels to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="d25bf-111">Postupy: Určete, na který panel model Windows Forms ovládací prvek stavový řádek.</span><span class="sxs-lookup"><span data-stu-id="d25bf-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)  
 <span data-ttu-id="d25bf-112">Vysvětluje, jak zpracovávat <xref:System.Windows.Forms.Control.Click> události vyvolané <xref:System.Windows.Forms.StatusBar> z ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d25bf-112">Explains how to handle <xref:System.Windows.Forms.Control.Click> events raised from the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="d25bf-113">Postupy: Nastavení velikosti panelů stavového řádku</span><span class="sxs-lookup"><span data-stu-id="d25bf-113">How to: Set the Size of Status-Bar Panels</span></span>](how-to-set-the-size-of-status-bar-panels.md)  
 <span data-ttu-id="d25bf-114">Poskytuje podrobné informace o vlastnostech, které řídí chování funkcí Šířka a velikost panelů stavového řádku za běhu.</span><span class="sxs-lookup"><span data-stu-id="d25bf-114">Gives details on the properties that control the width and resize behavior of status-bar panels at run time.</span></span>  
  
 [<span data-ttu-id="d25bf-115">Návod: Aktualizace informací stavového řádku za běhu</span><span class="sxs-lookup"><span data-stu-id="d25bf-115">Walkthrough: Updating Status Bar Information at Run Time</span></span>](walkthrough-updating-status-bar-information-at-run-time.md)  
 <span data-ttu-id="d25bf-116">Vysvětluje, jak programově řídit data v panelu stavového řádku.</span><span class="sxs-lookup"><span data-stu-id="d25bf-116">Explains how to programmatically control the data within status-bar panels.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d25bf-117">Reference</span><span class="sxs-lookup"><span data-stu-id="d25bf-117">Reference</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <span data-ttu-id="d25bf-118">Poskytuje referenční informace o třídě a jejích členech.</span><span class="sxs-lookup"><span data-stu-id="d25bf-118">Provides reference information on the class and its members.</span></span>  
  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <span data-ttu-id="d25bf-119">Nahradí a přidá do <xref:System.Windows.Forms.StatusBar> ovládacího prvku funkce.</span><span class="sxs-lookup"><span data-stu-id="d25bf-119">Replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d25bf-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="d25bf-120">Related Sections</span></span>  
 [<span data-ttu-id="d25bf-121">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d25bf-121">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="d25bf-122">Obsahuje úplný seznam model Windows Formsch ovládacích prvků s odkazy na informace o jejich použití.</span><span class="sxs-lookup"><span data-stu-id="d25bf-122">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
