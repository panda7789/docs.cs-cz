---
title: 'Postupy: Zobrazování chyb v prvku DataSet pomocí komponenty Windows Forms ErrorProvider'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- errors [Windows Forms], dataset errors
- error messages [Windows Forms], viewing in datasets
- ErrorProvider component [Windows Forms], dataset errors
ms.assetid: cbae023f-d651-4210-bdea-bcc5f037e321
ms.openlocfilehash: 48f333fbae816748813b370bccc559cea2714fa5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694045"
---
# <a name="how-to-view-errors-within-a-dataset-with-the-windows-forms-errorprovider-component"></a>Postupy: Zobrazování chyb v prvku DataSet pomocí komponenty Windows Forms ErrorProvider
Můžete použít Windows Forms <xref:System.Windows.Forms.ErrorProvider> komponenty, chcete-li zobrazit chyby sloupců v datové sadě nebo jiný zdroj dat. Pro <xref:System.Windows.Forms.ErrorProvider> komponenty pro zobrazení dat chyby ve formuláři, nemusí být přímo spojené s ovládacím prvkem. Jakmile je vázán na zdroj dat, může zobrazit ikona chyby vedle libovolný ovládací prvek, který je vázán ke stejnému zdroji dat.  
  
> [!NOTE]
>  Pokud změníte chyba zprostředkovatele <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> a <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> vlastnosti v době běhu, měli byste použít <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> metody, aby nedocházelo ke konfliktům.  
  
### <a name="to-display-data-errors"></a>Chcete-li zobrazit data chyby  
  
1.  Vytvořit vazbu komponentu v určitém sloupci v tabulce data.  
  
    ```vb  
    ' Assumes existence of DataSet1, DataTable1  
    TextBox1.DataBindings.Add("Text", DataSet1, "Customers.Name")  
    ErrorProvider1.DataSource = DataSet1  
    ErrorProvider1.DataMember = "Customers"  
    ```  
  
    ```csharp  
    // Assumes existence of DataSet1, DataTable1  
    textBox1.DataBindings.Add("Text", DataSet1, "Customers.Name");  
    errorProvider1.DataSource = DataSet1;  
    errorProvider1.DataMember = "Customers";  
    ```  
  
2.  Nastavte <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> vlastnost do formuláře.  
  
    ```vb  
    ErrorProvider1.ContainerControl = Me  
    ```  
  
    ```csharp  
    errorProvider1.ContainerControl = this;  
    ```  
  
3.  Nastavíte pozici aktuální záznam na řádek obsahující chybu sloupce.  
  
    ```vb  
    DataTable1.Rows(5).SetColumnError("Name", "Bad data in this row.")  
    Me.BindingContext(DataTable1).Position = 5  
    ```  
  
    ```csharp  
    DataTable1.Rows[5].SetColumnError("Name", "Bad data in this row.");  
    this.BindingContext [DataTable1].Position = 5;  
    ```  
  
## <a name="see-also"></a>Viz také:
- [Přehled komponenty ErrorProvider](../../../../docs/framework/winforms/controls/errorprovider-component-overview-windows-forms.md)
- [Postupy: Zobrazení ikon chyb pro ověřování formuláře pomocí součásti Windows Forms ErrorProvider](../../../../docs/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider.md)
