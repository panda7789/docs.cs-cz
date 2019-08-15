---
title: 'Postupy: Přidávání a odebírání položek pomocí ovládacího prvku Windows Forms ListView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: 62665746ea9fcd1553717b02b1f1349dc6415ab2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040089"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a>Postupy: Přidávání a odebírání položek pomocí ovládacího prvku Windows Forms ListView pomocí Návrháře

Proces přidání položky do ovládacího prvku model Windows Forms <xref:System.Windows.Forms.ListView> se skládá hlavně z určení položky a přiřazení vlastností k ní. Přidávání a odebírání položek seznamu lze provést kdykoli.

Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.ListView> ovládací prvek. Informace o nastavení takového projektu naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms.

### <a name="to-add-or-remove-items-using-the-designer"></a>Přidání nebo odebrání položek pomocí návrháře

1. <xref:System.Windows.Forms.ListView> Vyberte ovládací prvek.

2. V okně **vlastnosti** klikněte![na tlačítko se **třemi** tečkami (tlačítko se třemi tečkami (...) v okno Vlastnosti sady](./media/visual-studio-ellipsis-button.png)Visual Studio <xref:System.Windows.Forms.ListView.Items%2A> .) vedle vlastnosti.

     Zobrazí se **Editor kolekce ListViewItems** .

3. Chcete-li přidat položku, klikněte na tlačítko **Přidat** . Pak můžete nastavit vlastnosti nové položky, například <xref:System.Windows.Forms.ListView.Text%2A> vlastnosti a. <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>

4. Pokud chcete položku odebrat, vyberte ji a klikněte na tlačítko **Odebrat** .

## <a name="see-also"></a>Viz také:

- [Přehled ovládacího prvku ListView](listview-control-overview-windows-forms.md)
- [Postupy: Přidání sloupců do ovládacího prvku model Windows Forms ListView](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Postupy: Zobrazit podpoložky ve sloupcích s ovládacím prvkem model Windows Forms ListView](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Postupy: Zobrazit ikony pro ovládací prvek model Windows Forms ListView](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (model Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [Postupy: Seskupení položek v ovládacím prvku ListView model Windows Forms](how-to-group-items-in-a-windows-forms-listview-control.md)
