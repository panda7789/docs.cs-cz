---
title: 'Postupy: Zákaz ToolStripMenuItems pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
ms.openlocfilehash: 3ce18d40910145a076cc7084e2fba8ee0229c21f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a>Postupy: Zákaz ToolStripMenuItems pomocí Návrháře
Můžete omezit nebo rozšíří příkazy, které může uživatel provést povolením a deaktivace položek nabídky v reakci na aktivit uživatelů. Položky nabídky jsou ve výchozím nastavení povolené, pokud byly vytvořeny, ale to se dá upravit pomocí <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> vlastnost. Tuto vlastnost můžete upravit v době návrhu v **vlastnosti** okno nebo programově pomocí nastavení v kódu. Další informace najdete v tématu [postupy: zákaz ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-disable-a-menu-item-at-design-time"></a>Chcete-li zakázat položku nabídky v době návrhu  
  
1.  Pomocí položky nabídky ve formuláři, nastavte <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> vlastnost `false`.  
  
    > [!TIP]
    >  Zakázání položku nabídky první nebo nejvyšší úrovně v nabídce zakáže všechny položky nabídky obsažené v nabídce. Podobně zakázání položku nabídky, který má položky podnabídky zakáže dílčí položky. Pokud všechny příkazy dané nabídky jsou k dispozici pro uživatele, považuje programovací vhodné skrýt i zakázat celou nabídku, jak je to představuje čistou uživatelské rozhraní. Doporučujeme jak skrýt a zakázat v nabídce jako skryté samostatně nezabrání přístup k příkazu nabídky prostřednictvím klávesovou zkratku. Nastavte <xref:System.Windows.Forms.ToolStripItem.Visible%2A> vlastnost nabídka nejvyšší úrovně na `false` ke skrytí celé nabídky.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [Postupy: Skrytí ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)  
 [Přehled ovládacího prvku MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
