---
title: "ToolStripProgressBar – přehled ovládacího prvku"
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
- ToolStripProgressBar
helpviewer_keywords:
- toolbars [Windows Forms], progress bars
- progress controls [Windows Forms]
- ToolStripProgressBar control [Windows Forms], about ToolStripProgressBar control
ms.assetid: ec3ab522-5fe4-4b4d-a551-bc19e84f4774
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3ee73d87a65e9febed6ebd5ad981dcd548fc2404
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="toolstripprogressbar-control-overview"></a><span data-ttu-id="bc37f-102">ToolStripProgressBar – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="bc37f-102">ToolStripProgressBar Control Overview</span></span>
<span data-ttu-id="bc37f-103"><xref:System.Windows.Forms.ToolStripProgressBar> Kombinuje rafting a vykreslování funkce všech <xref:System.Windows.Forms.ToolStrip> ovládacích prvků pomocí jeho typické funkce sledování procesu.</span><span class="sxs-lookup"><span data-stu-id="bc37f-103">The <xref:System.Windows.Forms.ToolStripProgressBar> combines the rafting and rendering functionality of all <xref:System.Windows.Forms.ToolStrip> controls with its typical process-tracking functionality.</span></span> <span data-ttu-id="bc37f-104">A <xref:System.Windows.Forms.ToolStripProgressBar> nejvíce obvykle hostovaný <xref:System.Windows.Forms.StatusStrip>a méně často podle <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="bc37f-104">A <xref:System.Windows.Forms.ToolStripProgressBar> is most usually hosted by <xref:System.Windows.Forms.StatusStrip>, and less frequently by a <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
 <span data-ttu-id="bc37f-105">I když <xref:System.Windows.Forms.ToolStripProgressBar> nahrazuje a přidá funkce pro ovládací prvek v předchozích verzích <xref:System.Windows.Forms.ToolStripProgressBar> se zachovává kvůli zpětné kompatibilitě a budoucí použití, v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="bc37f-105">Although <xref:System.Windows.Forms.ToolStripProgressBar> replaces and adds functionality to the control in previous versions, <xref:System.Windows.Forms.ToolStripProgressBar> is retained for both backward compatibility and future use if desired.</span></span>  
  
### <a name="important-toolstripprogressbar-members"></a><span data-ttu-id="bc37f-106">Důležité ToolStripProgressBar členy</span><span class="sxs-lookup"><span data-stu-id="bc37f-106">Important ToolStripProgressBar Members</span></span>  
  
|<span data-ttu-id="bc37f-107">Název</span><span class="sxs-lookup"><span data-stu-id="bc37f-107">Name</span></span>|<span data-ttu-id="bc37f-108">Popis</span><span class="sxs-lookup"><span data-stu-id="bc37f-108">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripProgressBar.MarqueeAnimationSpeed%2A>|<span data-ttu-id="bc37f-109">Získá nebo nastaví hodnotu představující zpoždění mezi jednotlivými <xref:System.Windows.Forms.ProgressBarStyle.Marquee> zobrazení aktualizací v milisekundách.</span><span class="sxs-lookup"><span data-stu-id="bc37f-109">Gets or sets a value representing the delay between each <xref:System.Windows.Forms.ProgressBarStyle.Marquee> display update, in milliseconds.</span></span>|  
|<xref:System.Windows.Forms.ProgressBar.Maximum%2A>|<span data-ttu-id="bc37f-110">Získá nebo nastaví horní mez rozsahu, který je definovaný pro tuto <xref:System.Windows.Forms.ToolStripProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="bc37f-110">Gets or sets the upper bound of the range that is defined for this <xref:System.Windows.Forms.ToolStripProgressBar>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar.Minimum%2A>|<span data-ttu-id="bc37f-111">Získá nebo nastaví dolní mez rozsahu, který je definovaný pro tuto <xref:System.Windows.Forms.ToolStripProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="bc37f-111">Gets or sets the lower bound of the range that is defined for this <xref:System.Windows.Forms.ToolStripProgressBar>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar.Style%2A>|<span data-ttu-id="bc37f-112">Získá nebo nastaví styl, který <xref:System.Windows.Forms.ToolStripProgressBar> pomocí zobrazí průběh operace.</span><span class="sxs-lookup"><span data-stu-id="bc37f-112">Gets or sets the style that the <xref:System.Windows.Forms.ToolStripProgressBar> uses to display the progress of an operation.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar.Value%2A>|<span data-ttu-id="bc37f-113">Získá nebo nastaví aktuální hodnotu <xref:System.Windows.Forms.ToolStripProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="bc37f-113">Gets or sets the current value of the <xref:System.Windows.Forms.ToolStripProgressBar>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar.PerformStep%2A>|<span data-ttu-id="bc37f-114">Přejde aktuální pozici indikátoru průběhu podle množství <xref:System.Windows.Forms.ToolStripProgressBar.Step%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bc37f-114">Advances the current position of the progress bar by the amount of the <xref:System.Windows.Forms.ToolStripProgressBar.Step%2A> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bc37f-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="bc37f-115">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripProgressBar>
