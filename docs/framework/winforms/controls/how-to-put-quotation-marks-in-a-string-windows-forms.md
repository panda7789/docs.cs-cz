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
ms.openlocfilehash: 14180f0326b38872f5d1b112c3d9a87022fb79e9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59328059"
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a>Postupy: Vkládání uvozovek do řetězce (Windows Forms)
Někdy můžete chtít umístit uvozovky ("") v textovém řetězci. Příklad:  
  
 Marcela řekl: "Jste, které jsou považovat!"  
  
 Jako alternativu můžete použít také <xref:Microsoft.VisualBasic.ControlChars.Quote> pole jako konstanta.  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a>Umístit uvozovek do řetězce v kódu  
  
1. V jazyce Visual Basic vložte dva uvozovek za sebou jako vložený znak uvozovek. Ve Vizuálu C# a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], vložit řídicí sekvence \\"jako vložený znak uvozovek. Například pro vytvoření předchozí řetězce, použijte následující kód.  
  
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
  
2. Vložte znak ASCII nebo Unicode pro znak uvozovek. V jazyce Visual Basic použijte znak ASCII (34). Ve Vizuálu C#, použijte znak Unicode (\u0022).  
  
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
    >  V tomto příkladu nemůžete použít \u0022, protože nelze použít univerzální název znaku, který určuje znak v základní znakové sadě. V opačném případě můžete vytvářet C3851. Další informace najdete v tématu [Chyba kompilátoru C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).  
  
     -nebo-  
  
3. Můžete také Definujte konstantu znaku a použít ho místech.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.TextBox>
- <xref:Microsoft.VisualBasic.ControlChars.Quote>
- [Přehled ovládacího prvku TextBox](textbox-control-overview-windows-forms.md)
- [Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Postupy: Vytvoření pole jen pro čtení textu](how-to-create-a-read-only-text-box-windows-forms.md)
- [Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Postupy: Zobrazit více řádků v ovládacím prvku Windows Forms TextBox](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [Ovládací prvek TextBox](textbox-control-windows-forms.md)
