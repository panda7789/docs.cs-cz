---
title: Změna pořadí sloupců v ovládacím prvku DataGridView pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], order of
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- data [Windows Forms], displaying
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
ms.openlocfilehash: 7540203fb1c0465caeb045275734d1a7c6f25ee8
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628745"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Změna pořadí sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře

Když svážete ovládací prvek <xref:System.Windows.Forms.DataGridView> model Windows Forms ke zdroji dat, je pořadí zobrazení automaticky generovaných sloupců řízeno zdrojem dat. Pokud toto pořadí nevyhovuje vašim požadavkům, můžete změnit pořadí sloupců pomocí návrháře. Do ovládacího prvku můžete také přidat nevázané sloupce a změnit jejich pořadí zobrazení. Informace o tom, jak změnit pořadí sloupců pomocí kódu programu, naleznete v tématu [How to: Change pořadí sloupců v ovládacím prvku DataGridView model Windows Forms](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md).

Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.DataGridView>. Informace o nastavení takového projektu naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [How to: Add a controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-change-the-column-order-using-the-designer"></a>Změna pořadí sloupců pomocí návrháře

1. V pravém horním rohu ovládacího prvku <xref:System.Windows.Forms.DataGridView> klikněte na glyf akcí návrháře (![malé černé šipky](./media/designer-actions-glyph.gif)) a pak vyberte **Upravit sloupce**.

2. Vyberte sloupec ze seznamu **vybrané sloupce** .

3. Klikněte na šipku nahoru nebo dolů napravo od seznamu **vybrané sloupce** , dokud není vybraný sloupec v požadované pozici.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- [Postupy: Přidávání a odebírání sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Postupy: vytvoření projektu model Windows Forms aplikace](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Postupy: Přidávání ovládacích prvků do Windows Forms](how-to-add-controls-to-windows-forms.md)
