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
ms.openlocfilehash: 88b6a6023fbfdd8fa315fcd434357626ea69a9ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537765"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a>Kdy použít prvek Windows Forms ComboBox místo prvku ListBox
<xref:System.Windows.Forms.ComboBox> a <xref:System.Windows.Forms.ListBox> ovládacích prvků mají podobné chování a v některých případech může být zaměnitelné. Existují dobu, ale pokud jeden z nich je vhodnější pro úlohu.  
  
 Obecně platí pole se seznamem je vhodné, pokud je seznam navrhovaných volby a pole se seznamem je vhodné, pokud chcete omezit vstup na to, co je v seznamu. Pole se seznamem obsahuje textové pole pole, proto lze napsat volby nejsou na seznamu. Jedinou výjimkou je, když <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> je nastavena na <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>. V takovém případě bude ovládací prvek vyberte položku, pokud zadáte svůj první písmeno.  
  
 Kromě toho se seznamem ušetřit místo na formuláři. Protože úplný seznam se nezobrazí, dokud uživatel kliknutím na šipku dolů, můžete snadno začlenit pole se seznamem v malé místo, kde by vyhovovaly pole se seznamem. Výjimkou je, když <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> je nastavena na <xref:System.Windows.Forms.ComboBoxStyle.Simple>: se zobrazuje úplný seznam a pole se seznamem zabírá více místa, než by bylo pole se seznamem.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 [Postupy: Přidání a odebrání položek z ovládacích prvků ComboBox, ListBox nebo CheckedListBox z Windows Forms](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [Postupy: Řazení obsahu ovládacího prvku ComboBox, ListBox nebo CheckedListBox z Windows Forms](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [Ovládací prvky Windows Forms používané k výpisu možností](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
