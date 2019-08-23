---
title: 'Postupy: Tisk v modelu Windows Forms pomocí náhledu tisku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
ms.openlocfilehash: 07137d03dd9a20d8eab564757618e48e25b45353
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931757"
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a><span data-ttu-id="b7630-102">Postupy: Tisk v modelu Windows Forms pomocí náhledu tisku</span><span class="sxs-lookup"><span data-stu-id="b7630-102">How to: Print in Windows Forms Using Print Preview</span></span>
<span data-ttu-id="b7630-103">Kromě tiskových služeb je velmi běžné, že model Windows Forms programování nabízí náhled tisku.</span><span class="sxs-lookup"><span data-stu-id="b7630-103">It is very common in Windows Forms programming to offer print preview in addition to printing services.</span></span> <span data-ttu-id="b7630-104">Snadný způsob, jak do vaší aplikace přidat služby pro tisk ve verzi Preview, <xref:System.Windows.Forms.PrintPreviewDialog> je použít ovládací prvek v <xref:System.Drawing.Printing.PrintDocument.PrintPage> kombinaci s logikou zpracování událostí pro tisk souboru.</span><span class="sxs-lookup"><span data-stu-id="b7630-104">An easy way to add print preview services to your application is to use a <xref:System.Windows.Forms.PrintPreviewDialog> control in combination with the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event-handling logic for printing a file.</span></span>  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a><span data-ttu-id="b7630-105">Náhled textového dokumentu pomocí ovládacího prvku PrintPreviewDialog –</span><span class="sxs-lookup"><span data-stu-id="b7630-105">To preview a text document with a PrintPreviewDialog control</span></span>  
  
1. <span data-ttu-id="b7630-106">Do formuláře přidejte <xref:System.Drawing.Printing.PrintDocument>dva řetězce ,a.<xref:System.Windows.Forms.PrintPreviewDialog></span><span class="sxs-lookup"><span data-stu-id="b7630-106">Add a <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>, and two strings to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2. <span data-ttu-id="b7630-107"><xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> Nastavte vlastnost na dokument, který chcete vytisknout, a otevřete a přečtěte si obsah dokumentu do řetězce, který jste přidali dříve.</span><span class="sxs-lookup"><span data-stu-id="b7630-107">Set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the document's contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3. <span data-ttu-id="b7630-108">Stejně jako při tisku dokumentu <xref:System.Drawing.Printing.PrintDocument.PrintPage> <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> použijte v obslužné rutině události vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> třídy a obsah souboru k výpočtu řádků na stránku a vykreslení obsahu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="b7630-108">As you would for printing the document, in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the file contents to calculate lines per page and render the document's contents.</span></span> <span data-ttu-id="b7630-109">Po vykreslení každé stránky zkontrolujte, zda se jedná o poslední stránku, a nastavte <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="b7630-109">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="b7630-110">Událost <xref:System.Drawing.Printing.PrintDocument.PrintPage> je vyvolána, dokud <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> není `false`.</span><span class="sxs-lookup"><span data-stu-id="b7630-110">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="b7630-111">Po dokončení vykreslování dokumentu resetujte řetězec, který se má vykreslit.</span><span class="sxs-lookup"><span data-stu-id="b7630-111">When the document has finished rendering, reset the string to be rendered.</span></span> <span data-ttu-id="b7630-112">Také se ujistěte, že <xref:System.Drawing.Printing.PrintDocument.PrintPage> je událost přidružená ke své metodě zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="b7630-112">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b7630-113">Pokud jste v aplikaci nasadili tisk, možná jste už dokončili kroky 2 a 3.</span><span class="sxs-lookup"><span data-stu-id="b7630-113">You may have already completed steps 2 and 3 if you have implemented printing in your application.</span></span>  
  
     <span data-ttu-id="b7630-114">V následujícím příkladu kódu slouží obslužná rutina události k vytištění souboru "testPage. txt" ve stejném písmu použitém ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="b7630-114">In the following code example, the event handler is used to print the "testPage.txt" file in the same font used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4. <span data-ttu-id="b7630-115"><xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> Nastavte vlastnost <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku<xref:System.Drawing.Printing.PrintDocument> na součást ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="b7630-115">Set the <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintPreviewDialog> control to the <xref:System.Drawing.Printing.PrintDocument> component on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5. <span data-ttu-id="b7630-116"><xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> Zavolejte metodu<xref:System.Windows.Forms.PrintPreviewDialog> na ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="b7630-116">Call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method on the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="b7630-117">Obvykle byste volali <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> <xref:System.Windows.Forms.Control.Click> metodu pro zpracování událostí tlačítka.</span><span class="sxs-lookup"><span data-stu-id="b7630-117">You would typically call <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> from the <xref:System.Windows.Forms.Control.Click> event-handling method of a button.</span></span> <span data-ttu-id="b7630-118">Volání <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> vyvolává<xref:System.Drawing.Printing.PrintDocument.PrintPage> událost a<xref:System.Windows.Forms.PrintPreviewDialog> vykresluje výstup do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b7630-118">Calling <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> raises the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event and renders the output to the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="b7630-119">Když uživatel klikne na ikonu tisku v dialogovém okně, <xref:System.Drawing.Printing.PrintDocument.PrintPage> událost se znovu vyvolá a pošle se výstup do tiskárny místo dialogového okna Preview.</span><span class="sxs-lookup"><span data-stu-id="b7630-119">When the user clicks the print icon on the dialog, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised again, sending the output to the printer instead of the preview dialog.</span></span> <span data-ttu-id="b7630-120">To je důvod, proč se řetězec resetuje na konci procesu vykreslování v kroku 3.</span><span class="sxs-lookup"><span data-stu-id="b7630-120">This is why the string is reset at the end of the rendering process in step 3.</span></span>  
  
     <span data-ttu-id="b7630-121">Následující příklad kódu ukazuje <xref:System.Windows.Forms.Control.Click> metodu zpracování událostí pro tlačítko ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="b7630-121">The following code example shows the <xref:System.Windows.Forms.Control.Click> event-handling method for a button on the form.</span></span> <span data-ttu-id="b7630-122">Tato metoda zpracování události volá metody pro čtení dokumentu a zobrazení dialogového okna Náhled tisku.</span><span class="sxs-lookup"><span data-stu-id="b7630-122">This event-handling method calls the methods to read the document and show the print preview dialog.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="b7630-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="b7630-123">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b7630-124">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="b7630-124">Compiling the Code</span></span>  
 <span data-ttu-id="b7630-125">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="b7630-125">This example requires:</span></span>  
  
- <span data-ttu-id="b7630-126">Odkazy na sestavení System, System. Windows. Forms, System. Drawing.</span><span class="sxs-lookup"><span data-stu-id="b7630-126">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7630-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7630-127">See also</span></span>

- [<span data-ttu-id="b7630-128">Postupy: Vytiskněte textový soubor s více stránkami v model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b7630-128">How to: Print a Multi-Page Text File in Windows Forms</span></span>](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [<span data-ttu-id="b7630-129">Podpora tisku v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b7630-129">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
- [<span data-ttu-id="b7630-130">Zabezpečenější tisk ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b7630-130">More Secure Printing in Windows Forms</span></span>](../more-secure-printing-in-windows-forms.md)
