---
title: Skrýt sloupce v ovládacím prvku DataGridView pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], hiding
- DataGridView control [Windows Forms], column hiding
- data [Windows Forms], displaying
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
ms.openlocfilehash: 3c9a6bdeacbeb5929488e6af0054403db73c4239
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738651"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Skrývání sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře
Někdy budete chtít zobrazit pouze některé sloupce, které jsou k dispozici v ovládacím prvku model Windows Forms <xref:System.Windows.Forms.DataGridView>. Například můžete chtít zobrazit mzdový sloupec zaměstnanců uživatelům s přihlašovacími údaji pro správu při jejich skrývání od jiných uživatelů. Alternativně můžete chtít navazovat ovládací prvek na zdroj dat, který obsahuje mnoho sloupců, pouze některé z nich chcete zobrazit. V takovém případě obvykle odeberete sloupce, které nemají zájem o zobrazení, a ne jejich skrytí. Další informace naleznete v tématu [Postup: Přidání a odebrání sloupců v ovládacím prvku model Windows Forms DataGridView pomocí návrháře](add-and-remove-columns-in-the-datagrid-using-the-designer.md).

 Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.DataGridView>. Informace o nastavení takového projektu naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [How to: Add a controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-hide-a-column-using-the-designer"></a>Skrytí sloupce pomocí návrháře

1. V pravém horním rohu ovládacího prvku <xref:System.Windows.Forms.DataGridView> klikněte na glyf inteligentních značek (![glyf inteligentních značek](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) a pak vyberte **Upravit sloupce**.

2. Vyberte sloupec ze seznamu **vybrané sloupce** .

3. V mřížce **vlastnosti sloupce** nastavte vlastnost <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> na hodnotu `false`.

    > [!NOTE]
    > Sloupec můžete také při přidávání skrýt tak, že zrušíte zaškrtnutí políčka **viditelné** v dialogovém okně **Přidat sloupec** .

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [Postupy: Přidávání a odebírání sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Postupy: vytvoření projektu model Windows Forms aplikace](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Postupy: Přidávání ovládacích prvků do Windows Forms](how-to-add-controls-to-windows-forms.md)
