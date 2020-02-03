---
title: Přehled ovládacího prvku TextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TextBox
helpviewer_keywords:
- TextBox control [Windows Forms], about TextBox controls
- text boxes [Windows Forms], adding
ms.assetid: d1a9c7f5-fa53-480a-a75c-158f8649ea2f
ms.openlocfilehash: 06ab460d720d17331881b5ba653263160eaf3cb3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742804"
---
# <a name="textbox-control-overview-windows-forms"></a><span data-ttu-id="c1a40-102">TextBox – přehled ovládacího prvku (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="c1a40-102">TextBox Control Overview (Windows Forms)</span></span>
<span data-ttu-id="c1a40-103">Textová pole model Windows Forms slouží k získání vstupu od uživatele nebo k zobrazení textu.</span><span class="sxs-lookup"><span data-stu-id="c1a40-103">Windows Forms text boxes are used to get input from the user or to display text.</span></span> <span data-ttu-id="c1a40-104"><xref:System.Windows.Forms.TextBox> ovládací prvek se obecně používá pro upravitelný text, i když ho lze také nastavit jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="c1a40-104">The <xref:System.Windows.Forms.TextBox> control is generally used for editable text, although it can also be made read-only.</span></span> <span data-ttu-id="c1a40-105">Textová pole mohou zobrazovat více řádků, zalamovat text podle velikosti ovládacího prvku a přidat základní formátování.</span><span class="sxs-lookup"><span data-stu-id="c1a40-105">Text boxes can display multiple lines, wrap text to the size of the control, and add basic formatting.</span></span> <span data-ttu-id="c1a40-106">Ovládací prvek <xref:System.Windows.Forms.TextBox> poskytuje jeden styl formátu pro text zobrazený nebo zadaný do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c1a40-106">The <xref:System.Windows.Forms.TextBox> control provides a single format style for text displayed or entered into the control.</span></span> <span data-ttu-id="c1a40-107">Chcete-li zobrazit více typů formátovaného textu, použijte ovládací prvek <xref:System.Windows.Forms.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="c1a40-107">To display multiple types of formatted text, use the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="c1a40-108">Další informace najdete v tématu [Přehled ovládacího prvku RichTextBox](richtextbox-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="c1a40-108">For more information, see [RichTextBox Control Overview](richtextbox-control-overview-windows-forms.md).</span></span>  
  
## <a name="working-with-the-textbox-control"></a><span data-ttu-id="c1a40-109">Práce s ovládacím prvkem TextBox</span><span class="sxs-lookup"><span data-stu-id="c1a40-109">Working with the TextBox Control</span></span>  
 <span data-ttu-id="c1a40-110">Text zobrazený ovládacím prvkem je obsažen ve vlastnosti <xref:System.Windows.Forms.TextBox.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="c1a40-110">The text displayed by the control is contained in the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span> <span data-ttu-id="c1a40-111">Ve výchozím nastavení můžete do textového pole zadat až 2048 znaků.</span><span class="sxs-lookup"><span data-stu-id="c1a40-111">By default, you can enter up to 2048 characters in a text box.</span></span> <span data-ttu-id="c1a40-112">Pokud nastavíte vlastnost <xref:System.Windows.Forms.TextBox.Multiline%2A> na hodnotu `true`, můžete zadat až 32 KB textu.</span><span class="sxs-lookup"><span data-stu-id="c1a40-112">If you set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`, you can enter up to 32 KB of text.</span></span> <span data-ttu-id="c1a40-113">Vlastnost <xref:System.Windows.Forms.TextBox.Text%2A> lze nastavit v době návrhu pomocí okna vlastnosti, v době spuštění v kódu nebo uživatelským vstupem v době běhu.</span><span class="sxs-lookup"><span data-stu-id="c1a40-113">The <xref:System.Windows.Forms.TextBox.Text%2A> property can be set at design time with the Properties Window, at run time in code, or by user input at run time.</span></span> <span data-ttu-id="c1a40-114">Aktuální obsah textového pole lze načíst za běhu načtením vlastnosti <xref:System.Windows.Forms.TextBox.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="c1a40-114">The current contents of a text box can be retrieved at run time by reading the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
 <span data-ttu-id="c1a40-115">Následující příklad kódu nastaví text v ovládacím prvku v době běhu.</span><span class="sxs-lookup"><span data-stu-id="c1a40-115">The following code example sets text in the control at run time.</span></span> <span data-ttu-id="c1a40-116">Postup `InitializeMyControl` nebude proveden automaticky; musí být volána.</span><span class="sxs-lookup"><span data-stu-id="c1a40-116">The `InitializeMyControl` procedure will not execute automatically; it must be called.</span></span>  
  
```vb  
Private Sub InitializeMyControl()  
   ' Put some text into the control first.  
   TextBox1.Text = "This is a TextBox control."  
End Sub  
```  
  
```csharp  
private void InitializeMyControl() {  
   // Put some text into the control first.  
   textBox1.Text = "This is a TextBox control.";  
}  
```  
  
```cpp  
private:  
   void InitializeMyControl()  
   {  
      // Put some text into the control first.  
      textBox1->Text = "This is a TextBox control.";  
   }  
```  
  
## <a name="see-also"></a><span data-ttu-id="c1a40-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1a40-117">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="c1a40-118">Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="c1a40-118">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="c1a40-119">Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="c1a40-119">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="c1a40-120">Postupy: Vytvoření textového pole určeného jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="c1a40-120">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="c1a40-121">Postupy: Vkládání uvozovek do řetězce</span><span class="sxs-lookup"><span data-stu-id="c1a40-121">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="c1a40-122">Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="c1a40-122">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="c1a40-123">Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="c1a40-123">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="c1a40-124">Ovládací prvek TextBox</span><span class="sxs-lookup"><span data-stu-id="c1a40-124">TextBox Control</span></span>](textbox-control-windows-forms.md)
