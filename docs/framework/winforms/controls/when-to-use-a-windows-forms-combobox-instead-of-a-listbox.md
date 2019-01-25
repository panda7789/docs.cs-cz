---
title: Kdy použít prvek Windows Forms ComboBox místo prvku ListBox
ms.date: 03/30/2017
helpviewer_keywords:
- ListBox control [Windows Forms], adding and removing items
- ListBox control [Windows Forms], vs. ComboBox
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- ComboBox control [Windows Forms], compared to ListBox
- combo boxes [Windows Forms], compared to list boxes
- ListBox control [Windows Forms], accessing items
- ListCount property
ms.assetid: 7bcaea58-1cfa-46db-9baf-b75a69d8f9ec
ms.openlocfilehash: e6cdc7f0d54d54448a7b9ed42603b07c93eba719
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668337"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a>Kdy použít prvek Windows Forms ComboBox místo prvku ListBox
<xref:System.Windows.Forms.ComboBox> a <xref:System.Windows.Forms.ListBox> ovládací prvky mají podobné chování a v některých případech může být zaměnitelné. Existují však situace, kdy je vhodnější k úkolu jeden z nich.  
  
 Obecně platí je příslušné pole se seznamem, pokud je seznam navrhovaných volby a seznamu je vhodné, pokud chcete omezit vstup na to, co je v seznamu. Pole se seznamem obsahuje textové pole, takže lze napsat volby není v seznamu. Výjimkou je, když <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> je nastavena na <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>. V takovém případě bude ovládací prvek vyberte položku, pokud zadáte své první písmeno.  
  
 Kromě toho pole se seznamem ušetřit místo na formuláři. Protože úplný seznam se nezobrazí, dokud uživatel klepne na šipku dolů, pole se seznamem snadno vejde do omezeného místa, kde nevejde pole se seznamem. Výjimkou je, když <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> je nastavena na <xref:System.Windows.Forms.ComboBoxStyle.Simple>: Zobrazí úplný seznam a pole se seznamem zabírá více místa, než by bylo pole se seznamem.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Postupy: Přidání a odebrání položek z Windows Forms ComboBox, ListBox nebo CheckedListBox – ovládací prvek](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)
- [Postupy: Řazení obsahu Windows Forms ComboBox, ListBox nebo CheckedListBox – ovládací prvek](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Ovládací prvky Windows Forms používané k výpisu možností](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
