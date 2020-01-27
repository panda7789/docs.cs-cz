---
title: Nastavit sloupce jen pro čtení v ovládacím prvku DataGridView pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
ms.openlocfilehash: 51d9488ef83f7d2c1c01c9ffd756edf8944d738d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744973"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Převedení sloupců do režimu jen pro čtení v ovládacím prvku Windows Forms DataGridView pomocí Návrháře
Ve výchozím nastavení mohou uživatelé upravovat text a číselná data zobrazená v ovládacím prvku model Windows Forms <xref:System.Windows.Forms.DataGridView>. Chcete-li zobrazit data, která nejsou určena k úpravám, je nutné vytvořit sloupce, které obsahují data jen pro čtení. Informace o tom, jak nastavit ovládací prvek jen pro čtení, naleznete v tématu [How to: prevence a Dissčítání řádků v ovládacím prvku model Windows Forms DataGridView pomocí návrháře](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).

 Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.DataGridView>. Informace o nastavení takového projektu naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [How to: Add a controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-make-a-column-read-only-by-using-the-designer"></a>Zpřístupnění sloupce jen pro čtení pomocí návrháře

1. V pravém horním rohu ovládacího prvku <xref:System.Windows.Forms.DataGridView> klikněte na glyf inteligentních značek (![glyf inteligentních značek](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) a pak vyberte **Upravit sloupce**.

2. Vyberte sloupec ze seznamu **vybrané sloupce** .

3. V mřížce **vlastnosti sloupce** nastavte vlastnost <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> na hodnotu `true`.

    > [!NOTE]
    > Sloupec můžete také nastavit jen pro čtení, když ho přidáte výběrem zaškrtávacího políčka jen **pro čtení** v dialogovém okně **Přidat sloupec** .

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [Postupy: Přidávání a odebírání sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Postupy: Ochrana před přidáním a odstraněním řádku v ovládacím prvku Windows Forms DataGridView pomocí Návrháře](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)
- [Postupy: vytvoření projektu model Windows Forms aplikace](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Postupy: Přidávání ovládacích prvků do Windows Forms](how-to-add-controls-to-windows-forms.md)
