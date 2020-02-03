---
title: 'Postupy: tisk vícestránkového textového souboru'
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
ms.openlocfilehash: 51e30706bb7693988d611701d013792c82dccd0b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740658"
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a><span data-ttu-id="1dee2-102">Postupy: Tisk vícestránkového textového souboru ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1dee2-102">How to: Print a Multi-Page Text File in Windows Forms</span></span>
<span data-ttu-id="1dee2-103">Pro aplikace založené na systému Windows je velmi běžné tisknout text.</span><span class="sxs-lookup"><span data-stu-id="1dee2-103">It is very common for Windows-based applications to print text.</span></span> <span data-ttu-id="1dee2-104">Třída <xref:System.Drawing.Graphics> poskytuje metody pro kreslení objektů (grafika nebo text) do zařízení, jako je například obrazovka nebo tiskárna.</span><span class="sxs-lookup"><span data-stu-id="1dee2-104">The <xref:System.Drawing.Graphics> class provides methods for drawing objects (graphics or text) to a device, such as a screen or printer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1dee2-105"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> metody <xref:System.Windows.Forms.TextRenderer> nejsou podporovány pro tisk.</span><span class="sxs-lookup"><span data-stu-id="1dee2-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of <xref:System.Windows.Forms.TextRenderer> are not supported for printing.</span></span> <span data-ttu-id="1dee2-106">Vždy byste měli použít <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics>, jak je znázorněno v následujícím příkladu kódu pro vykreslení textu pro účely tisku.</span><span class="sxs-lookup"><span data-stu-id="1dee2-106">You should always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of <xref:System.Drawing.Graphics>, as shown in the following code example, to draw text for printing purposes.</span></span>  
  
### <a name="to-print-text"></a><span data-ttu-id="1dee2-107">Postup tisku textu</span><span class="sxs-lookup"><span data-stu-id="1dee2-107">To print text</span></span>  
  
1. <span data-ttu-id="1dee2-108">Přidejte do formuláře komponentu <xref:System.Drawing.Printing.PrintDocument> a řetězec.</span><span class="sxs-lookup"><span data-stu-id="1dee2-108">Add a <xref:System.Drawing.Printing.PrintDocument> component and a string to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2. <span data-ttu-id="1dee2-109">Při tisku dokumentu nastavte vlastnost <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> na dokument, který chcete vytisknout, a otevřete a přečtěte si obsah dokumentů do řetězce, který jste přidali dříve.</span><span class="sxs-lookup"><span data-stu-id="1dee2-109">If printing a document, set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the documents contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3. <span data-ttu-id="1dee2-110">V obslužné rutině události <xref:System.Drawing.Printing.PrintDocument.PrintPage> použijte vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> třídy <xref:System.Drawing.Printing.PrintPageEventArgs> a obsah dokumentu pro výpočet délky řádku a řádků na stránku.</span><span class="sxs-lookup"><span data-stu-id="1dee2-110">In the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the document contents to calculate line length and lines per page.</span></span> <span data-ttu-id="1dee2-111">Po vykreslení každé stránky zkontrolujte, zda se jedná o poslední stránku, a nastavte vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> <xref:System.Drawing.Printing.PrintPageEventArgs> odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="1dee2-111">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="1dee2-112">Událost <xref:System.Drawing.Printing.PrintDocument.PrintPage> je vyvolána, dokud není <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> `false`.</span><span class="sxs-lookup"><span data-stu-id="1dee2-112">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="1dee2-113">Také se ujistěte, že je událost <xref:System.Drawing.Printing.PrintDocument.PrintPage> spojena s metodou zpracování události.</span><span class="sxs-lookup"><span data-stu-id="1dee2-113">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
     <span data-ttu-id="1dee2-114">V následujícím příkladu kódu slouží obslužná rutina události k tisku obsahu souboru "testPage. txt" ve stejném písmu, které je použito ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="1dee2-114">In the following code example, the event handler is used to print the contents of the "testPage.txt" file in the same font as is used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="1dee2-115">Zavolejte metodu <xref:System.Drawing.Printing.PrintDocument.Print%2A> pro vyvolání události <xref:System.Drawing.Printing.PrintDocument.PrintPage>.</span><span class="sxs-lookup"><span data-stu-id="1dee2-115">Call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to raise the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="1dee2-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="1dee2-116">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1dee2-117">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1dee2-117">Compiling the Code</span></span>  
 <span data-ttu-id="1dee2-118">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="1dee2-118">This example requires:</span></span>  
  
- <span data-ttu-id="1dee2-119">Textový soubor s názvem testPage. txt obsahující text, který se má vytisknout, umístěný v kořenové složce jednotky C:\\.</span><span class="sxs-lookup"><span data-stu-id="1dee2-119">A text file named testPage.txt containing the text to print, located in the root of drive C:\\.</span></span> <span data-ttu-id="1dee2-120">Upravte kód pro tisk jiného souboru.</span><span class="sxs-lookup"><span data-stu-id="1dee2-120">Edit the code to print a different file.</span></span>  
  
- <span data-ttu-id="1dee2-121">Odkazy na sestavení System, System. Windows. Forms, System. Drawing.</span><span class="sxs-lookup"><span data-stu-id="1dee2-121">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
- <span data-ttu-id="1dee2-122">Informace o tom, jak tento příklad sestavit z příkazového řádku pro Visual Basic C#nebo vizuál, najdete v tématu [sestavování z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo při [sestavování z příkazového řádku pomocí CSc. exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="1dee2-122">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="1dee2-123">Tento příklad můžete vytvořit také v aplikaci Visual Studio vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="1dee2-123">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dee2-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="1dee2-124">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [<span data-ttu-id="1dee2-125">Podpora tisku v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1dee2-125">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
