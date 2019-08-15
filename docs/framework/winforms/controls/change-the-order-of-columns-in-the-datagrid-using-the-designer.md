---
title: 'Postupy: Změna pořadí sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], order of
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- data [Windows Forms], displaying
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
ms.openlocfilehash: bf77cf3705a470bbe00be383f6a5cb2d28bda34d
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039634"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Změna pořadí sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře

Při navázání ovládacího <xref:System.Windows.Forms.DataGridView> prvku model Windows Forms ke zdroji dat je pořadí zobrazení automaticky generovaných sloupců řízeno zdrojem dat. Pokud toto pořadí nevyhovuje vašim požadavkům, můžete změnit pořadí sloupců pomocí návrháře. Do ovládacího prvku můžete také přidat nevázané sloupce a změnit jejich pořadí zobrazení. Informace o tom, jak změnit pořadí sloupců pomocí kódu programu, [najdete v tématu How to: Změňte pořadí sloupců v ovládacím prvku](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)DataGridView model Windows Forms.

Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.DataGridView> ovládací prvek. Informace o nastavení takového projektu naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms.

## <a name="to-change-the-column-order-using-the-designer"></a>Změna pořadí sloupců pomocí návrháře

1. V pravém <xref:System.Windows.Forms.DataGridView> horním rohu ovládacího prvku klikněte na glyf inteligentních značek (![inteligentní značky glyf](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) a pak vyberte **Upravit sloupce**.

2. Vyberte sloupec ze seznamu **vybrané sloupce** .

3. Klikněte na šipku nahoru nebo dolů napravo od seznamu **vybrané sloupce** , dokud není vybraný sloupec v požadované pozici.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- [Postupy: Přidání a odebrání sloupců v ovládacím prvku DataGridView model Windows Forms pomocí návrháře](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Postupy: Vytvoření projektu model Windows Forms aplikace](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Postupy: Přidat ovládací prvky do model Windows Forms](how-to-add-controls-to-windows-forms.md)
