---
title: Přehled ovládacího prvku ComboBox
ms.date: 03/30/2017
f1_keywords:
- ComboBox
helpviewer_keywords:
- drop-down lists [Windows Forms], Windows Forms
- ComboBox control [Windows Forms], about ComboBox control
- drop-down lists [Windows Forms], ComboBox control
- combo boxes [Windows Forms], about combo boxes
ms.assetid: a58b393f-a614-45d1-8961-857a024b5acd
ms.openlocfilehash: 9fb270d7787902872a32a87c140316f756bd48aa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743844"
---
# <a name="combobox-control-overview-windows-forms"></a>ComboBox – přehled ovládacího prvku (Windows Forms)
Ovládací prvek model Windows Forms <xref:System.Windows.Forms.ComboBox> slouží k zobrazení dat v rozevíracím poli se seznamem. Ve výchozím nastavení se ovládací prvek <xref:System.Windows.Forms.ComboBox> zobrazí ve dvou částech: horní část je textové pole, které uživateli umožňuje zadat položku seznamu. Druhá část je seznam, ve kterém se zobrazuje seznam položek, ze kterých si uživatel může vybrat jednu. Další informace o dalších stylech pole se seznamem naleznete v tématu [kdy použít model Windows Forms pole se seznamem namísto seznamu](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md).  
  
 Vlastnost <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> vrací celočíselnou hodnotu, která odpovídá vybrané položce seznamu. Můžete programově změnit vybranou položku změnou <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> hodnoty v kódu; odpovídající položka v seznamu se zobrazí v textovém poli v poli se seznamem. Pokud není vybraná žádná položka, <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> hodnota je-1. Je-li vybrána první položka v seznamu, hodnota <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> je 0. Vlastnost <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> je podobná <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A>, ale vrátí samotnou položku, obvykle hodnotu řetězce. Vlastnost <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> odráží počet položek v seznamu a hodnota vlastnosti <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> je vždy jednou vyšší než největší možná hodnota <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A>, protože <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> je počítána od nuly.  
  
 Chcete-li přidat nebo odstranit položky v ovládacím prvku <xref:System.Windows.Forms.ComboBox>, použijte metodu <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Clear%2A> nebo <xref:System.Windows.Forms.ComboBox.ObjectCollection.Remove%2A>. Alternativně můžete přidat položky do seznamu pomocí vlastnosti <xref:System.Windows.Forms.ComboBox.Items%2A> v návrháři.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ComboBox>
- [Přehled ovládacího prvku ListBox](listbox-control-overview-windows-forms.md)
- [Kdy použít prvek Windows Forms ComboBox místo prvku ListBox](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [Postupy: Přidání a odebrání položek z ovládacích prvků ComboBox, ListBox nebo CheckedListBox z Windows Forms](add-and-remove-items-from-a-wf-combobox.md)
- [Postupy: Řazení obsahu ovládacího prvku ComboBox, ListBox nebo CheckedListBox z Windows Forms](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Postupy: Přístup ke konkrétním položkám v ovládacím prvku ComboBox, ListBox nebo CheckedListBox z Windows Forms](access-specific-items-in-a-wf-combobox-listbox-or-checkedlistbox.md)
- [Postupy: Vázání ovládacího prvku ComboBox nebo ListBox z Windows Forms k datům](how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)
- [Ovládací prvky Windows Forms používané k výpisu možností](windows-forms-controls-used-to-list-options.md)
- [Postupy: Vytvoření vyhledávací tabulky pro ovládací prvek ComboBox, ListBox nebo CheckedListBox z Windows Forms](create-a-lookup-table-for-a-wf-combobox-listbox.md)
