---
title: 'Postupy: Zobrazení palety barev pomocí komponenty ColorDialog'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- palettes [Windows Forms], showing color
- color dialog box [Windows Forms], showing color palettes
- colors [Windows Forms], allowing users to select
- color palettes [Windows Forms], dialog box
- ColorDialog component [Windows Forms], showing color palettes
- color palettes [Windows Forms], showing in ColorDialog component
- colors [Windows Forms], showing palettes
ms.assetid: ee050f61-dbc8-4436-ba22-51360981ab48
ms.openlocfilehash: fcaf5da9958cf66fb63bd753dc94cba9c10f62f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096033"
---
# <a name="how-to-show-a-color-palette-with-the-colordialog-component"></a>Postupy: Zobrazení palety barev pomocí komponenty ColorDialog
[ColorDialog](colordialog-component-windows-forms.md) komponenty paletu barev zobrazí a vrátí vlastnost obsahující barvu uživatel vybral.  
  
### <a name="to-choose-a-color-using-the-colordialog-component"></a>Vybrat barvu pomocí komponenty ColorDialog  
  
1.  Zobrazit dialog box pomocí <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody.  
  
2.  Použití <xref:System.Windows.Forms.DialogResult> a určí, jak bylo ukončeno dialogových oken.  
  
3.  Použití <xref:System.Windows.Forms.ColorDialog.Color%2A> vlastnost <xref:System.Windows.Forms.ColorDialog> součást pro nastavení vybrané barvy.  
  
     V následujícím příkladu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Click> otevře obslužné rutiny události <xref:System.Windows.Forms.ColorDialog> komponenty. Pokud barvu je zvolená a uživatel klikne na tlačítko **OK**, <xref:System.Windows.Forms.Button> barva pozadí ovládacího prvku nastavená na vybrané barvy. Příklad předpokládá, že váš formulář má <xref:System.Windows.Forms.Button> ovládacího prvku a <xref:System.Windows.Forms.ColorDialog> komponenty.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button1.Click  
       If ColorDialog1.ShowDialog() = DialogResult.OK Then  
          Button1.BackColor = ColorDialog1.Color  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(colorDialog1.ShowDialog() == DialogResult.OK)  
       {  
          button1.BackColor = colorDialog1.Color;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,   
          System::EventArgs ^ e)  
       {  
          if(colorDialog1->ShowDialog() == DialogResult::OK)  
          {  
             button1->BackColor = colorDialog1->Color;  
          }  
       }  
    ```  
  
     (Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=   
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ColorDialog>
- [Komponenta ColorDialog](colordialog-component-windows-forms.md)
