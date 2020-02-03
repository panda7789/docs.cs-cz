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
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a>Postupy: Zobrazení ikon chyby pro ověřování formuláře pomocí součásti Windows Forms ErrorProvider
Komponentu model Windows Forms <xref:System.Windows.Forms.ErrorProvider> můžete použít k zobrazení chybové ikony, když uživatel zadá neplatná data. Musíte mít alespoň dva ovládací prvky ve formuláři, aby bylo možné kartu mezi nimi a následně vyvolat ověřovací kód.  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a>Zobrazení ikony chyby, pokud je hodnota ovládacího prvku neplatná  
  
1. Přidejte dva ovládací prvky, například textová pole, do formuláře Windows.  
  
2. Přidejte do formuláře komponentu <xref:System.Windows.Forms.ErrorProvider>.  
  
3. Vyberte první ovládací prvek a přidejte kód do obslužné rutiny události <xref:System.Windows.Forms.Control.Validating>. Aby tento kód běžel správně, musí být procedura připojena k události. Další informace naleznete v tématu [Postupy: vytváření obslužných rutin událostí v době běhu pro model Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
     Následující kód testuje platnost dat, která uživatel zadal; Pokud jsou data neplatná, je volána metoda <xref:System.Windows.Forms.ErrorProvider.SetError%2A>. První argument metody <xref:System.Windows.Forms.ErrorProvider.SetError%2A> určuje, který ovládací prvek má zobrazit ikonu vedle. Druhý argument je chybový text, který se má zobrazit.  
  
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
  
     (Vizuál C#, vizuál C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4. Spusťte projekt. Typ je neplatný (v tomto příkladu nejsou číselná) data do prvního ovládacího prvku a potom na druhou. Když se zobrazí ikona chyby, najeďte na ni ukazatelem myši, aby se zobrazil text chyby.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ErrorProvider.SetError%2A>
- [Přehled komponenty ErrorProvider](errorprovider-component-overview-windows-forms.md)
- [Postupy: Zobrazování chyb v prvku DataSet pomocí komponenty Windows Forms ErrorProvider](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
