---
title: "StatusBar – ovládací prvek (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- StatusBar control [Windows Forms]
- status bars [Windows Forms], creating
ms.assetid: 6f543e27-cf78-4b7f-b4d0-6a8030155d48
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 775d1a350075811dc02ae33efd1a6ae05328c4ff
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="statusbar-control-windows-forms"></a><span data-ttu-id="aa681-102">StatusBar – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="aa681-102">StatusBar Control (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="aa681-103"><xref:System.Windows.Forms.ToolStripStatusLabel> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.StatusBar> řízení; však <xref:System.Windows.Forms.StatusBar> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte.</span><span class="sxs-lookup"><span data-stu-id="aa681-103">The <xref:System.Windows.Forms.ToolStripStatusLabel> control replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control; however, the <xref:System.Windows.Forms.StatusBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="aa681-104">Windows Forms <xref:System.Windows.Forms.StatusBar> řízení se používá ve formulářích jako oblast, obvykle zobrazují v dolní části okna, ve kterém aplikace můžete zobrazit různé typy informací o stavu.</span><span class="sxs-lookup"><span data-stu-id="aa681-104">The Windows Forms <xref:System.Windows.Forms.StatusBar> control is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="aa681-105"><xref:System.Windows.Forms.StatusBar>ovládací prvky může mít panelů stavového řádku na nich, které zobrazují ikony, které označují stav nebo řadu ikony v animace, který indikuje, že proces je v provozu. například aplikace Microsoft Word označující, že dokument je uložen.</span><span class="sxs-lookup"><span data-stu-id="aa681-105"><xref:System.Windows.Forms.StatusBar> controls can have status-bar panels on them that display icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, Microsoft Word indicating that the document is being saved.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aa681-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="aa681-106">In This Section</span></span>  
 [<span data-ttu-id="aa681-107">Přehled ovládacího prvku StatusBar</span><span class="sxs-lookup"><span data-stu-id="aa681-107">StatusBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)  
 <span data-ttu-id="aa681-108">Představuje obecné koncepty <xref:System.Windows.Forms.StatusBar> řízení, které umožňuje uživatelům zobrazit relevantní informace pro ovládací prvek, který má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="aa681-108">Introduces the general concepts of the <xref:System.Windows.Forms.StatusBar> control, which enables users to see relevant information for the control that has focus.</span></span>  
  
 [<span data-ttu-id="aa681-109">Postupy: přidání panelů do ovládacího prvku StatusBar</span><span class="sxs-lookup"><span data-stu-id="aa681-109">How to: Add Panels to a StatusBar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md)  
 <span data-ttu-id="aa681-110">Vysvětluje, jak přidat programovatelný panely k <xref:System.Windows.Forms.StatusBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="aa681-110">Explains how to add programmable panels to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="aa681-111">Postupy: určení panelu v ovládacím prvku Windows Forms StatusBar označeného kliknutím</span><span class="sxs-lookup"><span data-stu-id="aa681-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)  
 <span data-ttu-id="aa681-112">Vysvětluje, jak zpracovat <xref:System.Windows.Forms.Control.Click> události vyvolané z <xref:System.Windows.Forms.StatusBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="aa681-112">Explains how to handle <xref:System.Windows.Forms.Control.Click> events raised from the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="aa681-113">Postupy: nastavení velikosti panelů stavového řádku</span><span class="sxs-lookup"><span data-stu-id="aa681-113">How to: Set the Size of Status-Bar Panels</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-size-of-status-bar-panels.md)  
 <span data-ttu-id="aa681-114">Obsahuje údaje o vlastnosti, které řídí šířku a přizpůsobit chování panelů stavového řádku za běhu.</span><span class="sxs-lookup"><span data-stu-id="aa681-114">Gives details on the properties that control the width and resize behavior of status-bar panels at run time.</span></span>  
  
 [<span data-ttu-id="aa681-115">Návod: Aktualizace informací stavového řádku za běhu</span><span class="sxs-lookup"><span data-stu-id="aa681-115">Walkthrough: Updating Status Bar Information at Run Time</span></span>](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)  
 <span data-ttu-id="aa681-116">Vysvětluje, jak k programovému řízení dat v rámci panelů stavového řádku.</span><span class="sxs-lookup"><span data-stu-id="aa681-116">Explains how to programmatically control the data within status-bar panels.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="aa681-117">Odkaz</span><span class="sxs-lookup"><span data-stu-id="aa681-117">Reference</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <span data-ttu-id="aa681-118">Poskytuje referenční informace o třídě a její členy.</span><span class="sxs-lookup"><span data-stu-id="aa681-118">Provides reference information on the class and its members.</span></span>  
  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <span data-ttu-id="aa681-119">Nahradí a přidá funkce <xref:System.Windows.Forms.StatusBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="aa681-119">Replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="aa681-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="aa681-120">Related Sections</span></span>  
 [<span data-ttu-id="aa681-121">Ovládací prvky používané ve formulářích Windows</span><span class="sxs-lookup"><span data-stu-id="aa681-121">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="aa681-122">Poskytuje úplný seznam Windows Forms – ovládací prvky, odkazy na informace o jejich používání.</span><span class="sxs-lookup"><span data-stu-id="aa681-122">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
