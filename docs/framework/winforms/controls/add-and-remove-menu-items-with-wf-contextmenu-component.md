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
ms.openlocfilehash: 5d1862b1fc1398f0f8c2217b51c4efb93db639af
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957022"
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a><span data-ttu-id="39278-102">Postupy: Přidání a odebrání položek nabídky s komponentou Windows Forms ContextMenu</span><span class="sxs-lookup"><span data-stu-id="39278-102">How to: Add and Remove Menu Items with the Windows Forms ContextMenu Component</span></span>
<span data-ttu-id="39278-103">Vysvětluje, jak přidat a odebrat položky místní nabídky v model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="39278-103">Explains how to add and remove shortcut menu items in Windows Forms.</span></span>  
  
 <span data-ttu-id="39278-104">Komponenta model Windows Forms <xref:System.Windows.Forms.ContextMenu> poskytuje nabídku často používaných příkazů, které jsou relevantní pro vybraný objekt.</span><span class="sxs-lookup"><span data-stu-id="39278-104">The Windows Forms <xref:System.Windows.Forms.ContextMenu> component provides a menu of frequently used commands that are relevant to the selected object.</span></span> <span data-ttu-id="39278-105">Do místní nabídky můžete přidat položky přidáním <xref:System.Windows.Forms.MenuItem> objektů <xref:System.Windows.Forms.Menu.MenuItems%2A> do kolekce.</span><span class="sxs-lookup"><span data-stu-id="39278-105">You can add items to the shortcut menu by adding <xref:System.Windows.Forms.MenuItem> objects to the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection.</span></span>  
  
 <span data-ttu-id="39278-106">Položky můžete z místní nabídky odebrat trvale; v době běhu však může být vhodnější položky místo toho skrýt nebo zakázat.</span><span class="sxs-lookup"><span data-stu-id="39278-106">You can remove items from a shortcut menu permanently; however, at run time it may be more appropriate to hide or disable the items instead.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="39278-107">I <xref:System.Windows.Forms.MenuStrip> když <xref:System.Windows.Forms.ContextMenuStrip> a <xref:System.Windows.Forms.ContextMenu> v <xref:System.Windows.Forms.MainMenu> případě potřeby nahrazují a přidávají funkce do ovládacích prvků <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> v předchozích verzích a jsou zachované pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.</span><span class="sxs-lookup"><span data-stu-id="39278-107">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a><span data-ttu-id="39278-108">Odebrání položek z místní nabídky</span><span class="sxs-lookup"><span data-stu-id="39278-108">To remove items from a shortcut menu</span></span>  
  
1. <span data-ttu-id="39278-109">Pomocí metody <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> nebokolekce<xref:System.Windows.Forms.ContextMenu>komponenty odeberte konkrétní položku nabídky. <xref:System.Windows.Forms.Menu.MenuItems%2A> <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A></span><span class="sxs-lookup"><span data-stu-id="39278-109">Use the <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> or <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection of the <xref:System.Windows.Forms.ContextMenu> component to remove a particular menu item.</span></span>  
  
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
  
     <span data-ttu-id="39278-110">-nebo-</span><span class="sxs-lookup"><span data-stu-id="39278-110">-or-</span></span>  
  
2. <span data-ttu-id="39278-111">`Clear` Použijte metodu `MenuItems` kolekce komponentykodebránívšechpoložekznabídky.<xref:System.Windows.Forms.ContextMenu></span><span class="sxs-lookup"><span data-stu-id="39278-111">Use the `Clear` method of the `MenuItems` collection of the <xref:System.Windows.Forms.ContextMenu> component to remove all items from the menu.</span></span>  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="39278-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="39278-112">See also</span></span>

- <xref:System.Windows.Forms.ContextMenu>
- [<span data-ttu-id="39278-113">Komponenta ContextMenu</span><span class="sxs-lookup"><span data-stu-id="39278-113">ContextMenu Component</span></span>](contextmenu-component-windows-forms.md)
- [<span data-ttu-id="39278-114">Přehled komponenty ContextMenu</span><span class="sxs-lookup"><span data-stu-id="39278-114">ContextMenu Component Overview</span></span>](contextmenu-component-overview-windows-forms.md)
