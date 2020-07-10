---
title: Pole se seznamem vs. ListBox
description: Seznamte se s používáním model Windows Forms pole se seznamem a model Windows Forms seznamem a Naučte se, jak dejte vědět, kdy je jedna nebo druhá pro úkol vhodnější.
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
ms.openlocfilehash: ca6ad6bec2dbc30128ea09808af2806687b17a8c
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174416"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a>Kdy použít prvek Windows Forms ComboBox místo prvku ListBox
<xref:System.Windows.Forms.ComboBox> <xref:System.Windows.Forms.ListBox> Ovládací prvky a mají podobné chování a v některých případech mohou být zaměnitelné. Existují však situace, kdy je jedna nebo druhá pro úkol vhodnější.  
  
 Obecně je pole se seznamem vhodné, pokud existuje seznam navrhovaných možností a seznam je vhodný, když chcete omezit vstup na to, co je v seznamu. Pole se seznamem obsahuje pole textového pole, takže výběry, které nejsou na seznamu, lze zadat v. Výjimkou je, když <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> je vlastnost nastavena na <xref:System.Windows.Forms.ComboBoxStyle.DropDownList> . V takovém případě ovládací prvek vybere položku, pokud zadáte její první písmeno.  
  
 Kromě toho pole se seznamem šetří místo na formuláři. Vzhledem k tomu, že se úplný seznam nezobrazí, dokud uživatel neklikne na šipku dolů, pole se seznamem se dá snadno přizpůsobit na malé místo, kde se seznam nevejde. Výjimkou je, že pokud <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> je vlastnost nastavena na hodnotu <xref:System.Windows.Forms.ComboBoxStyle.Simple> : zobrazí se úplný seznam a pole se seznamem bude trvat více místa, než je pole seznamu.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Postupy: Přidání a odebrání položek z ovládacích prvků ComboBox, ListBox nebo CheckedListBox z Windows Forms](add-and-remove-items-from-a-wf-combobox.md)
- [Postupy: Řazení obsahu ovládacího prvku Windows Forms ComboBox, ListBox nebo CheckedListBox](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Ovládací prvky Windows Forms používané k výpisu možností](windows-forms-controls-used-to-list-options.md)
