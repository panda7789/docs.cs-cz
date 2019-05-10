---
title: 'Postupy: Tisk vícestránkového textového souboru v modelu Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], printing multiple pages
- text [Windows Forms], printing Windows Forms
- Windows Forms, printing text
- printing [Windows Forms], text
ms.assetid: 362427f8-03d4-4826-b49f-60ab066ad322
ms.openlocfilehash: 07e1bb4bcdcaa99635db293f23e5ecb689b6063e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64621333"
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a><span data-ttu-id="74905-102">Postupy: Tisk vícestránkového textového souboru v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="74905-102">How to: Print a Multi-Page Text File in Windows Forms</span></span>
<span data-ttu-id="74905-103">Je velmi běžné, že aplikace založené na Windows pro tisk textu.</span><span class="sxs-lookup"><span data-stu-id="74905-103">It is very common for Windows-based applications to print text.</span></span> <span data-ttu-id="74905-104"><xref:System.Drawing.Graphics> Třída poskytuje metody pro vykreslení objektů (grafiky nebo text) na zařízení, jako je obrazovka nebo tiskárny.</span><span class="sxs-lookup"><span data-stu-id="74905-104">The <xref:System.Drawing.Graphics> class provides methods for drawing objects (graphics or text) to a device, such as a screen or printer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74905-105"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> Metody <xref:System.Windows.Forms.TextRenderer> nejsou podporovány pro tisk.</span><span class="sxs-lookup"><span data-stu-id="74905-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of <xref:System.Windows.Forms.TextRenderer> are not supported for printing.</span></span> <span data-ttu-id="74905-106">Vždycky byste měli použít <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics>, jak je znázorněno v následujícím příkladu kódu, chcete-li nakreslit text pro účely tisku.</span><span class="sxs-lookup"><span data-stu-id="74905-106">You should always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of <xref:System.Drawing.Graphics>, as shown in the following code example, to draw text for printing purposes.</span></span>  
  
### <a name="to-print-text"></a><span data-ttu-id="74905-107">Tisk textu</span><span class="sxs-lookup"><span data-stu-id="74905-107">To print text</span></span>  
  
1. <span data-ttu-id="74905-108">Přidat <xref:System.Drawing.Printing.PrintDocument> komponenty a řetězec do formuláře.</span><span class="sxs-lookup"><span data-stu-id="74905-108">Add a <xref:System.Drawing.Printing.PrintDocument> component and a string to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2. <span data-ttu-id="74905-109">Pokud tisk dokumentu, nastavte <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> vlastnost v dokumentu, který chcete vytisknout a otevřít a číst obsah dokumentů na řetězec, který jste přidali dříve.</span><span class="sxs-lookup"><span data-stu-id="74905-109">If printing a document, set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the documents contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3. <span data-ttu-id="74905-110">V <xref:System.Drawing.Printing.PrintDocument.PrintPage> obslužná rutina události, použijte <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> třída a dokument obsah k výpočtu délky a řádky na jedné stránce řádků.</span><span class="sxs-lookup"><span data-stu-id="74905-110">In the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the document contents to calculate line length and lines per page.</span></span> <span data-ttu-id="74905-111">Po jednotlivých stránkách vykreslením, zkontrolujte, zda se jedná o poslední stránku a nastavit <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="74905-111">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="74905-112"><xref:System.Drawing.Printing.PrintDocument.PrintPage> Událost se vyvolá, dokud <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> je `false`.</span><span class="sxs-lookup"><span data-stu-id="74905-112">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="74905-113">Také se ujistěte, že <xref:System.Drawing.Printing.PrintDocument.PrintPage> událost je přidružena jeho metody zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="74905-113">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
     <span data-ttu-id="74905-114">V následujícím příkladu kódu obslužné rutiny události umožňuje vytisknout obsah souboru "testPage.txt" ve stejném písma se používá ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="74905-114">In the following code example, the event handler is used to print the contents of the "testPage.txt" file in the same font as is used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="74905-115">Volání <xref:System.Drawing.Printing.PrintDocument.Print%2A> metoda k vyvolání <xref:System.Drawing.Printing.PrintDocument.PrintPage> událostí.</span><span class="sxs-lookup"><span data-stu-id="74905-115">Call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to raise the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="74905-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="74905-116">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="74905-117">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="74905-117">Compiling the Code</span></span>  
 <span data-ttu-id="74905-118">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="74905-118">This example requires:</span></span>  
  
- <span data-ttu-id="74905-119">Textový soubor s názvem testPage.txt obsahující text pro tisk, umístěn v kořenové složce jednotky C:\\.</span><span class="sxs-lookup"><span data-stu-id="74905-119">A text file named testPage.txt containing the text to print, located in the root of drive C:\\.</span></span> <span data-ttu-id="74905-120">Upravte kód pro tisk jiný soubor.</span><span class="sxs-lookup"><span data-stu-id="74905-120">Edit the code to print a different file.</span></span>  
  
- <span data-ttu-id="74905-121">Odkazy na systém, System.Windows.Forms, System.Drawing sestavení.</span><span class="sxs-lookup"><span data-stu-id="74905-121">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
- <span data-ttu-id="74905-122">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="74905-122">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="74905-123">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="74905-123">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74905-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74905-124">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [<span data-ttu-id="74905-125">Podpora tisku v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="74905-125">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
