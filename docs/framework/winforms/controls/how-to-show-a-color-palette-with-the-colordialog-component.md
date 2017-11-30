---
title: "Postupy: Zobrazení palety barev pomocí součásti ColorDialog"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: af773141039d049e010742f339ec4f9363d73cc3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-show-a-color-palette-with-the-colordialog-component"></a>Postupy: Zobrazení palety barev pomocí součásti ColorDialog
[ColorDialog](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md) součást Zobrazí paletu barev a vrátí vlastnost obsahující barvu uživatel vybral.  
  
### <a name="to-choose-a-color-using-the-colordialog-component"></a>Vybrat barvu pomocí součásti ColorDialog  
  
1.  Zobrazí dialogové okno pole pomocí <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metoda.  
  
2.  Použití <xref:System.Windows.Forms.DialogResult> vlastnosti k určení, jak bylo ukončeno dialogové okno.  
  
3.  Použití <xref:System.Windows.Forms.ColorDialog.Color%2A> vlastnost <xref:System.Windows.Forms.ColorDialog> součást, kterou nastavení vybrané barvy.  
  
     V následujícím příkladu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Click> otevře obslužné rutiny události <xref:System.Windows.Forms.ColorDialog> součásti. Pokud barvu, která je zvolená a uživatel klikne na tlačítko **OK**, <xref:System.Windows.Forms.Button> barvu pozadí ovládacího prvku nastavena na vybrané barvy. Příklad předpokládá, že má formulář <xref:System.Windows.Forms.Button> řízení a <xref:System.Windows.Forms.ColorDialog> součásti.  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=   
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ColorDialog>  
 [ColorDialog – komponenta](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)
