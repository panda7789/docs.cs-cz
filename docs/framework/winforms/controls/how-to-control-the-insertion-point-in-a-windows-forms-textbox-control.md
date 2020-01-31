---
title: Řízení bodu vložení v ovládacím prvku TextBox
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
ms.openlocfilehash: fd4803820921f0c922a4ce885f809abee8fd4c6c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742204"
---
# <a name="how-to-control-the-insertion-point-in-a-windows-forms-textbox-control"></a><span data-ttu-id="0da16-102">Postupy: Řízení bodu pro vkládání v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="0da16-102">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>
<span data-ttu-id="0da16-103">Když ovládací prvek model Windows Forms <xref:System.Windows.Forms.TextBox> první dostane fokus, výchozí vložení v textovém poli je nalevo od existujícího textu.</span><span class="sxs-lookup"><span data-stu-id="0da16-103">When a Windows Forms <xref:System.Windows.Forms.TextBox> control first receives the focus, the default insertion within the text box is to the left of any existing text.</span></span> <span data-ttu-id="0da16-104">Uživatel může přesunout bod vložení pomocí klávesnice nebo myši.</span><span class="sxs-lookup"><span data-stu-id="0da16-104">The user can move the insertion point with the keyboard or the mouse.</span></span> <span data-ttu-id="0da16-105">Pokud textové pole ztratí a pak znovu získá fokus, bude kurzor místo, kde ho uživatel naposledy umístil.</span><span class="sxs-lookup"><span data-stu-id="0da16-105">If the text box loses and then regains the focus, the insertion point will be wherever the user last placed it.</span></span>  
  
 <span data-ttu-id="0da16-106">V některých případech může být toto chování ve vzájemném objednání uživatele.</span><span class="sxs-lookup"><span data-stu-id="0da16-106">In some cases, this behavior can be disconcerting to the user.</span></span> <span data-ttu-id="0da16-107">V aplikaci pro zpracování textu může uživatel očekávat, že se nové znaky objeví po jakémkoli existujícím textu.</span><span class="sxs-lookup"><span data-stu-id="0da16-107">In a word processing application, the user might expect new characters to appear after any existing text.</span></span> <span data-ttu-id="0da16-108">V aplikaci pro zadávání dat může uživatel očekávat, že nové znaky nahradí existující položku.</span><span class="sxs-lookup"><span data-stu-id="0da16-108">In a data entry application, the user might expect new characters to replace any existing entry.</span></span> <span data-ttu-id="0da16-109">Vlastnosti <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> a <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> umožňují upravit chování tak, aby vyhovovalo vašemu účelu.</span><span class="sxs-lookup"><span data-stu-id="0da16-109">The <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> and <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> properties enable you to modify the behavior to suit your purpose.</span></span>  
  
### <a name="to-control-the-insertion-point-in-a-textbox-control"></a><span data-ttu-id="0da16-110">Řízení bodu vložení v ovládacím prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="0da16-110">To control the insertion point in a TextBox control</span></span>  
  
1. <span data-ttu-id="0da16-111">Vlastnost <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> nastavte na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0da16-111">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property to an appropriate value.</span></span> <span data-ttu-id="0da16-112">Nula umístí kurzor hned nalevo od prvního znaku.</span><span class="sxs-lookup"><span data-stu-id="0da16-112">Zero places the insertion point immediately to the left of the first character.</span></span>  
  
2. <span data-ttu-id="0da16-113">Volitelné Vlastnost <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> nastavte na délku textu, který chcete vybrat.</span><span class="sxs-lookup"><span data-stu-id="0da16-113">(Optional) Set the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property to the length of the text you want to select.</span></span>  
  
     <span data-ttu-id="0da16-114">Následující kód vždy vrátí kurzor na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="0da16-114">The code below always returns the insertion point to 0.</span></span> <span data-ttu-id="0da16-115">Obslužná rutina události `TextBox1_Enter` musí být svázána s ovládacím prvkem. Další informace naleznete v tématu [vytváření obslužných rutin událostí v model Windows Forms](../creating-event-handlers-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="0da16-115">The `TextBox1_Enter` event handler must be bound to the control; for more information, see [Creating Event Handlers in Windows Forms](../creating-event-handlers-in-windows-forms.md).</span></span>  
  
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
  
## <a name="making-the-insertion-point-visible-by-default"></a><span data-ttu-id="0da16-116">Zpřístupnění bodu vložení ve výchozím nastavení</span><span class="sxs-lookup"><span data-stu-id="0da16-116">Making the Insertion Point Visible by Default</span></span>  
 <span data-ttu-id="0da16-117"><xref:System.Windows.Forms.TextBox> vkládání je ve výchozím nastavení viditelné pouze v případě, že je ovládací prvek <xref:System.Windows.Forms.TextBox> nejprve v pořadí prvků.</span><span class="sxs-lookup"><span data-stu-id="0da16-117">The <xref:System.Windows.Forms.TextBox> insertion point is visible by default in a new form only if the <xref:System.Windows.Forms.TextBox> control is first in the tab order.</span></span> <span data-ttu-id="0da16-118">V opačném případě se místo vložení zobrazí pouze v případě, že <xref:System.Windows.Forms.TextBox> fokus poskytnete buď pomocí klávesnice, nebo pomocí myši.</span><span class="sxs-lookup"><span data-stu-id="0da16-118">Otherwise, the insertion point appears only if you give the <xref:System.Windows.Forms.TextBox> the focus with either the keyboard or the mouse.</span></span>  
  
#### <a name="to-make-the-text-box-insertion-point-visible-by-default-on-a-new-form"></a><span data-ttu-id="0da16-119">Chcete-li, aby byl textový rámeček ve výchozím nastavení viditelný v novém formuláři</span><span class="sxs-lookup"><span data-stu-id="0da16-119">To make the text box insertion point visible by default on a new form</span></span>  
  
- <span data-ttu-id="0da16-120">Nastavte vlastnost <xref:System.Windows.Forms.Control.TabIndex%2A> <xref:System.Windows.Forms.TextBox>ho ovládacího prvku na hodnotu `0`.</span><span class="sxs-lookup"><span data-stu-id="0da16-120">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.Control.TabIndex%2A> property to `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0da16-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0da16-121">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="0da16-122">Přehled ovládacího prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="0da16-122">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="0da16-123">Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="0da16-123">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="0da16-124">Postupy: Vytvoření textového pole určeného jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="0da16-124">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="0da16-125">Postupy: Vkládání uvozovek do řetězce</span><span class="sxs-lookup"><span data-stu-id="0da16-125">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="0da16-126">Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="0da16-126">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="0da16-127">Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="0da16-127">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="0da16-128">Ovládací prvek TextBox</span><span class="sxs-lookup"><span data-stu-id="0da16-128">TextBox Control</span></span>](textbox-control-windows-forms.md)
