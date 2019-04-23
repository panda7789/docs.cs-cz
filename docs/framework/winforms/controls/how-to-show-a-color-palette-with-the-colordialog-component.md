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
ms.openlocfilehash: 587b2c3a502ec8a1cb2f4f7c0d981baa0f18ead6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59298016"
---
# <a name="how-to-show-a-color-palette-with-the-colordialog-component"></a><span data-ttu-id="d944a-102">Postupy: Zobrazení palety barev pomocí komponenty ColorDialog</span><span class="sxs-lookup"><span data-stu-id="d944a-102">How to: Show a Color Palette with the ColorDialog Component</span></span>
<span data-ttu-id="d944a-103">[ColorDialog](colordialog-component-windows-forms.md) komponenty paletu barev zobrazí a vrátí vlastnost obsahující barvu uživatel vybral.</span><span class="sxs-lookup"><span data-stu-id="d944a-103">The [ColorDialog](colordialog-component-windows-forms.md) component displays a palette of colors and returns a property containing the color the user has selected.</span></span>  
  
### <a name="to-choose-a-color-using-the-colordialog-component"></a><span data-ttu-id="d944a-104">Vybrat barvu pomocí komponenty ColorDialog</span><span class="sxs-lookup"><span data-stu-id="d944a-104">To choose a color using the ColorDialog component</span></span>  
  
1. <span data-ttu-id="d944a-105">Zobrazit dialog box pomocí <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d944a-105">Display the dialog box using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
2. <span data-ttu-id="d944a-106">Použití <xref:System.Windows.Forms.DialogResult> a určí, jak bylo ukončeno dialogových oken.</span><span class="sxs-lookup"><span data-stu-id="d944a-106">Use the <xref:System.Windows.Forms.DialogResult> property to determine how the dialog box was closed.</span></span>  
  
3. <span data-ttu-id="d944a-107">Použití <xref:System.Windows.Forms.ColorDialog.Color%2A> vlastnost <xref:System.Windows.Forms.ColorDialog> součást pro nastavení vybrané barvy.</span><span class="sxs-lookup"><span data-stu-id="d944a-107">Use the <xref:System.Windows.Forms.ColorDialog.Color%2A> property of the <xref:System.Windows.Forms.ColorDialog> component to set the chosen color.</span></span>  
  
     <span data-ttu-id="d944a-108">V následujícím příkladu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Click> otevře obslužné rutiny události <xref:System.Windows.Forms.ColorDialog> komponenty.</span><span class="sxs-lookup"><span data-stu-id="d944a-108">In the example below, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens a <xref:System.Windows.Forms.ColorDialog> component.</span></span> <span data-ttu-id="d944a-109">Pokud barvu je zvolená a uživatel klikne na tlačítko **OK**, <xref:System.Windows.Forms.Button> barva pozadí ovládacího prvku nastavená na vybrané barvy.</span><span class="sxs-lookup"><span data-stu-id="d944a-109">When a color is chosen and the user clicks **OK**, the <xref:System.Windows.Forms.Button> control's background color is set to the chosen color.</span></span> <span data-ttu-id="d944a-110">Příklad předpokládá, že váš formulář má <xref:System.Windows.Forms.Button> ovládacího prvku a <xref:System.Windows.Forms.ColorDialog> komponenty.</span><span class="sxs-lookup"><span data-stu-id="d944a-110">The example assumes your form has a <xref:System.Windows.Forms.Button> control and a <xref:System.Windows.Forms.ColorDialog> component.</span></span>  
  
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
  
     <span data-ttu-id="d944a-111">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="d944a-111">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=   
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d944a-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d944a-112">See also</span></span>

- <xref:System.Windows.Forms.ColorDialog>
- [<span data-ttu-id="d944a-113">Komponenta ColorDialog</span><span class="sxs-lookup"><span data-stu-id="d944a-113">ColorDialog Component</span></span>](colordialog-component-windows-forms.md)
