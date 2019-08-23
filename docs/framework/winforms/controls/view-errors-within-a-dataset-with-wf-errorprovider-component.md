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
ms.openlocfilehash: 3dbd2ccca607869a6f28bc5b3bd1c9f0769db9f5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950085"
---
# <a name="how-to-view-errors-within-a-dataset-with-the-windows-forms-errorprovider-component"></a>Postupy: Zobrazování chyb v prvku DataSet pomocí komponenty Windows Forms ErrorProvider
Komponentu model Windows Forms <xref:System.Windows.Forms.ErrorProvider> lze použít k zobrazení chyb ve sloupcích v rámci datové sady nebo jiného zdroje dat. <xref:System.Windows.Forms.ErrorProvider> Aby součást zobrazovala chyby dat ve formuláři, nemusí být přímo přidružena k ovládacímu prvku. Jakmile je svázán se zdrojem dat, může zobrazit ikonu chyby vedle libovolného ovládacího prvku vázaného na stejný zdroj dat.  
  
> [!NOTE]
> Pokud změníte poskytovatele <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> chyb a <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> vlastnosti za běhu <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> , měli byste použít metodu, aby nedocházelo ke konfliktům.  
  
### <a name="to-display-data-errors"></a>Zobrazení chyb dat  
  
1. Navažte komponentu na konkrétní sloupec v tabulce dat.  
  
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
  
2. <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> Nastavte vlastnost na formu.  
  
    ```vb  
    ErrorProvider1.ContainerControl = Me  
    ```  
  
    ```csharp  
    errorProvider1.ContainerControl = this;  
    ```  
  
3. Nastaví pozici aktuálního záznamu na řádek, který obsahuje chybu sloupce.  
  
    ```vb  
    DataTable1.Rows(5).SetColumnError("Name", "Bad data in this row.")  
    Me.BindingContext(DataTable1).Position = 5  
    ```  
  
    ```csharp  
    DataTable1.Rows[5].SetColumnError("Name", "Bad data in this row.");  
    this.BindingContext [DataTable1].Position = 5;  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Přehled komponenty ErrorProvider](errorprovider-component-overview-windows-forms.md)
- [Postupy: Zobrazit chybové ikony pro ověření formuláře pomocí součásti model Windows Forms ErrorProvider](display-error-icons-for-form-validation-with-wf-errorprovider.md)
