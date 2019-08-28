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
ms.openlocfilehash: f86a2934e799e4604693491dacbecc517d44d810
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046229"
---
# <a name="how-to-disable-toolstripmenuitems"></a>Postupy: Zakázání ToolStripMenuItems
Můžete omezit nebo rozšířit příkazy, které může uživatel provést, povolením a zakázáním položek nabídky v reakci na aktivity uživatelů. Položky nabídky jsou ve výchozím nastavení povoleny při jejich vytvoření, ale lze je upravit prostřednictvím <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> vlastnosti. Tuto vlastnost můžete manipulovat v době návrhu v okně **vlastnosti** nebo programově jejich nastavením v kódu.  
  
### <a name="to-disable-a-menu-item-programmatically"></a>Chcete-li zakázat položku nabídky programově  
  
- V rámci metody, kde nastavíte vlastnosti položky nabídky, přidejte kód pro nastavení <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> `false`vlastnosti na.  
  
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
    > Zakázáním první nebo nejvyšší úrovně položky nabídky v nabídce se skryjí všechny položky nabídky obsažené v nabídce, ale nezakáže se. Podobně zakázání položky nabídky, která má položky podnabídky, skryje položky podnabídky, ale nezakáže je. Nejsou-li pro uživatele k dispozici všechny příkazy v dané nabídce, považuje se za dobrý postup programování pro skrytí a vypnutí celé nabídky, protože to představuje čisté uživatelské rozhraní. Nabídku byste měli skrýt a zakázat a v nabídce zakázat každou položku a položku podnabídky, protože skrytím samotné neznemožníte přístup k příkazu nabídky prostřednictvím klávesové zkratky. Nastavte vlastnost položky nabídky nejvyšší úrovně na `false` hodnotu pro skrytí celé nabídky. <xref:System.Windows.Forms.ToolStripItem.Visible%2A>  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [Postupy: Skrýt ToolStripMenuItems](how-to-hide-toolstripmenuitems.md)
- [Přehled ovládacího prvku MenuStrip](menustrip-control-overview-windows-forms.md)
