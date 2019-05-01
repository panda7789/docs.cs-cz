---
title: Podpora tisku ve Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- forms [Windows Forms], printing (using designer)
- printing [Windows Forms], Windows Forms, support
- printing [Windows Forms], print support
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
ms.openlocfilehash: 8e008f2cb4b2f32cdba676e68d9fd790530e2b06
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011845"
---
# <a name="windows-forms-print-support"></a><span data-ttu-id="7cd2a-102">Podpora tisku ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7cd2a-102">Windows Forms Print Support</span></span>
<span data-ttu-id="7cd2a-103">Tisk ve Windows Forms se primárně skládá z použití [PrintDocument – komponenta](../controls/printdocument-component-windows-forms.md) komponenty, aby uživatelům tisknout a [printpreviewdialog – ovládací prvek](../controls/printpreviewdialog-control-windows-forms.md) ovládacího prvku, [PrintDialog Komponenta](../controls/printdialog-component-windows-forms.md) a [PageSetupDialog – komponenta](../controls/pagesetupdialog-component-windows-forms.md) součásti známému grafické rozhraní poskytovat Uživatelé zvyklí operačního systému Windows.</span><span class="sxs-lookup"><span data-stu-id="7cd2a-103">Printing in Windows Forms consists primarily of using the [PrintDocument Component](../controls/printdocument-component-windows-forms.md) component to enable the user to print, and the [PrintPreviewDialog Control](../controls/printpreviewdialog-control-windows-forms.md) control, [PrintDialog Component](../controls/printdialog-component-windows-forms.md) and [PageSetupDialog Component](../controls/pagesetupdialog-component-windows-forms.md) components to provide a familiar graphical interface to users accustomed to the Windows operating system.</span></span>  
  
 <span data-ttu-id="7cd2a-104">Obvykle vytvoříte novou instanci třídy <xref:System.Drawing.Printing.PrintDocument> komponenty, nastavte vlastnosti, které popisují, jak vytisknout pomocí <xref:System.Drawing.Printing.PrinterSettings> a <xref:System.Drawing.Printing.PageSettings> třídy a volání <xref:System.Drawing.Printing.PrintDocument.Print%2A> metoda ve skutečnosti vytisknout dokument.</span><span class="sxs-lookup"><span data-stu-id="7cd2a-104">Typically, you create a new instance of the <xref:System.Drawing.Printing.PrintDocument> component, set the properties that describe what to print using the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to actually print the document.</span></span>  
  
 <span data-ttu-id="7cd2a-105">V průběhu tisk z aplikace založené na Windows <xref:System.Drawing.Printing.PrintDocument> komponenty zobrazí přerušení tisku dialogové okno s které uživatele upozorní na to, že dochází k tisku a umožňují tiskové úlohy budou zrušeny.</span><span class="sxs-lookup"><span data-stu-id="7cd2a-105">During the course of printing from a Windows-based application, the <xref:System.Drawing.Printing.PrintDocument> component will show an abort print dialog box to alert users to the fact that printing is occurring and to allow the print job to be canceled.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7cd2a-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="7cd2a-106">In This Section</span></span>  
 [<span data-ttu-id="7cd2a-107">Postupy: Vytvoření tiskových úloh standardní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7cd2a-107">How to: Create Standard Windows Forms Print Jobs</span></span>](how-to-create-standard-windows-forms-print-jobs.md)  
 <span data-ttu-id="7cd2a-108">Vysvětluje způsob používání <xref:System.Drawing.Printing.PrintDocument> komponenty tisknout z formuláře Windows.</span><span class="sxs-lookup"><span data-stu-id="7cd2a-108">Explains how to use the <xref:System.Drawing.Printing.PrintDocument> component to print from a Windows Form.</span></span>  
  
 [<span data-ttu-id="7cd2a-109">Postupy: Zachycení uživatelského vstupu z komponenty PrintDialog při běhu</span><span class="sxs-lookup"><span data-stu-id="7cd2a-109">How to: Capture User Input from a PrintDialog at Run Time</span></span>](how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 <span data-ttu-id="7cd2a-110">Vysvětluje, jak upravit vybrané možnosti tisku prostřednictvím kódu programu pomocí <xref:System.Windows.Forms.PrintDialog> komponenty.</span><span class="sxs-lookup"><span data-stu-id="7cd2a-110">Explains how to modify selected print options programmatically using the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="7cd2a-111">Postupy: Volba tiskáren připojených k počítači uživatele v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7cd2a-111">How to: Choose the Printers Attached to a User's Computer in Windows Forms</span></span>](how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 <span data-ttu-id="7cd2a-112">Popisuje změny tiskárny pro tisk na použití <xref:System.Windows.Forms.PrintDialog> komponentu v době běhu.</span><span class="sxs-lookup"><span data-stu-id="7cd2a-112">Describes changing the printer to print to using the <xref:System.Windows.Forms.PrintDialog> component at run time.</span></span>  
  
 [<span data-ttu-id="7cd2a-113">Postupy: Tisk grafiky ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7cd2a-113">How to: Print Graphics in Windows Forms</span></span>](how-to-print-graphics-in-windows-forms.md)  
 <span data-ttu-id="7cd2a-114">Popisuje odesílání grafiky k tiskárně.</span><span class="sxs-lookup"><span data-stu-id="7cd2a-114">Describes sending graphics to the printer.</span></span>  
  
 [<span data-ttu-id="7cd2a-115">Postupy: Tisk vícestránkového textového souboru ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7cd2a-115">How to: Print a Multi-Page Text File in Windows Forms</span></span>](how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 <span data-ttu-id="7cd2a-116">Popisuje odesílání text, který tiskárnu.</span><span class="sxs-lookup"><span data-stu-id="7cd2a-116">Describes sending text to the printer.</span></span>  
  
 [<span data-ttu-id="7cd2a-117">Postupy: Kompletní Windows Forms tiskové úlohy</span><span class="sxs-lookup"><span data-stu-id="7cd2a-117">How to: Complete Windows Forms Print Jobs</span></span>](how-to-complete-windows-forms-print-jobs.md)  
 <span data-ttu-id="7cd2a-118">Vysvětluje, jak upozornit uživatele na dokončení tiskové úlohy.</span><span class="sxs-lookup"><span data-stu-id="7cd2a-118">Explains how to alert users to the completion of a print job.</span></span>  
  
 [<span data-ttu-id="7cd2a-119">Postupy: Tisk formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="7cd2a-119">How to: Print a Windows Form</span></span>](how-to-print-a-windows-form.md)  
 <span data-ttu-id="7cd2a-120">Ukazuje, jak vytisknout kopii aktuálního formuláře.</span><span class="sxs-lookup"><span data-stu-id="7cd2a-120">Shows how to print a copy of the current form.</span></span>  
  
 [<span data-ttu-id="7cd2a-121">Postupy: Tisk ve Windows Forms pomocí náhledu tisku</span><span class="sxs-lookup"><span data-stu-id="7cd2a-121">How to: Print in Windows Forms Using Print Preview</span></span>](how-to-print-in-windows-forms-using-print-preview.md)  
 <span data-ttu-id="7cd2a-122">Ukazuje, jak používat <xref:System.Windows.Forms.PrintPreviewDialog> pro tisk dokumentu.</span><span class="sxs-lookup"><span data-stu-id="7cd2a-122">Shows how to use a <xref:System.Windows.Forms.PrintPreviewDialog> for printing a document.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7cd2a-123">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="7cd2a-123">Related Sections</span></span>  
 [<span data-ttu-id="7cd2a-124">Komponenta PrintDocument</span><span class="sxs-lookup"><span data-stu-id="7cd2a-124">PrintDocument Component</span></span>](../controls/printdocument-component-windows-forms.md)  
 <span data-ttu-id="7cd2a-125">Vysvětluje použití <xref:System.Drawing.Printing.PrintDocument> komponenty.</span><span class="sxs-lookup"><span data-stu-id="7cd2a-125">Explains usage of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 [<span data-ttu-id="7cd2a-126">Komponenta PrintDialog</span><span class="sxs-lookup"><span data-stu-id="7cd2a-126">PrintDialog Component</span></span>](../controls/printdialog-component-windows-forms.md)  
 <span data-ttu-id="7cd2a-127">Vysvětluje použití <xref:System.Windows.Forms.PrintDialog> komponenty.</span><span class="sxs-lookup"><span data-stu-id="7cd2a-127">Explains usage of the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="7cd2a-128">Ovládací prvek PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="7cd2a-128">PrintPreviewDialog Control</span></span>](../controls/printpreviewdialog-control-windows-forms.md)  
 <span data-ttu-id="7cd2a-129">Vysvětluje použití <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7cd2a-129">Explains usage of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
 [<span data-ttu-id="7cd2a-130">Komponenta PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="7cd2a-130">PageSetupDialog Component</span></span>](../controls/pagesetupdialog-component-windows-forms.md)  
 <span data-ttu-id="7cd2a-131">Vysvětluje použití <xref:System.Windows.Forms.PageSetupDialog> komponenty.</span><span class="sxs-lookup"><span data-stu-id="7cd2a-131">Explains usage of the <xref:System.Windows.Forms.PageSetupDialog> component.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="7cd2a-132">Popisuje třídy v <xref:System.Drawing.Printing> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7cd2a-132">Describes the classes in the <xref:System.Drawing.Printing> namespace.</span></span>
