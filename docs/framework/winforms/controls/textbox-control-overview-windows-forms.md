---
title: TextBox – přehled ovládacího prvku (Windows Forms)
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
ms.openlocfilehash: a91b67df1071c79707bb20a68efb4d5e6f083ae0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61932545"
---
# <a name="textbox-control-overview-windows-forms"></a><span data-ttu-id="cf9e8-102">TextBox – přehled ovládacího prvku (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="cf9e8-102">TextBox Control Overview (Windows Forms)</span></span>
<span data-ttu-id="cf9e8-103">Windows Forms textová pole se používají k získání vstupy od uživatele nebo k zobrazení textu.</span><span class="sxs-lookup"><span data-stu-id="cf9e8-103">Windows Forms text boxes are used to get input from the user or to display text.</span></span> <span data-ttu-id="cf9e8-104"><xref:System.Windows.Forms.TextBox> Ovládací prvek se obecně používají pro upravitelný text, i když ji můžete také nastavit jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="cf9e8-104">The <xref:System.Windows.Forms.TextBox> control is generally used for editable text, although it can also be made read-only.</span></span> <span data-ttu-id="cf9e8-105">Textová pole můžete zobrazit více řádků, zalamovat text, který má velikost ovládacího prvku a přidat základní formátování.</span><span class="sxs-lookup"><span data-stu-id="cf9e8-105">Text boxes can display multiple lines, wrap text to the size of the control, and add basic formatting.</span></span> <span data-ttu-id="cf9e8-106"><xref:System.Windows.Forms.TextBox> Řízení poskytuje jeden formát styl textu zobrazit nebo zadat do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="cf9e8-106">The <xref:System.Windows.Forms.TextBox> control provides a single format style for text displayed or entered into the control.</span></span> <span data-ttu-id="cf9e8-107">Chcete-li zobrazit více typů formátovaný text, použijte <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="cf9e8-107">To display multiple types of formatted text, use the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="cf9e8-108">Další informace najdete v tématu [RichTextBox – Přehled ovládacího prvku](richtextbox-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="cf9e8-108">For more information, see [RichTextBox Control Overview](richtextbox-control-overview-windows-forms.md).</span></span>  
  
## <a name="working-with-the-textbox-control"></a><span data-ttu-id="cf9e8-109">Práce s ovládacím prvkem textového pole</span><span class="sxs-lookup"><span data-stu-id="cf9e8-109">Working with the TextBox Control</span></span>  
 <span data-ttu-id="cf9e8-110">Text zobrazený ovládacím prvkem je součástí <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="cf9e8-110">The text displayed by the control is contained in the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span> <span data-ttu-id="cf9e8-111">Ve výchozím nastavení můžete zadat maximálně 2048 znaků v textovém poli.</span><span class="sxs-lookup"><span data-stu-id="cf9e8-111">By default, you can enter up to 2048 characters in a text box.</span></span> <span data-ttu-id="cf9e8-112">Pokud jste nastavili <xref:System.Windows.Forms.TextBox.Multiline%2A> vlastnost `true`, můžete zadat až 32 KB textu.</span><span class="sxs-lookup"><span data-stu-id="cf9e8-112">If you set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`, you can enter up to 32 KB of text.</span></span> <span data-ttu-id="cf9e8-113"><xref:System.Windows.Forms.TextBox.Text%2A> Vlastnost lze nastavit v době návrhu pomocí okna vlastnosti v době běhu v kódu, nebo uživatelského vstupu v době běhu.</span><span class="sxs-lookup"><span data-stu-id="cf9e8-113">The <xref:System.Windows.Forms.TextBox.Text%2A> property can be set at design time with the Properties Window, at run time in code, or by user input at run time.</span></span> <span data-ttu-id="cf9e8-114">Je možné načíst aktuální obsah textového pole za běhu v článku <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="cf9e8-114">The current contents of a text box can be retrieved at run time by reading the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
 <span data-ttu-id="cf9e8-115">Následující příklad kódu nastaví text v ovládacím prvku v době běhu.</span><span class="sxs-lookup"><span data-stu-id="cf9e8-115">The following code example sets text in the control at run time.</span></span> <span data-ttu-id="cf9e8-116">`InitializeMyControl` Postup nespustí automaticky, musí být volána.</span><span class="sxs-lookup"><span data-stu-id="cf9e8-116">The `InitializeMyControl` procedure will not execute automatically; it must be called.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cf9e8-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cf9e8-117">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="cf9e8-118">Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="cf9e8-118">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="cf9e8-119">Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="cf9e8-119">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="cf9e8-120">Postupy: Vytvoření pole jen pro čtení textu</span><span class="sxs-lookup"><span data-stu-id="cf9e8-120">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="cf9e8-121">Postupy: Vkládání uvozovek do řetězce</span><span class="sxs-lookup"><span data-stu-id="cf9e8-121">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="cf9e8-122">Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="cf9e8-122">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="cf9e8-123">Postupy: Zobrazit více řádků v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="cf9e8-123">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="cf9e8-124">Ovládací prvek TextBox</span><span class="sxs-lookup"><span data-stu-id="cf9e8-124">TextBox Control</span></span>](textbox-control-windows-forms.md)
