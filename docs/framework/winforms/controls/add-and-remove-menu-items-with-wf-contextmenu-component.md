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
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a>Postupy: Přidání a odebrání položek nabídky se součástí Windows Forms ContextMenu
Vysvětluje, jak přidat a odebrat položky místní nabídky v model Windows Forms.  
  
 Komponenta model Windows Forms <xref:System.Windows.Forms.ContextMenu> poskytuje nabídku často používaných příkazů, které jsou relevantní pro vybraný objekt. Do místní nabídky můžete přidat položky přidáním <xref:System.Windows.Forms.MenuItem> objektů do kolekce <xref:System.Windows.Forms.Menu.MenuItems%2A>.  
  
 Položky můžete z místní nabídky odebrat trvale; v době běhu však může být vhodnější položky místo toho skrýt nebo zakázat.  
  
> [!IMPORTANT]
> I když <xref:System.Windows.Forms.MenuStrip> a <xref:System.Windows.Forms.ContextMenuStrip> nahrazují a přidává funkce do <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu>ových ovládacích prvků předchozích verzí, <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> se uchovávají pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a>Odebrání položek z místní nabídky  
  
1. Chcete-li odebrat konkrétní položku nabídky, použijte metodu <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> nebo <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> kolekce <xref:System.Windows.Forms.Menu.MenuItems%2A> součásti <xref:System.Windows.Forms.ContextMenu>.  
  
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
  
2. K odebrání všech položek z nabídky použijte metodu `Clear` kolekce `MenuItems` <xref:System.Windows.Forms.ContextMenu> komponenty.  
  
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
