---
title: Přidávání a odebírání sloupců v ovládacím prvku DataGridView pomocí návrháře
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: 717a0074f0750352a23b90a9b6e5eab1dc6c925a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732346"
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Přidávání a odebírání sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře
Ovládací prvek model Windows Forms <xref:System.Windows.Forms.DataGridView> musí obsahovat sloupce, aby se zobrazila data. Pokud plánujete naplnit ovládací prvek ručně, je nutné přidat sloupce sami. Alternativně můžete ovládací prvek navazovat na zdroj dat, který vygeneruje a automaticky naplní sloupce. Pokud zdroj dat obsahuje více sloupců, než chcete zobrazit, můžete odstranit nežádoucí sloupce.

 Následující postupy vyžadují projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.DataGridView>. Informace o nastavení takového projektu naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [How to: Add a controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-add-a-column-using-the-designer"></a>Přidání sloupce pomocí návrháře

1. V pravém horním rohu ovládacího prvku <xref:System.Windows.Forms.DataGridView> klikněte na glyf inteligentních značek (![glyf inteligentních značek](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) a pak vyberte **Přidat sloupec**.

2. V dialogovém okně **Přidat sloupec** zvolte možnost sloupec s **vazbou** a vyberte sloupec ze zdroje dat, nebo zvolte možnost **nevázaný sloupec** a definujte sloupec pomocí zadaných polí.

3. Kliknutím na tlačítko **Přidat** přidejte sloupec, což způsobí, že se zobrazí v návrháři, pokud existující sloupce již neplní oblast zobrazení ovládacího prvku.

    > [!NOTE]
    > Vlastnosti sloupce můžete změnit v dialogovém okně **Upravit sloupce** , ke kterému můžete přistupovat z inteligentní značky ovládacího prvku.

## <a name="to-remove-a-column-using-the-designer"></a>Odebrání sloupce pomocí návrháře

1. Vyberte možnost **Upravit sloupce** z inteligentní značky ovládacího prvku.

2. Vyberte sloupec ze seznamu **vybrané sloupce** .

3. Chcete-li odstranit sloupec, klikněte na tlačítko **Odebrat** . tím se z návrháře ztratí.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- [Postupy: vytvoření projektu model Windows Forms aplikace](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Postupy: Přidávání ovládacích prvků do Windows Forms](how-to-add-controls-to-windows-forms.md)
