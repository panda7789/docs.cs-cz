---
title: Tisk pomocí náhledu tisku
description: Naučte se, jak do aplikace přidat služby pro tisk ve verzi Preview pomocí ovládacího prvku model Windows Forms PrintPreviewDialog –.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
ms.openlocfilehash: abcf77db40f648df1a0cd49922bb49e5c9407811
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621610"
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a><span data-ttu-id="85055-103">Postupy: Tisk ve Windows Forms pomocí náhledu tisku</span><span class="sxs-lookup"><span data-stu-id="85055-103">How to: Print in Windows Forms Using Print Preview</span></span>
<span data-ttu-id="85055-104">Kromě tiskových služeb je velmi běžné, že model Windows Forms programování nabízí náhled tisku.</span><span class="sxs-lookup"><span data-stu-id="85055-104">It is very common in Windows Forms programming to offer print preview in addition to printing services.</span></span> <span data-ttu-id="85055-105">Snadný způsob, jak do vaší aplikace přidat služby pro tisk ve verzi Preview, je použít <xref:System.Windows.Forms.PrintPreviewDialog> ovládací prvek v kombinaci s <xref:System.Drawing.Printing.PrintDocument.PrintPage> logikou zpracování událostí pro tisk souboru.</span><span class="sxs-lookup"><span data-stu-id="85055-105">An easy way to add print preview services to your application is to use a <xref:System.Windows.Forms.PrintPreviewDialog> control in combination with the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event-handling logic for printing a file.</span></span>  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a><span data-ttu-id="85055-106">Náhled textového dokumentu pomocí ovládacího prvku PrintPreviewDialog –</span><span class="sxs-lookup"><span data-stu-id="85055-106">To preview a text document with a PrintPreviewDialog control</span></span>  
  
1. <span data-ttu-id="85055-107"><xref:System.Windows.Forms.PrintPreviewDialog> <xref:System.Drawing.Printing.PrintDocument> Do formuláře přidejte dva řetězce, a.</span><span class="sxs-lookup"><span data-stu-id="85055-107">Add a <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>, and two strings to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2. <span data-ttu-id="85055-108">Nastavte <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> vlastnost na dokument, který chcete vytisknout, a otevřete a přečtěte si obsah dokumentu do řetězce, který jste přidali dříve.</span><span class="sxs-lookup"><span data-stu-id="85055-108">Set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the document's contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3. <span data-ttu-id="85055-109">Stejně jako při tisku dokumentu <xref:System.Drawing.Printing.PrintDocument.PrintPage> použijte v obslužné rutině události <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> třídy a obsah souboru k výpočtu řádků na stránku a vykreslení obsahu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="85055-109">As you would for printing the document, in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the file contents to calculate lines per page and render the document's contents.</span></span> <span data-ttu-id="85055-110">Po vykreslení každé stránky zkontrolujte, zda se jedná o poslední stránku, a nastavte <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="85055-110">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="85055-111"><xref:System.Drawing.Printing.PrintDocument.PrintPage>Událost je vyvolána, dokud <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> není `false` .</span><span class="sxs-lookup"><span data-stu-id="85055-111">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="85055-112">Po dokončení vykreslování dokumentu resetujte řetězec, který se má vykreslit.</span><span class="sxs-lookup"><span data-stu-id="85055-112">When the document has finished rendering, reset the string to be rendered.</span></span> <span data-ttu-id="85055-113">Také se ujistěte, že <xref:System.Drawing.Printing.PrintDocument.PrintPage> je událost přidružená ke své metodě zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="85055-113">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="85055-114">Pokud jste v aplikaci nasadili tisk, možná jste už dokončili kroky 2 a 3.</span><span class="sxs-lookup"><span data-stu-id="85055-114">You may have already completed steps 2 and 3 if you have implemented printing in your application.</span></span>  
  
     <span data-ttu-id="85055-115">V následujícím příkladu kódu slouží obslužná rutina události k vytištění souboru "testPage.txt" ve stejném písmu, které je použito ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="85055-115">In the following code example, the event handler is used to print the "testPage.txt" file in the same font used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4. <span data-ttu-id="85055-116">Nastavte <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> vlastnost <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku na <xref:System.Drawing.Printing.PrintDocument> součást ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="85055-116">Set the <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintPreviewDialog> control to the <xref:System.Drawing.Printing.PrintDocument> component on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5. <span data-ttu-id="85055-117">Zavolejte <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu na <xref:System.Windows.Forms.PrintPreviewDialog> ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="85055-117">Call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method on the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="85055-118">Obvykle byste volali <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro <xref:System.Windows.Forms.Control.Click> zpracování událostí tlačítka.</span><span class="sxs-lookup"><span data-stu-id="85055-118">You would typically call <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> from the <xref:System.Windows.Forms.Control.Click> event-handling method of a button.</span></span> <span data-ttu-id="85055-119">Volání <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> vyvolává <xref:System.Drawing.Printing.PrintDocument.PrintPage> událost a vykresluje výstup do <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="85055-119">Calling <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> raises the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event and renders the output to the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="85055-120">Když uživatel klikne na ikonu tisku v dialogovém okně, <xref:System.Drawing.Printing.PrintDocument.PrintPage> událost se znovu vyvolá a pošle se výstup do tiskárny místo dialogového okna Preview.</span><span class="sxs-lookup"><span data-stu-id="85055-120">When the user clicks the print icon on the dialog, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised again, sending the output to the printer instead of the preview dialog.</span></span> <span data-ttu-id="85055-121">To je důvod, proč se řetězec resetuje na konci procesu vykreslování v kroku 3.</span><span class="sxs-lookup"><span data-stu-id="85055-121">This is why the string is reset at the end of the rendering process in step 3.</span></span>  
  
     <span data-ttu-id="85055-122">Následující příklad kódu ukazuje <xref:System.Windows.Forms.Control.Click> metodu zpracování událostí pro tlačítko ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="85055-122">The following code example shows the <xref:System.Windows.Forms.Control.Click> event-handling method for a button on the form.</span></span> <span data-ttu-id="85055-123">Tato metoda zpracování události volá metody pro čtení dokumentu a zobrazení dialogového okna Náhled tisku.</span><span class="sxs-lookup"><span data-stu-id="85055-123">This event-handling method calls the methods to read the document and show the print preview dialog.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="85055-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="85055-124">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="85055-125">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="85055-125">Compiling the Code</span></span>  
 <span data-ttu-id="85055-126">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="85055-126">This example requires:</span></span>  
  
- <span data-ttu-id="85055-127">Odkazy na sestavení System, System. Windows. Forms, System. Drawing.</span><span class="sxs-lookup"><span data-stu-id="85055-127">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85055-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85055-128">See also</span></span>

- [<span data-ttu-id="85055-129">Postupy: Tisk vícestránkového textového souboru v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="85055-129">How to: Print a Multi-Page Text File in Windows Forms</span></span>](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [<span data-ttu-id="85055-130">Podpora tisku ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="85055-130">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
- [<span data-ttu-id="85055-131">Bezpečnější tisk ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="85055-131">More Secure Printing in Windows Forms</span></span>](../more-secure-printing-in-windows-forms.md)
