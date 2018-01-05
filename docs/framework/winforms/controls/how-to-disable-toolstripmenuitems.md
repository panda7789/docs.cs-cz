---
title: "Postupy: Zákaz ToolStripMenuItems"
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
- ToolStripMenuItems [Windows Forms], enabling
- ToolStripMenuItems [Windows Forms], disabling
- menu items [Windows Forms], disabling
- disabling menu items
- menu items [Windows Forms], enabling
- menus [Windows Forms], disabling menu items
ms.assetid: bcc1da84-50fd-41d2-8475-103b581d5654
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0432c59979f8f595b481154f5b339e448ee66b06
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-disable-toolstripmenuitems"></a>Postupy: Zákaz ToolStripMenuItems
Můžete omezit nebo rozšíří příkazy, které může uživatel provést povolením a deaktivace položek nabídky v reakci na aktivit uživatelů. Položky nabídky jsou ve výchozím nastavení povolené, pokud byly vytvořeny, ale to se dá upravit pomocí <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> vlastnost. Tuto vlastnost můžete upravit v době návrhu v **vlastnosti** okno nebo programově pomocí nastavení v kódu.  
  
### <a name="to-disable-a-menu-item-programmatically"></a>Chcete-li zakázat položku nabídky prostřednictvím kódu programu  
  
-   V rámci metody, kde nastavíte vlastnosti položky nabídky, přidejte kód pro nastavení <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> vlastnost `false`.  
  
    ```vb  
    MenuItem1.Enabled = False  
    ```  
  
    ```csharp  
    menuItem1.Enabled = false;  
    ```  
  
    ```cpp  
    menuItem1->Enabled = false;  
    ```  
  
    > [!TIP]
    >  Zakázání položku nabídky první nebo nejvyšší úrovně v nabídce skryje všechny položky nabídky obsažené v nabídce, ale není je zakázána. Podobně zakázáním položky nabídky, která má položky podnabídky skryje položky podnabídky ale není je zakázána. Pokud všechny příkazy dané nabídky jsou k dispozici pro uživatele, považuje programovací vhodné skrýt i zakázat celou nabídku, jak je to představuje čistou uživatelské rozhraní. Doporučujeme skrýt a zakázat v nabídce a zakázat všechny položky a položku podnabídky v nabídce, protože skrytí samostatně nezabrání přístup k příkazu nabídky prostřednictvím klávesovou zkratku. Nastavte <xref:System.Windows.Forms.ToolStripItem.Visible%2A> vlastnost nabídka nejvyšší úrovně na `false` ke skrytí celé nabídky.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [Postupy: Skrytí ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)  
 [Přehled ovládacího prvku MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
