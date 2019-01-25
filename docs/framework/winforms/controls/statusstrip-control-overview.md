---
title: StatusStrip – přehled ovládacího prvku
ms.date: 03/30/2017
f1_keywords:
- StatusStrip
helpviewer_keywords:
- StatusStrip control [Windows Forms], about StatusStrip control
- status bars [Windows Forms], about status bars
ms.assetid: c0d9bcbb-f8b8-46ef-bae2-4146b8c8ce99
ms.openlocfilehash: 9356ca85003987eabf4f62a25acad45d73e144fe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627236"
---
# <a name="statusstrip-control-overview"></a><span data-ttu-id="89195-102">StatusStrip – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="89195-102">StatusStrip Control Overview</span></span>
<span data-ttu-id="89195-103">A <xref:System.Windows.Forms.StatusStrip> ovládací prvek zobrazí informace o objektu na zobrazení <xref:System.Windows.Forms.Form>, komponenty, nebo objektu kontextové informace, které se týkají tohoto objektu operace v rámci vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="89195-103">A <xref:System.Windows.Forms.StatusStrip> control displays information about an object being viewed on a <xref:System.Windows.Forms.Form>, the object's components, or contextual information that relates to that object's operation within your application.</span></span> <span data-ttu-id="89195-104">Obvykle <xref:System.Windows.Forms.StatusStrip> ovládací prvek se skládá z <xref:System.Windows.Forms.ToolStripStatusLabel> objektů, z nichž každý zobrazuje text nebo ikonu.</span><span class="sxs-lookup"><span data-stu-id="89195-104">Typically, a <xref:System.Windows.Forms.StatusStrip> control consists of <xref:System.Windows.Forms.ToolStripStatusLabel> objects, each of which displays text, an icon, or both.</span></span> <span data-ttu-id="89195-105"><xref:System.Windows.Forms.StatusStrip> Může také obsahovat <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton>, a <xref:System.Windows.Forms.ToolStripProgressBar> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="89195-105">The <xref:System.Windows.Forms.StatusStrip> can also contain <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton>, and <xref:System.Windows.Forms.ToolStripProgressBar> controls.</span></span>  
  
 <span data-ttu-id="89195-106">Výchozí hodnota <xref:System.Windows.Forms.StatusStrip> nemá žádné panelů.</span><span class="sxs-lookup"><span data-stu-id="89195-106">The default <xref:System.Windows.Forms.StatusStrip> has no panels.</span></span> <span data-ttu-id="89195-107">K přidání panelů do <xref:System.Windows.Forms.StatusStrip>, použijte <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="89195-107">To add panels to a <xref:System.Windows.Forms.StatusStrip>, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="89195-108">Není k dispozici rozsáhlou podporu pro zpracování <xref:System.Windows.Forms.StatusStrip> položky a běžné příkazy v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="89195-108">There is extensive support for handling <xref:System.Windows.Forms.StatusStrip> items and common commands in Visual Studio.</span></span>  
  
 <span data-ttu-id="89195-109">Viz také [StatusStrip – Editor kolekce položek](https://msdn.microsoft.com/library/ms233631\(v=vs.110\)), [StatusStrip – dialogové okno úlohy](https://msdn.microsoft.com/library/ms233642\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="89195-109">Also see [StatusStrip Items Collection Editor](https://msdn.microsoft.com/library/ms233631\(v=vs.110\)), [StatusStrip Tasks Dialog Box](https://msdn.microsoft.com/library/ms233642\(v=vs.110\)).</span></span>  
  
 <span data-ttu-id="89195-110">I když <xref:System.Windows.Forms.StatusStrip> nahrazuje a rozšiřuje <xref:System.Windows.Forms.StatusBar> ovládacího prvku z předchozích verzí <xref:System.Windows.Forms.StatusBar> se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="89195-110">Although <xref:System.Windows.Forms.StatusStrip> replaces and extends the <xref:System.Windows.Forms.StatusBar> control of previous versions, <xref:System.Windows.Forms.StatusBar> is retained for both backward compatibility and future use if you choose.</span></span>  
  
### <a name="important-statusstrip-members"></a><span data-ttu-id="89195-111">StatusStrip – důležité členy</span><span class="sxs-lookup"><span data-stu-id="89195-111">Important StatusStrip Members</span></span>  
  
|<span data-ttu-id="89195-112">Název</span><span class="sxs-lookup"><span data-stu-id="89195-112">Name</span></span>|<span data-ttu-id="89195-113">Popis</span><span class="sxs-lookup"><span data-stu-id="89195-113">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.StatusStrip.CanOverflow%2A>|<span data-ttu-id="89195-114">Získá nebo nastaví hodnotu označující, zda <xref:System.Windows.Forms.StatusStrip> podporuje přetečení funkce.</span><span class="sxs-lookup"><span data-stu-id="89195-114">Gets or sets a value indicating whether the <xref:System.Windows.Forms.StatusStrip> supports overflow functionality.</span></span>|  
|<xref:System.Windows.Forms.StatusStrip.Stretch%2A>|<span data-ttu-id="89195-115">Získá nebo nastaví hodnotu označující, zda <xref:System.Windows.Forms.StatusStrip> úsecích od začátku do konce v jeho <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="89195-115">Gets or sets a value indicating whether the <xref:System.Windows.Forms.StatusStrip> stretches from end to end in its <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
  
### <a name="important-statusstrip-companion-classes"></a><span data-ttu-id="89195-116">Třídy důležitého pomocníka StatusStrip</span><span class="sxs-lookup"><span data-stu-id="89195-116">Important StatusStrip Companion Classes</span></span>  
  
|<span data-ttu-id="89195-117">Název</span><span class="sxs-lookup"><span data-stu-id="89195-117">Name</span></span>|<span data-ttu-id="89195-118">Popis</span><span class="sxs-lookup"><span data-stu-id="89195-118">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|<span data-ttu-id="89195-119">Představuje v panelu <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="89195-119">Represents a panel in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|<span data-ttu-id="89195-120">Zobrazí přidružené <xref:System.Windows.Forms.ToolStripDropDown> ze kterého může uživatel vybrat jednu položku.</span><span class="sxs-lookup"><span data-stu-id="89195-120">Displays an associated <xref:System.Windows.Forms.ToolStripDropDown> from which the user can select a single item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|<span data-ttu-id="89195-121">Představuje ovládací prvek dvě části, která je standardní tlačítko a rozevírací nabídky.</span><span class="sxs-lookup"><span data-stu-id="89195-121">Represents a two-part control that is a standard button and a drop-down menu.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|<span data-ttu-id="89195-122">Zobrazí stav dokončení procesu.</span><span class="sxs-lookup"><span data-stu-id="89195-122">Displays the completion state of a process.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="89195-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89195-123">See also</span></span>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>
