---
title: 'Postupy: Vázání ovládacího prvku Windows Forms ComboBox nebo ListBox k datům'
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
ms.openlocfilehash: f361526c44f8fbb9ab282fe15ae109b67e8f01dd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922745"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a>Postupy: Vázání ovládacího prvku Windows Forms ComboBox nebo ListBox k datům
Můžete vytvořit <xref:System.Windows.Forms.ComboBox> propojení s daty <xref:System.Windows.Forms.ListBox> a provádět úkoly, jako je například procházení dat v databázi, zadávání nových dat nebo úprava stávajících dat.  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a>Svázání ovládacího prvku ComboBox nebo ListBox  
  
1. `DataSource` Nastavte vlastnost na objekt zdroje dat. Možné zdroje dat zahrnují <xref:System.Windows.Forms.BindingSource> vazbu na data, datovou tabulku, zobrazení dat, datovou sadu, Správce zobrazení dat, pole nebo libovolnou třídu, která <xref:System.Collections.IList> implementuje rozhraní. Další informace najdete v tématu [zdroje dat podporované nástrojem model Windows Forms](../data-sources-supported-by-windows-forms.md).  
  
2. Pokud vytváříte vazbu na tabulku, nastavte `DisplayMember` vlastnost na název sloupce ve zdroji dat.  
  
     \- nebo –  
  
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
    > Pokud jste vázáni na zdroj dat, který neimplementuje <xref:System.ComponentModel.IBindingList> rozhraní, <xref:System.Collections.ArrayList>jako je například, data vázaného ovládacího prvku nebudou aktualizována při aktualizaci zdroje dat. Například pokud máte pole se seznamem svázané <xref:System.Collections.ArrayList> s a data jsou přidána <xref:System.Collections.ArrayList>do, tyto nové položky se nezobrazí v poli se seznamem. Můžete však vynutit aktualizaci pole se seznamem voláním <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> metod a <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> <xref:System.Windows.Forms.BindingContext> na instanci třídy, ke které je ovládací prvek vázán.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Windows Forms – datová vazba](../windows-forms-data-binding.md)
- [Datové vazby a Windows Forms](../data-binding-and-windows-forms.md)
- [Ovládací prvky Windows Forms používané k výpisu možností](windows-forms-controls-used-to-list-options.md)
