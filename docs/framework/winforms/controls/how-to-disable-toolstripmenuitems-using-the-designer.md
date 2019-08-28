---
title: 'Postupy: Zakázání ToolStripMenuItems pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
ms.openlocfilehash: 692b6c11f6d58c52a0af29ed04ada45c48cae058
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046239"
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a>Postupy: Zakázání ToolStripMenuItems pomocí Návrháře
Můžete omezit nebo rozšířit příkazy, které může uživatel provést, povolením a zakázáním položek nabídky v reakci na aktivity uživatelů. Položky nabídky jsou ve výchozím nastavení povoleny při jejich vytvoření, ale lze je upravit prostřednictvím <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> vlastnosti. Tuto vlastnost můžete manipulovat v době návrhu v okně **vlastnosti** nebo programově jejich nastavením v kódu. Další informace najdete v tématu [jak: Zakáže ToolStripMenuItems](how-to-disable-toolstripmenuitems.md).

## <a name="to-disable-a-menu-item-at-design-time"></a>Zakázání položky nabídky v době návrhu

1. Pomocí položky nabídky vybrané ve formuláři nastavte <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> vlastnost na `false`hodnotu.

    > [!TIP]
    > Zakázáním první nebo nejvyšší položky nabídky v nabídce zakážete všechny položky nabídky obsažené v nabídce. Podobně zakázání položky nabídky, která má položky podnabídky, zakáže položky podnabídky. Nejsou-li pro uživatele k dispozici všechny příkazy v dané nabídce, považuje se za dobrý postup programování pro skrytí a vypnutí celé nabídky, protože to představuje čisté uživatelské rozhraní. V nabídce byste měli tuto nabídku skrýt a zakázat, protože pokud je skryjete samostatně, nebráníte přístup k příkazu nabídky prostřednictvím klávesové zkratky. Nastavte vlastnost položky nabídky nejvyšší úrovně na `false` hodnotu pro skrytí celé nabídky. <xref:System.Windows.Forms.ToolStripItem.Visible%2A>

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [Postupy: Skrýt ToolStripMenuItems](how-to-hide-toolstripmenuitems.md)
- [Přehled ovládacího prvku MenuStrip](menustrip-control-overview-windows-forms.md)
