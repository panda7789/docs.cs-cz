---
title: "Postupy: Skrytí ToolStripMenuItems"
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
- ToolStripMenuItems [Windows Forms], hiding
- MenuStrip control [Windows Forms], hiding menu items
- menus [Windows Forms], hiding menu items
- menu items [Windows Forms], hiding
- hiding menu items
ms.assetid: 418a768f-808a-44cd-8cef-f4e161883621
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6f5491cfbfc312b2ce3e35170ddc4edc8ee39a61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hide-toolstripmenuitems"></a>Postupy: Skrytí ToolStripMenuItems
Skrytí položek nabídky je způsob, jak řídit uživatelské rozhraní aplikace a omezit uživatele příkazy. Často můžete skrýt celou nabídku, když jsou všechny položky nabídky na něm není k dispozici. To představuje rušeni pro uživatele. Kromě toho můžete chtít skrýt i zakázat nabídka nebo položka nabídky, jak skrytí samostatně nezabrání uživatel přístup k příkazu nabídky pomocí klávesové zkratky.  
  
### <a name="to-hide-any-menu-item-programmatically"></a>Chcete-li skrýt všechny položky nabídky prostřednictvím kódu programu  
  
-   V rámci metody, kde nastavíte vlastnosti položky nabídky, přidejte kód pro nastavení <xref:System.Windows.Forms.ToolStripItem.Visible%2A> vlastnost `false`.  
  
    ```vb  
    MenuItem3.Visible = False  
    ```  
  
    ```csharp  
    menuItem3.Visible = false;  
    ```  
  
    ```cpp  
    menuItem3->Visible = false;  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>  
 <xref:System.Windows.Forms.MenuStrip>  
 [Přehled ovládacího prvku MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)  
 [Postupy: Zákaz ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md)
