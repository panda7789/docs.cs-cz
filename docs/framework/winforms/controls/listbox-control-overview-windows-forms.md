---
title: ListBox – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ListBox
helpviewer_keywords:
- list boxes [Windows Forms], about list boxes
- ListBox control [Windows Forms], about ListBox control
ms.assetid: 37ea226b-6fc8-4c70-936a-c6af4e0cad4c
ms.openlocfilehash: 58fb5c40ab054a71b6d15beaa00190f3eaff3019
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591549"
---
# <a name="listbox-control-overview-windows-forms"></a>ListBox – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ListBox> ovládací prvek zobrazí seznam, ze kterého může uživatel vybrat jednu nebo více položek. Pokud celkový počet položek překročí číslo, které mohou být zobrazeny, posuvník se automaticky přidá do <xref:System.Windows.Forms.ListBox> ovládacího prvku. Když <xref:System.Windows.Forms.ListBox.MultiColumn%2A> je nastavena na `true`, pole se seznamem zobrazí položky ve více sloupcích a zobrazí se vodorovný posuvník. Když <xref:System.Windows.Forms.ListBox.MultiColumn%2A> je nastavena na `false`, pole se seznamem zobrazí položky v jednom sloupci a se zobrazí svislý posuvník. Když <xref:System.Windows.Forms.ListBox.ScrollAlwaysVisible%2A> je nastavena na `true`, bez ohledu na počet položek, které se zobrazí posuvník. <xref:System.Windows.Forms.ListBox.SelectionMode%2A> Vlastnost určuje, kolik položek seznamu můžete vybrat najednou.  
  
## <a name="ways-to-change-the-listbox-control"></a>Způsoby, jak změnit ovládacího prvku ListBox  
 <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> Vlastnost vrací celočíselnou hodnotu, která odpovídá na první vybranou položku v seznamu. Vybrané položky můžete programově změnit tak, že změníte <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> hodnota v kódu; odpovídající položku v seznamu se budou zvýrazněny ve formuláři Windows. Pokud není vybrána žádná položka, <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> hodnotu -1. Pokud se vybere první položka v seznamu, <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> hodnota je 0. Pokud je vybráno více položek, <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> hodnota odpovídá vybrané položky, které se zobrazí v seznamu jako první. <xref:System.Windows.Forms.ListBox.SelectedItem%2A> Vlastnost je podobný <xref:System.Windows.Forms.ListBox.SelectedIndex%2A>, ale vrací přímo s příslušnou položkou, obvykle řetězcovou hodnotu. <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> Vlastnost odpovídá počtu položek v seznamu a hodnota <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> vlastnost je vždy jeden větší než největší možné <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> hodnotu, protože <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> je založený na nule.  
  
 Přidání nebo odstranění položek v <xref:System.Windows.Forms.ListBox> řídit, použijte <xref:System.Windows.Forms.ListBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Clear%2A> nebo <xref:System.Windows.Forms.ListBox.ObjectCollection.Remove%2A> metody. Alternativně můžete přidat položky do seznamu s použitím <xref:System.Windows.Forms.ListBox.Items%2A> vlastnost v době návrhu.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.ListBox>
- [Postupy: Přidání a odebrání položek z Windows Forms ComboBox, ListBox nebo CheckedListBox – ovládací prvek](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)
- [Postupy: Řazení obsahu Windows Forms ComboBox, ListBox nebo CheckedListBox – ovládací prvek](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Postupy: Windows Forms ComboBox nebo ListBox – ovládací prvek svázat Data](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)
- [Přehled ovládacího prvku ComboBox](../../../../docs/framework/winforms/controls/combobox-control-overview-windows-forms.md)
- [Přehled ovládacího prvku CheckedListBox](../../../../docs/framework/winforms/controls/checkedlistbox-control-overview-windows-forms.md)
- [Ovládací prvky Windows Forms používané k výpisu možností](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
- [Postupy: Vytvoření vyhledávací tabulky pro Windows Forms ComboBox, ListBox nebo CheckedListBox – ovládací prvek](../../../../docs/framework/winforms/controls/create-a-lookup-table-for-a-wf-combobox-listbox.md)
