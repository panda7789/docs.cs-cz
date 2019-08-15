---
title: 'Postupy: Zablokování sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], column freezing
- data [Windows Forms], displaying
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
ms.openlocfilehash: d38c8d73bc70e7e521b476ca78c8f102d003c538
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040338"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Zablokování sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře
Když uživatelé zobrazují data zobrazená v ovládacím <xref:System.Windows.Forms.DataGridView> prvku model Windows Forms, někdy potřebují často odkazovat na jeden sloupec nebo na sadu sloupců. Když například zobrazíte tabulku s informacemi o zákaznících, které obsahují mnoho sloupců, je vhodné zobrazit jméno zákazníka kdykoliv a povolit ostatním sloupců posouvání mimo viditelnou oblast.

 Chcete-li dosáhnout tohoto chování, můžete ukotvit sloupce v ovládacím prvku. Při ukotvení sloupce jsou zmrazeny také všechny sloupce vlevo (nebo napravo ve skriptech se zápisem zprava doleva). Zmrazené sloupce zůstávají na místě, zatímco všechny ostatní sloupce se můžou posouvat. Pokud je povoleno přeřazení sloupce, jsou zmrazené sloupce považovány za skupinu odlišnou od nezmrazených sloupců. Uživatelé mohou přemístit sloupce v obou skupinách, ale nemohou přesunout sloupec z jedné skupiny do druhé.

 Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.DataGridView> ovládací prvek. Informace o nastavení takového projektu naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms.

## <a name="to-freeze-a-column-using-the-designer"></a>Ukotvení sloupce pomocí návrháře

1. V pravém <xref:System.Windows.Forms.DataGridView> horním rohu ovládacího prvku klikněte na glyf inteligentních značek (![inteligentní značky glyf](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) a pak vyberte **Upravit sloupce**.

2. Vyberte sloupec ze seznamu **vybrané sloupce** .

3. V mřížce **vlastnosti sloupce** nastavte <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> vlastnost na `true`hodnotu.

    > [!NOTE]
    >  Sloupec můžete také při přidávání ukotvit tak, že vyberete políčko **zmrazené** v dialogovém okně **Přidat sloupec** .

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- [Postupy: Přidání a odebrání sloupců v ovládacím prvku DataGridView model Windows Forms pomocí návrháře](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Postupy: Povolit změnu pořadí sloupců v ovládacím prvku DataGridView model Windows Forms pomocí návrháře](enable-column-reordering-in-the-datagrid-using-the-designer.md)
- [Postupy: Zobrazení textu zprava doleva v model Windows Forms pro globalizaci](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100))
- [Postupy: Vytvoření projektu model Windows Forms aplikace](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Postupy: Přidat ovládací prvky do model Windows Forms](how-to-add-controls-to-windows-forms.md)
