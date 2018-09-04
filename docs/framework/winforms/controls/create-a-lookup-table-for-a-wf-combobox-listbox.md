---
title: 'Postupy: Vytvoření vyhledávací tabulky pro ovládací prvek Windows Forms ComboBox, ListBox nebo CheckedListBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CheckedListBox control [Windows Forms], creating lookup tables
- lookup tables
- list boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], lookup tables
- ComboBox control [Windows Forms], lookup table
- lookup tables [Windows Forms], creating for controls
- combo boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], creating lookup tables
ms.assetid: 4ce35f12-1f4e-4317-92d1-af8686a8cfaa
ms.openlocfilehash: b719f2112aac1292b668fe199d48de4b0b60ed21
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43659135"
---
# <a name="how-to-create-a-lookup-table-for-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>Postupy: Vytvoření vyhledávací tabulky pro ovládací prvek Windows Forms ComboBox, ListBox nebo CheckedListBox
Někdy je užitečné zobrazit data ve formátu uživatelsky přívětivé ve formuláři Windows Forms, ale ukládat data ve formátu, který má více smysl pro váš program. Například může zobrazit formulář objednávky pro potravin položky nabídky podle názvu v seznamu. Tabulka dat záznam pořadí by ale obsahovat jedinečné identifikační čísla představující potravinovém. Příklad toho, jak ukládat a zobrazovat data formulář objednávky potravin naleznete v následujících tabulkách.  
  
### <a name="orderdetailstable"></a>OrderDetailsTable  
  
|ID objednávky|ID položky|Množství|  
|-------------|------------|--------------|  
|4085|12|1|  
|4086|13|3|  
  
### <a name="itemtable"></a>ItemTable  
  
|ID|Název|  
|--------|----------|  
|12|Brambory|  
|13|Kuřecí|  
  
 V tomto scénáři, jedné tabulky **OrderDetailsTable**, ukládá informace jste obeznámeni s zobrazení a uložení. Ale pro úsporu místa, dělá to docela nejasné způsobem. V další tabulce **ItemTable**, obsahuje pouze informace vzhled o které ID číslo je ekvivalentní, na které potravin název a nic o objednávkách skutečné potravin.  
  
 **ItemTable** je připojen k <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, nebo <xref:System.Windows.Forms.CheckedListBox> řízení prostřednictvím tři vlastnosti. `DataSource` Vlastnost obsahuje název této tabulky. `DisplayMember` Vlastnost obsahuje sloupce dat této tabulky, kterou chcete zobrazit v ovládacím prvku (food název). `ValueMember` Vlastnost obsahuje sloupce dat této tabulky s uložené informace (identifikační číslo).  
  
 **OrderDetailsTable** je připojen k ovládací prvek pomocí jeho vazby kolekce přistupovat prostřednictvím <xref:System.Windows.Forms.Control.DataBindings%2A> vlastnost. Při přidání objektu vazby ke kolekci připojíte vlastnosti ovládacího prvku do konkrétního datového člena (sloupec ID čísla) ve zdroji dat ( **OrderDetailsTable**). Při provedení výběru v ovládacím prvku Tato tabulka je, kde je uložen vstup formuláře.  
  
### <a name="to-create-a-lookup-table"></a>Vytvoření vyhledávací tabulky  
  
1.  Přidat <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, nebo <xref:System.Windows.Forms.CheckedListBox> ovládacího prvku na formuláři.  
  
2.  Připojení ke zdroji dat.  
  
3.  Vytvořte datová relace mezi tabulkami. Zobrazit [Úvod do objektů DataRelation](https://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192).  
  
4.  Nastavte následující vlastnosti. To můžete udělat v kódu nebo v návrháři.  
  
    |Vlastnost|Nastavení|  
    |--------------|-------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|Tabulka, která obsahuje informace, o které ID číslo odpovídá které položce. V předchozím scénáři je to `ItemTable`.|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|Sloupec tabulky zdroje dat, který chcete zobrazit v ovládacím prvku. V předchozím scénáři je to `"Name"` (Pokud chcete nastavit v kódu, použijte uvozovky).|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|Sloupec tabulky zdroje dat, obsahující uložené informace. V předchozím scénáři je to `"ID"` (Pokud chcete nastavit v kódu, použijte uvozovky).|  
  
5.  V postupu, zavolejte <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> metodu <xref:System.Windows.Forms.ControlBindingsCollection> třída pro vytvoření vazby ovládacího prvku <xref:System.Windows.Forms.ListControl.SelectedValue%2A> vlastnost do tabulky záznam vstup formuláře. Můžete také uděláte v Návrháři místo v kódu, díky přístupu do ovládacího prvku <xref:System.Windows.Forms.Control.DataBindings%2A> vlastnost **vlastnosti** okna. V předchozím scénáři je to `OrderDetailsTable`, a sloupec je `"ItemID"`.  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Datové vazby a Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [Přehled ovládacího prvku ListBox](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)  
 [Přehled ovládacího prvku ComboBox](../../../../docs/framework/winforms/controls/combobox-control-overview-windows-forms.md)  
 [Přehled ovládacího prvku CheckedListBox](../../../../docs/framework/winforms/controls/checkedlistbox-control-overview-windows-forms.md)  
 [Ovládací prvky Windows Forms používané k výpisu možností](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
