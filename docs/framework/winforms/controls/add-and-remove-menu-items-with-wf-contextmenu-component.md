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
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a>Postupy: Přidání a odebrání položek nabídky s komponentou Windows Forms ContextMenu
Vysvětluje, jak přidávat a odebírat položky místní nabídky do formulářů Windows.  
  
 Windows Forms <xref:System.Windows.Forms.ContextMenu> komponenta obsahuje nabídku s často používanými příkazy, které jsou relevantní pro vybraný objekt. Můžete přidat položky do místní nabídky přidáním <xref:System.Windows.Forms.MenuItem> objektů <xref:System.Windows.Forms.Menu.MenuItems%2A> kolekce.  
  
 Položky můžete odebrat z místní nabídky trvale; ale za běhu může být vhodnější pro skrytí nebo místo toho zakázat položky.  
  
> [!IMPORTANT]
>  I když <xref:System.Windows.Forms.MenuStrip> a <xref:System.Windows.Forms.ContextMenuStrip> nahradit a přidání funkce, které <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> ovládací prvky z předchozích verzí <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> se zachovají pro zpětnou kompatibilitu a budoucí použití, pokud se rozhodnete.  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a>Odebrat položky z místní nabídky  
  
1. Použití <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> nebo <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> metodu <xref:System.Windows.Forms.Menu.MenuItems%2A> kolekce <xref:System.Windows.Forms.ContextMenu> komponenty odebrat konkrétní položku.  
  
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
  
2. Použití `Clear` metodu `MenuItems` kolekce <xref:System.Windows.Forms.ContextMenu> komponenty odebrat všechny položky v nabídce.  
  
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
