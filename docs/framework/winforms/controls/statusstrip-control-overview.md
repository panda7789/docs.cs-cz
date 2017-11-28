---
title: "StatusStrip – přehled ovládacího prvku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: StatusStrip
helpviewer_keywords:
- StatusStrip control [Windows Forms], about StatusStrip control
- status bars [Windows Forms], about status bars
ms.assetid: c0d9bcbb-f8b8-46ef-bae2-4146b8c8ce99
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e5f06d155972846b3c04a60d448b300d8cdc5d1c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="statusstrip-control-overview"></a><span data-ttu-id="29e4d-102">StatusStrip – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="29e4d-102">StatusStrip Control Overview</span></span>
<span data-ttu-id="29e4d-103">A <xref:System.Windows.Forms.StatusStrip> ovládací prvek zobrazí informace o objektu se zobrazit na <xref:System.Windows.Forms.Form>, součásti objektu nebo kontextové informace, která má vztah k operaci tento objekt v rámci vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="29e4d-103">A <xref:System.Windows.Forms.StatusStrip> control displays information about an object being viewed on a <xref:System.Windows.Forms.Form>, the object's components, or contextual information that relates to that object's operation within your application.</span></span> <span data-ttu-id="29e4d-104">Obvykle <xref:System.Windows.Forms.StatusStrip> řízení se skládá z <xref:System.Windows.Forms.ToolStripStatusLabel> objekty, z nichž každý zobrazí text, ikonu nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="29e4d-104">Typically, a <xref:System.Windows.Forms.StatusStrip> control consists of <xref:System.Windows.Forms.ToolStripStatusLabel> objects, each of which displays text, an icon, or both.</span></span> <span data-ttu-id="29e4d-105"><xref:System.Windows.Forms.StatusStrip> Může také obsahovat <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton>, a <xref:System.Windows.Forms.ToolStripProgressBar> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="29e4d-105">The <xref:System.Windows.Forms.StatusStrip> can also contain <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton>, and <xref:System.Windows.Forms.ToolStripProgressBar> controls.</span></span>  
  
 <span data-ttu-id="29e4d-106">Výchozí hodnota <xref:System.Windows.Forms.StatusStrip> nemá žádné panelů.</span><span class="sxs-lookup"><span data-stu-id="29e4d-106">The default <xref:System.Windows.Forms.StatusStrip> has no panels.</span></span> <span data-ttu-id="29e4d-107">Přidání panelů do <xref:System.Windows.Forms.StatusStrip>, použijte <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="29e4d-107">To add panels to a <xref:System.Windows.Forms.StatusStrip>, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="29e4d-108">Je rozsáhlá podpora pro zpracování <xref:System.Windows.Forms.StatusStrip> položky a běžné příkazy v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="29e4d-108">There is extensive support for handling <xref:System.Windows.Forms.StatusStrip> items and common commands in Visual Studio.</span></span>  
  
 <span data-ttu-id="29e4d-109">Viz také [Editor kolekce položek StatusStrip](http://msdn.microsoft.com/library/ms233631\(v=vs.110\)), [Úkoly prvku StatusStrip](http://msdn.microsoft.com/library/ms233642\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="29e4d-109">Also see [StatusStrip Items Collection Editor](http://msdn.microsoft.com/library/ms233631\(v=vs.110\)), [StatusStrip Tasks Dialog Box](http://msdn.microsoft.com/library/ms233642\(v=vs.110\)).</span></span>  
  
 <span data-ttu-id="29e4d-110">I když <xref:System.Windows.Forms.StatusStrip> nahrazuje a rozšiřuje <xref:System.Windows.Forms.StatusBar> řízení předchozí verze, <xref:System.Windows.Forms.StatusBar> se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte.</span><span class="sxs-lookup"><span data-stu-id="29e4d-110">Although <xref:System.Windows.Forms.StatusStrip> replaces and extends the <xref:System.Windows.Forms.StatusBar> control of previous versions, <xref:System.Windows.Forms.StatusBar> is retained for both backward compatibility and future use if you choose.</span></span>  
  
### <a name="important-statusstrip-members"></a><span data-ttu-id="29e4d-111">Důležité StatusStrip členy</span><span class="sxs-lookup"><span data-stu-id="29e4d-111">Important StatusStrip Members</span></span>  
  
|<span data-ttu-id="29e4d-112">Název</span><span class="sxs-lookup"><span data-stu-id="29e4d-112">Name</span></span>|<span data-ttu-id="29e4d-113">Popis</span><span class="sxs-lookup"><span data-stu-id="29e4d-113">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.StatusStrip.CanOverflow%2A>|<span data-ttu-id="29e4d-114">Získá nebo nastaví hodnotu, která určuje zda <xref:System.Windows.Forms.StatusStrip> podporuje přetečení funkce.</span><span class="sxs-lookup"><span data-stu-id="29e4d-114">Gets or sets a value indicating whether the <xref:System.Windows.Forms.StatusStrip> supports overflow functionality.</span></span>|  
|<xref:System.Windows.Forms.StatusStrip.Stretch%2A>|<span data-ttu-id="29e4d-115">Získá nebo nastaví hodnotu, která určuje zda <xref:System.Windows.Forms.StatusStrip> úsecích z konce v jeho <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="29e4d-115">Gets or sets a value indicating whether the <xref:System.Windows.Forms.StatusStrip> stretches from end to end in its <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
  
### <a name="important-statusstrip-companion-classes"></a><span data-ttu-id="29e4d-116">Třídy důležitého pomocníka StatusStrip</span><span class="sxs-lookup"><span data-stu-id="29e4d-116">Important StatusStrip Companion Classes</span></span>  
  
|<span data-ttu-id="29e4d-117">Název</span><span class="sxs-lookup"><span data-stu-id="29e4d-117">Name</span></span>|<span data-ttu-id="29e4d-118">Popis</span><span class="sxs-lookup"><span data-stu-id="29e4d-118">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|<span data-ttu-id="29e4d-119">Představuje panelu v <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="29e4d-119">Represents a panel in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|<span data-ttu-id="29e4d-120">Zobrazí přiřazený <xref:System.Windows.Forms.ToolStripDropDown> ze kterého může uživatel vybrat jednu položku.</span><span class="sxs-lookup"><span data-stu-id="29e4d-120">Displays an associated <xref:System.Windows.Forms.ToolStripDropDown> from which the user can select a single item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|<span data-ttu-id="29e4d-121">Reprezentuje ovládací prvek dvoudílný článek, který je standardní tlačítko a z rozevírací nabídky.</span><span class="sxs-lookup"><span data-stu-id="29e4d-121">Represents a two-part control that is a standard button and a drop-down menu.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|<span data-ttu-id="29e4d-122">Zobrazí stav dokončení procesu.</span><span class="sxs-lookup"><span data-stu-id="29e4d-122">Displays the completion state of a process.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="29e4d-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="29e4d-123">See Also</span></span>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>
