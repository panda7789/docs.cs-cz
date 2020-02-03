---
title: Přidání sloupců do ovládacího prvku ListView pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
ms.openlocfilehash: 627f8627aac861877a05c13def07427199807754
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744604"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a>Postupy: Přidávání sloupců do ovládacího prvku Windows Forms ListView pomocí Návrháře

Ovládací prvek model Windows Forms <xref:System.Windows.Forms.ListView> může zobrazit více sloupců pro každou položku seznamu, pokud je v zobrazení **podrobností** . Sloupce můžete použít k zobrazení několika typů informací o každé položce seznamu. Například seznam souborů může zobrazit název souboru, typ souboru, velikost a datum poslední změny souboru. Informace o naplnění sloupců po jejich vytvoření naleznete v tématu [How to: Display items in Columns with model Windows Forms ListView Control](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).

Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.ListView>. Informace o nastavení takového projektu naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [How to: Add a controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="to-add-columns-in-the-designer"></a>Přidání sloupců v Návrháři

1. V okně **vlastnosti** nastavte vlastnost <xref:System.Windows.Forms.ListView.View%2A> ovládacího prvku na hodnotu <xref:System.Windows.Forms.View.Details>.

2. V okně **vlastnosti** klikněte na tlačítko se **třemi tečkami** (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio.](./media/visual-studio-ellipsis-button.png)) vedle vlastnosti <xref:System.Windows.Forms.ListView.Columns%2A>.

     Zobrazí se **Editor kolekce ColumnHeader** .

3. Pomocí tlačítka **Přidat** přidejte nové sloupce. Pak můžete vybrat záhlaví sloupce a nastavit jeho text (titulek sloupce), zarovnání textu a šířku.

## <a name="see-also"></a>Viz také

- [Přehled ovládacího prvku ListView](listview-control-overview-windows-forms.md)
- [Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Postupy: Zobrazení podřízených položek ve sloupcích pomocí ovládacího prvku Windows Forms ListView](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Postupy: Zobrazení ikon pro ovládací prvek Windows Forms ListView](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
