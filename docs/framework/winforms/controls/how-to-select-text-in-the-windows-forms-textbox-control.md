---
title: Výběr textu v ovládacím prvku TextBox
description: Naučte se, jak vybrat text programově v ovládacím prvku model Windows Forms TextBox. Také se dozvíte, jak vizuálně upozornit čtenáře pozice nalezeného řetězce.
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
ms.openlocfilehash: b8fdaff76461c4d6766dfc6afaef5e814d982834
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621558"
---
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a><span data-ttu-id="ee19a-104">Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="ee19a-104">How to: Select Text in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="ee19a-105">Text můžete v ovládacím prvku model Windows Forms vybrat programově <xref:System.Windows.Forms.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="ee19a-105">You can select text programmatically in the Windows Forms <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="ee19a-106">Například pokud vytvoříte funkci, která vyhledává text konkrétního řetězce, můžete vybrat text, který vizuálně upozorní čtenáře nalezené pozice řetězce.</span><span class="sxs-lookup"><span data-stu-id="ee19a-106">For example, if you create a function that searches text for a particular string, you can select the text to visually alert the reader of the found string's position.</span></span>  
  
### <a name="to-select-text-programmatically"></a><span data-ttu-id="ee19a-107">Výběr textu prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="ee19a-107">To select text programmatically</span></span>  
  
1. <span data-ttu-id="ee19a-108">Nastavte <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> vlastnost na začátek textu, který chcete vybrat.</span><span class="sxs-lookup"><span data-stu-id="ee19a-108">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property to the beginning of the text you want to select.</span></span>  
  
     <span data-ttu-id="ee19a-109"><xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A>Vlastnost je číslo, které označuje pozici kurzoru v řetězci textu, přičemž 0 je největší pozice vlevo.</span><span class="sxs-lookup"><span data-stu-id="ee19a-109">The <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property is a number that indicates the insertion point within the string of text, with 0 being the left-most position.</span></span> <span data-ttu-id="ee19a-110">Pokud <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> je vlastnost nastavena na hodnotu větší nebo rovna počtu znaků v textovém poli, je kurzor umístěn za posledním znakem.</span><span class="sxs-lookup"><span data-stu-id="ee19a-110">If the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property is set to a value equal to or greater than the number of characters in the text box, the insertion point is placed after the last character.</span></span>  
  
2. <span data-ttu-id="ee19a-111">Nastavte <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> vlastnost na délku textu, který chcete vybrat.</span><span class="sxs-lookup"><span data-stu-id="ee19a-111">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property to the length of the text you want to select.</span></span>  
  
     <span data-ttu-id="ee19a-112"><xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>Vlastnost je číselná hodnota, která nastavuje šířku bodu vložení.</span><span class="sxs-lookup"><span data-stu-id="ee19a-112">The <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property is a numeric value that sets the width of the insertion point.</span></span> <span data-ttu-id="ee19a-113">Nastavení <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> na číslo větší než 0 způsobí, že počet znaků, který má být vybrán, počínaje aktuálním místem vložení.</span><span class="sxs-lookup"><span data-stu-id="ee19a-113">Setting the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> to a number greater than 0 causes that number of characters to be selected, starting from the current insertion point.</span></span>  
  
3. <span data-ttu-id="ee19a-114">Volitelné Přístup k vybranému textu prostřednictvím <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ee19a-114">(Optional) Access the selected text through the <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> property.</span></span>  
  
     <span data-ttu-id="ee19a-115">Následující kód vybírá obsah textového pole, když dojde k události ovládacího prvku <xref:System.Windows.Forms.Control.Enter> .</span><span class="sxs-lookup"><span data-stu-id="ee19a-115">The code below selects the contents of a text box when the control's <xref:System.Windows.Forms.Control.Enter> event occurs.</span></span> <span data-ttu-id="ee19a-116">Tento příklad kontroluje, zda textové pole má hodnotu pro <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost, která není nebo je `null` prázdným řetězcem.</span><span class="sxs-lookup"><span data-stu-id="ee19a-116">This example checks if the text box has a value for the <xref:System.Windows.Forms.TextBox.Text%2A> property that is not `null` or an empty string.</span></span> <span data-ttu-id="ee19a-117">Když textové pole dostane fokus, je vybrán aktuální text v textovém poli.</span><span class="sxs-lookup"><span data-stu-id="ee19a-117">When the text box receives the focus, the current text in the text box is selected.</span></span> <span data-ttu-id="ee19a-118">`TextBox1_Enter`Obslužná rutina události musí být svázána s ovládacím prvkem. Další informace naleznete v tématu [How to: Create event handlers za běhu pro model Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="ee19a-118">The `TextBox1_Enter` event handler must be bound to the control; for more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
     <span data-ttu-id="ee19a-119">Chcete-li otestovat tento příklad, stiskněte klávesu TAB, dokud textové pole nemá fokus.</span><span class="sxs-lookup"><span data-stu-id="ee19a-119">To test this example, press the Tab key until the text box has the focus.</span></span> <span data-ttu-id="ee19a-120">Pokud kliknete na textové pole, text nebude vybrán.</span><span class="sxs-lookup"><span data-stu-id="ee19a-120">If you click in the text box, the text is unselected.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ee19a-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee19a-121">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="ee19a-122">Přehled ovládacího prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="ee19a-122">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="ee19a-123">Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="ee19a-123">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="ee19a-124">Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="ee19a-124">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="ee19a-125">Postupy: Vytvoření textového pole určeného jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ee19a-125">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="ee19a-126">Postupy: Vkládání uvozovek do řetězce</span><span class="sxs-lookup"><span data-stu-id="ee19a-126">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="ee19a-127">Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="ee19a-127">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="ee19a-128">TextBox – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="ee19a-128">TextBox Control</span></span>](textbox-control-windows-forms.md)
