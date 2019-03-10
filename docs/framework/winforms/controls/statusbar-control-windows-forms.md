---
title: StatusBar – ovládací prvek (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- StatusBar control [Windows Forms]
- status bars [Windows Forms], creating
ms.assetid: 6f543e27-cf78-4b7f-b4d0-6a8030155d48
ms.openlocfilehash: 9ef6bc125a641538e7fd2da4c17c5f25dfc62709
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718464"
---
# <a name="statusbar-control-windows-forms"></a><span data-ttu-id="349b3-102">StatusBar – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="349b3-102">StatusBar Control (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="349b3-103"><xref:System.Windows.Forms.ToolStripStatusLabel> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.StatusBar> řízení; však <xref:System.Windows.Forms.StatusBar> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="349b3-103">The <xref:System.Windows.Forms.ToolStripStatusLabel> control replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control; however, the <xref:System.Windows.Forms.StatusBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="349b3-104">Windows Forms <xref:System.Windows.Forms.StatusBar> ovládací prvek se používá ve formulářích jako oblast, obvykle se zobrazí v dolní části okna, ve kterém může aplikace zobrazit různé druhy informací o stavu.</span><span class="sxs-lookup"><span data-stu-id="349b3-104">The Windows Forms <xref:System.Windows.Forms.StatusBar> control is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="349b3-105"><xref:System.Windows.Forms.StatusBar> ovládací prvky můžete mít stavový řádek na nich zobrazit panely ikony k označení stavu nebo řady ikony animace, který indikuje, že proces funguje; například Microsoft Word označující, že dokument se ukládá.</span><span class="sxs-lookup"><span data-stu-id="349b3-105"><xref:System.Windows.Forms.StatusBar> controls can have status-bar panels on them that display icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, Microsoft Word indicating that the document is being saved.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="349b3-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="349b3-106">In This Section</span></span>  
 [<span data-ttu-id="349b3-107">Přehled ovládacího prvku StatusBar</span><span class="sxs-lookup"><span data-stu-id="349b3-107">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)  
 <span data-ttu-id="349b3-108">Představuje obecné koncepty <xref:System.Windows.Forms.StatusBar> ovládací prvek, který umožňuje uživatelům zobrazit důležité informace pro ovládací prvek, který má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="349b3-108">Introduces the general concepts of the <xref:System.Windows.Forms.StatusBar> control, which enables users to see relevant information for the control that has focus.</span></span>  
  
 [<span data-ttu-id="349b3-109">Postupy: Přidání panelů do ovládacího prvku StatusBar</span><span class="sxs-lookup"><span data-stu-id="349b3-109">How to: Add Panels to a StatusBar Control</span></span>](how-to-add-panels-to-a-statusbar-control.md)  
 <span data-ttu-id="349b3-110">Vysvětluje, jak přidat programovatelný panelů <xref:System.Windows.Forms.StatusBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="349b3-110">Explains how to add programmable panels to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="349b3-111">Postupy: Určení panelu v ovládacím prvku Windows Forms StatusBar označeného kliknutím</span><span class="sxs-lookup"><span data-stu-id="349b3-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)  
 <span data-ttu-id="349b3-112">Vysvětluje, jak zpracovat <xref:System.Windows.Forms.Control.Click> události vyvolané z <xref:System.Windows.Forms.StatusBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="349b3-112">Explains how to handle <xref:System.Windows.Forms.Control.Click> events raised from the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="349b3-113">Postupy: Nastavení velikosti panelů stavového řádku</span><span class="sxs-lookup"><span data-stu-id="349b3-113">How to: Set the Size of Status-Bar Panels</span></span>](how-to-set-the-size-of-status-bar-panels.md)  
 <span data-ttu-id="349b3-114">Obsahuje údaje o vlastnosti, které řídí šířku a změna velikosti panelů stavového chování za běhu.</span><span class="sxs-lookup"><span data-stu-id="349b3-114">Gives details on the properties that control the width and resize behavior of status-bar panels at run time.</span></span>  
  
 [<span data-ttu-id="349b3-115">Návod: Aktualizace informací stavového řádku za běhu</span><span class="sxs-lookup"><span data-stu-id="349b3-115">Walkthrough: Updating Status Bar Information at Run Time</span></span>](walkthrough-updating-status-bar-information-at-run-time.md)  
 <span data-ttu-id="349b3-116">Vysvětluje, jak programově řídit data v rámci panelů stavového řádku.</span><span class="sxs-lookup"><span data-stu-id="349b3-116">Explains how to programmatically control the data within status-bar panels.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="349b3-117">Odkaz</span><span class="sxs-lookup"><span data-stu-id="349b3-117">Reference</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <span data-ttu-id="349b3-118">Poskytuje referenční informace o třídě a její členy.</span><span class="sxs-lookup"><span data-stu-id="349b3-118">Provides reference information on the class and its members.</span></span>  
  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <span data-ttu-id="349b3-119">Nahradí a přidá funkce, které <xref:System.Windows.Forms.StatusBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="349b3-119">Replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="349b3-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="349b3-120">Related Sections</span></span>  
 [<span data-ttu-id="349b3-121">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="349b3-121">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="349b3-122">Obsahuje úplný seznam všech ovládacích prvcích Windows Forms, s odkazy na informace o jejich použití.</span><span class="sxs-lookup"><span data-stu-id="349b3-122">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
