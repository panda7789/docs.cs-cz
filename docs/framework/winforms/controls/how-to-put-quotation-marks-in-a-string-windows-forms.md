---
title: 'Postupy: Vkládání uvozovek do řetězce (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- quotation marks
- TextBox control [Windows Forms], displaying quotation marks
- quotation marks [Windows Forms], adding to strings in text boxes
ms.assetid: 68bdc3f3-4177-4eab-99cd-cac17a82b515
ms.openlocfilehash: 7fcc2e8692880f1e5c2b8df807cf7943a5575c56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a>Postupy: Vkládání uvozovek do řetězce (Windows Forms)
V některých případech můžete chtít umístit uvozovky ("") v textového řetězce. Příklad:  
  
 Jana uvedená "Jste si zaslouží zpracovávat!"  
  
 Alternativně můžete také použít <xref:Microsoft.VisualBasic.ControlChars.Quote> pole jako konstanta.  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a>Umístit uvozovek do řetězce v kódu  
  
1.  V jazyce Visual Basic vložte dva znaky uvozovek za sebou jako embedded znak uvozovek. V jazyce Visual C# a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], vložte řídicí sekvence \\"jako embedded znak uvozovek. Například pokud chcete vytvořit předchozí řetězec, použijte následující kód.  
  
    ```vb  
    Private Sub InsertQuote()  
       TextBox1.Text = "She said, ""You deserve a treat!"" "  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertQuote(){  
       textBox1.Text = "She said, \"You deserve a treat!\" ";  
    }  
    ```  
  
    ```cpp  
    private:  
       void InsertQuote()  
       {  
          textBox1->Text = "She said, \"You deserve a treat!\" ";  
       }  
    ```  
  
     -nebo-  
  
2.  Vložte znak ASCII nebo Unicode pro uvozovky. V jazyce Visual Basic použijte znaků ASCII (34). V jazyce Visual C#, použijte znak Unicode (\u0022).  
  
    ```vb  
    Private Sub InsertAscii()  
       TextBox1.Text = "She said, " & Chr(34) & "You deserve a treat!" & Chr(34)  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertAscii(){  
       textBox1.Text = "She said, " + '\u0022' + "You deserve a treat!" + '\u0022';  
    }  
    ```  
  
    > [!NOTE]
    >  V tomto příkladu nemůžete použít \u0022, protože nelze použít název universal znak, který označuje znak v základní znakovou sadu. Jinak vytvořit C3851. Další informace najdete v tématu [C3851 Chyba kompilátoru](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).  
  
     -nebo-  
  
3.  Můžete také definovat konstanta znaku a použít ho tam, kde je potřeba.  
  
    ```vb  
    Const quote As String = """"  
    TextBox1.Text = "She said, " & quote & "You deserve a treat!" & quote  
    ```  
  
    ```csharp  
    const string quote = "\"";  
    textBox1.Text = "She said, " + quote +  "You deserve a treat!"+ quote ;  
    ```  
  
    ```cpp  
    const String^ quote = "\"";  
    textBox1->Text = String::Concat("She said, ",  
       const_cast<String^>(quote), "You deserve a treat!",  
       const_cast<String^>(quote));  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.TextBox>  
 <xref:Microsoft.VisualBasic.ControlChars.Quote>  
 [Přehled ovládacího prvku TextBox](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [Postupy: Vytvoření textového pole určeného jen pro čtení](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [Ovládací prvek TextBox](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
