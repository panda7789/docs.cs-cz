---
title: "ComboBox – přehled ovládacího prvku (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ComboBox
helpviewer_keywords:
- drop-down lists [Windows Forms], Windows Forms
- ComboBox control [Windows Forms], about ComboBox control
- drop-down lists [Windows Forms], ComboBox control
- combo boxes [Windows Forms], about combo boxes
ms.assetid: a58b393f-a614-45d1-8961-857a024b5acd
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 801ebb97c6ee52ce52bbb8f96a07d55e68ca6f1d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="combobox-control-overview-windows-forms"></a>ComboBox – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ComboBox> řízení se používá k zobrazení dat v rozevíracím seznamem. Ve výchozím nastavení <xref:System.Windows.Forms.ComboBox> ovládací prvek se zobrazí ve dvou částech: horní část je textového pole, která umožňuje uživatelům zadejte položku seznamu. Druhá část je pole se seznamem, který zobrazí seznam položek, ze kterých může uživatel vybrat jeden. Další informace o dalších styly – pole se seznamem najdete v tématu [kdy použít Windows Forms ComboBox Instead of ListBox](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md).  
  
 <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> Vlastnost vrací celočíselnou hodnotu, která odpovídá na vybrané položky seznamu. Vybraná položka prostřednictvím kódu programu můžete změnit změnou <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> hodnoty v kódu; odpovídající položku v seznamu se zobrazí v části textového pole se seznamem. Pokud není vybrána žádná položka, <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> hodnota je -1. Pokud se vybere první položka v seznamu, pak se <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> hodnota je 0. <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> Vlastnost je podobná <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> , ale vrátí položku samostatně, obvykle hodnotu řetězce. <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> Vlastnost odráží počet položek v seznamu a hodnotu <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> vlastnost je vždy jedna více než největší možné <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> hodnota, protože <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> je počítáno od nuly.  
  
 K přidání nebo odstranění položek v <xref:System.Windows.Forms.ComboBox> řídit, použijte <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Clear%2A> nebo <xref:System.Windows.Forms.ComboBox.ObjectCollection.Remove%2A> metoda. Alternativně můžete přidat položky do seznamu pomocí <xref:System.Windows.Forms.ComboBox.Items%2A> vlastnost v návrháři.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ComboBox>  
 [Přehled ovládacího prvku ListBox](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)  
 [Kdy použít prvek Windows Forms ComboBox místo prvku ListBox](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)  
 [Postupy: Přidání a odebrání položek z ovládacích prvků ComboBox, ListBox nebo CheckedListBox z Windows Forms](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [Postupy: Řazení obsahu ovládacího prvku ComboBox, ListBox nebo CheckedListBox z Windows Forms](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [Postupy: Přístup ke konkrétním položkám v ovládacím prvku ComboBox, ListBox nebo CheckedListBox z Windows Forms](../../../../docs/framework/winforms/controls/access-specific-items-in-a-wf-combobox-listbox-or-checkedlistbox.md)  
 [Postupy: Vázání ovládacího prvku ComboBox nebo ListBox z Windows Forms k datům](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)  
 [Ovládací prvky Windows Forms používané k výpisu možností](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)  
 [Postupy: Vytvoření vyhledávací tabulky pro ovládací prvek ComboBox, ListBox nebo CheckedListBox z Windows Forms](../../../../docs/framework/winforms/controls/create-a-lookup-table-for-a-wf-combobox-listbox.md)
