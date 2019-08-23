---
title: 'Postupy: Vložení uvozovek do řetězce (model Windows Forms)'
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
ms.openlocfilehash: 20828f75eeae9df33fcc22d8558b26a8a1ab2bdc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910422"
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a>Postupy: Vložení uvozovek do řetězce (model Windows Forms)
Někdy je vhodné umístit uvozovky ("") do textového řetězce. Příklad:  
  
 Uvedli jsme, že poslouží jako "považovat za".  
  
 Jako alternativu můžete také použít <xref:Microsoft.VisualBasic.ControlChars.Quote> pole jako konstantu.  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a>Vložení uvozovek do řetězce v kódu  
  
1. V Visual Basic vložte do řádku dvě uvozovky jako vložený znak uvozovek. V vizuálu C# a vizuálu C++vložte řídicí sekvenci \\jako vloženou uvozovku. Chcete-li například vytvořit předchozí řetězec, použijte následující kód.  
  
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
  
2. Vložte znak ASCII nebo Unicode pro uvozovky. V Visual Basic použijte znak ASCII (34). V vizuálu C#použijte znak Unicode (\u0022).  
  
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
    > V tomto příkladu nelze použít \u0022, protože nemůžete použít univerzální název znaku, který určuje znak v základní znakové sadě. V opačném případě budete mít C3851. Další informace najdete v tématu [Chyba kompilátoru C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).  
  
     -nebo-  
  
3. Můžete také definovat konstantu pro znak a použít ho tam, kde je to potřeba.  
  
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
- [Postupy: Řízení místa vložení v ovládacím prvku TextBox model Windows Forms](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Postupy: Textové pole pro vytvoření hesla pomocí ovládacího prvku model Windows Forms TextBox](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Postupy: Vytvoření textového pole určeného jen pro čtení](how-to-create-a-read-only-text-box-windows-forms.md)
- [Postupy: Výběr textu v ovládacím prvku model Windows Forms TextBox](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Postupy: Zobrazit více řádků v ovládacím prvku model Windows Forms TextBox](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [Ovládací prvek TextBox](textbox-control-windows-forms.md)
