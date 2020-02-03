---
title: Zobrazit chybové ikony pro ověření formuláře pomocí součásti ErrorProvider
ms.date: 03/30/2017
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
ms.openlocfilehash: a1e346e332db489351f59c9a0c03ae731baf3dc3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745911"
---
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a><span data-ttu-id="6c14b-102">Postupy: Zobrazení ikon chyby pro ověřování formuláře pomocí součásti Windows Forms ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="6c14b-102">How to: Display Error Icons for Form Validation with the Windows Forms ErrorProvider Component</span></span>
<span data-ttu-id="6c14b-103">Komponentu model Windows Forms <xref:System.Windows.Forms.ErrorProvider> můžete použít k zobrazení chybové ikony, když uživatel zadá neplatná data.</span><span class="sxs-lookup"><span data-stu-id="6c14b-103">You can use a Windows Forms <xref:System.Windows.Forms.ErrorProvider> component to display an error icon when the user enters invalid data.</span></span> <span data-ttu-id="6c14b-104">Musíte mít alespoň dva ovládací prvky ve formuláři, aby bylo možné kartu mezi nimi a následně vyvolat ověřovací kód.</span><span class="sxs-lookup"><span data-stu-id="6c14b-104">You must have at least two controls on the form in order to tab between them and thereby invoke the validation code.</span></span>  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a><span data-ttu-id="6c14b-105">Zobrazení ikony chyby, pokud je hodnota ovládacího prvku neplatná</span><span class="sxs-lookup"><span data-stu-id="6c14b-105">To display an error icon when a control's value is invalid</span></span>  
  
1. <span data-ttu-id="6c14b-106">Přidejte dva ovládací prvky, například textová pole, do formuláře Windows.</span><span class="sxs-lookup"><span data-stu-id="6c14b-106">Add two controls — for example, text boxes — to a Windows Form.</span></span>  
  
2. <span data-ttu-id="6c14b-107">Přidejte do formuláře komponentu <xref:System.Windows.Forms.ErrorProvider>.</span><span class="sxs-lookup"><span data-stu-id="6c14b-107">Add an <xref:System.Windows.Forms.ErrorProvider> component to the form.</span></span>  
  
3. <span data-ttu-id="6c14b-108">Vyberte první ovládací prvek a přidejte kód do obslužné rutiny události <xref:System.Windows.Forms.Control.Validating>.</span><span class="sxs-lookup"><span data-stu-id="6c14b-108">Select the first control and add code to its <xref:System.Windows.Forms.Control.Validating> event handler.</span></span> <span data-ttu-id="6c14b-109">Aby tento kód běžel správně, musí být procedura připojena k události.</span><span class="sxs-lookup"><span data-stu-id="6c14b-109">In order for this code to run properly, the procedure must be connected to the event.</span></span> <span data-ttu-id="6c14b-110">Další informace naleznete v tématu [Postupy: vytváření obslužných rutin událostí v době běhu pro model Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6c14b-110">For more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
     <span data-ttu-id="6c14b-111">Následující kód testuje platnost dat, která uživatel zadal; Pokud jsou data neplatná, je volána metoda <xref:System.Windows.Forms.ErrorProvider.SetError%2A>.</span><span class="sxs-lookup"><span data-stu-id="6c14b-111">The following code tests the validity of the data the user has entered; if the data is invalid, the <xref:System.Windows.Forms.ErrorProvider.SetError%2A> method is called.</span></span> <span data-ttu-id="6c14b-112">První argument metody <xref:System.Windows.Forms.ErrorProvider.SetError%2A> určuje, který ovládací prvek má zobrazit ikonu vedle.</span><span class="sxs-lookup"><span data-stu-id="6c14b-112">The first argument of the <xref:System.Windows.Forms.ErrorProvider.SetError%2A> method specifies which control to display the icon next to.</span></span> <span data-ttu-id="6c14b-113">Druhý argument je chybový text, který se má zobrazit.</span><span class="sxs-lookup"><span data-stu-id="6c14b-113">The second argument is the error text to display.</span></span>  
  
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
  
     <span data-ttu-id="6c14b-114">(Vizuál C#, vizuál C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="6c14b-114">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4. <span data-ttu-id="6c14b-115">Spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="6c14b-115">Run the project.</span></span> <span data-ttu-id="6c14b-116">Typ je neplatný (v tomto příkladu nejsou číselná) data do prvního ovládacího prvku a potom na druhou.</span><span class="sxs-lookup"><span data-stu-id="6c14b-116">Type invalid (in this example, non-numeric) data into the first control, and then tab to the second.</span></span> <span data-ttu-id="6c14b-117">Když se zobrazí ikona chyby, najeďte na ni ukazatelem myši, aby se zobrazil text chyby.</span><span class="sxs-lookup"><span data-stu-id="6c14b-117">When the error icon is displayed, point at it with the mouse pointer to see the error text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c14b-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c14b-118">See also</span></span>

- <xref:System.Windows.Forms.ErrorProvider.SetError%2A>
- [<span data-ttu-id="6c14b-119">Přehled komponenty ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="6c14b-119">ErrorProvider Component Overview</span></span>](errorprovider-component-overview-windows-forms.md)
- [<span data-ttu-id="6c14b-120">Postupy: Zobrazování chyb v prvku DataSet pomocí komponenty Windows Forms ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="6c14b-120">How to: View Errors Within a DataSet with the Windows Forms ErrorProvider Component</span></span>](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
