---
title: 'Postupy: Vkládání uvozovek do řetězce'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- quotation marks
- TextBox control [Windows Forms], displaying quotation marks
- quotation marks [Windows Forms], adding to strings in text boxes
ms.assetid: 68bdc3f3-4177-4eab-99cd-cac17a82b515
ms.openlocfilehash: c14747291d6c41144eef97b258f852bbe14ef07d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735894"
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a><span data-ttu-id="38173-102">Postupy: Vkládání uvozovek do řetězce (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="38173-102">How to: Put Quotation Marks in a String (Windows Forms)</span></span>
<span data-ttu-id="38173-103">Někdy je vhodné umístit uvozovky ("") do textového řetězce.</span><span class="sxs-lookup"><span data-stu-id="38173-103">Sometimes you might want to place quotation marks (" ") in a string of text.</span></span> <span data-ttu-id="38173-104">Příklad:</span><span class="sxs-lookup"><span data-stu-id="38173-104">For example:</span></span>  
  
 <span data-ttu-id="38173-105">Uvedli jsme, že poslouží jako "považovat za".</span><span class="sxs-lookup"><span data-stu-id="38173-105">She said, "You deserve a treat!"</span></span>  
  
 <span data-ttu-id="38173-106">Jako alternativu můžete také použít pole <xref:Microsoft.VisualBasic.ControlChars.Quote> jako konstantu.</span><span class="sxs-lookup"><span data-stu-id="38173-106">As an alternative, you can also use the <xref:Microsoft.VisualBasic.ControlChars.Quote> field as a constant.</span></span>  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a><span data-ttu-id="38173-107">Vložení uvozovek do řetězce v kódu</span><span class="sxs-lookup"><span data-stu-id="38173-107">To place quotation marks in a string in your code</span></span>  
  
1. <span data-ttu-id="38173-108">V Visual Basic vložte do řádku dvě uvozovky jako vložený znak uvozovek.</span><span class="sxs-lookup"><span data-stu-id="38173-108">In Visual Basic, insert two quotation marks in a row as an embedded quotation mark.</span></span> <span data-ttu-id="38173-109">V vizuálu C# a vizuálu C++vložte řídicí sekvenci \\"jako vložený znak uvozovek.</span><span class="sxs-lookup"><span data-stu-id="38173-109">In Visual C# and Visual C++, insert the escape sequence \\" as an embedded quotation mark.</span></span> <span data-ttu-id="38173-110">Chcete-li například vytvořit předchozí řetězec, použijte následující kód.</span><span class="sxs-lookup"><span data-stu-id="38173-110">For example, to create the preceding string, use the following code.</span></span>  
  
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
  
     <span data-ttu-id="38173-111">-nebo-</span><span class="sxs-lookup"><span data-stu-id="38173-111">-or-</span></span>  
  
2. <span data-ttu-id="38173-112">Vložte znak ASCII nebo Unicode pro uvozovky.</span><span class="sxs-lookup"><span data-stu-id="38173-112">Insert the ASCII or Unicode character for a quotation mark.</span></span> <span data-ttu-id="38173-113">V Visual Basic použijte znak ASCII (34).</span><span class="sxs-lookup"><span data-stu-id="38173-113">In Visual Basic, use the ASCII character (34).</span></span> <span data-ttu-id="38173-114">V vizuálu C#použijte znak Unicode (\u0022).</span><span class="sxs-lookup"><span data-stu-id="38173-114">In Visual C#, use the Unicode character (\u0022).</span></span>  
  
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
    > <span data-ttu-id="38173-115">V tomto příkladu nelze použít \u0022, protože nemůžete použít univerzální název znaku, který určuje znak v základní znakové sadě.</span><span class="sxs-lookup"><span data-stu-id="38173-115">In this example, you cannot use \u0022 because you cannot use a universal character name that designates a character in the basic character set.</span></span> <span data-ttu-id="38173-116">V opačném případě budete mít C3851.</span><span class="sxs-lookup"><span data-stu-id="38173-116">Otherwise, you produce C3851.</span></span> <span data-ttu-id="38173-117">Další informace najdete v tématu [Chyba kompilátoru C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span><span class="sxs-lookup"><span data-stu-id="38173-117">For more information, see [Compiler Error C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span></span>  
  
     <span data-ttu-id="38173-118">-nebo-</span><span class="sxs-lookup"><span data-stu-id="38173-118">-or-</span></span>  
  
3. <span data-ttu-id="38173-119">Můžete také definovat konstantu pro znak a použít ho tam, kde je to potřeba.</span><span class="sxs-lookup"><span data-stu-id="38173-119">You can also define a constant for the character, and use it where needed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="38173-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38173-120">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:Microsoft.VisualBasic.ControlChars.Quote>
- [<span data-ttu-id="38173-121">Přehled ovládacího prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="38173-121">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="38173-122">Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="38173-122">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="38173-123">Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="38173-123">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="38173-124">Postupy: Vytvoření textového pole určeného jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="38173-124">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="38173-125">Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="38173-125">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="38173-126">Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="38173-126">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="38173-127">Ovládací prvek TextBox</span><span class="sxs-lookup"><span data-stu-id="38173-127">TextBox Control</span></span>](textbox-control-windows-forms.md)
