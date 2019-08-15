---
title: 'Postupy: Skrytí sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], hiding
- DataGridView control [Windows Forms], column hiding
- data [Windows Forms], displaying
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
ms.openlocfilehash: d502a89913e108254848151e9058ac6ae83a9638
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039773"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Skrytí sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře
Někdy budete chtít zobrazit pouze některé sloupce, které jsou k dispozici v ovládacím prvku model Windows Forms <xref:System.Windows.Forms.DataGridView> . Například můžete chtít zobrazit mzdový sloupec zaměstnanců uživatelům s přihlašovacími údaji pro správu při jejich skrývání od jiných uživatelů. Alternativně můžete chtít navazovat ovládací prvek na zdroj dat, který obsahuje mnoho sloupců, pouze některé z nich chcete zobrazit. V takovém případě obvykle odeberete sloupce, které nemají zájem o zobrazení, a ne jejich skrytí. Další informace najdete v tématu [jak: Přidejte a odeberte sloupce v ovládacím prvku model Windows Forms DataGridView pomocí návrháře](add-and-remove-columns-in-the-datagrid-using-the-designer.md).

 Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.DataGridView> ovládací prvek. Informace o nastavení takového projektu naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms.

## <a name="to-hide-a-column-using-the-designer"></a>Skrytí sloupce pomocí návrháře

1. V pravém <xref:System.Windows.Forms.DataGridView> horním rohu ovládacího prvku klikněte na glyf inteligentních značek (![inteligentní značky glyf](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) a pak vyberte **Upravit sloupce**.

2. Vyberte sloupec ze seznamu **vybrané sloupce** .

3. V mřížce **vlastnosti sloupce** nastavte <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> vlastnost na `false`hodnotu.

    > [!NOTE]
    >  Sloupec můžete také při přidávání skrýt tak, že zrušíte zaškrtnutí políčka **viditelné** v dialogovém okně **Přidat sloupec** .

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [Postupy: Přidání a odebrání sloupců v ovládacím prvku DataGridView model Windows Forms pomocí návrháře](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Postupy: Vytvoření projektu model Windows Forms aplikace](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Postupy: Přidat ovládací prvky do model Windows Forms](how-to-add-controls-to-windows-forms.md)
