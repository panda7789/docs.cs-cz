---
title: 'Postupy: Zobrazení seznamu písem pomocí součásti FontDialog'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- fonts [Windows Forms], showing list
- FontDialog component [Windows Forms]
- fonts [Windows Forms], attributes
- Font property [Windows Forms], setting with FontDialog component
- Font dialog box [Windows Forms], displaying
- fonts [Windows Forms], selecting
ms.assetid: 35692c1b-0937-4b7a-9207-1ae6bdc244a0
ms.openlocfilehash: fe291df1648da5002ce3173a68208bbad659705d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-show-a-font-list-with-the-fontdialog-component"></a>Postupy: Zobrazení seznamu písem pomocí součásti FontDialog
[FontDialog](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md) součást umožňuje uživatelům vybrat písmo, jakož i změnit jeho vlastnosti zobrazení, jako je například váhy a jeho velikost.  
  
 Písma vybraného v dialogovém okně je vrácený v <xref:System.Windows.Forms.FontDialog.Font%2A> vlastnost. Proto je využívat výhod písmo vybraný uživatelem stejně snadná jako vlastnost pro čtení.  
  
### <a name="to-select-font-properties-using-the-fontdialog-component"></a>Chcete-li vybrat vlastnosti písem pomocí součásti FontDialog  
  
1.  Zobrazí dialogové okno pole pomocí <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metoda.  
  
2.  Použití <xref:System.Windows.Forms.DialogResult> vlastnosti k určení, jak bylo ukončeno dialogové okno.  
  
3.  Použití <xref:System.Windows.Forms.FontDialog.Font%2A> vlastnost nastavující požadované písmo.  
  
     V následujícím příkladu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Click> otevře obslužné rutiny události <xref:System.Windows.Forms.FontDialog> součásti. Pokud je písmo zvolený a uživatel klikne na tlačítko **OK**, <xref:System.Windows.Forms.FontDialog.Font%2A> vlastnost <xref:System.Windows.Forms.TextBox> ovládací prvek, který je ve formuláři je nastavena na zvolené písmo. Příklad předpokládá, že má formulář <xref:System.Windows.Forms.Button> řízení, <xref:System.Windows.Forms.TextBox> řízení a <xref:System.Windows.Forms.FontDialog> součásti.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       If FontDialog1.ShowDialog() = DialogResult.OK Then  
          TextBox1.Font = FontDialog1.Font  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(fontDialog1.ShowDialog() == DialogResult.OK)  
       {  
          textBox1.Font = fontDialog1.Font;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if(fontDialog1->ShowDialog() == DialogResult::OK)  
          {  
             textBox1->Font = fontDialog1->Font;  
          }  
       }  
    ```  
  
     (Visual C# a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.FontDialog>  
 [Komponenta FontDialog](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md)
