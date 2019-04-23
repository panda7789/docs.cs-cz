---
title: ListBox – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ListBox
helpviewer_keywords:
- list boxes [Windows Forms], about list boxes
- ListBox control [Windows Forms], about ListBox control
ms.assetid: 37ea226b-6fc8-4c70-936a-c6af4e0cad4c
ms.openlocfilehash: f70246d4a4d158815ee9662036eca8edeb891d85
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104193"
---
# <a name="listbox-control-overview-windows-forms"></a>ListBox – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ListBox> ovládací prvek zobrazí seznam, ze kterého může uživatel vybrat jednu nebo více položek. Pokud celkový počet položek překročí číslo, které mohou být zobrazeny, posuvník se automaticky přidá do <xref:System.Windows.Forms.ListBox> ovládacího prvku. Když <xref:System.Windows.Forms.ListBox.MultiColumn%2A> je nastavena na `true`, pole se seznamem zobrazí položky ve více sloupcích a zobrazí se vodorovný posuvník. Když <xref:System.Windows.Forms.ListBox.MultiColumn%2A> je nastavena na `false`, pole se seznamem zobrazí položky v jednom sloupci a se zobrazí svislý posuvník. Když <xref:System.Windows.Forms.ListBox.ScrollAlwaysVisible%2A> je nastavena na `true`, bez ohledu na počet položek, které se zobrazí posuvník. <xref:System.Windows.Forms.ListBox.SelectionMode%2A> Vlastnost určuje, kolik položek seznamu můžete vybrat najednou.  
  
## <a name="ways-to-change-the-listbox-control"></a>Způsoby, jak změnit ovládacího prvku ListBox  
 <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> Vlastnost vrací celočíselnou hodnotu, která odpovídá na první vybranou položku v seznamu. Vybrané položky můžete programově změnit tak, že změníte <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> hodnota v kódu; odpovídající položku v seznamu se budou zvýrazněny ve formuláři Windows. Pokud není vybrána žádná položka, <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> hodnotu -1. Pokud se vybere první položka v seznamu, <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> hodnota je 0. Pokud je vybráno více položek, <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> hodnota odpovídá vybrané položky, které se zobrazí v seznamu jako první. <xref:System.Windows.Forms.ListBox.SelectedItem%2A> Vlastnost je podobný <xref:System.Windows.Forms.ListBox.SelectedIndex%2A>, ale vrací přímo s příslušnou položkou, obvykle řetězcovou hodnotu. <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> Vlastnost odpovídá počtu položek v seznamu a hodnota <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> vlastnost je vždy jeden větší než největší možné <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> hodnotu, protože <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> je založený na nule.  
  
 Přidání nebo odstranění položek v <xref:System.Windows.Forms.ListBox> řídit, použijte <xref:System.Windows.Forms.ListBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Clear%2A> nebo <xref:System.Windows.Forms.ListBox.ObjectCollection.Remove%2A> metody. Alternativně můžete přidat položky do seznamu s použitím <xref:System.Windows.Forms.ListBox.Items%2A> vlastnost v době návrhu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ListBox>
- [Postupy: Přidání a odebrání položek z Windows Forms ComboBox, ListBox nebo CheckedListBox – ovládací prvek](add-and-remove-items-from-a-wf-combobox.md)
- [Postupy: Řazení obsahu Windows Forms ComboBox, ListBox nebo CheckedListBox – ovládací prvek](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Postupy: Windows Forms ComboBox nebo ListBox – ovládací prvek svázat Data](how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)
- [Přehled ovládacího prvku ComboBox](combobox-control-overview-windows-forms.md)
- [Přehled ovládacího prvku CheckedListBox](checkedlistbox-control-overview-windows-forms.md)
- [Ovládací prvky Windows Forms používané k výpisu možností](windows-forms-controls-used-to-list-options.md)
- [Postupy: Vytvoření vyhledávací tabulky pro Windows Forms ComboBox, ListBox nebo CheckedListBox – ovládací prvek](create-a-lookup-table-for-a-wf-combobox-listbox.md)
