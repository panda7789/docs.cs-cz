---
title: 'Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], selecting text programmatically
- text boxes [Windows Forms], selecting text programmatically
- text [Windows Forms], selecting in text boxes programmatically
ms.assetid: 8c591546-6a01-45c7-8e03-f78431f903b1
ms.openlocfilehash: df2aec3ff108c0106f29e453a93b06c60e67c6af
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649411"
---
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a><span data-ttu-id="56511-102">Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="56511-102">How to: Select Text in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="56511-103">Text můžete vybrat programově v rozhraní Windows Forms <xref:System.Windows.Forms.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="56511-103">You can select text programmatically in the Windows Forms <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="56511-104">Pokud vytvoříte funkci, která hledá text pro určitý řetězec, můžete vybrat text, který má vizuální upozornění čtečky nalezený řetězec pozici.</span><span class="sxs-lookup"><span data-stu-id="56511-104">For example, if you create a function that searches text for a particular string, you can select the text to visually alert the reader of the found string's position.</span></span>  
  
### <a name="to-select-text-programmatically"></a><span data-ttu-id="56511-105">Chcete-li vybrat text prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="56511-105">To select text programmatically</span></span>  
  
1.  <span data-ttu-id="56511-106">Nastavte <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> vlastnost na začátek textu, který chcete vybrat.</span><span class="sxs-lookup"><span data-stu-id="56511-106">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property to the beginning of the text you want to select.</span></span>  
  
     <span data-ttu-id="56511-107"><xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> Vlastnost je číslo, které označuje kurzor do textového řetězce, s 0 se pozice nejvíce vlevo.</span><span class="sxs-lookup"><span data-stu-id="56511-107">The <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property is a number that indicates the insertion point within the string of text, with 0 being the left-most position.</span></span> <span data-ttu-id="56511-108">Pokud <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> je nastavena na hodnotu roven nebo větší než počet znaků v textovém poli, kurzor je umístěn za posledním znakem.</span><span class="sxs-lookup"><span data-stu-id="56511-108">If the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property is set to a value equal to or greater than the number of characters in the text box, the insertion point is placed after the last character.</span></span>  
  
2.  <span data-ttu-id="56511-109">Nastavte <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> vlastnost Délka textu, kterou chcete vybrat.</span><span class="sxs-lookup"><span data-stu-id="56511-109">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property to the length of the text you want to select.</span></span>  
  
     <span data-ttu-id="56511-110"><xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> Vlastnost má číselnou hodnotu, která nastavuje šířku kurzor.</span><span class="sxs-lookup"><span data-stu-id="56511-110">The <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property is a numeric value that sets the width of the insertion point.</span></span> <span data-ttu-id="56511-111">Nastavení <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> na číslo větší než 0 způsobí, že se tento počet znaků, které mají být vybrán, od z do aktuálního místa vložení.</span><span class="sxs-lookup"><span data-stu-id="56511-111">Setting the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> to a number greater than 0 causes that number of characters to be selected, starting from the current insertion point.</span></span>  
  
3.  <span data-ttu-id="56511-112">(Volitelné) Přístup prostřednictvím vybraný text <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="56511-112">(Optional) Access the selected text through the <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> property.</span></span>  
  
     <span data-ttu-id="56511-113">Kód uvedený níže vybere obsah textového pole, když ovládací prvek <xref:System.Windows.Forms.Control.Enter> dojde k události.</span><span class="sxs-lookup"><span data-stu-id="56511-113">The code below selects the contents of a text box when the control's <xref:System.Windows.Forms.Control.Enter> event occurs.</span></span> <span data-ttu-id="56511-114">Tento příklad kontroluje, jestli do textového pole má hodnotu <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost, která není `null` nebo prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="56511-114">This example checks if the text box has a value for the <xref:System.Windows.Forms.TextBox.Text%2A> property that is not `null` or an empty string.</span></span> <span data-ttu-id="56511-115">Když bude vybrán, do textového pole, je vybrána aktuální text v textovém poli.</span><span class="sxs-lookup"><span data-stu-id="56511-115">When the text box receives the focus, the current text in the text box is selected.</span></span> <span data-ttu-id="56511-116">`TextBox1_Enter` Obslužné rutiny události musí být vázán na ovládací prvek; další informace naleznete v tématu [jak: Vytváření obslužných rutin událostí pro Windows Forms v době běhu](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="56511-116">The `TextBox1_Enter` event handler must be bound to the control; for more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
     <span data-ttu-id="56511-117">K otestování v tomto příkladu, stiskněte klávesu Tab, dokud do textového pole má fokus.</span><span class="sxs-lookup"><span data-stu-id="56511-117">To test this example, press the Tab key until the text box has the focus.</span></span> <span data-ttu-id="56511-118">Pokud kliknete do textového pole, text byl zrušen výběr cesty.</span><span class="sxs-lookup"><span data-stu-id="56511-118">If you click in the text box, the text is unselected.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="56511-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56511-119">See also</span></span>
- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="56511-120">Přehled ovládacího prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="56511-120">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="56511-121">Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="56511-121">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="56511-122">Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="56511-122">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="56511-123">Postupy: Vytvoření pole jen pro čtení textu</span><span class="sxs-lookup"><span data-stu-id="56511-123">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="56511-124">Postupy: Vkládání uvozovek do řetězce</span><span class="sxs-lookup"><span data-stu-id="56511-124">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="56511-125">Postupy: Zobrazit více řádků v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="56511-125">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="56511-126">Ovládací prvek TextBox</span><span class="sxs-lookup"><span data-stu-id="56511-126">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
