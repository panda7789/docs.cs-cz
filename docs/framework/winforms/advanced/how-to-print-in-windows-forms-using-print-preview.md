---
title: Tisk pomocí náhledu tisku
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
ms.openlocfilehash: 1975c902fdb56326c763f2e2fc11e381ffc7fbd3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740604"
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a><span data-ttu-id="f5664-102">Postupy: Tisk ve Windows Forms pomocí náhledu tisku</span><span class="sxs-lookup"><span data-stu-id="f5664-102">How to: Print in Windows Forms Using Print Preview</span></span>
<span data-ttu-id="f5664-103">Kromě tiskových služeb je velmi běžné, že model Windows Forms programování nabízí náhled tisku.</span><span class="sxs-lookup"><span data-stu-id="f5664-103">It is very common in Windows Forms programming to offer print preview in addition to printing services.</span></span> <span data-ttu-id="f5664-104">Snadný způsob, jak do vaší aplikace přidat služby pro tisk ve verzi Preview, je použít ovládací prvek <xref:System.Windows.Forms.PrintPreviewDialog> v kombinaci s logikou zpracování událostí <xref:System.Drawing.Printing.PrintDocument.PrintPage> pro tisk souboru.</span><span class="sxs-lookup"><span data-stu-id="f5664-104">An easy way to add print preview services to your application is to use a <xref:System.Windows.Forms.PrintPreviewDialog> control in combination with the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event-handling logic for printing a file.</span></span>  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a><span data-ttu-id="f5664-105">Náhled textového dokumentu pomocí ovládacího prvku PrintPreviewDialog –</span><span class="sxs-lookup"><span data-stu-id="f5664-105">To preview a text document with a PrintPreviewDialog control</span></span>  
  
1. <span data-ttu-id="f5664-106">Přidejte do formuláře <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>a dva řetězce.</span><span class="sxs-lookup"><span data-stu-id="f5664-106">Add a <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>, and two strings to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2. <span data-ttu-id="f5664-107">Nastavte vlastnost <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> na dokument, který chcete vytisknout, a otevřete a přečtěte si obsah dokumentu do řetězce, který jste přidali dříve.</span><span class="sxs-lookup"><span data-stu-id="f5664-107">Set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the document's contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3. <span data-ttu-id="f5664-108">Stejně jako při tisku dokumentu použijte v obslužné rutině události <xref:System.Drawing.Printing.PrintDocument.PrintPage> vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> třídy <xref:System.Drawing.Printing.PrintPageEventArgs> a obsah souboru pro výpočet řádků na stránku a vykreslení obsahu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f5664-108">As you would for printing the document, in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the file contents to calculate lines per page and render the document's contents.</span></span> <span data-ttu-id="f5664-109">Po vykreslení každé stránky zkontrolujte, zda se jedná o poslední stránku, a nastavte vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> <xref:System.Drawing.Printing.PrintPageEventArgs> odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="f5664-109">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="f5664-110">Událost <xref:System.Drawing.Printing.PrintDocument.PrintPage> je vyvolána, dokud není <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> `false`.</span><span class="sxs-lookup"><span data-stu-id="f5664-110">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="f5664-111">Po dokončení vykreslování dokumentu resetujte řetězec, který se má vykreslit.</span><span class="sxs-lookup"><span data-stu-id="f5664-111">When the document has finished rendering, reset the string to be rendered.</span></span> <span data-ttu-id="f5664-112">Také se ujistěte, že je událost <xref:System.Drawing.Printing.PrintDocument.PrintPage> spojena s metodou zpracování události.</span><span class="sxs-lookup"><span data-stu-id="f5664-112">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f5664-113">Pokud jste v aplikaci nasadili tisk, možná jste už dokončili kroky 2 a 3.</span><span class="sxs-lookup"><span data-stu-id="f5664-113">You may have already completed steps 2 and 3 if you have implemented printing in your application.</span></span>  
  
     <span data-ttu-id="f5664-114">V následujícím příkladu kódu slouží obslužná rutina události k vytištění souboru "testPage. txt" ve stejném písmu použitém ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="f5664-114">In the following code example, the event handler is used to print the "testPage.txt" file in the same font used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4. <span data-ttu-id="f5664-115">Nastavte vlastnost <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> ovládacího prvku <xref:System.Windows.Forms.PrintPreviewDialog> na součást <xref:System.Drawing.Printing.PrintDocument> na formuláři.</span><span class="sxs-lookup"><span data-stu-id="f5664-115">Set the <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintPreviewDialog> control to the <xref:System.Drawing.Printing.PrintDocument> component on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5. <span data-ttu-id="f5664-116">V ovládacím prvku <xref:System.Windows.Forms.PrintPreviewDialog> volejte metodu <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="f5664-116">Call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method on the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="f5664-117">Obvykle byste volali <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> z metody <xref:System.Windows.Forms.Control.Click> zpracování událostí tlačítka.</span><span class="sxs-lookup"><span data-stu-id="f5664-117">You would typically call <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> from the <xref:System.Windows.Forms.Control.Click> event-handling method of a button.</span></span> <span data-ttu-id="f5664-118">Volání <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> vyvolává událost <xref:System.Drawing.Printing.PrintDocument.PrintPage> a vykresluje výstup do ovládacího prvku <xref:System.Windows.Forms.PrintPreviewDialog>.</span><span class="sxs-lookup"><span data-stu-id="f5664-118">Calling <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> raises the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event and renders the output to the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="f5664-119">Když uživatel klikne na ikonu tisku v dialogovém okně, událost <xref:System.Drawing.Printing.PrintDocument.PrintPage> se znovu vyvolá a pošle se výstup do tiskárny místo dialogového okna Preview.</span><span class="sxs-lookup"><span data-stu-id="f5664-119">When the user clicks the print icon on the dialog, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised again, sending the output to the printer instead of the preview dialog.</span></span> <span data-ttu-id="f5664-120">To je důvod, proč se řetězec resetuje na konci procesu vykreslování v kroku 3.</span><span class="sxs-lookup"><span data-stu-id="f5664-120">This is why the string is reset at the end of the rendering process in step 3.</span></span>  
  
     <span data-ttu-id="f5664-121">Následující příklad kódu ukazuje metodu zpracování událostí <xref:System.Windows.Forms.Control.Click> pro tlačítko ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="f5664-121">The following code example shows the <xref:System.Windows.Forms.Control.Click> event-handling method for a button on the form.</span></span> <span data-ttu-id="f5664-122">Tato metoda zpracování události volá metody pro čtení dokumentu a zobrazení dialogového okna Náhled tisku.</span><span class="sxs-lookup"><span data-stu-id="f5664-122">This event-handling method calls the methods to read the document and show the print preview dialog.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="f5664-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5664-123">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f5664-124">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f5664-124">Compiling the Code</span></span>  
 <span data-ttu-id="f5664-125">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="f5664-125">This example requires:</span></span>  
  
- <span data-ttu-id="f5664-126">Odkazy na sestavení System, System. Windows. Forms, System. Drawing.</span><span class="sxs-lookup"><span data-stu-id="f5664-126">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5664-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5664-127">See also</span></span>

- [<span data-ttu-id="f5664-128">Postupy: Tisk vícestránkového textového souboru v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f5664-128">How to: Print a Multi-Page Text File in Windows Forms</span></span>](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [<span data-ttu-id="f5664-129">Podpora tisku v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f5664-129">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
- [<span data-ttu-id="f5664-130">Zabezpečenější tisk ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f5664-130">More Secure Printing in Windows Forms</span></span>](../more-secure-printing-in-windows-forms.md)
