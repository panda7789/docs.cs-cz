---
title: ContextMenuStrip – přehled ovládacího prvku
ms.date: 03/30/2017
f1_keywords:
- ContextMenuStrip
helpviewer_keywords:
- context menus [Windows Forms], ContextMenuStrip control [Windows Forms]
- shortcut menus [Windows Forms], ContextMenuStrip control [Windows Forms]
- ContextMenuStrip control [Windows Forms], about ContextMenuStrip control
ms.assetid: 9787cdb3-88f1-4198-972f-eefd9524ce39
ms.openlocfilehash: e4a6add5297ba7db606ca1891e9279141f8d6d20
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962161"
---
# <a name="contextmenustrip-control-overview"></a><span data-ttu-id="6482d-102">ContextMenuStrip – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="6482d-102">ContextMenuStrip Control Overview</span></span>
> [!NOTE]
> <span data-ttu-id="6482d-103">Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.ContextMenu> ovládacímu prvku. ovládací prvek však <xref:System.Windows.Forms.ContextMenu> zůstává zachován z důvodu zpětné kompatibility a budoucího použití, pokud zvolíte. <xref:System.Windows.Forms.ContextMenuStrip></span><span class="sxs-lookup"><span data-stu-id="6482d-103">The <xref:System.Windows.Forms.ContextMenuStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ContextMenu> control; however, the <xref:System.Windows.Forms.ContextMenu> control is retained for backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="6482d-104">Místní nabídky, označované také jako kontextové nabídky, se zobrazí na pozici myši, když uživatel klikne pravým tlačítkem myši.</span><span class="sxs-lookup"><span data-stu-id="6482d-104">Shortcut menus, also called context menus, appear at the mouse position when the user clicks the right mouse button.</span></span> <span data-ttu-id="6482d-105">Místní *nabídky* poskytují možnosti pro oblast klienta nebo ovládací prvek v umístění ukazatele myši.</span><span class="sxs-lookup"><span data-stu-id="6482d-105">Shortcut *menus* provide options for the client area or the control at the mouse pointer location.</span></span>  
  
 <span data-ttu-id="6482d-106">Ovládací prvek je navržen tak, aby fungoval bez problémů s <xref:System.Windows.Forms.ToolStrip> novými a souvisejícími ovládacími prvky, <xref:System.Windows.Forms.ContextMenuStrip> ale můžete k němu přidružit jiné ovládací prvky stejně jako snadno. <xref:System.Windows.Forms.ContextMenuStrip></span><span class="sxs-lookup"><span data-stu-id="6482d-106">The <xref:System.Windows.Forms.ContextMenuStrip> control is designed to work seamlessly with the new <xref:System.Windows.Forms.ToolStrip> and related controls, but you can associate a <xref:System.Windows.Forms.ContextMenuStrip> with other controls just as easily.</span></span>  
  
 <span data-ttu-id="6482d-107">V následující tabulce jsou uvedeny důležité <xref:System.Windows.Forms.ContextMenuStrip> doprovodné třídy.</span><span class="sxs-lookup"><span data-stu-id="6482d-107">The following table shows the important <xref:System.Windows.Forms.ContextMenuStrip> companion classes.</span></span>  
  
|<span data-ttu-id="6482d-108">Třída</span><span class="sxs-lookup"><span data-stu-id="6482d-108">Class</span></span>|<span data-ttu-id="6482d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="6482d-109">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<span data-ttu-id="6482d-110">Představuje možnost s možností volby, která se <xref:System.Windows.Forms.MenuStrip> zobrazí <xref:System.Windows.Forms.ContextMenuStrip>na nebo.</span><span class="sxs-lookup"><span data-stu-id="6482d-110">Represents a selectable option displayed on a <xref:System.Windows.Forms.MenuStrip> or <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="6482d-111">Představuje ovládací prvek, který umožňuje uživateli vybrat jednu položku ze seznamu, který se zobrazí, když uživatel klikne na <xref:System.Windows.Forms.ToolStripDropDownButton> položku nabídky nebo na vyšší úroveň.</span><span class="sxs-lookup"><span data-stu-id="6482d-111">Represents a control that enables the user to select a single item from a list that is displayed when the user clicks a <xref:System.Windows.Forms.ToolStripDropDownButton> or a higher-level menu item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|<span data-ttu-id="6482d-112">Poskytuje základní funkce pro ovládací prvky odvozené <xref:System.Windows.Forms.ToolStripItem> z těchto zobrazených rozevíracích položek při kliknutí.</span><span class="sxs-lookup"><span data-stu-id="6482d-112">Provides basic functionality for controls derived from <xref:System.Windows.Forms.ToolStripItem> that display drop-down items when clicked.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6482d-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6482d-113">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
