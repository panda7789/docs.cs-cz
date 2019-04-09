---
title: StatusStrip – přehled ovládacího prvku
ms.date: 03/30/2017
f1_keywords:
- StatusStrip
helpviewer_keywords:
- StatusStrip control [Windows Forms], about StatusStrip control
- status bars [Windows Forms], about status bars
ms.assetid: c0d9bcbb-f8b8-46ef-bae2-4146b8c8ce99
ms.openlocfilehash: f6f2d4b19b7ec91c964c72e3aca85e0253c7cc22
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129711"
---
# <a name="statusstrip-control-overview"></a><span data-ttu-id="0bebf-102">StatusStrip – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="0bebf-102">StatusStrip Control Overview</span></span>
<span data-ttu-id="0bebf-103">A <xref:System.Windows.Forms.StatusStrip> ovládací prvek zobrazí informace o objektu na zobrazení <xref:System.Windows.Forms.Form>, komponenty, nebo objektu kontextové informace, které se týkají tohoto objektu operace v rámci vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="0bebf-103">A <xref:System.Windows.Forms.StatusStrip> control displays information about an object being viewed on a <xref:System.Windows.Forms.Form>, the object's components, or contextual information that relates to that object's operation within your application.</span></span> <span data-ttu-id="0bebf-104">Obvykle <xref:System.Windows.Forms.StatusStrip> ovládací prvek se skládá z <xref:System.Windows.Forms.ToolStripStatusLabel> objektů, z nichž každý zobrazuje text nebo ikonu.</span><span class="sxs-lookup"><span data-stu-id="0bebf-104">Typically, a <xref:System.Windows.Forms.StatusStrip> control consists of <xref:System.Windows.Forms.ToolStripStatusLabel> objects, each of which displays text, an icon, or both.</span></span> <span data-ttu-id="0bebf-105"><xref:System.Windows.Forms.StatusStrip> Může také obsahovat <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton>, a <xref:System.Windows.Forms.ToolStripProgressBar> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="0bebf-105">The <xref:System.Windows.Forms.StatusStrip> can also contain <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton>, and <xref:System.Windows.Forms.ToolStripProgressBar> controls.</span></span>  
  
 <span data-ttu-id="0bebf-106">Výchozí hodnota <xref:System.Windows.Forms.StatusStrip> nemá žádné panelů.</span><span class="sxs-lookup"><span data-stu-id="0bebf-106">The default <xref:System.Windows.Forms.StatusStrip> has no panels.</span></span> <span data-ttu-id="0bebf-107">K přidání panelů do <xref:System.Windows.Forms.StatusStrip>, použijte <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="0bebf-107">To add panels to a <xref:System.Windows.Forms.StatusStrip>, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="0bebf-108">Není k dispozici rozsáhlou podporu pro zpracování <xref:System.Windows.Forms.StatusStrip> položky a běžné příkazy v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0bebf-108">There is extensive support for handling <xref:System.Windows.Forms.StatusStrip> items and common commands in Visual Studio.</span></span>  
  
 <span data-ttu-id="0bebf-109">Viz také [StatusStrip – Editor kolekce položek](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233631(v=vs.100)) a [StatusStrip – dialogové okno úlohy](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233642(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0bebf-109">Also see [StatusStrip Items Collection Editor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233631(v=vs.100)) and [StatusStrip Tasks Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233642(v=vs.100)).</span></span>  
  
 <span data-ttu-id="0bebf-110">I když <xref:System.Windows.Forms.StatusStrip> nahrazuje a rozšiřuje <xref:System.Windows.Forms.StatusBar> ovládacího prvku z předchozích verzí <xref:System.Windows.Forms.StatusBar> se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="0bebf-110">Although <xref:System.Windows.Forms.StatusStrip> replaces and extends the <xref:System.Windows.Forms.StatusBar> control of previous versions, <xref:System.Windows.Forms.StatusBar> is retained for both backward compatibility and future use if you choose.</span></span>  
  
### <a name="important-statusstrip-members"></a><span data-ttu-id="0bebf-111">StatusStrip – důležité členy</span><span class="sxs-lookup"><span data-stu-id="0bebf-111">Important StatusStrip Members</span></span>  
  
|<span data-ttu-id="0bebf-112">Name</span><span class="sxs-lookup"><span data-stu-id="0bebf-112">Name</span></span>|<span data-ttu-id="0bebf-113">Popis</span><span class="sxs-lookup"><span data-stu-id="0bebf-113">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.StatusStrip.CanOverflow%2A>|<span data-ttu-id="0bebf-114">Získá nebo nastaví hodnotu označující, zda <xref:System.Windows.Forms.StatusStrip> podporuje přetečení funkce.</span><span class="sxs-lookup"><span data-stu-id="0bebf-114">Gets or sets a value indicating whether the <xref:System.Windows.Forms.StatusStrip> supports overflow functionality.</span></span>|  
|<xref:System.Windows.Forms.StatusStrip.Stretch%2A>|<span data-ttu-id="0bebf-115">Získá nebo nastaví hodnotu označující, zda <xref:System.Windows.Forms.StatusStrip> úsecích od začátku do konce v jeho <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="0bebf-115">Gets or sets a value indicating whether the <xref:System.Windows.Forms.StatusStrip> stretches from end to end in its <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
  
### <a name="important-statusstrip-companion-classes"></a><span data-ttu-id="0bebf-116">Třídy důležitého pomocníka StatusStrip</span><span class="sxs-lookup"><span data-stu-id="0bebf-116">Important StatusStrip Companion Classes</span></span>  
  
|<span data-ttu-id="0bebf-117">Name</span><span class="sxs-lookup"><span data-stu-id="0bebf-117">Name</span></span>|<span data-ttu-id="0bebf-118">Popis</span><span class="sxs-lookup"><span data-stu-id="0bebf-118">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|<span data-ttu-id="0bebf-119">Představuje v panelu <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0bebf-119">Represents a panel in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|<span data-ttu-id="0bebf-120">Zobrazí přidružené <xref:System.Windows.Forms.ToolStripDropDown> ze kterého může uživatel vybrat jednu položku.</span><span class="sxs-lookup"><span data-stu-id="0bebf-120">Displays an associated <xref:System.Windows.Forms.ToolStripDropDown> from which the user can select a single item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|<span data-ttu-id="0bebf-121">Představuje ovládací prvek dvě části, která je standardní tlačítko a rozevírací nabídky.</span><span class="sxs-lookup"><span data-stu-id="0bebf-121">Represents a two-part control that is a standard button and a drop-down menu.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|<span data-ttu-id="0bebf-122">Zobrazí stav dokončení procesu.</span><span class="sxs-lookup"><span data-stu-id="0bebf-122">Displays the completion state of a process.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0bebf-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0bebf-123">See also</span></span>

- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>
