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
ms.openlocfilehash: b869898a20008343b6c6cbe4bc7e399fc86fb232
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054013"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a>Postupy: Vázání ovládacího prvku Windows Forms ComboBox nebo ListBox k datům
Můžete vytvořit vazbu <xref:System.Windows.Forms.ComboBox> a <xref:System.Windows.Forms.ListBox> k datům s cílem provést úlohy, jako je procházení dat v databázi, zadáním nových dat nebo úpravy existující data.  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a>K vytvoření vazby ovládacího prvku ComboBox nebo ListBox  
  
1. Nastavte `DataSource` vlastnost na objekt zdroje dat. Zdroje dat patří <xref:System.Windows.Forms.BindingSource> vázán na data, data tabulky, zobrazení dat, datové sady, data zobrazení, správce, pole nebo jakékoli třídy, která implementuje <xref:System.Collections.IList> rozhraní. Další informace najdete v tématu [zdroje dat podporované rozhraním Windows Forms](../data-sources-supported-by-windows-forms.md).  
  
2. Pokud vytváříte vazbu na tabulku, nastavte `DisplayMember` nastavte na název sloupce ve zdroji dat.  
  
     \- nebo –  
  
     Pokud se vazba na <xref:System.Collections.IList>, nastavte veřejnou vlastnost typu v seznamu zobrazit člena.  
  
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
    >  Pokud jsou vázány na zdroj dat, který neimplementuje <xref:System.ComponentModel.IBindingList> rozhraní, například <xref:System.Collections.ArrayList>, vázaného ovládacího prvku dat nebude aktualizovat, když dojde k aktualizaci zdroje dat. Například pokud máte pole se seznamem povinen <xref:System.Collections.ArrayList> a data je přidána do <xref:System.Collections.ArrayList>, tyto nové položky v poli se seznamem nezobrazí. Ale můžete vynutit pole se seznamem aktualizovat voláním <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> a <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> metody instance <xref:System.Windows.Forms.BindingContext> třídy pro ovládací prvek vázán.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Windows Forms – datová vazba](../windows-forms-data-binding.md)
- [Datové vazby a Windows Forms](../data-binding-and-windows-forms.md)
- [Ovládací prvky Windows Forms používané k výpisu možností](windows-forms-controls-used-to-list-options.md)
