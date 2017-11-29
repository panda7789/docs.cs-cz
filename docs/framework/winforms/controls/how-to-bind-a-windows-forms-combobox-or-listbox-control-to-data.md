---
title: "Postupy: Vázání ovládacího prvku Windows Forms ComboBox nebo ListBox k datům"
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6193e4cc86a470f046c220dc21150e0fc0bf792a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a>Postupy: Vázání ovládacího prvku Windows Forms ComboBox nebo ListBox k datům
Můžete vytvořit vazbu <xref:System.Windows.Forms.ComboBox> a <xref:System.Windows.Forms.ListBox> k datům a provádět úlohy, jako je například procházení dat v databázi, zadávání nová data nebo úpravou existující data.  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a>K vytvoření vazby ovládacího prvku ComboBox nebo ListBox  
  
1.  Nastavte `DataSource` vlastnost, která má objekt zdroje dat. Zdroje dat možné zahrnout <xref:System.Windows.Forms.BindingSource> vázána na data, data tabulky, zobrazení dat, datové sady, data zobrazení, správce, pole nebo jakákoli třída, která implementuje <xref:System.Collections.IList> rozhraní. Další informace najdete v tématu [datového zdroje podporované rozhraním Windows Forms](../../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md).  
  
2.  Pokud vytváříte vazbu do tabulky, nastavte `DisplayMember` vlastnost na název sloupce v datovém zdroji.  
  
     \-nebo –  
  
     Pokud vytváříte vazbu <xref:System.Collections.IList>, člen zobrazení nastavit na veřejné vlastnosti typu v seznamu.  
  
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
    >  Pokud jsou vázány na zdroj dat, který neimplementuje <xref:System.ComponentModel.IBindingList> rozhraní, například <xref:System.Collections.ArrayList>, nebude při aktualizaci zdroje dat aktualizovat data připojeného ovládacího prvku. Například pokud máte pole se seznamem se vázána na <xref:System.Collections.ArrayList> a data se přidá <xref:System.Collections.ArrayList>, tyto nové položky se nebude zobrazovat na pole se seznamem. Ale můžete vynutit pole se seznamem aktualizovat volání <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> a <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> metody na instanci systému <xref:System.Windows.Forms.BindingContext> třídy pro ovládací prvek vázán.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 [Windows Forms – datová vazba](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Datová vazba a systém Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [Windows Forms – ovládací prvky používané k výpisu možností](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
