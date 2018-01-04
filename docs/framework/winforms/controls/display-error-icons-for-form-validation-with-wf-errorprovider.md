---
title: "Postupy: Zobrazení ikon chyby pro ověřování formuláře pomocí součásti Windows Forms ErrorProvider"
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
- cpp
helpviewer_keywords:
- errors [Windows Forms], displaying to users
- error icons
- ErrorProvider component [Windows Forms], displaying error icons
- error messages [Windows Forms], displaying icons
ms.assetid: 3b681a32-9db4-497b-a34b-34980eabee46
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 738ca9670635f78e8cb04318b192127184766c3c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a><span data-ttu-id="cffca-102">Postupy: Zobrazení ikon chyby pro ověřování formuláře pomocí součásti Windows Forms ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="cffca-102">How to: Display Error Icons for Form Validation with the Windows Forms ErrorProvider Component</span></span>
<span data-ttu-id="cffca-103">Můžete použít Windows Forms <xref:System.Windows.Forms.ErrorProvider> součást zobrazíte ikonu chyby, když uživatel zadá neplatná data.</span><span class="sxs-lookup"><span data-stu-id="cffca-103">You can use a Windows Forms <xref:System.Windows.Forms.ErrorProvider> component to display an error icon when the user enters invalid data.</span></span> <span data-ttu-id="cffca-104">Musí mít alespoň dva ovládací prvky na formuláři kartě mezi nimi a tím vyvolání ověřovacího kódu.</span><span class="sxs-lookup"><span data-stu-id="cffca-104">You must have at least two controls on the form in order to tab between them and thereby invoke the validation code.</span></span>  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a><span data-ttu-id="cffca-105">Zobrazit ikonu chyby při ovládacího prvku hodnota je neplatná.</span><span class="sxs-lookup"><span data-stu-id="cffca-105">To display an error icon when a control's value is invalid</span></span>  
  
1.  <span data-ttu-id="cffca-106">Přidání ovládacích prvků dvě – například textová pole – na formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="cffca-106">Add two controls — for example, text boxes — to a Windows Form.</span></span>  
  
2.  <span data-ttu-id="cffca-107">Přidat <xref:System.Windows.Forms.ErrorProvider> součásti pro formulář.</span><span class="sxs-lookup"><span data-stu-id="cffca-107">Add an <xref:System.Windows.Forms.ErrorProvider> component to the form.</span></span>  
  
3.  <span data-ttu-id="cffca-108">Vyberte první prvek a přidat kód pro jeho <xref:System.Windows.Forms.Control.Validating> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="cffca-108">Select the first control and add code to its <xref:System.Windows.Forms.Control.Validating> event handler.</span></span> <span data-ttu-id="cffca-109">Aby pro tento kód správně spouštět postup musí být připojen k události.</span><span class="sxs-lookup"><span data-stu-id="cffca-109">In order for this code to run properly, the procedure must be connected to the event.</span></span> <span data-ttu-id="cffca-110">Další informace najdete v tématu [postupy: vytváření obslužných rutin událostí spustit čas pro Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="cffca-110">For more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
     <span data-ttu-id="cffca-111">Následující kód testy platnosti dat, která uživatel zadal; Pokud je neplatná, data <xref:System.Windows.Forms.ErrorProvider.SetError%2A> metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="cffca-111">The following code tests the validity of the data the user has entered; if the data is invalid, the <xref:System.Windows.Forms.ErrorProvider.SetError%2A> method is called.</span></span> <span data-ttu-id="cffca-112">První argument funkce <xref:System.Windows.Forms.ErrorProvider.SetError%2A> metoda určuje, kterého ovládacího prvku na ikonu vedle položky zobrazení.</span><span class="sxs-lookup"><span data-stu-id="cffca-112">The first argument of the <xref:System.Windows.Forms.ErrorProvider.SetError%2A> method specifies which control to display the icon next to.</span></span> <span data-ttu-id="cffca-113">Druhý argument je zobrazený text chyby.</span><span class="sxs-lookup"><span data-stu-id="cffca-113">The second argument is the error text to display.</span></span>  
  
    ```vb  
    Private Sub TextBox1_Validating(ByVal Sender As Object, _  
       ByVal e As System.ComponentModel.CancelEventArgs) Handles _  
       TextBox1.Validating  
          If Not IsNumeric(TextBox1.Text) Then  
             ErrorProvider1.SetError(TextBox1, "Not a numeric value.")  
          Else  
             ' Clear the error.  
             ErrorProvider1.SetError(TextBox1, "")  
          End If  
    End Sub  
    ```  
  
    ```csharp  
    protected void textBox1_Validating (object sender,  
       System.ComponentModel.CancelEventArgs e)  
    {  
       try  
       {  
          int x = Int32.Parse(textBox1.Text);  
          errorProvider1.SetError(textBox1, "");  
       }  
       catch (Exception ex)  
       {  
          errorProvider1.SetError(textBox1, "Not an integer value.");  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void textBox1_Validating(System::Object ^  sender,  
          System::ComponentModel::CancelEventArgs ^  e)  
       {  
          try  
          {  
             int x = Int32::Parse(textBox1->Text);  
             errorProvider1->SetError(textBox1, "");  
          }  
          catch (System::Exception ^ ex)  
          {  
             errorProvider1->SetError(textBox1, "Not an integer value.");  
          }  
       }  
    ```  
  
     <span data-ttu-id="cffca-114">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="cffca-114">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4.  <span data-ttu-id="cffca-115">Spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="cffca-115">Run the project.</span></span> <span data-ttu-id="cffca-116">Zadejte (v tomto příkladu jiné než číselné) neplatná data do první prvek a potom karty druhou.</span><span class="sxs-lookup"><span data-stu-id="cffca-116">Type invalid (in this example, non-numeric) data into the first control, and then tab to the second.</span></span> <span data-ttu-id="cffca-117">Když se zobrazí ikona chyby, přejděte na to ukazatel myši zobrazíte text chyby.</span><span class="sxs-lookup"><span data-stu-id="cffca-117">When the error icon is displayed, point at it with the mouse pointer to see the error text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cffca-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="cffca-118">See Also</span></span>  
 <xref:System.Windows.Forms.ErrorProvider.SetError%2A>  
 [<span data-ttu-id="cffca-119">Přehled komponenty ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="cffca-119">ErrorProvider Component Overview</span></span>](../../../../docs/framework/winforms/controls/errorprovider-component-overview-windows-forms.md)  
 [<span data-ttu-id="cffca-120">Postupy: Zobrazování chyb v prvku DataSet pomocí komponenty Windows Forms ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="cffca-120">How to: View Errors Within a DataSet with the Windows Forms ErrorProvider Component</span></span>](../../../../docs/framework/winforms/controls/view-errors-within-a-dataset-with-wf-errorprovider-component.md)
