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
ms.openlocfilehash: 190b53a248a77f03dd5d8cb13cb59a439fa9960d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157622"
---
# <a name="how-to-view-errors-within-a-dataset-with-the-windows-forms-errorprovider-component"></a><span data-ttu-id="687cb-102">Postupy: Zobrazování chyb v prvku DataSet pomocí komponenty Windows Forms ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="687cb-102">How to: View Errors Within a DataSet with the Windows Forms ErrorProvider Component</span></span>
<span data-ttu-id="687cb-103">Můžete použít Windows Forms <xref:System.Windows.Forms.ErrorProvider> komponenty, chcete-li zobrazit chyby sloupců v datové sadě nebo jiný zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="687cb-103">You can use the Windows Forms <xref:System.Windows.Forms.ErrorProvider> component to view column errors within a dataset or other data source.</span></span> <span data-ttu-id="687cb-104">Pro <xref:System.Windows.Forms.ErrorProvider> komponenty pro zobrazení dat chyby ve formuláři, nemusí být přímo spojené s ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="687cb-104">For an <xref:System.Windows.Forms.ErrorProvider> component to display data errors on a form, it does not have to be directly associated with a control.</span></span> <span data-ttu-id="687cb-105">Jakmile je vázán na zdroj dat, může zobrazit ikona chyby vedle libovolný ovládací prvek, který je vázán ke stejnému zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="687cb-105">Once it is bound to a data source, it can display an error icon next to any control that is bound to the same data source.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="687cb-106">Pokud změníte chyba zprostředkovatele <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> a <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> vlastnosti v době běhu, měli byste použít <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> metody, aby nedocházelo ke konfliktům.</span><span class="sxs-lookup"><span data-stu-id="687cb-106">If you change the error provider's <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> and <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> properties at run time, you should use the <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> method to avoid conflicts.</span></span>  
  
### <a name="to-display-data-errors"></a><span data-ttu-id="687cb-107">Chcete-li zobrazit data chyby</span><span class="sxs-lookup"><span data-stu-id="687cb-107">To display data errors</span></span>  
  
1.  <span data-ttu-id="687cb-108">Vytvořit vazbu komponentu v určitém sloupci v tabulce data.</span><span class="sxs-lookup"><span data-stu-id="687cb-108">Bind the component to a specific column within a data table.</span></span>  
  
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
  
2.  <span data-ttu-id="687cb-109">Nastavte <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> vlastnost do formuláře.</span><span class="sxs-lookup"><span data-stu-id="687cb-109">Set the <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> property to the form.</span></span>  
  
    ```vb  
    ErrorProvider1.ContainerControl = Me  
    ```  
  
    ```csharp  
    errorProvider1.ContainerControl = this;  
    ```  
  
3.  <span data-ttu-id="687cb-110">Nastavíte pozici aktuální záznam na řádek obsahující chybu sloupce.</span><span class="sxs-lookup"><span data-stu-id="687cb-110">Set the position of the current record to a row that contains a column error.</span></span>  
  
    ```vb  
    DataTable1.Rows(5).SetColumnError("Name", "Bad data in this row.")  
    Me.BindingContext(DataTable1).Position = 5  
    ```  
  
    ```csharp  
    DataTable1.Rows[5].SetColumnError("Name", "Bad data in this row.");  
    this.BindingContext [DataTable1].Position = 5;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="687cb-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="687cb-111">See also</span></span>

- [<span data-ttu-id="687cb-112">Přehled komponenty ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="687cb-112">ErrorProvider Component Overview</span></span>](errorprovider-component-overview-windows-forms.md)
- [<span data-ttu-id="687cb-113">Postupy: Zobrazení ikon chyby pro ověřování formuláře pomocí komponenty Windows Forms ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="687cb-113">How to: Display Error Icons for Form Validation with the Windows Forms ErrorProvider Component</span></span>](display-error-icons-for-form-validation-with-wf-errorprovider.md)
