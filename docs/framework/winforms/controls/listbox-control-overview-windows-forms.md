---
title: Přehled ovládacího prvku ListBox
ms.date: 03/30/2017
f1_keywords:
- ListBox
helpviewer_keywords:
- list boxes [Windows Forms], about list boxes
- ListBox control [Windows Forms], about ListBox control
ms.assetid: 37ea226b-6fc8-4c70-936a-c6af4e0cad4c
ms.openlocfilehash: 1abf8bea5c786f2ce326631370fa294ada09a92c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745179"
---
# <a name="listbox-control-overview-windows-forms"></a>ListBox – přehled ovládacího prvku (Windows Forms)
Ovládací prvek model Windows Forms <xref:System.Windows.Forms.ListBox> zobrazí seznam, ze kterého může uživatel vybrat jednu nebo více položek. Pokud celkový počet položek překročí počet, který lze zobrazit, je automaticky přidán posuvník do ovládacího prvku <xref:System.Windows.Forms.ListBox>. Je-li vlastnost <xref:System.Windows.Forms.ListBox.MultiColumn%2A> nastavena na hodnotu `true`, zobrazí se v seznamu položky ve více sloupcích a zobrazí se vodorovný posuvník. Je-li vlastnost <xref:System.Windows.Forms.ListBox.MultiColumn%2A> nastavena na hodnotu `false`, zobrazí se v seznamu položky v jednom sloupci a zobrazí se svislý posuvník. Pokud je <xref:System.Windows.Forms.ListBox.ScrollAlwaysVisible%2A> nastaveno na `true`, zobrazí se posuvník bez ohledu na počet položek. Vlastnost <xref:System.Windows.Forms.ListBox.SelectionMode%2A> určuje, kolik položek seznamu může být vybráno v daném čase.  
  
## <a name="ways-to-change-the-listbox-control"></a>Způsoby, jak změnit ovládací prvek ListBox  
 Vlastnost <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> vrací celočíselnou hodnotu, která odpovídá první vybrané položce v poli seznamu. Můžete programově změnit vybranou položku změnou <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> hodnoty v kódu; odpovídající položka v seznamu se zvýrazní ve formuláři Windows. Pokud není vybraná žádná položka, <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> hodnota je-1. Pokud je vybraná první položka v seznamu, <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> hodnota je 0. Je-li vybráno více položek, hodnota <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> odráží vybranou položku, která se v seznamu zobrazí jako první. Vlastnost <xref:System.Windows.Forms.ListBox.SelectedItem%2A> je podobná <xref:System.Windows.Forms.ListBox.SelectedIndex%2A>, ale vrátí samotnou položku, obvykle hodnotu řetězce. Vlastnost <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> odráží počet položek v seznamu a hodnota vlastnosti <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> je vždy jednou vyšší než největší možná hodnota <xref:System.Windows.Forms.ListBox.SelectedIndex%2A>, protože <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> je počítána od nuly.  
  
 Chcete-li přidat nebo odstranit položky v ovládacím prvku <xref:System.Windows.Forms.ListBox>, použijte metodu <xref:System.Windows.Forms.ListBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Clear%2A> nebo <xref:System.Windows.Forms.ListBox.ObjectCollection.Remove%2A>. Alternativně můžete přidat položky do seznamu pomocí vlastnosti <xref:System.Windows.Forms.ListBox.Items%2A> v době návrhu.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ListBox>
- [Postupy: Přidání a odebrání položek z ovládacích prvků ComboBox, ListBox nebo CheckedListBox z Windows Forms](add-and-remove-items-from-a-wf-combobox.md)
- [Postupy: Řazení obsahu ovládacího prvku ComboBox, ListBox nebo CheckedListBox z Windows Forms](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Postupy: Vázání ovládacího prvku ComboBox nebo ListBox z Windows Forms k datům](how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)
- [Přehled ovládacího prvku ComboBox](combobox-control-overview-windows-forms.md)
- [Přehled ovládacího prvku CheckedListBox](checkedlistbox-control-overview-windows-forms.md)
- [Ovládací prvky Windows Forms používané k výpisu možností](windows-forms-controls-used-to-list-options.md)
- [Postupy: Vytvoření vyhledávací tabulky pro ovládací prvek ComboBox, ListBox nebo CheckedListBox z Windows Forms](create-a-lookup-table-for-a-wf-combobox-listbox.md)
