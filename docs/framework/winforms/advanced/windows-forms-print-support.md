---
title: Podpora tisku
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- forms [Windows Forms], printing (using designer)
- printing [Windows Forms], Windows Forms, support
- printing [Windows Forms], print support
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
ms.openlocfilehash: d6e8f60db7afe2f1b04eaae6fe71aa93e5c22cae
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732489"
---
# <a name="windows-forms-print-support"></a><span data-ttu-id="2bc73-102">Podpora tisku ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2bc73-102">Windows Forms Print Support</span></span>
<span data-ttu-id="2bc73-103">Tisk v model Windows Forms se skládá hlavně z použití komponenty [komponenty PrintDocument](../controls/printdocument-component-windows-forms.md) , aby mohl uživatel tisknout, a ovládací prvek [řízení PrintPreviewDialog –](../controls/printpreviewdialog-control-windows-forms.md) , komponenty [PrintDialog komponenty](../controls/printdialog-component-windows-forms.md) a komponenty [PageSetupDialog](../controls/pagesetupdialog-component-windows-forms.md) poskytují známé grafické rozhraní pro uživatele, kteří jsou zvyklí na operační systém Windows.</span><span class="sxs-lookup"><span data-stu-id="2bc73-103">Printing in Windows Forms consists primarily of using the [PrintDocument Component](../controls/printdocument-component-windows-forms.md) component to enable the user to print, and the [PrintPreviewDialog Control](../controls/printpreviewdialog-control-windows-forms.md) control, [PrintDialog Component](../controls/printdialog-component-windows-forms.md) and [PageSetupDialog Component](../controls/pagesetupdialog-component-windows-forms.md) components to provide a familiar graphical interface to users accustomed to the Windows operating system.</span></span>  
  
 <span data-ttu-id="2bc73-104">Obvykle vytvoříte novou instanci součásti <xref:System.Drawing.Printing.PrintDocument>, nastavíte vlastnosti, které popisují, co tisknout pomocí tříd <xref:System.Drawing.Printing.PrinterSettings> a <xref:System.Drawing.Printing.PageSettings>, a zavolejte metodu <xref:System.Drawing.Printing.PrintDocument.Print%2A> pro skutečný tisk dokumentu.</span><span class="sxs-lookup"><span data-stu-id="2bc73-104">Typically, you create a new instance of the <xref:System.Drawing.Printing.PrintDocument> component, set the properties that describe what to print using the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to actually print the document.</span></span>  
  
 <span data-ttu-id="2bc73-105">V průběhu tisku z aplikace pro systém Windows bude <xref:System.Drawing.Printing.PrintDocument> komponenta zobrazovat dialogové okno přerušit tisk, aby byli uživatelé upozorněni na skutečnost, že k tisku dochází a zda se má tisková úloha zrušit.</span><span class="sxs-lookup"><span data-stu-id="2bc73-105">During the course of printing from a Windows-based application, the <xref:System.Drawing.Printing.PrintDocument> component will show an abort print dialog box to alert users to the fact that printing is occurring and to allow the print job to be canceled.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2bc73-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2bc73-106">In This Section</span></span>  
 [<span data-ttu-id="2bc73-107">Postupy: Vytváření standardních tiskových úloh modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2bc73-107">How to: Create Standard Windows Forms Print Jobs</span></span>](how-to-create-standard-windows-forms-print-jobs.md)  
 <span data-ttu-id="2bc73-108">Vysvětluje, jak používat komponentu <xref:System.Drawing.Printing.PrintDocument> k tisku z formuláře Windows Form.</span><span class="sxs-lookup"><span data-stu-id="2bc73-108">Explains how to use the <xref:System.Drawing.Printing.PrintDocument> component to print from a Windows Form.</span></span>  
  
 [<span data-ttu-id="2bc73-109">Postupy: Zachycení uživatelského vstupu z komponenty PrintDialog při běhu</span><span class="sxs-lookup"><span data-stu-id="2bc73-109">How to: Capture User Input from a PrintDialog at Run Time</span></span>](how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 <span data-ttu-id="2bc73-110">Vysvětluje, jak upravit vybrané možnosti tisku programově pomocí <xref:System.Windows.Forms.PrintDialog> komponenty.</span><span class="sxs-lookup"><span data-stu-id="2bc73-110">Explains how to modify selected print options programmatically using the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="2bc73-111">Postupy: Volba tiskáren připojených k počítači uživatele v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2bc73-111">How to: Choose the Printers Attached to a User's Computer in Windows Forms</span></span>](how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 <span data-ttu-id="2bc73-112">V této části najdete popis změny tiskárny pro tisk pomocí <xref:System.Windows.Forms.PrintDialog> komponenty v době běhu.</span><span class="sxs-lookup"><span data-stu-id="2bc73-112">Describes changing the printer to print to using the <xref:System.Windows.Forms.PrintDialog> component at run time.</span></span>  
  
 [<span data-ttu-id="2bc73-113">Postupy: Tisk grafiky v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2bc73-113">How to: Print Graphics in Windows Forms</span></span>](how-to-print-graphics-in-windows-forms.md)  
 <span data-ttu-id="2bc73-114">Popisuje odeslání grafiky na tiskárnu.</span><span class="sxs-lookup"><span data-stu-id="2bc73-114">Describes sending graphics to the printer.</span></span>  
  
 [<span data-ttu-id="2bc73-115">Postupy: Tisk vícestránkového textového souboru v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2bc73-115">How to: Print a Multi-Page Text File in Windows Forms</span></span>](how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 <span data-ttu-id="2bc73-116">Popisuje odeslání textu do tiskárny.</span><span class="sxs-lookup"><span data-stu-id="2bc73-116">Describes sending text to the printer.</span></span>  
  
 [<span data-ttu-id="2bc73-117">Postupy: Dokončení tiskových úloh modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2bc73-117">How to: Complete Windows Forms Print Jobs</span></span>](how-to-complete-windows-forms-print-jobs.md)  
 <span data-ttu-id="2bc73-118">Vysvětluje, jak upozornit uživatele na dokončení tiskové úlohy.</span><span class="sxs-lookup"><span data-stu-id="2bc73-118">Explains how to alert users to the completion of a print job.</span></span>  
  
 [<span data-ttu-id="2bc73-119">Postupy: Tisk formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="2bc73-119">How to: Print a Windows Form</span></span>](how-to-print-a-windows-form.md)  
 <span data-ttu-id="2bc73-120">Ukazuje, jak vytisknout kopii aktuálního formuláře.</span><span class="sxs-lookup"><span data-stu-id="2bc73-120">Shows how to print a copy of the current form.</span></span>  
  
 [<span data-ttu-id="2bc73-121">Postupy: Tisk v modelu Windows Forms pomocí náhledu tisku</span><span class="sxs-lookup"><span data-stu-id="2bc73-121">How to: Print in Windows Forms Using Print Preview</span></span>](how-to-print-in-windows-forms-using-print-preview.md)  
 <span data-ttu-id="2bc73-122">Ukazuje, jak použít <xref:System.Windows.Forms.PrintPreviewDialog> pro tisk dokumentu.</span><span class="sxs-lookup"><span data-stu-id="2bc73-122">Shows how to use a <xref:System.Windows.Forms.PrintPreviewDialog> for printing a document.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2bc73-123">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="2bc73-123">Related Sections</span></span>  
 [<span data-ttu-id="2bc73-124">Komponenta PrintDocument</span><span class="sxs-lookup"><span data-stu-id="2bc73-124">PrintDocument Component</span></span>](../controls/printdocument-component-windows-forms.md)  
 <span data-ttu-id="2bc73-125">Vysvětluje použití součásti <xref:System.Drawing.Printing.PrintDocument>.</span><span class="sxs-lookup"><span data-stu-id="2bc73-125">Explains usage of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 [<span data-ttu-id="2bc73-126">Komponenta PrintDialog</span><span class="sxs-lookup"><span data-stu-id="2bc73-126">PrintDialog Component</span></span>](../controls/printdialog-component-windows-forms.md)  
 <span data-ttu-id="2bc73-127">Vysvětluje použití součásti <xref:System.Windows.Forms.PrintDialog>.</span><span class="sxs-lookup"><span data-stu-id="2bc73-127">Explains usage of the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="2bc73-128">Ovládací prvek PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="2bc73-128">PrintPreviewDialog Control</span></span>](../controls/printpreviewdialog-control-windows-forms.md)  
 <span data-ttu-id="2bc73-129">Vysvětluje použití ovládacího prvku <xref:System.Windows.Forms.PrintPreviewDialog>.</span><span class="sxs-lookup"><span data-stu-id="2bc73-129">Explains usage of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
 [<span data-ttu-id="2bc73-130">Komponenta PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="2bc73-130">PageSetupDialog Component</span></span>](../controls/pagesetupdialog-component-windows-forms.md)  
 <span data-ttu-id="2bc73-131">Vysvětluje použití součásti <xref:System.Windows.Forms.PageSetupDialog>.</span><span class="sxs-lookup"><span data-stu-id="2bc73-131">Explains usage of the <xref:System.Windows.Forms.PageSetupDialog> component.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="2bc73-132">Popisuje třídy v oboru názvů <xref:System.Drawing.Printing>.</span><span class="sxs-lookup"><span data-stu-id="2bc73-132">Describes the classes in the <xref:System.Drawing.Printing> namespace.</span></span>
