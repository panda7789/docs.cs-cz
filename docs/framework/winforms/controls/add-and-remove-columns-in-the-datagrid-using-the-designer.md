---
title: 'Postupy: Přidávání a odebírání sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře'
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: 7a3029192ab0da4a954dfd7d3d258a00b154924e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957117"
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Přidávání a odebírání sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře
Aby bylo <xref:System.Windows.Forms.DataGridView> možné zobrazit data, musí mít ovládací prvek model Windows Forms sloupce. Pokud plánujete naplnit ovládací prvek ručně, je nutné přidat sloupce sami. Alternativně můžete ovládací prvek navazovat na zdroj dat, který vygeneruje a automaticky naplní sloupce. Pokud zdroj dat obsahuje více sloupců, než chcete zobrazit, můžete odstranit nežádoucí sloupce.

 Následující postupy vyžadují projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.DataGridView> ovládací prvek. Informace o nastavení takového projektu naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms.

## <a name="to-add-a-column-using-the-designer"></a>Přidání sloupce pomocí návrháře

1. V pravém <xref:System.Windows.Forms.DataGridView> horním rohu ovládacího prvku klikněte na glyf inteligentních značek (![inteligentní značky glyf](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) a pak vyberte **Přidat sloupec**.

2. V dialogovém okně **Přidat sloupec** zvolte možnost sloupec s **vazbou** a vyberte sloupec ze zdroje dat, nebo zvolte možnost nevázaný **sloupec** a definujte sloupec pomocí zadaných polí.

3. Kliknutím na tlačítko **Přidat** přidejte sloupec, což způsobí, že se zobrazí v návrháři, pokud existující sloupce již neplní oblast zobrazení ovládacího prvku.

    > [!NOTE]
    > Vlastnosti sloupce můžete změnit v dialogovém okně **Upravit sloupce** , ke kterému můžete přistupovat z inteligentní značky ovládacího prvku.

## <a name="to-remove-a-column-using-the-designer"></a>Odebrání sloupce pomocí návrháře

1. Vyberte možnost **Upravit sloupce** z inteligentní značky ovládacího prvku.

2. Vyberte sloupec ze seznamu **vybrané sloupce** .

3. Chcete-li odstranit sloupec, klikněte na tlačítko **Odebrat** . tím se z návrháře ztratí.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- [Postupy: Vytvoření projektu model Windows Forms aplikace](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Postupy: Přidat ovládací prvky do model Windows Forms](how-to-add-controls-to-windows-forms.md)
