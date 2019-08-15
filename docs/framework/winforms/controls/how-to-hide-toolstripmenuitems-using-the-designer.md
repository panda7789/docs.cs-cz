---
title: 'Postupy: Skrytí ToolStripMenuItems pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
ms.openlocfilehash: 968d34a5f79d469ef62beaa8ac96742d73391b22
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039748"
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a>Postupy: Skrytí ToolStripMenuItems pomocí Návrháře
Skrytím položek nabídky je způsob, jak řídit uživatelské rozhraní (UI) aplikace a omezit uživatelské příkazy. Často budete chtít skrýt celou nabídku, pokud nejsou k dispozici všechny položky nabídky, které jsou v ní dostupné. To představuje méně odvolání pro uživatele. Kromě toho můžete chtít skrýt a zakázat položku nabídky nebo nabídky, protože když je skryjete samostatně, nezabráníte uživateli v přístupu k příkazu nabídky pomocí klávesových zkratek. Další informace o zakázání položek nabídky naleznete v tématu [How to: Zakáže ToolStripMenuItems pomocí návrháře](how-to-disable-toolstripmenuitems-using-the-designer.md).

## <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a>Skrytí nabídky nejvyšší úrovně a jejích položek podnabídky

1. Vyberte položku nabídky nejvyšší úrovně a nastavte její <xref:System.Windows.Forms.ToolStripItem.Visible%2A> vlastnost `false`nebo <xref:System.Windows.Forms.ToolStripItem.Available%2A> .

     Když skryjete položku nabídky nejvyšší úrovně, všechny položky nabídky v této nabídce jsou také skryté. Pokud kliknete někam jinam než na <xref:System.Windows.Forms.MenuStrip> nastavení po nastavení <xref:System.Windows.Forms.ToolStripItem.Visible%2A> na `false`, zobrazí se z formuláře celá položka nabídky nejvyšší úrovně a její položky podnabídky, takže se zobrazí efekt spuštění vaší akce. Chcete-li zobrazit skrytou položku nabídky nejvyšší úrovně v době návrhu, klikněte na <xref:System.Windows.Forms.MenuStrip> položku v **panelu komponenty**, v části **Osnova dokumentu**nebo v horní části mřížky vlastností.

> [!NOTE]
>  Celou nabídku s výjimkou podřízených nabídek rozhraní více dokumentů (MDI) ve scénáři sloučení budete skrývat zřídka.

## <a name="to-hide-a-submenu-item"></a>Skrytí položky podnabídky

1. Vyberte položku podnabídky a nastavte její <xref:System.Windows.Forms.ToolStripItem.Visible%2A> vlastnost na `false`.

     Když skryjete položku podnabídky, zůstane viditelná ve formuláři v době návrhu, takže ji můžete snadno vybrat pro další práci. Ve skutečnosti bude v době běhu skrytá.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>
- <xref:System.Windows.Forms.ToolStripItem.Available%2A>
- <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>
- [Přehled ovládacího prvku MenuStrip](menustrip-control-overview-windows-forms.md)
- [Postupy: Zakázat ToolStripMenuItems pomocí návrháře](how-to-disable-toolstripmenuitems-using-the-designer.md)
