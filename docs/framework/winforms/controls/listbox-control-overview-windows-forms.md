---
title: "ListBox – přehled ovládacího prvku (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ListBox
helpviewer_keywords:
- list boxes [Windows Forms], about list boxes
- ListBox control [Windows Forms], about ListBox control
ms.assetid: 37ea226b-6fc8-4c70-936a-c6af4e0cad4c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6e73d76a2d9b31a87bf5a693b5ffa387d7ab5cef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="listbox-control-overview-windows-forms"></a>ListBox – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ListBox> zobrazí seznam, ze kterého může uživatel vybrat jeden nebo více položek. Pokud celkový počet položek překročí číslo, které mohou být zobrazeny, posuvník se automaticky přidá do <xref:System.Windows.Forms.ListBox> ovládacího prvku. Když <xref:System.Windows.Forms.ListBox.MultiColumn%2A> je nastavena na `true`, pole se seznamem zobrazí položky v více sloupců a zobrazí se vodorovného posuvníku. Když <xref:System.Windows.Forms.ListBox.MultiColumn%2A> je nastavena na `false`, pole se seznamem zobrazí položky do jednoho sloupce a zobrazí se svislého posuvníku. Když <xref:System.Windows.Forms.ListBox.ScrollAlwaysVisible%2A> je nastaven na `true`, bez ohledu na počet položek, které se zobrazí posuvníku. <xref:System.Windows.Forms.ListBox.SelectionMode%2A> Vlastnost určuje, kolik položek seznamu lze vybrat současně.  
  
## <a name="ways-to-change-the-listbox-control"></a>Způsoby, jak změnit ListBox – ovládací prvek  
 <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> Vlastnost vrací celočíselnou hodnotu, která odpovídá na první vybranou položku v seznamu. Vybraná položka prostřednictvím kódu programu můžete změnit změnou <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> hodnoty v kódu; odpovídající položku v seznamu se zvýrazní na formuláři Windows. Pokud není vybrána žádná položka, <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> hodnota je -1. Pokud se vybere první položka v seznamu, <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> hodnota je 0. Když je vybraných více položek, <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> hodnota odpovídá vybrané položky, který se zobrazí na začátku seznamu. <xref:System.Windows.Forms.ListBox.SelectedItem%2A> Vlastnost je podobná <xref:System.Windows.Forms.ListBox.SelectedIndex%2A>, ale vrátí položku samostatně, obvykle hodnotu řetězce. <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> Vlastnost odráží počet položek v seznamu a hodnotu <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> vlastnost je vždy jedna více než největší možné <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> hodnota, protože <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> je počítáno od nuly.  
  
 K přidání nebo odstranění položek v <xref:System.Windows.Forms.ListBox> řídit, použijte <xref:System.Windows.Forms.ListBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Clear%2A> nebo <xref:System.Windows.Forms.ListBox.ObjectCollection.Remove%2A> metoda. Alternativně můžete přidat položky do seznamu pomocí <xref:System.Windows.Forms.ListBox.Items%2A> vlastnost v době návrhu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ListBox>  
 [Postupy: Přidání a odebrání položek z Windows Forms ComboBox, ListBox nebo CheckedListBox – ovládací prvek](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [Postupy: řazení obsahu ovládacího prvku Windows Forms ComboBox, ListBox nebo CheckedListBox – ovládací prvek](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [Postupy: vytvoření vazby Windows Forms ComboBox nebo ListBox – ovládací prvek k datům](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)  
 [Přehled ovládacího prvku ComboBox](../../../../docs/framework/winforms/controls/combobox-control-overview-windows-forms.md)  
 [Přehled ovládacího prvku CheckedListBox](../../../../docs/framework/winforms/controls/checkedlistbox-control-overview-windows-forms.md)  
 [Windows Forms – ovládací prvky používané k výpisu možností](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)  
 [Postupy: vytvoření vyhledávací tabulky pro Windows Forms ComboBox, ListBox nebo CheckedListBox – ovládací prvek](../../../../docs/framework/winforms/controls/create-a-lookup-table-for-a-wf-combobox-listbox.md)
