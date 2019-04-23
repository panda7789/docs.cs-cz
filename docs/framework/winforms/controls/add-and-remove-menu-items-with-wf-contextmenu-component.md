---
title: 'Postupy: Přidání a odebrání položek nabídky s komponentou Windows Forms ContextMenu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- context menus [Windows Forms], removing items
- ContextMenu component [Windows Forms], adding items
- shortcut menus [Windows Forms], removing items
- shortcut menus [Windows Forms], examples
- context menus [Windows Forms], adding items
- shortcut menus [Windows Forms], adding items
- ContextMenu component [Windows Forms], removing items
- context menus [Windows Forms], examples
- examples [Windows Forms], context menus
ms.assetid: 426d1eaf-7fb8-4b0b-8a33-5e8721786ea4
ms.openlocfilehash: cf70a5cc426b6c6075d1deb11aa2685c39a065c0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59332180"
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a><span data-ttu-id="3939e-102">Postupy: Přidání a odebrání položek nabídky s komponentou Windows Forms ContextMenu</span><span class="sxs-lookup"><span data-stu-id="3939e-102">How to: Add and Remove Menu Items with the Windows Forms ContextMenu Component</span></span>
<span data-ttu-id="3939e-103">Vysvětluje, jak přidávat a odebírat položky místní nabídky do formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="3939e-103">Explains how to add and remove shortcut menu items in Windows Forms.</span></span>  
  
 <span data-ttu-id="3939e-104">Windows Forms <xref:System.Windows.Forms.ContextMenu> komponenta obsahuje nabídku s často používanými příkazy, které jsou relevantní pro vybraný objekt.</span><span class="sxs-lookup"><span data-stu-id="3939e-104">The Windows Forms <xref:System.Windows.Forms.ContextMenu> component provides a menu of frequently used commands that are relevant to the selected object.</span></span> <span data-ttu-id="3939e-105">Můžete přidat položky do místní nabídky přidáním <xref:System.Windows.Forms.MenuItem> objektů <xref:System.Windows.Forms.Menu.MenuItems%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="3939e-105">You can add items to the shortcut menu by adding <xref:System.Windows.Forms.MenuItem> objects to the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection.</span></span>  
  
 <span data-ttu-id="3939e-106">Položky můžete odebrat z místní nabídky trvale; ale za běhu může být vhodnější pro skrytí nebo místo toho zakázat položky.</span><span class="sxs-lookup"><span data-stu-id="3939e-106">You can remove items from a shortcut menu permanently; however, at run time it may be more appropriate to hide or disable the items instead.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3939e-107">I když <xref:System.Windows.Forms.MenuStrip> a <xref:System.Windows.Forms.ContextMenuStrip> nahradit a přidání funkce, které <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> ovládací prvky z předchozích verzí <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> se zachovají pro zpětnou kompatibilitu a budoucí použití, pokud se rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="3939e-107">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a><span data-ttu-id="3939e-108">Odebrat položky z místní nabídky</span><span class="sxs-lookup"><span data-stu-id="3939e-108">To remove items from a shortcut menu</span></span>  
  
1. <span data-ttu-id="3939e-109">Použití <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> nebo <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> metodu <xref:System.Windows.Forms.Menu.MenuItems%2A> kolekce <xref:System.Windows.Forms.ContextMenu> komponenty odebrat konkrétní položku.</span><span class="sxs-lookup"><span data-stu-id="3939e-109">Use the <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> or <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection of the <xref:System.Windows.Forms.ContextMenu> component to remove a particular menu item.</span></span>  
  
    ```vb  
    ' Removes the first item in the shortcut menu.  
    ContextMenu1.MenuItems.RemoveAt(0)  
    ' Removes a particular object from the shortcut menu.  
    ContextMenu1.MenuItems.Remove(mnuItemNew)  
    ```  
  
    ```csharp  
    // Removes the first item in the shortcut menu.  
    contextMenu1.MenuItems.RemoveAt(0);  
    // Removes a particular object from the shortcut menu.  
    contextMenu1.MenuItems.Remove(mnuItemNew);  
    ```  
  
    ```cpp  
    // Removes the first item in the shortcut menu.  
    contextMenu1->MenuItems->RemoveAt(0);  
    // Removes a particular object from the shortcut menu.  
    contextMenu1->MenuItems->Remove(mnuItemNew);  
    ```  
  
     <span data-ttu-id="3939e-110">-nebo-</span><span class="sxs-lookup"><span data-stu-id="3939e-110">-or-</span></span>  
  
2. <span data-ttu-id="3939e-111">Použití `Clear` metodu `MenuItems` kolekce <xref:System.Windows.Forms.ContextMenu> komponenty odebrat všechny položky v nabídce.</span><span class="sxs-lookup"><span data-stu-id="3939e-111">Use the `Clear` method of the `MenuItems` collection of the <xref:System.Windows.Forms.ContextMenu> component to remove all items from the menu.</span></span>  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3939e-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3939e-112">See also</span></span>

- <xref:System.Windows.Forms.ContextMenu>
- [<span data-ttu-id="3939e-113">Komponenta ContextMenu</span><span class="sxs-lookup"><span data-stu-id="3939e-113">ContextMenu Component</span></span>](contextmenu-component-windows-forms.md)
- [<span data-ttu-id="3939e-114">Přehled komponenty ContextMenu</span><span class="sxs-lookup"><span data-stu-id="3939e-114">ContextMenu Component Overview</span></span>](contextmenu-component-overview-windows-forms.md)
