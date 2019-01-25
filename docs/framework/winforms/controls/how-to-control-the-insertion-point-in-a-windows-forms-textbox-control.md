---
title: 'Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], insertion point
- insertion points [Windows Forms], TextBox controls
- text boxes [Windows Forms], controlling insertion point
ms.assetid: 5bee7d34-5121-429e-ab1f-d8ff67bc74c1
ms.openlocfilehash: 6ed49cac8341551dd0900a8468990e314a16e7b6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660187"
---
# <a name="how-to-control-the-insertion-point-in-a-windows-forms-textbox-control"></a><span data-ttu-id="be04d-102">Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="be04d-102">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>
<span data-ttu-id="be04d-103">Když prvku Windows Forms <xref:System.Windows.Forms.TextBox> ovládací prvek nejprve dostane fokus, je výchozí kurzor v textovém poli na levé straně jakýkoli existující text.</span><span class="sxs-lookup"><span data-stu-id="be04d-103">When a Windows Forms <xref:System.Windows.Forms.TextBox> control first receives the focus, the default insertion within the text box is to the left of any existing text.</span></span> <span data-ttu-id="be04d-104">Uživatel může přesunout kurzor pomocí klávesnice nebo myši.</span><span class="sxs-lookup"><span data-stu-id="be04d-104">The user can move the insertion point with the keyboard or the mouse.</span></span> <span data-ttu-id="be04d-105">Pokud textové pole ztratí a potom získá fokus, kurzor se všude, kde uživatel naposledy vložili.</span><span class="sxs-lookup"><span data-stu-id="be04d-105">If the text box loses and then regains the focus, the insertion point will be wherever the user last placed it.</span></span>  
  
 <span data-ttu-id="be04d-106">V některých případech může být toto chování zneklidňovat uživateli.</span><span class="sxs-lookup"><span data-stu-id="be04d-106">In some cases, this behavior can be disconcerting to the user.</span></span> <span data-ttu-id="be04d-107">V textovém editoru aplikace, uživatel může očekávat, že znaky nového objevovat po jakýkoli existující text.</span><span class="sxs-lookup"><span data-stu-id="be04d-107">In a word processing application, the user might expect new characters to appear after any existing text.</span></span> <span data-ttu-id="be04d-108">V aplikaci vstupní data uživatel může očekávat znaky nového nahradit všechny existující položky.</span><span class="sxs-lookup"><span data-stu-id="be04d-108">In a data entry application, the user might expect new characters to replace any existing entry.</span></span> <span data-ttu-id="be04d-109"><xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> a <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> vlastnosti umožňují změnit chování při vyhovovaly vašim konkrétním potřebám.</span><span class="sxs-lookup"><span data-stu-id="be04d-109">The <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> and <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> properties enable you to modify the behavior to suit your purpose.</span></span>  
  
### <a name="to-control-the-insertion-point-in-a-textbox-control"></a><span data-ttu-id="be04d-110">K řízení místa vložení v ovládacím prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="be04d-110">To control the insertion point in a TextBox control</span></span>  
  
1.  <span data-ttu-id="be04d-111">Nastavte <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> vlastnost na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="be04d-111">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property to an appropriate value.</span></span> <span data-ttu-id="be04d-112">Nula umístí kurzor bezprostředně nalevo od prvního znaku.</span><span class="sxs-lookup"><span data-stu-id="be04d-112">Zero places the insertion point immediately to the left of the first character.</span></span>  
  
2.  <span data-ttu-id="be04d-113">(Volitelné) Nastavte <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> vlastnost Délka textu, kterou chcete vybrat.</span><span class="sxs-lookup"><span data-stu-id="be04d-113">(Optional) Set the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property to the length of the text you want to select.</span></span>  
  
     <span data-ttu-id="be04d-114">Následující kód vždy vrátí kurzor na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="be04d-114">The code below always returns the insertion point to 0.</span></span> <span data-ttu-id="be04d-115">`TextBox1_Enter` Obslužné rutiny události musí být vázán na ovládací prvek; další informace naleznete v tématu [vytváření obslužných rutin událostí ve Windows Forms](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="be04d-115">The `TextBox1_Enter` event handler must be bound to the control; for more information, see [Creating Event Handlers in Windows Forms](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md).</span></span>  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       TextBox1.SelectionStart = 0  
       TextBox1.SelectionLength = 0  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(Object sender, System.EventArgs e) {  
       textBox1.SelectionStart = 0;  
       textBox1.SelectionLength = 0;  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = 0;  
       }  
    ```  
  
## <a name="making-the-insertion-point-visible-by-default"></a><span data-ttu-id="be04d-116">Ve výchozím nastavení zviditelnění kurzor</span><span class="sxs-lookup"><span data-stu-id="be04d-116">Making the Insertion Point Visible by Default</span></span>  
 <span data-ttu-id="be04d-117"><xref:System.Windows.Forms.TextBox> Viditelné ve výchozím nastavení nového formuláře pouze tehdy, pokud je kurzor <xref:System.Windows.Forms.TextBox> ovládací prvek je první v pořadí.</span><span class="sxs-lookup"><span data-stu-id="be04d-117">The <xref:System.Windows.Forms.TextBox> insertion point is visible by default in a new form only if the <xref:System.Windows.Forms.TextBox> control is first in the tab order.</span></span> <span data-ttu-id="be04d-118">V opačném případě se zobrazí kurzor pouze v případě, že přidělíte <xref:System.Windows.Forms.TextBox> fokusu pomocí klávesnice nebo myši.</span><span class="sxs-lookup"><span data-stu-id="be04d-118">Otherwise, the insertion point appears only if you give the <xref:System.Windows.Forms.TextBox> the focus with either the keyboard or the mouse.</span></span>  
  
#### <a name="to-make-the-text-box-insertion-point-visible-by-default-on-a-new-form"></a><span data-ttu-id="be04d-119">Ke zviditelnění pole kurzor text ve výchozím nastavení nový formulář</span><span class="sxs-lookup"><span data-stu-id="be04d-119">To make the text box insertion point visible by default on a new form</span></span>  
  
-   <span data-ttu-id="be04d-120">Nastavte <xref:System.Windows.Forms.TextBox> ovládacího prvku <xref:System.Windows.Forms.Control.TabIndex%2A> vlastnost `0`.</span><span class="sxs-lookup"><span data-stu-id="be04d-120">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.Control.TabIndex%2A> property to `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be04d-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="be04d-121">See also</span></span>
- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="be04d-122">Přehled ovládacího prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="be04d-122">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="be04d-123">Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="be04d-123">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="be04d-124">Postupy: Vytvoření pole jen pro čtení textu</span><span class="sxs-lookup"><span data-stu-id="be04d-124">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="be04d-125">Postupy: Vkládání uvozovek do řetězce</span><span class="sxs-lookup"><span data-stu-id="be04d-125">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="be04d-126">Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="be04d-126">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="be04d-127">Postupy: Zobrazit více řádků v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="be04d-127">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="be04d-128">Ovládací prvek TextBox</span><span class="sxs-lookup"><span data-stu-id="be04d-128">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
