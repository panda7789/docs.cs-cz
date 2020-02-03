---
title: Nastavení střídajících se stylů řádků pro ovládací prvek DataGridView pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- ledger-like formats
- DataGridView control [Windows Forms], row style alternation
- Windows Forms, rows
- rows [Windows Forms], alternating
- data [Windows Forms], displaying
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
ms.openlocfilehash: 74f65d03a359136de943f8a2937ed5e5f1e62519
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743044"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Nastavení stylů střídavých řádků pro ovládací prvek Windows Forms DataGridView pomocí Návrháře

Tabulková data jsou často prezentována ve formátu, ve kterém mají střídavé řádky odlišné barvy pozadí. Tento formát usnadňuje uživatelům informace o tom, které buňky jsou v jednotlivých řádcích, zejména u rozsáhlých tabulek, které mají mnoho sloupců.

Pomocí ovládacího prvku <xref:System.Windows.Forms.DataGridView> můžete zadat úplné informace o stylu pro střídavé řádky. K odlišení střídajících se řádků můžete použít vlastnosti stylu, jako je barva popředí a písmo, kromě barvy pozadí. Další informace naleznete v tématu [styly buněk v ovládacím prvku DataGridView model Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).

Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.DataGridView>. Informace o nastavení takového projektu naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [How to: Add a controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="define-styles-for-alternating-rows"></a>Definovat styly pro střídavé řádky

1. V návrháři vyberte ovládací prvek <xref:System.Windows.Forms.DataGridView>.

2. V okně **vlastnosti** klikněte na tlačítko se třemi tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio.](./media/visual-studio-ellipsis-button.png)) vedle vlastnosti <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>.

3. V dialogovém okně **Tvůrce CellStyle** definujte styl nastavením vlastností a pomocí podokna **náhledu** potvrďte své volby. Styly, které zadáte, se použijí pro každý další řádek zobrazený v ovládacím prvku počínaje druhým.

4. Chcete-li definovat styly pro zbývající řádky, opakujte kroky 2 a 3 pomocí vlastnosti <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>.

    > [!NOTE]
    > Buňky se zobrazují pomocí stylů děděných z více vlastností. Další informace o dědičnosti stylu naleznete v tématu [styly buněk v ovládacím prvku DataGridView model Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- [Styly buňky v ovládacím prvku Windows Forms DataGridView](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Používání Návrháře s ovládacím prvkem Windows Forms DataGridView](using-the-designer-with-the-windows-forms-datagridview-control.md)
- [Postupy: vytvoření projektu model Windows Forms aplikace](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Postupy: Přidávání ovládacích prvků do Windows Forms](how-to-add-controls-to-windows-forms.md)
