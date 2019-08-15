---
title: 'Postupy: Přidávání sloupců do ovládacího prvku Windows Forms ListView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
ms.openlocfilehash: e82fbcf63047873ebc6e5c40b8b9fbeb14a672e5
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038183"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a>Postupy: Přidávání sloupců do ovládacího prvku Windows Forms ListView pomocí Návrháře

Ovládací prvek <xref:System.Windows.Forms.ListView> model Windows Forms může zobrazit více sloupců pro každou položku seznamu, pokud je v zobrazení **podrobností** . Sloupce můžete použít k zobrazení několika typů informací o každé položce seznamu. Například seznam souborů může zobrazit název souboru, typ souboru, velikost a datum poslední změny souboru. Informace o naplnění sloupců po jejich vytvoření najdete v tématu [How to: Zobrazí podpoložky ve sloupcích s ovládacím prvkem](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)model Windows Forms ListView.

Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.ListView> ovládací prvek. Informace o nastavení takového projektu naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms.


### <a name="to-add-columns-in-the-designer"></a>Přidání sloupců v Návrháři

1. V okně **vlastnosti** nastavte <xref:System.Windows.Forms.ListView.View%2A> vlastnost ovládacího prvku na <xref:System.Windows.Forms.View.Details>hodnotu.

2. V okně **vlastnosti** klikněte na tlačítko se **třemi** tečkami![(tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual](./media/visual-studio-ellipsis-button.png) <xref:System.Windows.Forms.ListView.Columns%2A> Studio.) vedle vlastnosti.

     Zobrazí se **Editor kolekce ColumnHeader** .

3. Pomocí tlačítka **Přidat** přidejte nové sloupce. Pak můžete vybrat záhlaví sloupce a nastavit jeho text (titulek sloupce), zarovnání textu a šířku.

## <a name="see-also"></a>Viz také:

- [Přehled ovládacího prvku ListView](listview-control-overview-windows-forms.md)
- [Postupy: Přidávání a odebírání položek pomocí ovládacího prvku model Windows Forms ListView](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Postupy: Zobrazit podpoložky ve sloupcích s ovládacím prvkem model Windows Forms ListView](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Postupy: Zobrazit ikony pro ovládací prvek model Windows Forms ListView](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (model Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
