---
title: "Postupy: Zobrazování chyb v prvku DataSet pomocí součásti Windows Forms ErrorProvider"
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
- errors [Windows Forms], dataset errors
- error messages [Windows Forms], viewing in datasets
- ErrorProvider component [Windows Forms], dataset errors
ms.assetid: cbae023f-d651-4210-bdea-bcc5f037e321
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 28c90df258db8480f68eea05f922b36f30d81a3f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-view-errors-within-a-dataset-with-the-windows-forms-errorprovider-component"></a>Postupy: Zobrazování chyb v prvku DataSet pomocí součásti Windows Forms ErrorProvider
Můžete použít Windows Forms <xref:System.Windows.Forms.ErrorProvider> komponenty zobrazte sloupec chyby v rámci datové sady nebo jiné zdroje dat. Pro <xref:System.Windows.Forms.ErrorProvider> komponenty k zobrazení chyb dat ve formuláři, nemusí být přímo spojené s ovládacím prvkem. Jakmile je vázán na zdroj dat, můžete zobrazit ikonu chyby vedle libovolný ovládací prvek, který je vázaný na stejném datovém zdroji.  
  
> [!NOTE]
>  Pokud změníte chyba zprostředkovatele <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> a <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> vlastnosti v době běhu, měli byste použít <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> metoda, aby nedocházelo ke konfliktům.  
  
### <a name="to-display-data-errors"></a>K zobrazení chyb dat  
  
1.  Vytvoření vazby komponentu s konkrétní sloupec v tabulce data.  
  
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
  
2.  Nastavte <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> vlastnosti formuláře.  
  
    ```vb  
    ErrorProvider1.ContainerControl = Me  
    ```  
  
    ```csharp  
    errorProvider1.ContainerControl = this;  
    ```  
  
3.  Nastavte pozici na aktuální záznam na řádek, který obsahuje chybu sloupce.  
  
    ```vb  
    DataTable1.Rows(5).SetColumnError("Name", "Bad data in this row.")  
    Me.BindingContext(DataTable1).Position = 5  
    ```  
  
    ```csharp  
    DataTable1.Rows[5].SetColumnError("Name", "Bad data in this row.");  
    this.BindingContext [DataTable1].Position = 5;  
    ```  
  
## <a name="see-also"></a>Viz také  
 [ErrorProvider – přehled komponenty](../../../../docs/framework/winforms/controls/errorprovider-component-overview-windows-forms.md)  
 [Postupy: zobrazení ikon chyby pro ověřování formuláře pomocí ovládacího prvku Windows Forms ErrorProvider – komponenta](../../../../docs/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider.md)
