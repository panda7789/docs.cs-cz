---
title: Vazba ovládacího prvku ComboBox nebo ListBox na data
description: Naučte se navazovat model Windows Forms pole se seznamem a seznamem na data, abyste mohli provádět úlohy, jako jsou data procházení v databázi, zadávat nová data nebo upravovat stávající data.
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
ms.openlocfilehash: 0c07dc90ddc91061c5f34b5a237082cb444e89d9
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324063"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a>Postupy: Vázání ovládacího prvku Windows Forms ComboBox nebo ListBox k datům
Můžete vytvořit propojení s <xref:System.Windows.Forms.ComboBox> <xref:System.Windows.Forms.ListBox> daty a provádět úkoly, jako je například procházení dat v databázi, zadávání nových dat nebo úprava stávajících dat.  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a>Svázání ovládacího prvku ComboBox nebo ListBox  
  
1. Nastavte `DataSource` vlastnost na objekt zdroje dat. Možné zdroje dat zahrnují <xref:System.Windows.Forms.BindingSource> vazbu na data, datovou tabulku, zobrazení dat, datovou sadu, Správce zobrazení dat, pole nebo libovolnou třídu, která implementuje <xref:System.Collections.IList> rozhraní. Další informace najdete v tématu [zdroje dat podporované nástrojem model Windows Forms](../data-sources-supported-by-windows-forms.md).  
  
2. Pokud vytváříte vazbu na tabulku, nastavte `DisplayMember` vlastnost na název sloupce ve zdroji dat.  
  
     \-ani  
  
     Pokud vytváříte vazbu na <xref:System.Collections.IList> , nastavte člena zobrazení na veřejnou vlastnost typu v seznamu.  
  
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
    > Pokud jste vázáni na zdroj dat, který neimplementuje rozhraní, jako je například <xref:System.ComponentModel.IBindingList> <xref:System.Collections.ArrayList> , data vázaného ovládacího prvku nebudou aktualizována při aktualizaci zdroje dat. Například pokud máte pole se seznamem svázané s <xref:System.Collections.ArrayList> a data jsou přidána do <xref:System.Collections.ArrayList> , tyto nové položky se nezobrazí v poli se seznamem. Můžete však vynutit aktualizaci pole se seznamem voláním <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> metod a na instanci <xref:System.Windows.Forms.BindingContext> třídy, ke které je ovládací prvek vázán.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Windows Forms – datová vazba](../windows-forms-data-binding.md)
- [Datové vazby a rozhraní Windows Forms](../data-binding-and-windows-forms.md)
- [Ovládací prvky Windows Forms používané k výpisu možností](windows-forms-controls-used-to-list-options.md)
