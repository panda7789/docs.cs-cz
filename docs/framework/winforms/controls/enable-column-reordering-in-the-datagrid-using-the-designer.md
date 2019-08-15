---
title: 'Postupy: Povolení změny pořadí sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- columns [Windows Forms], reordering
- data [Windows Forms], displaying
ms.assetid: d82bd69c-6799-4439-a32c-91139c5901d1
ms.openlocfilehash: 3864ce70f058259b597df904311bd4a48218b151
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040350"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Povolení změny pořadí sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře
Když uživatelé zobrazují data zobrazená v <xref:System.Windows.Forms.DataGridView> ovládacím prvku model Windows Forms, někdy chtějí porovnat hodnoty v určitých sloupcích. To může být nevhodné, pokud jsou sloupce v ovládacím prvku široce oddělené, zejména pokud se uživatelé musí posunout zpátky a vodorovně, aby viděli všechny sloupce, které vás zajímají. Úkol porovnání hodnot sloupce můžete usnadnit tím, že uživatelům umožníte změnit pořadí sloupců. Když povolíte změnu pořadí sloupců, uživatelé můžou přesunout sloupec na novou pozici přetažením záhlaví sloupce myší.

 Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.DataGridView> ovládací prvek. Informace o nastavení takového projektu naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms.

## <a name="to-enable-column-reordering"></a>Povolení Změna pořadí sloupců

- V pravém horním <xref:System.Windows.Forms.DataGridView> rohu ovládacího prvku klikněte na glyf inteligentních značek ((./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")![glyf inteligentních značek]) a pak vyberte **Povolit změnu pořadí sloupců**.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [Postupy: Ukotvit sloupce v ovládacím prvku DataGridView model Windows Forms pomocí návrháře](freeze-columns-in-the-datagrid-using-the-designer.md)
- [Postupy: Vytvoření projektu model Windows Forms aplikace](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Postupy: Přidat ovládací prvky do model Windows Forms](how-to-add-controls-to-windows-forms.md)
