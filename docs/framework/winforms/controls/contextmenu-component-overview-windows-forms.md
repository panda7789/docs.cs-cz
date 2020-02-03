---
title: ContextMenu – přehled komponenty
ms.date: 03/30/2017
f1_keywords:
- ContextMenu
helpviewer_keywords:
- ContextMenu component [Windows Forms], about ContextMenu component
- context menus [Windows Forms], ContextMenu component
- shortcut menus [Windows Forms], ContextMenu component
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
ms.openlocfilehash: 83740221894941d09d1014585513043851a518e5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746197"
---
# <a name="contextmenu-component-overview-windows-forms"></a><span data-ttu-id="390b6-102">ContextMenu – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="390b6-102">ContextMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="390b6-103">I když <xref:System.Windows.Forms.MenuStrip> a <xref:System.Windows.Forms.ContextMenuStrip> nahrazují a přidává funkce do <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu>ových ovládacích prvků předchozích verzí, <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> se uchovávají pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.</span><span class="sxs-lookup"><span data-stu-id="390b6-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="390b6-104">Pomocí součásti model Windows Forms <xref:System.Windows.Forms.ContextMenu> můžete uživatelům poskytnout snadno dostupnou místní nabídku často používaných příkazů, které jsou přidruženy k vybranému objektu.</span><span class="sxs-lookup"><span data-stu-id="390b6-104">With the Windows Forms <xref:System.Windows.Forms.ContextMenu> component, you can provide users with an easily accessible shortcut menu of frequently used commands that are associated with the selected object.</span></span> <span data-ttu-id="390b6-105">Položky v místní nabídce jsou často podmnožinou položek z hlavních nabídek, které se zobrazují jinde v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="390b6-105">The items in a shortcut menu are frequently a subset of the items from main menus that appear elsewhere in the application.</span></span> <span data-ttu-id="390b6-106">Uživatel má obvykle přístup k místní nabídce kliknutím pravým tlačítkem myši.</span><span class="sxs-lookup"><span data-stu-id="390b6-106">A user can typically access a shortcut menu by right-clicking the mouse.</span></span> <span data-ttu-id="390b6-107">V model Windows Forms jsou místní nabídky přidruženy k ovládacím prvkům.</span><span class="sxs-lookup"><span data-stu-id="390b6-107">On Windows Forms, shortcut menus are associated with controls.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="390b6-108">Klíčové vlastnosti</span><span class="sxs-lookup"><span data-stu-id="390b6-108">Key Properties</span></span>  
 <span data-ttu-id="390b6-109">Místní nabídku můžete přidružit ovládacím prvkem nastavením vlastnosti <xref:System.Windows.Forms.Control.ContextMenu%2A> ovládacího prvku na součást <xref:System.Windows.Forms.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="390b6-109">You can associate a shortcut menu with a control by setting the control's <xref:System.Windows.Forms.Control.ContextMenu%2A> property to the <xref:System.Windows.Forms.ContextMenu> component.</span></span> <span data-ttu-id="390b6-110">Jedna místní nabídka může být přidružena k více ovládacím prvkům, ale každý ovládací prvek může mít pouze jednu místní nabídku.</span><span class="sxs-lookup"><span data-stu-id="390b6-110">A single shortcut menu can be associated with multiple controls, but each control can have only one shortcut menu.</span></span>  
  
 <span data-ttu-id="390b6-111">Klíčovou vlastností součásti <xref:System.Windows.Forms.ContextMenu> je vlastnost <xref:System.Windows.Forms.Menu.MenuItems%2A>.</span><span class="sxs-lookup"><span data-stu-id="390b6-111">The key property of the <xref:System.Windows.Forms.ContextMenu> component is the <xref:System.Windows.Forms.Menu.MenuItems%2A> property.</span></span> <span data-ttu-id="390b6-112">Položky nabídky můžete přidat programově vytvářením <xref:System.Windows.Forms.MenuItem> objektů a jejich přidáním do <xref:System.Windows.Forms.Menu.MenuItemCollection> místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="390b6-112">You can add menu items by programmatically creating <xref:System.Windows.Forms.MenuItem> objects and adding them to the <xref:System.Windows.Forms.Menu.MenuItemCollection> of the shortcut menu.</span></span> <span data-ttu-id="390b6-113">Vzhledem k tomu, že se položky v místní nabídce obvykle vykreslí z jiných nabídek, budete nejčastěji přidávat položky do místní nabídky tak, že je zkopírujete.</span><span class="sxs-lookup"><span data-stu-id="390b6-113">Because the items in a shortcut menu are usually drawn from other menus, you will most frequently add items to a shortcut menu by copying them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="390b6-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="390b6-114">See also</span></span>

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
