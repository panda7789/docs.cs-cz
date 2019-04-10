---
title: ComboBox – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ComboBox
helpviewer_keywords:
- drop-down lists [Windows Forms], Windows Forms
- ComboBox control [Windows Forms], about ComboBox control
- drop-down lists [Windows Forms], ComboBox control
- combo boxes [Windows Forms], about combo boxes
ms.assetid: a58b393f-a614-45d1-8961-857a024b5acd
ms.openlocfilehash: 80056771744c9b97828a024adf32638e545a839e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211569"
---
# <a name="combobox-control-overview-windows-forms"></a>ComboBox – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ComboBox> ovládacího prvku se používá k zobrazení dat v rozevíracím seznamem. Ve výchozím nastavení <xref:System.Windows.Forms.ComboBox> ovládací prvek se zobrazí ve dvou částech: hlavní část je textové pole, která umožňuje uživateli zadat položku seznamu. Druhá část je pole se seznamem, který zobrazuje seznam položek, ze kterého může uživatel vybrat jednu. Další informace o dalších styly – pole se seznamem, naleznete v tématu [kdy použít Windows Forms ComboBox Instead of ListBox](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md).  
  
 <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> Vlastnost vrátí celočíselnou hodnotu, která odpovídá vybrané položky seznamu. Vybrané položky můžete programově změnit tak, že změníte <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> hodnota v kódu; odpovídající položku v seznamu se zobrazí v části textového pole, pole se seznamem. Pokud není vybrána žádná položka, <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> hodnotu -1. Pokud se vybere první položka v seznamu, pak bude <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> hodnota je 0. <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> Vlastnost je podobný <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> , ale vrací přímo s příslušnou položkou, obvykle řetězcovou hodnotu. <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> Vlastnost odpovídá počtu položek v seznamu a hodnota <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> vlastnost je vždy jeden větší než největší možné <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> hodnotu, protože <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> je založený na nule.  
  
 Přidání nebo odstranění položek v <xref:System.Windows.Forms.ComboBox> řídit, použijte <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Clear%2A> nebo <xref:System.Windows.Forms.ComboBox.ObjectCollection.Remove%2A> metody. Alternativně můžete přidat položky do seznamu s použitím <xref:System.Windows.Forms.ComboBox.Items%2A> vlastnost v návrháři.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ComboBox>
- [Přehled ovládacího prvku ListBox](listbox-control-overview-windows-forms.md)
- [Kdy použít prvek Windows Forms ComboBox místo prvku ListBox](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [Postupy: Přidání a odebrání položek z ovládacích prvků Windows Forms ComboBox, ListBox nebo CheckedListBox](add-and-remove-items-from-a-wf-combobox.md)
- [Postupy: Řazení obsahu ovládacího prvku Windows Forms ComboBox, ListBox nebo CheckedListBox](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Postupy: Přístup ke konkrétním položkám v ovládacím prvku Windows Forms ComboBox, ListBox nebo CheckedListBox](access-specific-items-in-a-wf-combobox-listbox-or-checkedlistbox.md)
- [Postupy: Vázání ovládacího prvku Windows Forms ComboBox nebo ListBox k datům](how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)
- [Ovládací prvky Windows Forms používané k výpisu možností](windows-forms-controls-used-to-list-options.md)
- [Postupy: Vytvoření vyhledávací tabulky pro ovládací prvek Windows Forms ComboBox, ListBox nebo CheckedListBox](create-a-lookup-table-for-a-wf-combobox-listbox.md)
