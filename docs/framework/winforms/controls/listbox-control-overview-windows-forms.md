---
title: ListBox – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ListBox
helpviewer_keywords:
- list boxes [Windows Forms], about list boxes
- ListBox control [Windows Forms], about ListBox control
ms.assetid: 37ea226b-6fc8-4c70-936a-c6af4e0cad4c
ms.openlocfilehash: d4cb423a6f32778695abeae725da9755b610d209
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537561"
---
# <a name="listbox-control-overview-windows-forms"></a>ListBox – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ListBox> zobrazí seznam, ze kterého může uživatel vybrat jeden nebo více položek. Pokud celkový počet položek překročí číslo, které mohou být zobrazeny, posuvník se automaticky přidá do <xref:System.Windows.Forms.ListBox> ovládacího prvku. Když <xref:System.Windows.Forms.ListBox.MultiColumn%2A> je nastavena na `true`, pole se seznamem zobrazí položky v více sloupců a zobrazí se vodorovného posuvníku. Když <xref:System.Windows.Forms.ListBox.MultiColumn%2A> je nastavena na `false`, pole se seznamem zobrazí položky do jednoho sloupce a zobrazí se svislého posuvníku. Když <xref:System.Windows.Forms.ListBox.ScrollAlwaysVisible%2A> je nastaven na `true`, bez ohledu na počet položek, které se zobrazí posuvníku. <xref:System.Windows.Forms.ListBox.SelectionMode%2A> Vlastnost určuje, kolik položek seznamu lze vybrat současně.  
  
## <a name="ways-to-change-the-listbox-control"></a>Způsoby, jak změnit ListBox – ovládací prvek  
 <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> Vlastnost vrací celočíselnou hodnotu, která odpovídá na první vybranou položku v seznamu. Vybraná položka prostřednictvím kódu programu můžete změnit změnou <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> hodnoty v kódu; odpovídající položku v seznamu se zvýrazní na formuláři Windows. Pokud není vybrána žádná položka, <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> hodnota je -1. Pokud se vybere první položka v seznamu, <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> hodnota je 0. Když je vybraných více položek, <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> hodnota odpovídá vybrané položky, který se zobrazí na začátku seznamu. <xref:System.Windows.Forms.ListBox.SelectedItem%2A> Vlastnost je podobná <xref:System.Windows.Forms.ListBox.SelectedIndex%2A>, ale vrátí položku samostatně, obvykle hodnotu řetězce. <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> Vlastnost odráží počet položek v seznamu a hodnotu <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> vlastnost je vždy jedna více než největší možné <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> hodnota, protože <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> je počítáno od nuly.  
  
 K přidání nebo odstranění položek v <xref:System.Windows.Forms.ListBox> řídit, použijte <xref:System.Windows.Forms.ListBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Clear%2A> nebo <xref:System.Windows.Forms.ListBox.ObjectCollection.Remove%2A> metoda. Alternativně můžete přidat položky do seznamu pomocí <xref:System.Windows.Forms.ListBox.Items%2A> vlastnost v době návrhu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ListBox>  
 [Postupy: Přidání a odebrání položek z ovládacích prvků ComboBox, ListBox nebo CheckedListBox z Windows Forms](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [Postupy: Řazení obsahu ovládacího prvku ComboBox, ListBox nebo CheckedListBox z Windows Forms](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [Postupy: Vázání ovládacího prvku ComboBox nebo ListBox z Windows Forms k datům](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)  
 [Přehled ovládacího prvku ComboBox](../../../../docs/framework/winforms/controls/combobox-control-overview-windows-forms.md)  
 [Přehled ovládacího prvku CheckedListBox](../../../../docs/framework/winforms/controls/checkedlistbox-control-overview-windows-forms.md)  
 [Ovládací prvky Windows Forms používané k výpisu možností](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)  
 [Postupy: Vytvoření vyhledávací tabulky pro ovládací prvek ComboBox, ListBox nebo CheckedListBox z Windows Forms](../../../../docs/framework/winforms/controls/create-a-lookup-table-for-a-wf-combobox-listbox.md)
