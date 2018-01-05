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
ms.workload: dotnet
ms.openlocfilehash: 27ef4200996108e378273c5f813106d4f82dacd8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-view-errors-within-a-dataset-with-the-windows-forms-errorprovider-component"></a><span data-ttu-id="ae1ac-102">Postupy: Zobrazování chyb v prvku DataSet pomocí součásti Windows Forms ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="ae1ac-102">How to: View Errors Within a DataSet with the Windows Forms ErrorProvider Component</span></span>
<span data-ttu-id="ae1ac-103">Můžete použít Windows Forms <xref:System.Windows.Forms.ErrorProvider> komponenty zobrazte sloupec chyby v rámci datové sady nebo jiné zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-103">You can use the Windows Forms <xref:System.Windows.Forms.ErrorProvider> component to view column errors within a dataset or other data source.</span></span> <span data-ttu-id="ae1ac-104">Pro <xref:System.Windows.Forms.ErrorProvider> komponenty k zobrazení chyb dat ve formuláři, nemusí být přímo spojené s ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-104">For an <xref:System.Windows.Forms.ErrorProvider> component to display data errors on a form, it does not have to be directly associated with a control.</span></span> <span data-ttu-id="ae1ac-105">Jakmile je vázán na zdroj dat, můžete zobrazit ikonu chyby vedle libovolný ovládací prvek, který je vázaný na stejném datovém zdroji.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-105">Once it is bound to a data source, it can display an error icon next to any control that is bound to the same data source.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae1ac-106">Pokud změníte chyba zprostředkovatele <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> a <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> vlastnosti v době běhu, měli byste použít <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> metoda, aby nedocházelo ke konfliktům.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-106">If you change the error provider's <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> and <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> properties at run time, you should use the <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> method to avoid conflicts.</span></span>  
  
### <a name="to-display-data-errors"></a><span data-ttu-id="ae1ac-107">K zobrazení chyb dat</span><span class="sxs-lookup"><span data-stu-id="ae1ac-107">To display data errors</span></span>  
  
1.  <span data-ttu-id="ae1ac-108">Vytvoření vazby komponentu s konkrétní sloupec v tabulce data.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-108">Bind the component to a specific column within a data table.</span></span>  
  
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
  
2.  <span data-ttu-id="ae1ac-109">Nastavte <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> vlastnosti formuláře.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-109">Set the <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> property to the form.</span></span>  
  
    ```vb  
    ErrorProvider1.ContainerControl = Me  
    ```  
  
    ```csharp  
    errorProvider1.ContainerControl = this;  
    ```  
  
3.  <span data-ttu-id="ae1ac-110">Nastavte pozici na aktuální záznam na řádek, který obsahuje chybu sloupce.</span><span class="sxs-lookup"><span data-stu-id="ae1ac-110">Set the position of the current record to a row that contains a column error.</span></span>  
  
    ```vb  
    DataTable1.Rows(5).SetColumnError("Name", "Bad data in this row.")  
    Me.BindingContext(DataTable1).Position = 5  
    ```  
  
    ```csharp  
    DataTable1.Rows[5].SetColumnError("Name", "Bad data in this row.");  
    this.BindingContext [DataTable1].Position = 5;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ae1ac-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae1ac-111">See Also</span></span>  
 [<span data-ttu-id="ae1ac-112">Přehled komponenty ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="ae1ac-112">ErrorProvider Component Overview</span></span>](../../../../docs/framework/winforms/controls/errorprovider-component-overview-windows-forms.md)  
 [<span data-ttu-id="ae1ac-113">Postupy: Zobrazení ikon chyb pro ověřování formuláře pomocí komponenty Windows Forms ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="ae1ac-113">How to: Display Error Icons for Form Validation with the Windows Forms ErrorProvider Component</span></span>](../../../../docs/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider.md)
