---
title: Přidání a odebrání položek nabídky s komponentou v nabídce
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
ms.openlocfilehash: 989ab6d47ec761930a32f542b5fa1136e831f73d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746279"
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a><span data-ttu-id="be4dd-102">Postupy: Přidání a odebrání položek nabídky se součástí Windows Forms ContextMenu</span><span class="sxs-lookup"><span data-stu-id="be4dd-102">How to: Add and Remove Menu Items with the Windows Forms ContextMenu Component</span></span>
<span data-ttu-id="be4dd-103">Vysvětluje, jak přidat a odebrat položky místní nabídky v model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="be4dd-103">Explains how to add and remove shortcut menu items in Windows Forms.</span></span>  
  
 <span data-ttu-id="be4dd-104">Komponenta model Windows Forms <xref:System.Windows.Forms.ContextMenu> poskytuje nabídku často používaných příkazů, které jsou relevantní pro vybraný objekt.</span><span class="sxs-lookup"><span data-stu-id="be4dd-104">The Windows Forms <xref:System.Windows.Forms.ContextMenu> component provides a menu of frequently used commands that are relevant to the selected object.</span></span> <span data-ttu-id="be4dd-105">Do místní nabídky můžete přidat položky přidáním <xref:System.Windows.Forms.MenuItem> objektů do kolekce <xref:System.Windows.Forms.Menu.MenuItems%2A>.</span><span class="sxs-lookup"><span data-stu-id="be4dd-105">You can add items to the shortcut menu by adding <xref:System.Windows.Forms.MenuItem> objects to the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection.</span></span>  
  
 <span data-ttu-id="be4dd-106">Položky můžete z místní nabídky odebrat trvale; v době běhu však může být vhodnější položky místo toho skrýt nebo zakázat.</span><span class="sxs-lookup"><span data-stu-id="be4dd-106">You can remove items from a shortcut menu permanently; however, at run time it may be more appropriate to hide or disable the items instead.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="be4dd-107">I když <xref:System.Windows.Forms.MenuStrip> a <xref:System.Windows.Forms.ContextMenuStrip> nahrazují a přidává funkce do <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu>ových ovládacích prvků předchozích verzí, <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> se uchovávají pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.</span><span class="sxs-lookup"><span data-stu-id="be4dd-107">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a><span data-ttu-id="be4dd-108">Odebrání položek z místní nabídky</span><span class="sxs-lookup"><span data-stu-id="be4dd-108">To remove items from a shortcut menu</span></span>  
  
1. <span data-ttu-id="be4dd-109">Chcete-li odebrat konkrétní položku nabídky, použijte metodu <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> nebo <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> kolekce <xref:System.Windows.Forms.Menu.MenuItems%2A> součásti <xref:System.Windows.Forms.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="be4dd-109">Use the <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> or <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection of the <xref:System.Windows.Forms.ContextMenu> component to remove a particular menu item.</span></span>  
  
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
  
     <span data-ttu-id="be4dd-110">-nebo-</span><span class="sxs-lookup"><span data-stu-id="be4dd-110">-or-</span></span>  
  
2. <span data-ttu-id="be4dd-111">K odebrání všech položek z nabídky použijte metodu `Clear` kolekce `MenuItems` <xref:System.Windows.Forms.ContextMenu> komponenty.</span><span class="sxs-lookup"><span data-stu-id="be4dd-111">Use the `Clear` method of the `MenuItems` collection of the <xref:System.Windows.Forms.ContextMenu> component to remove all items from the menu.</span></span>  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="be4dd-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="be4dd-112">See also</span></span>

- <xref:System.Windows.Forms.ContextMenu>
- [<span data-ttu-id="be4dd-113">Komponenta ContextMenu</span><span class="sxs-lookup"><span data-stu-id="be4dd-113">ContextMenu Component</span></span>](contextmenu-component-windows-forms.md)
- [<span data-ttu-id="be4dd-114">Přehled komponenty ContextMenu</span><span class="sxs-lookup"><span data-stu-id="be4dd-114">ContextMenu Component Overview</span></span>](contextmenu-component-overview-windows-forms.md)
