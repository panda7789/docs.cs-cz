---
title: ContextMenu – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ContextMenu
helpviewer_keywords:
- ContextMenu component [Windows Forms], about ContextMenu component
- context menus [Windows Forms], ContextMenu component
- shortcut menus [Windows Forms], ContextMenu component
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
ms.openlocfilehash: 6ae7817bc158f30fbf55b5f6228ecdf134d6657d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962187"
---
# <a name="contextmenu-component-overview-windows-forms"></a><span data-ttu-id="1b7fa-102">ContextMenu – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="1b7fa-102">ContextMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="1b7fa-103">I <xref:System.Windows.Forms.MenuStrip> když <xref:System.Windows.Forms.ContextMenuStrip> a <xref:System.Windows.Forms.ContextMenu> v <xref:System.Windows.Forms.MainMenu> případě potřeby nahrazují a přidávají funkce do ovládacích prvků <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> v předchozích verzích a jsou zachované pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.</span><span class="sxs-lookup"><span data-stu-id="1b7fa-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="1b7fa-104">Pomocí komponenty model Windows Forms <xref:System.Windows.Forms.ContextMenu> můžete uživatelům poskytnout snadno dostupnou místní nabídku často používaných příkazů, které jsou přidruženy k vybranému objektu.</span><span class="sxs-lookup"><span data-stu-id="1b7fa-104">With the Windows Forms <xref:System.Windows.Forms.ContextMenu> component, you can provide users with an easily accessible shortcut menu of frequently used commands that are associated with the selected object.</span></span> <span data-ttu-id="1b7fa-105">Položky v místní nabídce jsou často podmnožinou položek z hlavních nabídek, které se zobrazují jinde v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1b7fa-105">The items in a shortcut menu are frequently a subset of the items from main menus that appear elsewhere in the application.</span></span> <span data-ttu-id="1b7fa-106">Uživatel má obvykle přístup k místní nabídce kliknutím pravým tlačítkem myši.</span><span class="sxs-lookup"><span data-stu-id="1b7fa-106">A user can typically access a shortcut menu by right-clicking the mouse.</span></span> <span data-ttu-id="1b7fa-107">V model Windows Forms jsou místní nabídky přidruženy k ovládacím prvkům.</span><span class="sxs-lookup"><span data-stu-id="1b7fa-107">On Windows Forms, shortcut menus are associated with controls.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="1b7fa-108">Vlastnosti klíče</span><span class="sxs-lookup"><span data-stu-id="1b7fa-108">Key Properties</span></span>  
 <span data-ttu-id="1b7fa-109">Můžete přidružit místní nabídku k ovládacímu prvku nastavením <xref:System.Windows.Forms.Control.ContextMenu%2A> vlastnosti ovládacího prvku <xref:System.Windows.Forms.ContextMenu> na komponentu.</span><span class="sxs-lookup"><span data-stu-id="1b7fa-109">You can associate a shortcut menu with a control by setting the control's <xref:System.Windows.Forms.Control.ContextMenu%2A> property to the <xref:System.Windows.Forms.ContextMenu> component.</span></span> <span data-ttu-id="1b7fa-110">Jedna místní nabídka může být přidružena k více ovládacím prvkům, ale každý ovládací prvek může mít pouze jednu místní nabídku.</span><span class="sxs-lookup"><span data-stu-id="1b7fa-110">A single shortcut menu can be associated with multiple controls, but each control can have only one shortcut menu.</span></span>  
  
 <span data-ttu-id="1b7fa-111">Klíčovou vlastností <xref:System.Windows.Forms.ContextMenu> komponenty <xref:System.Windows.Forms.Menu.MenuItems%2A> je vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1b7fa-111">The key property of the <xref:System.Windows.Forms.ContextMenu> component is the <xref:System.Windows.Forms.Menu.MenuItems%2A> property.</span></span> <span data-ttu-id="1b7fa-112">Položky nabídky lze přidat programově vytvářením <xref:System.Windows.Forms.MenuItem> objektů a jejich přidáním <xref:System.Windows.Forms.Menu.MenuItemCollection> do místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="1b7fa-112">You can add menu items by programmatically creating <xref:System.Windows.Forms.MenuItem> objects and adding them to the <xref:System.Windows.Forms.Menu.MenuItemCollection> of the shortcut menu.</span></span> <span data-ttu-id="1b7fa-113">Vzhledem k tomu, že se položky v místní nabídce obvykle vykreslí z jiných nabídek, budete nejčastěji přidávat položky do místní nabídky tak, že je zkopírujete.</span><span class="sxs-lookup"><span data-stu-id="1b7fa-113">Because the items in a shortcut menu are usually drawn from other menus, you will most frequently add items to a shortcut menu by copying them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b7fa-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1b7fa-114">See also</span></span>

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
