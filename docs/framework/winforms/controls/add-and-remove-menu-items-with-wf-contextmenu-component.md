---
title: "Postupy: Přidání a odebrání položek nabídky se součástí Windows Forms ContextMenu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cf0e579d5cf377169eeb4d394c4127d53fd54540
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a>Postupy: Přidání a odebrání položek nabídky se součástí Windows Forms ContextMenu
Vysvětluje, jak přidávat a odebírat položky místní nabídky v systému Windows Forms.  
  
 Windows Forms <xref:System.Windows.Forms.ContextMenu> součást poskytuje nabídky často používané příkazy, které jsou relevantní pro vybraný objekt. Položky můžete přidat do místní nabídky přidáním <xref:System.Windows.Forms.MenuItem> objekty ke <xref:System.Windows.Forms.Menu.MenuItems%2A> kolekce.  
  
 Položky můžete odebrat z místní nabídky trvale; však v době běhu to může být vhodnější pro skrytí nebo místo toho zakázat položky.  
  
> [!IMPORTANT]
>  I když <xref:System.Windows.Forms.MenuStrip> a <xref:System.Windows.Forms.ContextMenuStrip> nahradit a přidání funkce do <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> ovládací prvky předchozí verze, <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> se zachovají pro zpětnou kompatibilitu a budoucí použití, pokud si zvolíte.  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a>Odebrat položky z místní nabídky  
  
1.  Použití <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> nebo <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> metodu <xref:System.Windows.Forms.Menu.MenuItems%2A> kolekce <xref:System.Windows.Forms.ContextMenu> součást, odeberte položku konkrétní nabídky.  
  
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
  
2.  Použití `Clear` metodu `MenuItems` kolekce <xref:System.Windows.Forms.ContextMenu> součást odebrat všechny položky v nabídce.  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ContextMenu>  
 [ContextMenu – komponenta](../../../../docs/framework/winforms/controls/contextmenu-component-windows-forms.md)  
 [ContextMenu – přehled komponenty](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)
