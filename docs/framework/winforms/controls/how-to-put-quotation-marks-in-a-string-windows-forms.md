---
title: 'Postupy: Vkládání uvozovek do řetězce (Windows Forms)'
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
ms.openlocfilehash: 7e48e948b52cd512dba81d643fb6a42a2d90723f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113201"
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a><span data-ttu-id="84c06-102">Postupy: Vkládání uvozovek do řetězce (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="84c06-102">How to: Put Quotation Marks in a String (Windows Forms)</span></span>
<span data-ttu-id="84c06-103">Někdy můžete chtít umístit uvozovky ("") v textovém řetězci.</span><span class="sxs-lookup"><span data-stu-id="84c06-103">Sometimes you might want to place quotation marks (" ") in a string of text.</span></span> <span data-ttu-id="84c06-104">Příklad:</span><span class="sxs-lookup"><span data-stu-id="84c06-104">For example:</span></span>  
  
 <span data-ttu-id="84c06-105">Marcela řekl: "Jste, které jsou považovat!"</span><span class="sxs-lookup"><span data-stu-id="84c06-105">She said, "You deserve a treat!"</span></span>  
  
 <span data-ttu-id="84c06-106">Jako alternativu můžete použít také <xref:Microsoft.VisualBasic.ControlChars.Quote> pole jako konstanta.</span><span class="sxs-lookup"><span data-stu-id="84c06-106">As an alternative, you can also use the <xref:Microsoft.VisualBasic.ControlChars.Quote> field as a constant.</span></span>  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a><span data-ttu-id="84c06-107">Umístit uvozovek do řetězce v kódu</span><span class="sxs-lookup"><span data-stu-id="84c06-107">To place quotation marks in a string in your code</span></span>  
  
1.  <span data-ttu-id="84c06-108">V jazyce Visual Basic vložte dva uvozovek za sebou jako vložený znak uvozovek.</span><span class="sxs-lookup"><span data-stu-id="84c06-108">In Visual Basic, insert two quotation marks in a row as an embedded quotation mark.</span></span> <span data-ttu-id="84c06-109">Ve Vizuálu C# a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], vložit řídicí sekvence \\"jako vložený znak uvozovek.</span><span class="sxs-lookup"><span data-stu-id="84c06-109">In Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], insert the escape sequence \\" as an embedded quotation mark.</span></span> <span data-ttu-id="84c06-110">Například pro vytvoření předchozí řetězce, použijte následující kód.</span><span class="sxs-lookup"><span data-stu-id="84c06-110">For example, to create the preceding string, use the following code.</span></span>  
  
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
  
     <span data-ttu-id="84c06-111">-nebo-</span><span class="sxs-lookup"><span data-stu-id="84c06-111">-or-</span></span>  
  
2.  <span data-ttu-id="84c06-112">Vložte znak ASCII nebo Unicode pro znak uvozovek.</span><span class="sxs-lookup"><span data-stu-id="84c06-112">Insert the ASCII or Unicode character for a quotation mark.</span></span> <span data-ttu-id="84c06-113">V jazyce Visual Basic použijte znak ASCII (34).</span><span class="sxs-lookup"><span data-stu-id="84c06-113">In Visual Basic, use the ASCII character (34).</span></span> <span data-ttu-id="84c06-114">Ve Vizuálu C#, použijte znak Unicode (\u0022).</span><span class="sxs-lookup"><span data-stu-id="84c06-114">In Visual C#, use the Unicode character (\u0022).</span></span>  
  
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
    >  <span data-ttu-id="84c06-115">V tomto příkladu nemůžete použít \u0022, protože nelze použít univerzální název znaku, který určuje znak v základní znakové sadě.</span><span class="sxs-lookup"><span data-stu-id="84c06-115">In this example, you cannot use \u0022 because you cannot use a universal character name that designates a character in the basic character set.</span></span> <span data-ttu-id="84c06-116">V opačném případě můžete vytvářet C3851.</span><span class="sxs-lookup"><span data-stu-id="84c06-116">Otherwise, you produce C3851.</span></span> <span data-ttu-id="84c06-117">Další informace najdete v tématu [Chyba kompilátoru C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span><span class="sxs-lookup"><span data-stu-id="84c06-117">For more information, see [Compiler Error C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span></span>  
  
     <span data-ttu-id="84c06-118">-nebo-</span><span class="sxs-lookup"><span data-stu-id="84c06-118">-or-</span></span>  
  
3.  <span data-ttu-id="84c06-119">Můžete také Definujte konstantu znaku a použít ho místech.</span><span class="sxs-lookup"><span data-stu-id="84c06-119">You can also define a constant for the character, and use it where needed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="84c06-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="84c06-120">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:Microsoft.VisualBasic.ControlChars.Quote>
- [<span data-ttu-id="84c06-121">Přehled ovládacího prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="84c06-121">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="84c06-122">Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="84c06-122">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="84c06-123">Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="84c06-123">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="84c06-124">Postupy: Vytvoření textového pole určeného jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="84c06-124">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="84c06-125">Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="84c06-125">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="84c06-126">Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="84c06-126">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="84c06-127">Ovládací prvek TextBox</span><span class="sxs-lookup"><span data-stu-id="84c06-127">TextBox Control</span></span>](textbox-control-windows-forms.md)
