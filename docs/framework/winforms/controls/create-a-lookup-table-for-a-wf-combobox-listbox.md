---
title: "Postupy: Vytvoření vyhledávací tabulky pro ovládací prvek Windows Forms ComboBox, ListBox nebo CheckedListBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 93f49a8fbd2cc8ffae94e4dcbbc4babf7c1137cd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-lookup-table-for-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>Postupy: Vytvoření vyhledávací tabulky pro ovládací prvek Windows Forms ComboBox, ListBox nebo CheckedListBox
Někdy je užitečné zobrazit data ve formátu uživatelsky přívětivý ve formuláři Windows, ale ukládání dat do formátu, který je smysluplnější do vaší aplikace. Například může zobrazit formulář objednávky pro jídlo položek nabídky v seznamu s názvem. Datová tabulka záznam pořadí by však obsahovat jedinečná čísla ID představující jídlo. Příklad toho, jak ukládat a zobrazit formulář objednávky data pro jídlo v následujících tabulkách.  
  
### <a name="orderdetailstable"></a>OrderDetailsTable  
  
|OrderID|ItemID|Množství|  
|-------------|------------|--------------|  
|4085|12|1|  
|4086|13|3|  
  
### <a name="itemtable"></a>ItemTable  
  
|ID|Název|  
|--------|----------|  
|12|Určené|  
|13|Kuřecí|  
  
 V tomto scénáři, jedna tabulka, **OrderDetailsTable**, ukládá informace jste se zobrazení a ukládání. Ušetřit místo, se ale tak poměrně jako nesrozumitelné způsobem. V tabulce **ItemTable**, obsahuje pouze informace týkající se vzhled o které ID číslo je ekvivalentní, na které jídlo název a nic o skutečné jídlo objednávky.  
  
 **ItemTable** je připojený k <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, nebo <xref:System.Windows.Forms.CheckedListBox> řízení prostřednictvím tři vlastnosti. `DataSource` Vlastnost obsahuje název této tabulky. `DisplayMember` Vlastnost obsahuje sloupce dat z této tabulky, které chcete zobrazit v ovládacím prvku (název jídlo). `ValueMember` Vlastnost obsahuje sloupce dat této tabulky s uložené informace (číslo ID).  
  
 **OrderDetailsTable** je připojen k ovládacímu prvku jeho vazby kolekce přistupovat prostřednictvím <xref:System.Windows.Forms.Control.DataBindings%2A> vlastnost. Když přidáte objekt vazby ke kolekci, připojíte vlastnost ovládacího prvku na konkrétní data člena (sloupec ID čísla) ve zdroji dat ( **OrderDetailsTable**). Při výběru v ovládacím prvku, je tato tabulka uložení vstup formuláře.  
  
### <a name="to-create-a-lookup-table"></a>K vytvoření vyhledávací tabulky  
  
1.  Přidat <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, nebo <xref:System.Windows.Forms.CheckedListBox> ovládacího prvku do formuláře.  
  
2.  Připojení ke zdroji dat.  
  
3.  Vytvořte vztah data mezi dvěma tabulkami. V tématu [Úvod do objektů DataRelation](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192).  
  
4.  Nastavte následující vlastnosti. Lze nastavit v kódu nebo v návrháři.  
  
    |Vlastnost|Nastavení|  
    |--------------|-------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|Tabulka, která obsahuje informace o ID, které se rovná která položka číslo. V předchozím scénáři je to `ItemTable`.|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|Sloupec tabulky zdroje dat, která chcete zobrazit v ovládacím prvku. V předchozím scénáři je to `"Name"` (Pokud chcete nastavit v kódu, použijte uvozovky).|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|Sloupec tabulky zdroje dat, která obsahuje informace o uložené. V předchozím scénáři je to `"ID"` (Pokud chcete nastavit v kódu, použijte uvozovky).|  
  
5.  V postupu, volání <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> metodu <xref:System.Windows.Forms.ControlBindingsCollection> třídy pro vazbu ovládacího prvku <xref:System.Windows.Forms.ListControl.SelectedValue%2A> vlastnost, která má v tabulce zaznamenávání vstup formuláře. Můžete také to provedete v Návrháři místo v kódu, přístup k ovládacího prvku <xref:System.Windows.Forms.Control.DataBindings%2A> vlastnost **vlastnosti** okno. V předchozím scénáři je to `OrderDetailsTable`, a sloupec je `"ItemID"`.  
  
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
