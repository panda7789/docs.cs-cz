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
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a>Postupy: Přidání a odebrání položek nabídky s komponentou Windows Forms ContextMenu
Vysvětluje, jak přidat a odebrat položky místní nabídky v model Windows Forms.  
  
 Komponenta model Windows Forms <xref:System.Windows.Forms.ContextMenu> poskytuje nabídku často používaných příkazů, které jsou relevantní pro vybraný objekt. Do místní nabídky můžete přidat položky přidáním <xref:System.Windows.Forms.MenuItem> objektů <xref:System.Windows.Forms.Menu.MenuItems%2A> do kolekce.  
  
 Položky můžete z místní nabídky odebrat trvale; v době běhu však může být vhodnější položky místo toho skrýt nebo zakázat.  
  
> [!IMPORTANT]
> I <xref:System.Windows.Forms.MenuStrip> když <xref:System.Windows.Forms.ContextMenuStrip> a <xref:System.Windows.Forms.ContextMenu> v <xref:System.Windows.Forms.MainMenu> případě potřeby nahrazují a přidávají funkce do ovládacích prvků <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> v předchozích verzích a jsou zachované pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a>Odebrání položek z místní nabídky  
  
1. Pomocí metody <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> nebokolekce<xref:System.Windows.Forms.ContextMenu>komponenty odeberte konkrétní položku nabídky. <xref:System.Windows.Forms.Menu.MenuItems%2A> <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A>  
  
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
  
     -nebo-  
  
2. `Clear` Použijte metodu `MenuItems` kolekce komponentykodebránívšechpoložekznabídky.<xref:System.Windows.Forms.ContextMenu>  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ContextMenu>
- [Komponenta ContextMenu](contextmenu-component-windows-forms.md)
- [Přehled komponenty ContextMenu](contextmenu-component-overview-windows-forms.md)
