---
title: Povolit změnu pořadí sloupců v ovládacím prvku DataGridView pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- columns [Windows Forms], reordering
- data [Windows Forms], displaying
ms.assetid: d82bd69c-6799-4439-a32c-91139c5901d1
ms.openlocfilehash: 823c0064b2710ab5dfd0f67edf95374590d4490b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745839"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Povolení změny pořadí sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře
Když uživatelé budou zobrazovat data zobrazená v ovládacím prvku model Windows Forms <xref:System.Windows.Forms.DataGridView>, někdy chtějí porovnat hodnoty v určitých sloupcích. To může být nevhodné, pokud jsou sloupce v ovládacím prvku široce oddělené, zejména pokud se uživatelé musí posunout zpátky a vodorovně, aby viděli všechny sloupce, které vás zajímají. Úkol porovnání hodnot sloupce můžete usnadnit tím, že uživatelům umožníte změnit pořadí sloupců. Když povolíte změnu pořadí sloupců, uživatelé můžou přesunout sloupec na novou pozici přetažením záhlaví sloupce myší.

 Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.DataGridView>. Informace o nastavení takového projektu naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [How to: Add a controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-enable-column-reordering"></a>Povolení Změna pořadí sloupců

- Klikněte na glyf inteligentních značek (![glyf inteligentních značek](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) v pravém horním rohu ovládacího prvku <xref:System.Windows.Forms.DataGridView> a pak vyberte **Povolit změnu pořadí sloupců**.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [Postupy: Zablokování sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře](freeze-columns-in-the-datagrid-using-the-designer.md)
- [Postupy: vytvoření projektu model Windows Forms aplikace](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Postupy: Přidávání ovládacích prvků do Windows Forms](how-to-add-controls-to-windows-forms.md)
