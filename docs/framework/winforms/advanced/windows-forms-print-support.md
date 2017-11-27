---
title: Podpora tisku ve Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- forms [Windows Forms], printing (using designer)
- printing [Windows Forms], Windows Forms, support
- printing [Windows Forms], print support
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 029d5ed424061807cf04446cbb10424ae20afba2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="windows-forms-print-support"></a><span data-ttu-id="1d945-102">Podpora tisku ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1d945-102">Windows Forms Print Support</span></span>
<span data-ttu-id="1d945-103">Tisk ve Windows Forms se primárně skládá z pomocí [PrintDocument – komponenta](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) komponenty, aby uživatelům tisknout a [printpreviewdialog – ovládací prvek](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md) řízení, [PrintDialog Součást](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) a [PageSetupDialog – komponenta](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) součásti, které poskytují obeznámeni grafické rozhraní uživatelům zvykli na operačním systému Windows.</span><span class="sxs-lookup"><span data-stu-id="1d945-103">Printing in Windows Forms consists primarily of using the [PrintDocument Component](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) component to enable the user to print, and the [PrintPreviewDialog Control](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md) control, [PrintDialog Component](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) and [PageSetupDialog Component](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) components to provide a familiar graphical interface to users accustomed to the Windows operating system.</span></span>  
  
 <span data-ttu-id="1d945-104">Obvykle vytvoříte novou instanci třídy <xref:System.Drawing.Printing.PrintDocument> součást, nastavte vlastnosti, které popisují, co tisknout, pomocí <xref:System.Drawing.Printing.PrinterSettings> a <xref:System.Drawing.Printing.PageSettings> třídy a volání <xref:System.Drawing.Printing.PrintDocument.Print%2A> metoda ve skutečnosti tisk dokumentu.</span><span class="sxs-lookup"><span data-stu-id="1d945-104">Typically, you create a new instance of the <xref:System.Drawing.Printing.PrintDocument> component, set the properties that describe what to print using the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to actually print the document.</span></span>  
  
 <span data-ttu-id="1d945-105">Během tisku z aplikace systému Windows <xref:System.Drawing.Printing.PrintDocument> součást zobrazí přerušení tiskové dialogové které uživatele upozorní na to, že dochází k tisku a umožnit tiskové úlohy ke zrušení.</span><span class="sxs-lookup"><span data-stu-id="1d945-105">During the course of printing from a Windows-based application, the <xref:System.Drawing.Printing.PrintDocument> component will show an abort print dialog box to alert users to the fact that printing is occurring and to allow the print job to be canceled.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1d945-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1d945-106">In This Section</span></span>  
 [<span data-ttu-id="1d945-107">Postupy: Vytvoření tiskových úloh standardní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1d945-107">How to: Create Standard Windows Forms Print Jobs</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 <span data-ttu-id="1d945-108">Vysvětluje, jak používat <xref:System.Drawing.Printing.PrintDocument> součást tisknout z formuláře Windows.</span><span class="sxs-lookup"><span data-stu-id="1d945-108">Explains how to use the <xref:System.Drawing.Printing.PrintDocument> component to print from a Windows Form.</span></span>  
  
 [<span data-ttu-id="1d945-109">Postupy: zachycení uživatelského vstupu z komponenty PrintDialog za běhu</span><span class="sxs-lookup"><span data-stu-id="1d945-109">How to: Capture User Input from a PrintDialog at Run Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 <span data-ttu-id="1d945-110">Vysvětluje, jak upravit vybranou možností tisku programově pomocí <xref:System.Windows.Forms.PrintDialog> součásti.</span><span class="sxs-lookup"><span data-stu-id="1d945-110">Explains how to modify selected print options programmatically using the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="1d945-111">Postupy: volba tiskáren připojených k počítači uživatele v systému Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1d945-111">How to: Choose the Printers Attached to a User's Computer in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 <span data-ttu-id="1d945-112">Popisuje změnu tiskárny pro tisk pomocí <xref:System.Windows.Forms.PrintDialog> součásti v době běhu.</span><span class="sxs-lookup"><span data-stu-id="1d945-112">Describes changing the printer to print to using the <xref:System.Windows.Forms.PrintDialog> component at run time.</span></span>  
  
 [<span data-ttu-id="1d945-113">Postupy: tisk grafiky ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1d945-113">How to: Print Graphics in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)  
 <span data-ttu-id="1d945-114">Popisuje odesílání grafiky na tiskárnu.</span><span class="sxs-lookup"><span data-stu-id="1d945-114">Describes sending graphics to the printer.</span></span>  
  
 [<span data-ttu-id="1d945-115">Postupy: Tisk vícestránkového textového souboru v systému Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1d945-115">How to: Print a Multi-Page Text File in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 <span data-ttu-id="1d945-116">Popisuje odesílání textu na tiskárnu.</span><span class="sxs-lookup"><span data-stu-id="1d945-116">Describes sending text to the printer.</span></span>  
  
 [<span data-ttu-id="1d945-117">Postupy: dokončení Windows Forms tiskové úlohy</span><span class="sxs-lookup"><span data-stu-id="1d945-117">How to: Complete Windows Forms Print Jobs</span></span>](../../../../docs/framework/winforms/advanced/how-to-complete-windows-forms-print-jobs.md)  
 <span data-ttu-id="1d945-118">Vysvětluje, jak upozornit uživatele na dokončení tiskových úloh.</span><span class="sxs-lookup"><span data-stu-id="1d945-118">Explains how to alert users to the completion of a print job.</span></span>  
  
 [<span data-ttu-id="1d945-119">Postupy: tisk formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="1d945-119">How to: Print a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-a-windows-form.md)  
 <span data-ttu-id="1d945-120">Ukazuje, jak chcete vytisknout kopii aktuálního formuláře.</span><span class="sxs-lookup"><span data-stu-id="1d945-120">Shows how to print a copy of the current form.</span></span>  
  
 [<span data-ttu-id="1d945-121">Postupy: tisk ve Windows Forms pomocí náhledu tisku</span><span class="sxs-lookup"><span data-stu-id="1d945-121">How to: Print in Windows Forms Using Print Preview</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md)  
 <span data-ttu-id="1d945-122">Ukazuje, jak používat <xref:System.Windows.Forms.PrintPreviewDialog> pro tisk dokumentu.</span><span class="sxs-lookup"><span data-stu-id="1d945-122">Shows how to use a <xref:System.Windows.Forms.PrintPreviewDialog> for printing a document.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1d945-123">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="1d945-123">Related Sections</span></span>  
 [<span data-ttu-id="1d945-124">PrintDocument – komponenta</span><span class="sxs-lookup"><span data-stu-id="1d945-124">PrintDocument Component</span></span>](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)  
 <span data-ttu-id="1d945-125">Popisuje použití <xref:System.Drawing.Printing.PrintDocument> součásti.</span><span class="sxs-lookup"><span data-stu-id="1d945-125">Explains usage of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 [<span data-ttu-id="1d945-126">PrintDialog – komponenta</span><span class="sxs-lookup"><span data-stu-id="1d945-126">PrintDialog Component</span></span>](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 <span data-ttu-id="1d945-127">Popisuje použití <xref:System.Windows.Forms.PrintDialog> součásti.</span><span class="sxs-lookup"><span data-stu-id="1d945-127">Explains usage of the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="1d945-128">Printpreviewdialog – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="1d945-128">PrintPreviewDialog Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 <span data-ttu-id="1d945-129">Popisuje použití <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1d945-129">Explains usage of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
 [<span data-ttu-id="1d945-130">PageSetupDialog – komponenta</span><span class="sxs-lookup"><span data-stu-id="1d945-130">PageSetupDialog Component</span></span>](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)  
 <span data-ttu-id="1d945-131">Popisuje použití <xref:System.Windows.Forms.PageSetupDialog> součásti.</span><span class="sxs-lookup"><span data-stu-id="1d945-131">Explains usage of the <xref:System.Windows.Forms.PageSetupDialog> component.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="1d945-132">Popisuje třídy v <xref:System.Drawing.Printing> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1d945-132">Describes the classes in the <xref:System.Drawing.Printing> namespace.</span></span>
