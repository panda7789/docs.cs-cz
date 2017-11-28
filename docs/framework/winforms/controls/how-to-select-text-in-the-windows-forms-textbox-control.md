---
title: "Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox"
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
- TextBox control [Windows Forms], selecting text programmatically
- text boxes [Windows Forms], selecting text programmatically
- text [Windows Forms], selecting in text boxes programmatically
ms.assetid: 8c591546-6a01-45c7-8e03-f78431f903b1
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 08ad19f3daca43fb33e845b632ac7d92b00f544c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a><span data-ttu-id="704ac-102">Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="704ac-102">How to: Select Text in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="704ac-103">Můžete vybrat text prostřednictvím kódu programu v systému Windows Forms <xref:System.Windows.Forms.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="704ac-103">You can select text programmatically in the Windows Forms <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="704ac-104">Například pokud vytvoříte funkci, která hledá text pro určitý řetězec, můžete vybrat text, který má vizuální upozornění čtečky nalezen řetězec pozici.</span><span class="sxs-lookup"><span data-stu-id="704ac-104">For example, if you create a function that searches text for a particular string, you can select the text to visually alert the reader of the found string's position.</span></span>  
  
### <a name="to-select-text-programmatically"></a><span data-ttu-id="704ac-105">Výběr textu prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="704ac-105">To select text programmatically</span></span>  
  
1.  <span data-ttu-id="704ac-106">Nastavte <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> vlastnost na začátek textu, který chcete vybrat.</span><span class="sxs-lookup"><span data-stu-id="704ac-106">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property to the beginning of the text you want to select.</span></span>  
  
     <span data-ttu-id="704ac-107"><xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> Vlastnost je číslo, které určuje bod vložení v rámci textový řetězec, se 0 znamená pozici nejvíce vlevo.</span><span class="sxs-lookup"><span data-stu-id="704ac-107">The <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property is a number that indicates the insertion point within the string of text, with 0 being the left-most position.</span></span> <span data-ttu-id="704ac-108">Pokud <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> je nastavena na hodnotu rovna nebo větší než počet znaků v textovém poli, za poslední znak je umístěn kurzor.</span><span class="sxs-lookup"><span data-stu-id="704ac-108">If the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property is set to a value equal to or greater than the number of characters in the text box, the insertion point is placed after the last character.</span></span>  
  
2.  <span data-ttu-id="704ac-109">Nastavte <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> vlastnost, která má délku textu, kterou chcete vybrat.</span><span class="sxs-lookup"><span data-stu-id="704ac-109">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property to the length of the text you want to select.</span></span>  
  
     <span data-ttu-id="704ac-110"><xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> Vlastnost je číselnou hodnotu, která nastaví šířku kurzoru.</span><span class="sxs-lookup"><span data-stu-id="704ac-110">The <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property is a numeric value that sets the width of the insertion point.</span></span> <span data-ttu-id="704ac-111">Nastavení <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> na číslo větší než 0 způsobí, že tento počet znaků, který má být vybrán, od aktuální kurzor.</span><span class="sxs-lookup"><span data-stu-id="704ac-111">Setting the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> to a number greater than 0 causes that number of characters to be selected, starting from the current insertion point.</span></span>  
  
3.  <span data-ttu-id="704ac-112">(Volitelné) Přístup k vybraný text prostřednictvím <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="704ac-112">(Optional) Access the selected text through the <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> property.</span></span>  
  
     <span data-ttu-id="704ac-113">Kód pod vybere obsahu textového pole, kdy ovládacího prvku <xref:System.Windows.Forms.Control.Enter> dojde k události.</span><span class="sxs-lookup"><span data-stu-id="704ac-113">The code below selects the contents of a text box when the control's <xref:System.Windows.Forms.Control.Enter> event occurs.</span></span> <span data-ttu-id="704ac-114">Tento příklad zkontroluje, zda textového pole má hodnotu <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost, která není `null` nebo prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="704ac-114">This example checks if the text box has a value for the <xref:System.Windows.Forms.TextBox.Text%2A> property that is not `null` or an empty string.</span></span> <span data-ttu-id="704ac-115">Když bude vybrán, textového pole, je vybrána aktuální text v textovém poli.</span><span class="sxs-lookup"><span data-stu-id="704ac-115">When the text box receives the focus, the current text in the text box is selected.</span></span> <span data-ttu-id="704ac-116">`TextBox1_Enter` Obslužné rutiny události musí být vázána k ovládacímu prvku; další informace naleznete v tématu [postupy: vytváření obslužných rutin událostí spustit čas pro Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="704ac-116">The `TextBox1_Enter` event handler must be bound to the control; for more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
     <span data-ttu-id="704ac-117">K testování v tomto příkladu, stiskněte klávesu Tabulátor, dokud textové pole je aktivní.</span><span class="sxs-lookup"><span data-stu-id="704ac-117">To test this example, press the Tab key until the text box has the focus.</span></span> <span data-ttu-id="704ac-118">Pokud kliknete na tlačítko do textového pole, je text nezaškrtnuté.</span><span class="sxs-lookup"><span data-stu-id="704ac-118">If you click in the text box, the text is unselected.</span></span>  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       If (Not String.IsNullOrEmpty(TextBox1.Text)) Then  
          TextBox1.SelectionStart = 0  
          TextBox1.SelectionLength = TextBox1.Text.Length  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(object sender, System.EventArgs e){  
       if (!String.IsNullOrEmpty(textBox1.Text))  
       {  
          textBox1.SelectionStart = 0;  
          textBox1.SelectionLength = textBox1.Text.Length;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^ sender,  
          System::EventArgs ^ e) {  
       if (!System::String::IsNullOrEmpty(textBox1->Text))  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = textBox1->Text->Length;  
       }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="704ac-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="704ac-119">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="704ac-120">Přehled ovládacího prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="704ac-120">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="704ac-121">Postupy: řízení bodu pro vkládání v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="704ac-121">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="704ac-122">Postupy: vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="704ac-122">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="704ac-123">Postupy: vytvoření jen pro čtení textového pole</span><span class="sxs-lookup"><span data-stu-id="704ac-123">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="704ac-124">Postupy: vkládání uvozovek do řetězce</span><span class="sxs-lookup"><span data-stu-id="704ac-124">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="704ac-125">Postupy: zobrazení více řádků v systému Windows Forms TextBox – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="704ac-125">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="704ac-126">TextBox – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="704ac-126">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
