---
title: 'Postupy: Zakázání ToolStripMenuItems'
ms.date: 03/30/2017
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
ms.openlocfilehash: a480cd29eef1a79a69f702eed7cd02c28d7ea3de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954224"
---
# <a name="how-to-disable-toolstripmenuitems"></a>Postupy: Zakázání ToolStripMenuItems
Můžete omezit nebo rozšířit příkazy, které uživatel může díky povolování a zakazování položky nabídky v reakci na aktivity uživatelů. Položky nabídky jsou ve výchozím nastavení povolená, když se vytvoří, ale tuto možnost lze upravit pomocí <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> vlastnost. Tuto vlastnost můžete upravit v době návrhu **vlastnosti** okno nebo programově podle nastavení v kódu.  
  
### <a name="to-disable-a-menu-item-programmatically"></a>Chcete-li zakázat položku nabídky prostřednictvím kódu programu  
  
- V rámci metody, kde nastavíte vlastnosti položky nabídky, přidejte kód pro nastavení <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> vlastnost `false`.  
  
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
    >  Zakázání nabídek nejvyšší úrovně nebo první položku v nabídce skryje všechny položky nabídky obsažené v nabídce, ale je nezakáže. Podobně zakázání položku nabídky, která má položky podnabídky skryje položky podnabídky, ale není je vypnout. Pokud všechny příkazy v dané nabídky jsou k dispozici pro uživatele, programovací vhodné skrýt i zakázat celou nabídku, bude považován, jak to představuje čisté uživatelské rozhraní. By měl skrýt a zakázat v nabídce a zakažte každé položky a podnabídky položky v nabídce, protože skrytí samostatně nezabraňuje přístup k příkazu nabídky prostřednictvím klávesovou zkratku. Nastavte <xref:System.Windows.Forms.ToolStripItem.Visible%2A> vlastnosti položky nabídek nejvyšší úrovně na `false` skrýt celé nabídky.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [Postupy: Skrytí ToolStripMenuItems](how-to-hide-toolstripmenuitems.md)
- [Přehled ovládacího prvku MenuStrip](menustrip-control-overview-windows-forms.md)
