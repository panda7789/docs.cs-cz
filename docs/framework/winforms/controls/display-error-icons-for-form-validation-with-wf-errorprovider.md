---
title: 'Postupy: Zobrazení ikon chyby pro ověřování formuláře pomocí komponenty Windows Forms ErrorProvider'
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
ms.openlocfilehash: 9487d4f82878ffefe17c576b16f654293ef01106
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59316502"
---
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a>Postupy: Zobrazení ikon chyby pro ověřování formuláře pomocí komponenty Windows Forms ErrorProvider
Můžete použít Windows Forms <xref:System.Windows.Forms.ErrorProvider> komponenty mají zobrazovat ikona chyby, když uživatel zadá neplatná data. Musí mít aspoň dva ovládací prvky ve formuláři, aby bylo možné kartě mezi nimi a tím vyvolat kód pro ověření.  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a>Chcete-li zobrazit ikona chyby při hodnota ovládacího prvku není platná.  
  
1. Přidejte dva ovládací prvky – například textová pole, do formuláře Windows.  
  
2. Přidat <xref:System.Windows.Forms.ErrorProvider> komponentu do formuláře.  
  
3. Vyberte první ovládací prvek a přidat kód pro jeho <xref:System.Windows.Forms.Control.Validating> obslužné rutiny události. Aby tento kód, aby běžel bez problémů procedura musí být připojen k události. Další informace najdete v tématu [jak: Vytváření obslužných rutin událostí pro Windows Forms v době běhu](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
     Následující kód ověřuje platnost sady dat, která uživatel zadal; Pokud jsou data neplatná, <xref:System.Windows.Forms.ErrorProvider.SetError%2A> metoda je volána. Prvním argumentem funkce <xref:System.Windows.Forms.ErrorProvider.SetError%2A> metody Určuje, který ovládací prvek zobrazuje ikona vedle položky. Druhý argument je zobrazený text chyby.  
  
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
  
     (Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4. Spusťte projekt. Zadejte (v tomto příkladu nečíselné) neplatná data na první ovládací prvek a potom karty na druhou. Pokud se zobrazuje ikona chyby, přejděte na něj s ukazatelem myši zobrazíte text chyby.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ErrorProvider.SetError%2A>
- [Přehled komponenty ErrorProvider](errorprovider-component-overview-windows-forms.md)
- [Postupy: Zobrazování chyb v prvku DataSet pomocí komponenty Windows Forms ErrorProvider](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
