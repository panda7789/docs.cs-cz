---
title: Vazba ovládacího prvku ComboBox nebo ListBox na data
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], binding to controls
- list boxes [Windows Forms], data binding
- ComboBox control [Windows Forms], data binding
- data binding [Windows Forms], combo boxes
- ListBox control [Windows Forms], data binding
- combo boxes [Windows Forms], data binding
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- data-bound controls [Windows Forms], Windows Forms
ms.assetid: dfd7f081-8bea-4a41-86a3-86a1934828ef
ms.openlocfilehash: 99d9b53b32d6faae888b134d4ed486980c05a75b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742031"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a>Postupy: Vázání ovládacího prvku Windows Forms ComboBox nebo ListBox k datům
Můžete navazovat <xref:System.Windows.Forms.ComboBox> a <xref:System.Windows.Forms.ListBox> na data, abyste mohli provádět úlohy, jako je například procházení dat v databázi, zadávání nových dat nebo úprava stávajících dat.  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a>Svázání ovládacího prvku ComboBox nebo ListBox  
  
1. Vlastnost `DataSource` nastavte na objekt zdroje dat. Možné zdroje dat zahrnují <xref:System.Windows.Forms.BindingSource> vázaný na data, datovou tabulku, zobrazení dat, datovou sadu, Správce zobrazení dat, pole nebo libovolnou třídu, která implementuje rozhraní <xref:System.Collections.IList>. Další informace najdete v tématu [zdroje dat podporované nástrojem model Windows Forms](../data-sources-supported-by-windows-forms.md).  
  
2. Pokud vytváříte vazbu na tabulku, nastavte vlastnost `DisplayMember` na název sloupce ve zdroji dat.  
  
     \- nebo-  
  
     Pokud vytváříte vazbu na <xref:System.Collections.IList>, nastavte člena zobrazení na veřejnou vlastnost typu v seznamu.  
  
    ```vb  
    Private Sub BindComboBox()  
      ComboBox1.DataSource = DataSet1.Tables("Suppliers")  
      ComboBox1.DisplayMember = "ProductName"  
    End Sub  
    ```  
  
    ```csharp  
    private void BindComboBox()  
    {  
      comboBox1.DataSource = dataSet1.Tables["Suppliers"];  
      comboBox1.DisplayMember = "ProductName";  
    }  
    ```  
  
    > [!NOTE]
    > Pokud jste vázáni na zdroj dat, který neimplementuje rozhraní <xref:System.ComponentModel.IBindingList>, například <xref:System.Collections.ArrayList>, data vázaného ovládacího prvku nebudou aktualizována při aktualizaci zdroje dat. Například pokud máte pole se seznamem vázané na <xref:System.Collections.ArrayList> a data jsou přidána do <xref:System.Collections.ArrayList>, tyto nové položky se nezobrazí v poli se seznamem. Můžete však vynutit aktualizaci pole se seznamem voláním <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> a <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A>ch metod na instanci třídy <xref:System.Windows.Forms.BindingContext>, ke které je ovládací prvek vázán.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Windows Forms – datová vazba](../windows-forms-data-binding.md)
- [Datové vazby a Windows Forms](../data-binding-and-windows-forms.md)
- [Ovládací prvky Windows Forms používané k výpisu možností](windows-forms-controls-used-to-list-options.md)
