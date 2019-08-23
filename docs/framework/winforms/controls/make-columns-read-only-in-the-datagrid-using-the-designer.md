---
title: 'Postupy: Převedení sloupců do režimu jen pro čtení v ovládacím prvku Windows Forms DataGridView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
ms.openlocfilehash: 82be9d31ff6bb3f2f5dd8a55b4426103d466bdd6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952095"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Převedení sloupců do režimu jen pro čtení v ovládacím prvku Windows Forms DataGridView pomocí Návrháře
Ve výchozím nastavení mohou uživatelé upravovat text a číselná data zobrazená v ovládacím <xref:System.Windows.Forms.DataGridView> prvku model Windows Forms. Chcete-li zobrazit data, která nejsou určena k úpravám, je nutné vytvořit sloupce, které obsahují data jen pro čtení. Informace o tom, jak nastavit ovládací prvek jen pro čtení, najdete v [tématu How to: Zabraňte přidávání a odstraňování řádků v ovládacím prvku DataGridView model Windows Forms pomocí návrháře](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).

 Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.DataGridView> ovládací prvek. Informace o nastavení takového projektu naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms.

## <a name="to-make-a-column-read-only-by-using-the-designer"></a>Zpřístupnění sloupce jen pro čtení pomocí návrháře

1. V pravém <xref:System.Windows.Forms.DataGridView> horním rohu ovládacího prvku klikněte na glyf inteligentních značek (![inteligentní značky glyf](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) a pak vyberte **Upravit sloupce**.

2. Vyberte sloupec ze seznamu **vybrané sloupce** .

3. V mřížce **vlastnosti sloupce** nastavte <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> vlastnost na `true`hodnotu.

    > [!NOTE]
    > Sloupec můžete také nastavit jen pro čtení, když ho přidáte výběrem zaškrtávacího políčka jen **pro čtení** v dialogovém okně **Přidat sloupec** .

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [Postupy: Přidání a odebrání sloupců v ovládacím prvku DataGridView model Windows Forms pomocí návrháře](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Postupy: Zabránit přidávání a odstraňování řádků v ovládacím prvku DataGridView model Windows Forms pomocí návrháře](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)
- [Postupy: Vytvoření projektu model Windows Forms aplikace](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Postupy: Přidat ovládací prvky do model Windows Forms](how-to-add-controls-to-windows-forms.md)
