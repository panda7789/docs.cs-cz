---
title: 'Postupy: Vkládání uvozovek do řetězce (Windows Forms)'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- quotation marks
- TextBox control [Windows Forms], displaying quotation marks
- quotation marks [Windows Forms], adding to strings in text boxes
ms.assetid: 68bdc3f3-4177-4eab-99cd-cac17a82b515
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dd7c6a460f24b1406ad914e20b9113920814737c
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a><span data-ttu-id="88e9d-102">Postupy: Vkládání uvozovek do řetězce (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="88e9d-102">How to: Put Quotation Marks in a String (Windows Forms)</span></span>
<span data-ttu-id="88e9d-103">V některých případech můžete chtít umístit uvozovky ("") v textového řetězce.</span><span class="sxs-lookup"><span data-stu-id="88e9d-103">Sometimes you might want to place quotation marks (" ") in a string of text.</span></span> <span data-ttu-id="88e9d-104">Příklad:</span><span class="sxs-lookup"><span data-stu-id="88e9d-104">For example:</span></span>  
  
 <span data-ttu-id="88e9d-105">Jana uvedená "Jste si zaslouží zpracovávat!"</span><span class="sxs-lookup"><span data-stu-id="88e9d-105">She said, "You deserve a treat!"</span></span>  
  
 <span data-ttu-id="88e9d-106">Alternativně můžete také použít <xref:Microsoft.VisualBasic.ControlChars.Quote> pole jako konstanta.</span><span class="sxs-lookup"><span data-stu-id="88e9d-106">As an alternative, you can also use the <xref:Microsoft.VisualBasic.ControlChars.Quote> field as a constant.</span></span>  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a><span data-ttu-id="88e9d-107">Umístit uvozovek do řetězce v kódu</span><span class="sxs-lookup"><span data-stu-id="88e9d-107">To place quotation marks in a string in your code</span></span>  
  
1.  <span data-ttu-id="88e9d-108">V jazyce Visual Basic vložte dva znaky uvozovek za sebou jako embedded znak uvozovek.</span><span class="sxs-lookup"><span data-stu-id="88e9d-108">In Visual Basic, insert two quotation marks in a row as an embedded quotation mark.</span></span> <span data-ttu-id="88e9d-109">V jazyce Visual C# a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], vložte řídicí sekvence \\"jako embedded znak uvozovek.</span><span class="sxs-lookup"><span data-stu-id="88e9d-109">In Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], insert the escape sequence \\" as an embedded quotation mark.</span></span> <span data-ttu-id="88e9d-110">Například pokud chcete vytvořit předchozí řetězec, použijte následující kód.</span><span class="sxs-lookup"><span data-stu-id="88e9d-110">For example, to create the preceding string, use the following code.</span></span>  
  
    ```vb  
    Private Sub InsertQuote()  
       TextBox1.Text = "She said, ""You deserve a treat!"" "  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertQuote(){  
       textBox1.Text = "She said, \"You deserve a treat!\" ";  
    }  
    ```  
  
    ```cpp  
    private:  
       void InsertQuote()  
       {  
          textBox1->Text = "She said, \"You deserve a treat!\" ";  
       }  
    ```  
  
     <span data-ttu-id="88e9d-111">-nebo-</span><span class="sxs-lookup"><span data-stu-id="88e9d-111">-or-</span></span>  
  
2.  <span data-ttu-id="88e9d-112">Vložte znak ASCII nebo Unicode pro uvozovky.</span><span class="sxs-lookup"><span data-stu-id="88e9d-112">Insert the ASCII or Unicode character for a quotation mark.</span></span> <span data-ttu-id="88e9d-113">V jazyce Visual Basic použijte znaků ASCII (34).</span><span class="sxs-lookup"><span data-stu-id="88e9d-113">In Visual Basic, use the ASCII character (34).</span></span> <span data-ttu-id="88e9d-114">V jazyce Visual C#, použijte znak Unicode (\u0022).</span><span class="sxs-lookup"><span data-stu-id="88e9d-114">In Visual C#, use the Unicode character (\u0022).</span></span>  
  
    ```vb  
    Private Sub InsertAscii()  
       TextBox1.Text = "She said, " & Chr(34) & "You deserve a treat!" & Chr(34)  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertAscii(){  
       textBox1.Text = "She said, " + '\u0022' + "You deserve a treat!" + '\u0022';  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="88e9d-115">V tomto příkladu nemůžete použít \u0022, protože nelze použít název universal znak, který označuje znak v základní znakovou sadu.</span><span class="sxs-lookup"><span data-stu-id="88e9d-115">In this example, you cannot use \u0022 because you cannot use a universal character name that designates a character in the basic character set.</span></span> <span data-ttu-id="88e9d-116">Jinak vytvořit C3851.</span><span class="sxs-lookup"><span data-stu-id="88e9d-116">Otherwise, you produce C3851.</span></span> <span data-ttu-id="88e9d-117">Další informace najdete v tématu [C3851 Chyba kompilátoru](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span><span class="sxs-lookup"><span data-stu-id="88e9d-117">For more information, see [Compiler Error C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span></span>  
  
     <span data-ttu-id="88e9d-118">-nebo-</span><span class="sxs-lookup"><span data-stu-id="88e9d-118">-or-</span></span>  
  
3.  <span data-ttu-id="88e9d-119">Můžete také definovat konstanta znaku a použít ho tam, kde je potřeba.</span><span class="sxs-lookup"><span data-stu-id="88e9d-119">You can also define a constant for the character, and use it where needed.</span></span>  
  
    ```vb  
    Const quote As String = """"  
    TextBox1.Text = "She said, " & quote & "You deserve a treat!" & quote  
    ```  
  
    ```csharp  
    const string quote = "\"";  
    textBox1.Text = "She said, " + quote +  "You deserve a treat!"+ quote ;  
    ```  
  
    ```cpp  
    const String^ quote = "\"";  
    textBox1->Text = String::Concat("She said, ",  
       const_cast<String^>(quote), "You deserve a treat!",  
       const_cast<String^>(quote));  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="88e9d-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="88e9d-120">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 <xref:Microsoft.VisualBasic.ControlChars.Quote>  
 [<span data-ttu-id="88e9d-121">Přehled ovládacího prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="88e9d-121">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="88e9d-122">Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="88e9d-122">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="88e9d-123">Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="88e9d-123">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="88e9d-124">Postupy: Vytvoření textového pole určeného jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="88e9d-124">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="88e9d-125">Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="88e9d-125">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="88e9d-126">Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="88e9d-126">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="88e9d-127">Ovládací prvek TextBox</span><span class="sxs-lookup"><span data-stu-id="88e9d-127">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
