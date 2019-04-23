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
ms.openlocfilehash: 23699c67de616ba3f535d2527a315aebe7448d3f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979469"
---
# <a name="contextmenustrip-control-overview"></a><span data-ttu-id="29d32-102">ContextMenuStrip – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="29d32-102">ContextMenuStrip Control Overview</span></span>
> [!NOTE]
>  <span data-ttu-id="29d32-103"><xref:System.Windows.Forms.ContextMenuStrip> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.ContextMenu> řízení; však <xref:System.Windows.Forms.ContextMenu> ovládací prvek je zachován z důvodu zpětné kompatibility a budoucí použití, pokud se rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="29d32-103">The <xref:System.Windows.Forms.ContextMenuStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ContextMenu> control; however, the <xref:System.Windows.Forms.ContextMenu> control is retained for backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="29d32-104">Místní nabídky, také nazývané kontextové nabídky, se zobrazí pod kurzor myši, když uživatel klikne pravým tlačítkem myši.</span><span class="sxs-lookup"><span data-stu-id="29d32-104">Shortcut menus, also called context menus, appear at the mouse position when the user clicks the right mouse button.</span></span> <span data-ttu-id="29d32-105">Místní *nabídky* poskytují možnosti pro klientské oblasti nebo ovládacího prvku při umístění ukazatele myši.</span><span class="sxs-lookup"><span data-stu-id="29d32-105">Shortcut *menus* provide options for the client area or the control at the mouse pointer location.</span></span>  
  
 <span data-ttu-id="29d32-106"><xref:System.Windows.Forms.ContextMenuStrip> Ovládací prvek je určen pro bezproblémově fungují s novou <xref:System.Windows.Forms.ToolStrip> a související ovládací prvky, ale můžete přiřadit <xref:System.Windows.Forms.ContextMenuStrip> s jinými ovládacími prvky stejně snadno.</span><span class="sxs-lookup"><span data-stu-id="29d32-106">The <xref:System.Windows.Forms.ContextMenuStrip> control is designed to work seamlessly with the new <xref:System.Windows.Forms.ToolStrip> and related controls, but you can associate a <xref:System.Windows.Forms.ContextMenuStrip> with other controls just as easily.</span></span>  
  
 <span data-ttu-id="29d32-107">V následující tabulce jsou uvedeny důležité <xref:System.Windows.Forms.ContextMenuStrip> doprovodné třídy.</span><span class="sxs-lookup"><span data-stu-id="29d32-107">The following table shows the important <xref:System.Windows.Forms.ContextMenuStrip> companion classes.</span></span>  
  
|<span data-ttu-id="29d32-108">Třída</span><span class="sxs-lookup"><span data-stu-id="29d32-108">Class</span></span>|<span data-ttu-id="29d32-109">Popis</span><span class="sxs-lookup"><span data-stu-id="29d32-109">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<span data-ttu-id="29d32-110">Představuje volitelnou možnost zobrazí na <xref:System.Windows.Forms.MenuStrip> nebo <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="29d32-110">Represents a selectable option displayed on a <xref:System.Windows.Forms.MenuStrip> or <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="29d32-111">Představuje ovládací prvek, který umožňuje uživateli vybrat jednu položku ze seznamu, který se zobrazí, když uživatel klikne <xref:System.Windows.Forms.ToolStripDropDownButton> nebo vyšší úrovně položku nabídky.</span><span class="sxs-lookup"><span data-stu-id="29d32-111">Represents a control that enables the user to select a single item from a list that is displayed when the user clicks a <xref:System.Windows.Forms.ToolStripDropDownButton> or a higher-level menu item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|<span data-ttu-id="29d32-112">Poskytuje základní funkce pro ovládací prvky je odvozena z <xref:System.Windows.Forms.ToolStripItem> , který zobrazí rozevírací seznam položek při kliknutí na.</span><span class="sxs-lookup"><span data-stu-id="29d32-112">Provides basic functionality for controls derived from <xref:System.Windows.Forms.ToolStripItem> that display drop-down items when clicked.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="29d32-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29d32-113">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
