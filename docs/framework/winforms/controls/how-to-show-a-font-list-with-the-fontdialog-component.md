---
title: 'Postupy: Zobrazení seznamu písem pomocí komponenty FontDialog'
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
ms.openlocfilehash: 05e9b5e1280d0318354b0d47f4d78f7ec1c5f4e7
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053452"
---
# <a name="how-to-show-a-font-list-with-the-fontdialog-component"></a>Postupy: Zobrazení seznamu písem pomocí komponenty FontDialog
[FontDialog](fontdialog-component-windows-forms.md) komponenta umožňuje uživatelům vybrat písmo, jakož i jeho zobrazení aspekty, jako je například váha a jeho velikost změnit.  
  
 Písmo vybrané v dialogovém okně se vrátí v <xref:System.Windows.Forms.FontDialog.Font%2A> vlastnost. Využití výhod písmo vybrané uživatelem. je proto stejně snadné jako vlastnost pro čtení.  
  
### <a name="to-select-font-properties-using-the-fontdialog-component"></a>Chcete-li vybrat vlastnosti písem pomocí komponenty FontDialog  
  
1. Zobrazit dialog box pomocí <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody.  
  
2. Použití <xref:System.Windows.Forms.DialogResult> a určí, jak bylo ukončeno dialogových oken.  
  
3. Použití <xref:System.Windows.Forms.FontDialog.Font%2A> vlastnosti chcete nastavit požadované písmo.  
  
     V následujícím příkladu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Click> otevře obslužné rutiny události <xref:System.Windows.Forms.FontDialog> komponenty. Pokud je písmo zvolené a uživatel klikne na tlačítko **OK**, <xref:System.Windows.Forms.FontDialog.Font%2A> vlastnost <xref:System.Windows.Forms.TextBox> ovládací prvek, který je ve formuláři je nastavena na zvolené písmo. Příklad předpokládá, že váš formulář má <xref:System.Windows.Forms.Button> ovládací prvek, <xref:System.Windows.Forms.TextBox> ovládacího prvku a <xref:System.Windows.Forms.FontDialog> komponenty.  
  
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
  
     (Visual C# a vizuální C++) Umístěte následující kód do konstruktoru formuláře k registraci obslužné rutiny události.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.FontDialog>
- [Komponenta FontDialog](fontdialog-component-windows-forms.md)
