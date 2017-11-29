---
title: "ContextMenuStrip – přehled ovládacího prvku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ContextMenuStrip
helpviewer_keywords:
- context menus [Windows Forms], ContextMenuStrip control [Windows Forms]
- shortcut menus [Windows Forms], ContextMenuStrip control [Windows Forms]
- ContextMenuStrip control [Windows Forms], about ContextMenuStrip control
ms.assetid: 9787cdb3-88f1-4198-972f-eefd9524ce39
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c04e8095d84468ee7574b31f0a30fb6f2d2b03a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="contextmenustrip-control-overview"></a><span data-ttu-id="803fe-102">ContextMenuStrip – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="803fe-102">ContextMenuStrip Control Overview</span></span>
> [!NOTE]
>  <span data-ttu-id="803fe-103"><xref:System.Windows.Forms.ContextMenuStrip> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.ContextMenu> řízení; však <xref:System.Windows.Forms.ContextMenu> řízení se zachovává kvůli zpětné kompatibility a budoucí použití, pokud si zvolíte.</span><span class="sxs-lookup"><span data-stu-id="803fe-103">The <xref:System.Windows.Forms.ContextMenuStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ContextMenu> control; however, the <xref:System.Windows.Forms.ContextMenu> control is retained for backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="803fe-104">Místní nabídky, označované taky jako kontextové nabídky, se zobrazí na pozici myši při kliknutí pravým tlačítkem myši.</span><span class="sxs-lookup"><span data-stu-id="803fe-104">Shortcut menus, also called context menus, appear at the mouse position when the user clicks the right mouse button.</span></span> <span data-ttu-id="803fe-105">Zástupce *nabídky* zadejte možnosti pro klientské oblasti nebo v umístění ukazatele myši ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="803fe-105">Shortcut *menus* provide options for the client area or the control at the mouse pointer location.</span></span>  
  
 <span data-ttu-id="803fe-106"><xref:System.Windows.Forms.ContextMenuStrip> Ovládací prvek je určen bezproblémově pracovat s novým <xref:System.Windows.Forms.ToolStrip> a související ovládací prvky, ale můžete přidružit <xref:System.Windows.Forms.ContextMenuStrip> s dalšími kontrolami stejně snadno.</span><span class="sxs-lookup"><span data-stu-id="803fe-106">The <xref:System.Windows.Forms.ContextMenuStrip> control is designed to work seamlessly with the new <xref:System.Windows.Forms.ToolStrip> and related controls, but you can associate a <xref:System.Windows.Forms.ContextMenuStrip> with other controls just as easily.</span></span>  
  
 <span data-ttu-id="803fe-107">V následující tabulce jsou uvedeny důležité <xref:System.Windows.Forms.ContextMenuStrip> doprovodné třídy.</span><span class="sxs-lookup"><span data-stu-id="803fe-107">The following table shows the important <xref:System.Windows.Forms.ContextMenuStrip> companion classes.</span></span>  
  
|<span data-ttu-id="803fe-108">Třída</span><span class="sxs-lookup"><span data-stu-id="803fe-108">Class</span></span>|<span data-ttu-id="803fe-109">Popis</span><span class="sxs-lookup"><span data-stu-id="803fe-109">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<span data-ttu-id="803fe-110">Představuje volitelný možnost zobrazí na <xref:System.Windows.Forms.MenuStrip> nebo <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="803fe-110">Represents a selectable option displayed on a <xref:System.Windows.Forms.MenuStrip> or <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="803fe-111">Reprezentuje ovládací prvek, který umožňuje uživateli vybrat jednu položku ze seznamu, který se zobrazí, když uživatel klikne <xref:System.Windows.Forms.ToolStripDropDownButton> nebo vyšší úrovni položku nabídky.</span><span class="sxs-lookup"><span data-stu-id="803fe-111">Represents a control that enables the user to select a single item from a list that is displayed when the user clicks a <xref:System.Windows.Forms.ToolStripDropDownButton> or a higher-level menu item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|<span data-ttu-id="803fe-112">Poskytuje základní funkce pro ovládací prvky odvozené od <xref:System.Windows.Forms.ToolStripItem> , zobrazí rozevírací seznam položky při kliknutí na.</span><span class="sxs-lookup"><span data-stu-id="803fe-112">Provides basic functionality for controls derived from <xref:System.Windows.Forms.ToolStripItem> that display drop-down items when clicked.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="803fe-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="803fe-113">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 <xref:System.Windows.Forms.ToolStripDropDown>
