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
ms.openlocfilehash: 18a9a4bca42117233c4b01a4aeb6cffcb79119d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726400"
---
# <a name="how-to-show-a-font-list-with-the-fontdialog-component"></a><span data-ttu-id="76cc4-102">Postupy: Zobrazení seznamu písem pomocí součásti FontDialog</span><span class="sxs-lookup"><span data-stu-id="76cc4-102">How to: Show a Font List with the FontDialog Component</span></span>
<span data-ttu-id="76cc4-103">[FontDialog](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md) komponenta umožňuje uživatelům vybrat písmo, jakož i jeho zobrazení aspekty, jako je například váha a jeho velikost změnit.</span><span class="sxs-lookup"><span data-stu-id="76cc4-103">The [FontDialog](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md) component allows users to select a font, as well as change its display aspects, such as its weight and size.</span></span>  
  
 <span data-ttu-id="76cc4-104">Písmo vybrané v dialogovém okně se vrátí v <xref:System.Windows.Forms.FontDialog.Font%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="76cc4-104">The font selected in the dialog box is returned in the <xref:System.Windows.Forms.FontDialog.Font%2A> property.</span></span> <span data-ttu-id="76cc4-105">Využití výhod písmo vybrané uživatelem. je proto stejně snadné jako vlastnost pro čtení.</span><span class="sxs-lookup"><span data-stu-id="76cc4-105">Thus, taking advantage of the font selected by the user is as easy as reading a property.</span></span>  
  
### <a name="to-select-font-properties-using-the-fontdialog-component"></a><span data-ttu-id="76cc4-106">Chcete-li vybrat vlastnosti písem pomocí komponenty FontDialog</span><span class="sxs-lookup"><span data-stu-id="76cc4-106">To select font properties using the FontDialog Component</span></span>  
  
1.  <span data-ttu-id="76cc4-107">Zobrazit dialog box pomocí <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="76cc4-107">Display the dialog box using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
2.  <span data-ttu-id="76cc4-108">Použití <xref:System.Windows.Forms.DialogResult> a určí, jak bylo ukončeno dialogových oken.</span><span class="sxs-lookup"><span data-stu-id="76cc4-108">Use the <xref:System.Windows.Forms.DialogResult> property to determine how the dialog box was closed.</span></span>  
  
3.  <span data-ttu-id="76cc4-109">Použití <xref:System.Windows.Forms.FontDialog.Font%2A> vlastnosti chcete nastavit požadované písmo.</span><span class="sxs-lookup"><span data-stu-id="76cc4-109">Use the <xref:System.Windows.Forms.FontDialog.Font%2A> property to set the desired font.</span></span>  
  
     <span data-ttu-id="76cc4-110">V následujícím příkladu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Click> otevře obslužné rutiny události <xref:System.Windows.Forms.FontDialog> komponenty.</span><span class="sxs-lookup"><span data-stu-id="76cc4-110">In the example below, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens a <xref:System.Windows.Forms.FontDialog> component.</span></span> <span data-ttu-id="76cc4-111">Pokud je písmo zvolené a uživatel klikne na tlačítko **OK**, <xref:System.Windows.Forms.FontDialog.Font%2A> vlastnost <xref:System.Windows.Forms.TextBox> ovládací prvek, který je ve formuláři je nastavena na zvolené písmo.</span><span class="sxs-lookup"><span data-stu-id="76cc4-111">When a font is chosen and the user clicks **OK**, the <xref:System.Windows.Forms.FontDialog.Font%2A> property of a <xref:System.Windows.Forms.TextBox> control that is on the form is set to the chosen font.</span></span> <span data-ttu-id="76cc4-112">Příklad předpokládá, že váš formulář má <xref:System.Windows.Forms.Button> ovládací prvek, <xref:System.Windows.Forms.TextBox> ovládacího prvku a <xref:System.Windows.Forms.FontDialog> komponenty.</span><span class="sxs-lookup"><span data-stu-id="76cc4-112">The example assumes your form has a <xref:System.Windows.Forms.Button> control, a  <xref:System.Windows.Forms.TextBox> control, and a <xref:System.Windows.Forms.FontDialog> component.</span></span>  
  
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
  
     <span data-ttu-id="76cc4-113">(Visual C# a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="76cc4-113">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="76cc4-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="76cc4-114">See also</span></span>
- <xref:System.Windows.Forms.FontDialog>
- [<span data-ttu-id="76cc4-115">Komponenta FontDialog</span><span class="sxs-lookup"><span data-stu-id="76cc4-115">FontDialog Component</span></span>](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md)
