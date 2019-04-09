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
ms.openlocfilehash: 2acbcc9197a630a993471c22e572a4f3ed682c64
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090560"
---
# <a name="contextmenu-component-overview-windows-forms"></a><span data-ttu-id="5f12d-102">ContextMenu – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="5f12d-102">ContextMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="5f12d-103">I když <xref:System.Windows.Forms.MenuStrip> a <xref:System.Windows.Forms.ContextMenuStrip> nahradit a přidání funkce, které <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> ovládací prvky z předchozích verzí <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> se zachovají pro zpětnou kompatibilitu a budoucí použití, pokud se rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="5f12d-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="5f12d-104">Pomocí Windows Forms <xref:System.Windows.Forms.ContextMenu> součásti, můžete poskytnout uživatelům snadno k dispozici nabídku s často používanými příkazy, které jsou spojeny s vybraným objektem.</span><span class="sxs-lookup"><span data-stu-id="5f12d-104">With the Windows Forms <xref:System.Windows.Forms.ContextMenu> component, you can provide users with an easily accessible shortcut menu of frequently used commands that are associated with the selected object.</span></span> <span data-ttu-id="5f12d-105">Položky v místní nabídce jsou často podmnožinou položky z hlavní nabídky, které jsou zobrazeny jinde v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5f12d-105">The items in a shortcut menu are frequently a subset of the items from main menus that appear elsewhere in the application.</span></span> <span data-ttu-id="5f12d-106">Uživatel obvykle můžete přistupovat k místní nabídce kliknutím pravým tlačítkem myši.</span><span class="sxs-lookup"><span data-stu-id="5f12d-106">A user can typically access a shortcut menu by right-clicking the mouse.</span></span> <span data-ttu-id="5f12d-107">Ve Windows Forms jsou spojeny s ovládacími prvky místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="5f12d-107">On Windows Forms, shortcut menus are associated with controls.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="5f12d-108">Vlastnosti klíče</span><span class="sxs-lookup"><span data-stu-id="5f12d-108">Key Properties</span></span>  
 <span data-ttu-id="5f12d-109">Můžete přidružit místní nabídku ovládacího prvku tak, že nastavíte ovládacího prvku <xref:System.Windows.Forms.Control.ContextMenu%2A> vlastnost <xref:System.Windows.Forms.ContextMenu> komponenty.</span><span class="sxs-lookup"><span data-stu-id="5f12d-109">You can associate a shortcut menu with a control by setting the control's <xref:System.Windows.Forms.Control.ContextMenu%2A> property to the <xref:System.Windows.Forms.ContextMenu> component.</span></span> <span data-ttu-id="5f12d-110">Jeden místní nabídky můžou být spojené s více ovládacích prvků, ale každý ovládací prvek může mít pouze jednu nabídku.</span><span class="sxs-lookup"><span data-stu-id="5f12d-110">A single shortcut menu can be associated with multiple controls, but each control can have only one shortcut menu.</span></span>  
  
 <span data-ttu-id="5f12d-111">Klíčové vlastnosti <xref:System.Windows.Forms.ContextMenu> komponenta je <xref:System.Windows.Forms.Menu.MenuItems%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5f12d-111">The key property of the <xref:System.Windows.Forms.ContextMenu> component is the <xref:System.Windows.Forms.Menu.MenuItems%2A> property.</span></span> <span data-ttu-id="5f12d-112">Můžete přidat položky nabídky programové vytvoření <xref:System.Windows.Forms.MenuItem> objekty a jejich přidání na <xref:System.Windows.Forms.Menu.MenuItemCollection> v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="5f12d-112">You can add menu items by programmatically creating <xref:System.Windows.Forms.MenuItem> objects and adding them to the <xref:System.Windows.Forms.Menu.MenuItemCollection> of the shortcut menu.</span></span> <span data-ttu-id="5f12d-113">Protože položek v místní nabídce jsou obvykle nakreslen z jiných nabídek, nejčastěji přidáte položky místní nabídky jejich zkopírováním.</span><span class="sxs-lookup"><span data-stu-id="5f12d-113">Because the items in a shortcut menu are usually drawn from other menus, you will most frequently add items to a shortcut menu by copying them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f12d-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5f12d-114">See also</span></span>

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
