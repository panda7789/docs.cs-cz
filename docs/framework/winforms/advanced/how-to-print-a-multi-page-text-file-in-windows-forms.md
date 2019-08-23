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
ms.openlocfilehash: bd858279a4d8a3509a91bcd1c62fb1f61d6d2bb9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931792"
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a><span data-ttu-id="5ad04-102">Postupy: Tisk vícestránkového textového souboru v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5ad04-102">How to: Print a Multi-Page Text File in Windows Forms</span></span>
<span data-ttu-id="5ad04-103">Pro aplikace založené na systému Windows je velmi běžné tisknout text.</span><span class="sxs-lookup"><span data-stu-id="5ad04-103">It is very common for Windows-based applications to print text.</span></span> <span data-ttu-id="5ad04-104"><xref:System.Drawing.Graphics> Třída poskytuje metody pro kreslení objektů (grafika nebo text) do zařízení, jako je například obrazovka nebo tiskárna.</span><span class="sxs-lookup"><span data-stu-id="5ad04-104">The <xref:System.Drawing.Graphics> class provides methods for drawing objects (graphics or text) to a device, such as a screen or printer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5ad04-105"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> Metodypro<xref:System.Windows.Forms.TextRenderer> nejsou podporovány pro tisk.</span><span class="sxs-lookup"><span data-stu-id="5ad04-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of <xref:System.Windows.Forms.TextRenderer> are not supported for printing.</span></span> <span data-ttu-id="5ad04-106">Vždy byste měli použít <xref:System.Drawing.Graphics.DrawString%2A> <xref:System.Drawing.Graphics>metody, jak je znázorněno v následujícím příkladu kódu pro vykreslení textu pro účely tisku.</span><span class="sxs-lookup"><span data-stu-id="5ad04-106">You should always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of <xref:System.Drawing.Graphics>, as shown in the following code example, to draw text for printing purposes.</span></span>  
  
### <a name="to-print-text"></a><span data-ttu-id="5ad04-107">Postup tisku textu</span><span class="sxs-lookup"><span data-stu-id="5ad04-107">To print text</span></span>  
  
1. <span data-ttu-id="5ad04-108"><xref:System.Drawing.Printing.PrintDocument> Přidejte komponentu a řetězec do formuláře.</span><span class="sxs-lookup"><span data-stu-id="5ad04-108">Add a <xref:System.Drawing.Printing.PrintDocument> component and a string to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2. <span data-ttu-id="5ad04-109">Při tisku dokumentu nastavte <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> vlastnost na dokument, který chcete vytisknout, a otevřete a přečtěte si obsah dokumentů do řetězce, který jste přidali dříve.</span><span class="sxs-lookup"><span data-stu-id="5ad04-109">If printing a document, set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the documents contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3. <span data-ttu-id="5ad04-110">V obslužné rutině <xref:System.Drawing.Printing.PrintPageEventArgs> <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> <xref:System.Drawing.Printing.PrintDocument.PrintPage> události použijte vlastnost třídy a obsah dokumentu k výpočtu délky řádku a řádků na stránce.</span><span class="sxs-lookup"><span data-stu-id="5ad04-110">In the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the document contents to calculate line length and lines per page.</span></span> <span data-ttu-id="5ad04-111">Po vykreslení každé stránky zkontrolujte, zda se jedná o poslední stránku, a nastavte <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="5ad04-111">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="5ad04-112">Událost <xref:System.Drawing.Printing.PrintDocument.PrintPage> je vyvolána, dokud <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> není `false`.</span><span class="sxs-lookup"><span data-stu-id="5ad04-112">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="5ad04-113">Také se ujistěte, že <xref:System.Drawing.Printing.PrintDocument.PrintPage> je událost přidružená ke své metodě zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="5ad04-113">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
     <span data-ttu-id="5ad04-114">V následujícím příkladu kódu slouží obslužná rutina události k tisku obsahu souboru "testPage. txt" ve stejném písmu, které je použito ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="5ad04-114">In the following code example, the event handler is used to print the contents of the "testPage.txt" file in the same font as is used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="5ad04-115">Zavolejte metodu pro vyvolání <xref:System.Drawing.Printing.PrintDocument.PrintPage>události. <xref:System.Drawing.Printing.PrintDocument.Print%2A></span><span class="sxs-lookup"><span data-stu-id="5ad04-115">Call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to raise the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="5ad04-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="5ad04-116">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5ad04-117">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="5ad04-117">Compiling the Code</span></span>  
 <span data-ttu-id="5ad04-118">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="5ad04-118">This example requires:</span></span>  
  
- <span data-ttu-id="5ad04-119">Textový soubor s názvem testPage. txt obsahující text, který se má vytisknout, umístěný v kořenové složce jednotky C\\:.</span><span class="sxs-lookup"><span data-stu-id="5ad04-119">A text file named testPage.txt containing the text to print, located in the root of drive C:\\.</span></span> <span data-ttu-id="5ad04-120">Upravte kód pro tisk jiného souboru.</span><span class="sxs-lookup"><span data-stu-id="5ad04-120">Edit the code to print a different file.</span></span>  
  
- <span data-ttu-id="5ad04-121">Odkazy na sestavení System, System. Windows. Forms, System. Drawing.</span><span class="sxs-lookup"><span data-stu-id="5ad04-121">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
- <span data-ttu-id="5ad04-122">Informace o tom, jak tento příklad sestavit z příkazového řádku pro Visual Basic C#nebo vizuál, najdete v tématu sestavování [z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo při sestavování z [příkazového řádku pomocí CSc. exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5ad04-122">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="5ad04-123">Tento příklad můžete vytvořit také v aplikaci Visual Studio vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="5ad04-123">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ad04-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5ad04-124">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [<span data-ttu-id="5ad04-125">Podpora tisku v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5ad04-125">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
