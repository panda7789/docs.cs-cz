---
title: 'Postupy: Zobrazení palety barev pomocí součásti ColorDialog'
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
ms.openlocfilehash: 0406ef7a32678bd149c0024348a7adf1f0b72926
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141780"
---
# <a name="how-to-show-a-color-palette-with-the-colordialog-component"></a>Postupy: Zobrazení palety barev pomocí součásti ColorDialog
Komponenta [ColorDialog](colordialog-component-windows-forms.md) zobrazí paletu barev a vrátí vlastnost obsahující barvu, kterou uživatel vybral.  
  
### <a name="to-choose-a-color-using-the-colordialog-component"></a>Výběr barvy pomocí komponenty ColorDialog  
  
1. Zobrazení dialogového okna <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> pomocí metody.  
  
2. Pomocí <xref:System.Windows.Forms.DialogResult> vlastnosti určete, jak bylo dialogové okno uzavřeno.  
  
3. Použijte <xref:System.Windows.Forms.ColorDialog.Color%2A> vlastnost komponenty <xref:System.Windows.Forms.ColorDialog> k nastavení zvolené barvy.  
  
     V níže uvedeném <xref:System.Windows.Forms.Button> příkladu <xref:System.Windows.Forms.Control.Click> ovládací ho <xref:System.Windows.Forms.ColorDialog> ovládacího prvku otevře součást. Když je vybrána barva a **OK**uživatel <xref:System.Windows.Forms.Button> klepne na OK , je barva pozadí ovládacího prvku nastavena na vybranou barvu. Příklad předpokládá, že formulář <xref:System.Windows.Forms.Button> má <xref:System.Windows.Forms.ColorDialog> ovládací prvek a součást.  
  
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
  
     (Visual C#, Visual C++) Umístěte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ColorDialog>
- [ColorDialog – komponenta](colordialog-component-windows-forms.md)
