---
title: Vytvoření vyhledávací tabulky pro ovládací prvek ComboBox, ListBox nebo CheckedListBox
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
ms.openlocfilehash: 4bbbc66a56c7ce269c2dabd593db88f96907d755
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737366"
---
# <a name="how-to-create-a-lookup-table-for-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>Postupy: Vytvoření vyhledávací tabulky pro ovládací prvek Windows Forms ComboBox, ListBox nebo CheckedListBox
Někdy je užitečné zobrazit data v uživatelsky přívětivém formátu formuláře Windows, ale data ukládat ve formátu, který je pro váš program smysluplnější. Například formulář objednávky pro potraviny může zobrazit položky nabídky podle názvu v seznamu. Data, která záznam obsahuje, ale budou obsahovat jedinečná čísla ID představující jídlo. V následujících tabulkách je uveden příklad ukládání a zobrazení dat z pořadí pro potraviny.  
  
### <a name="orderdetailstable"></a>OrderDetailsTable  
  
|Seskup|ItemID|Množství|  
|-------------|------------|--------------|  
|4085|12|1|  
|4086|13|3|  
  
### <a name="itemtable"></a>Položkace  
  
|ID|Name|  
|--------|----------|  
|12|Hlíz|  
|13|Nainstalováním|  
  
 V tomto scénáři jedna tabulka **OrderDetailsTable**ukládá skutečné informace, které se týkají zobrazení a uložení. Pokud ale chcete ušetřit místo, je to poměrně nešifrovaným způsobem. Druhá tabulka, **položka**, obsahuje pouze informace o vzhledu, jejichž číslo ID je ekvivalentní k tomu, který název potravy a nic o skutečných seřazeních potravin.  
  
 Vlastnost **Item** je připojena k ovládacímu prvku <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>nebo <xref:System.Windows.Forms.CheckedListBox> prostřednictvím tří vlastností. Vlastnost `DataSource` obsahuje název této tabulky. Vlastnost `DisplayMember` obsahuje datový sloupec této tabulky, který chcete zobrazit v ovládacím prvku (název potravy). Vlastnost `ValueMember` obsahuje datový sloupec v tabulce s uloženými informacemi (číslo ID).  
  
 **OrderDetailsTable** je připojen k ovládacímu prvku prostřednictvím kolekce vazeb, ke kterému se přistupoval prostřednictvím vlastnosti <xref:System.Windows.Forms.Control.DataBindings%2A>. Když přidáte objekt vazby do kolekce, připojíte vlastnost ovládacího prvku ke konkrétnímu datovému členu (sloupci čísel ID) ve zdroji dat ( **OrderDetailsTable**). V případě, že je v ovládacím prvku proveden výběr, v této tabulce je uložen vstup z formuláře.  
  
### <a name="to-create-a-lookup-table"></a>Vytvoření vyhledávací tabulky  
  
1. Do formuláře přidejte ovládací prvek <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>nebo <xref:System.Windows.Forms.CheckedListBox>.  
  
2. Připojte se ke zdroji dat.  
  
3. Vytvořte datový vztah mezi oběma tabulkami. Viz [Úvod do objektů DataRelation](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0k21zcyx(v=vs.120)).  
  
4. Nastavte následující vlastnosti. Můžou být nastavené v kódu nebo v návrháři.  
  
    |Vlastnost|Nastavení|  
    |--------------|-------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|Tabulka obsahující informace o tom, které číslo ID je ekvivalentní k této položce. V předchozím scénáři je to `ItemTable`.|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|Sloupec tabulky zdroje dat, který chcete zobrazit v ovládacím prvku. V předchozím scénáři se jedná o `"Name"` (pro nastavení v kódu použijte uvozovky).|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|Sloupec tabulky zdroje dat, který obsahuje uložené informace. V předchozím scénáři se jedná o `"ID"` (pro nastavení v kódu použijte uvozovky).|  
  
5. V proceduře zavolejte metodu <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> třídy <xref:System.Windows.Forms.ControlBindingsCollection>, abyste navázali vlastnost <xref:System.Windows.Forms.ListControl.SelectedValue%2A> ovládacího prvku na tabulku zaznamenávající vstup formuláře. Můžete to provést také v Návrháři místo v kódu, a to tak, že v okně **vlastnosti** přistupujete k vlastnosti <xref:System.Windows.Forms.Control.DataBindings%2A> ovládacího prvku. V předchozím scénáři je to `OrderDetailsTable`a sloupec je `"ItemID"`.  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Datové vazby a Windows Forms](../data-binding-and-windows-forms.md)
- [Přehled ovládacího prvku ListBox](listbox-control-overview-windows-forms.md)
- [Přehled ovládacího prvku ComboBox](combobox-control-overview-windows-forms.md)
- [Přehled ovládacího prvku CheckedListBox](checkedlistbox-control-overview-windows-forms.md)
- [Ovládací prvky Windows Forms používané k výpisu možností](windows-forms-controls-used-to-list-options.md)
