---
title: 'Postupy: Zobrazení palety barev pomocí součásti ColorDialog'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
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
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f3f75c6ec29b82c70d4160ccc40ddb9ced0ea711
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-show-a-color-palette-with-the-colordialog-component"></a><span data-ttu-id="1531f-102">Postupy: Zobrazení palety barev pomocí součásti ColorDialog</span><span class="sxs-lookup"><span data-stu-id="1531f-102">How to: Show a Color Palette with the ColorDialog Component</span></span>
<span data-ttu-id="1531f-103">[ColorDialog](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md) součást Zobrazí paletu barev a vrátí vlastnost obsahující barvu uživatel vybral.</span><span class="sxs-lookup"><span data-stu-id="1531f-103">The [ColorDialog](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md) component displays a palette of colors and returns a property containing the color the user has selected.</span></span>  
  
### <a name="to-choose-a-color-using-the-colordialog-component"></a><span data-ttu-id="1531f-104">Vybrat barvu pomocí součásti ColorDialog</span><span class="sxs-lookup"><span data-stu-id="1531f-104">To choose a color using the ColorDialog component</span></span>  
  
1.  <span data-ttu-id="1531f-105">Zobrazí dialogové okno pole pomocí <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="1531f-105">Display the dialog box using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
2.  <span data-ttu-id="1531f-106">Použití <xref:System.Windows.Forms.DialogResult> vlastnosti k určení, jak bylo ukončeno dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="1531f-106">Use the <xref:System.Windows.Forms.DialogResult> property to determine how the dialog box was closed.</span></span>  
  
3.  <span data-ttu-id="1531f-107">Použití <xref:System.Windows.Forms.ColorDialog.Color%2A> vlastnost <xref:System.Windows.Forms.ColorDialog> součást, kterou nastavení vybrané barvy.</span><span class="sxs-lookup"><span data-stu-id="1531f-107">Use the <xref:System.Windows.Forms.ColorDialog.Color%2A> property of the <xref:System.Windows.Forms.ColorDialog> component to set the chosen color.</span></span>  
  
     <span data-ttu-id="1531f-108">V následujícím příkladu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Click> otevře obslužné rutiny události <xref:System.Windows.Forms.ColorDialog> součásti.</span><span class="sxs-lookup"><span data-stu-id="1531f-108">In the example below, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens a <xref:System.Windows.Forms.ColorDialog> component.</span></span> <span data-ttu-id="1531f-109">Pokud barvu, která je zvolená a uživatel klikne na tlačítko **OK**, <xref:System.Windows.Forms.Button> barvu pozadí ovládacího prvku nastavena na vybrané barvy.</span><span class="sxs-lookup"><span data-stu-id="1531f-109">When a color is chosen and the user clicks **OK**, the <xref:System.Windows.Forms.Button> control's background color is set to the chosen color.</span></span> <span data-ttu-id="1531f-110">Příklad předpokládá, že má formulář <xref:System.Windows.Forms.Button> řízení a <xref:System.Windows.Forms.ColorDialog> součásti.</span><span class="sxs-lookup"><span data-stu-id="1531f-110">The example assumes your form has a <xref:System.Windows.Forms.Button> control and a <xref:System.Windows.Forms.ColorDialog> component.</span></span>  
  
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
  
     <span data-ttu-id="1531f-111">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="1531f-111">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=   
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1531f-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="1531f-112">See Also</span></span>  
 <xref:System.Windows.Forms.ColorDialog>  
 [<span data-ttu-id="1531f-113">Komponenta ColorDialog</span><span class="sxs-lookup"><span data-stu-id="1531f-113">ColorDialog Component</span></span>](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)
