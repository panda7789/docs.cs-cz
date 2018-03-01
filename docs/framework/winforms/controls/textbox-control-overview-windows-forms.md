---
title: "TextBox – přehled ovládacího prvku (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4d7312246c43157ca9cd6c7b41d2b110586721c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="textbox-control-overview-windows-forms"></a><span data-ttu-id="3c995-102">TextBox – přehled ovládacího prvku (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="3c995-102">TextBox Control Overview (Windows Forms)</span></span>
<span data-ttu-id="3c995-103">Windows Forms textová pole se používají k získání vstup od uživatele nebo k zobrazení textu.</span><span class="sxs-lookup"><span data-stu-id="3c995-103">Windows Forms text boxes are used to get input from the user or to display text.</span></span> <span data-ttu-id="3c995-104"><xref:System.Windows.Forms.TextBox> Řízení se obecně používají pro upravovat text, i když ho můžete také provést jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="3c995-104">The <xref:System.Windows.Forms.TextBox> control is generally used for editable text, although it can also be made read-only.</span></span> <span data-ttu-id="3c995-105">Textová pole můžete zobrazit více řádků, zalomení textu velikosti ovládacího prvku a přidat základní formátování.</span><span class="sxs-lookup"><span data-stu-id="3c995-105">Text boxes can display multiple lines, wrap text to the size of the control, and add basic formatting.</span></span> <span data-ttu-id="3c995-106"><xref:System.Windows.Forms.TextBox> Řízení poskytuje jeden formát styl textu zobrazuje nebo je zadán do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3c995-106">The <xref:System.Windows.Forms.TextBox> control provides a single format style for text displayed or entered into the control.</span></span> <span data-ttu-id="3c995-107">Chcete-li zobrazit více typů formátovaný text, použijte <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3c995-107">To display multiple types of formatted text, use the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="3c995-108">Další informace najdete v tématu [– Přehled ovládacího prvku RichTextBox](../../../../docs/framework/winforms/controls/richtextbox-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="3c995-108">For more information, see [RichTextBox Control Overview](../../../../docs/framework/winforms/controls/richtextbox-control-overview-windows-forms.md).</span></span>  
  
## <a name="working-with-the-textbox-control"></a><span data-ttu-id="3c995-109">Práce s ovládacím prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="3c995-109">Working with the TextBox Control</span></span>  
 <span data-ttu-id="3c995-110">Je součástí textu zobrazovaného ovládacím prvkem <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3c995-110">The text displayed by the control is contained in the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span> <span data-ttu-id="3c995-111">Ve výchozím nastavení můžete zadat až 2048 znaků v textovém poli.</span><span class="sxs-lookup"><span data-stu-id="3c995-111">By default, you can enter up to 2048 characters in a text box.</span></span> <span data-ttu-id="3c995-112">Pokud nastavíte <xref:System.Windows.Forms.TextBox.Multiline%2A> vlastnost `true`, můžete zadat až 32 KB textu.</span><span class="sxs-lookup"><span data-stu-id="3c995-112">If you set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`, you can enter up to 32 KB of text.</span></span> <span data-ttu-id="3c995-113"><xref:System.Windows.Forms.TextBox.Text%2A> Vlastnost lze nastavit v době návrhu pomocí okna vlastností v době běhu v kódu, nebo uživatelského vstupu v době běhu.</span><span class="sxs-lookup"><span data-stu-id="3c995-113">The <xref:System.Windows.Forms.TextBox.Text%2A> property can be set at design time with the Properties Window, at run time in code, or by user input at run time.</span></span> <span data-ttu-id="3c995-114">Aktuální obsahu textového pole můžete získat v době běhu čtením <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3c995-114">The current contents of a text box can be retrieved at run time by reading the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
 <span data-ttu-id="3c995-115">Následující příklad kódu nastaví text v ovládacím prvku za běhu.</span><span class="sxs-lookup"><span data-stu-id="3c995-115">The following code example sets text in the control at run time.</span></span> <span data-ttu-id="3c995-116">`InitializeMyControl` Postup nebude automaticky spustit; musí být volána.</span><span class="sxs-lookup"><span data-stu-id="3c995-116">The `InitializeMyControl` procedure will not execute automatically; it must be called.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3c995-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="3c995-117">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="3c995-118">Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="3c995-118">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="3c995-119">Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="3c995-119">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="3c995-120">Postupy: Vytvoření textového pole určeného jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="3c995-120">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="3c995-121">Postupy: Vkládání uvozovek do řetězce</span><span class="sxs-lookup"><span data-stu-id="3c995-121">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="3c995-122">Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="3c995-122">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="3c995-123">Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="3c995-123">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="3c995-124">Ovládací prvek TextBox</span><span class="sxs-lookup"><span data-stu-id="3c995-124">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
