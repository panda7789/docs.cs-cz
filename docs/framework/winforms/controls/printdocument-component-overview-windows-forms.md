---
title: "PrintDocument – přehled komponenty (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 414a7972550558b40403b7f4cbfd9a49194666be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="printdocument-component-overview-windows-forms"></a><span data-ttu-id="1fac6-102">PrintDocument – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="1fac6-102">PrintDocument Component Overview (Windows Forms)</span></span>
<span data-ttu-id="1fac6-103">Windows Forms [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) komponenta se používá k nastavení vlastnosti, které popisují, co chcete vytisknout a schopnost tisk dokumentu v rámci aplikace pro systém Windows.</span><span class="sxs-lookup"><span data-stu-id="1fac6-103">The Windows Forms [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) component is used to set the properties that describe what to print and the ability to print the document within Windows-based applications.</span></span> <span data-ttu-id="1fac6-104">Může sloužit ve spojení s [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) součást, kterou je možné v ovládacím prvku všech aspektů tisk dokumentu.</span><span class="sxs-lookup"><span data-stu-id="1fac6-104">It can be used in conjunction with the [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) component to be in control of all aspects of document printing.</span></span>  
  
## <a name="working-with-the-printdocument-component"></a><span data-ttu-id="1fac6-105">Práce s komponentě PrintDocument</span><span class="sxs-lookup"><span data-stu-id="1fac6-105">Working with the PrintDocument Component</span></span>  
 <span data-ttu-id="1fac6-106">Dva hlavní scénáře, které zahrnují <xref:System.Drawing.Printing.PrintDocument> komponenty jsou:</span><span class="sxs-lookup"><span data-stu-id="1fac6-106">Two of the main scenarios that involve the <xref:System.Drawing.Printing.PrintDocument> component are:</span></span>  
  
-   <span data-ttu-id="1fac6-107">Jednoduché tiskové úlohy, jako je například tisk jednotlivých textového souboru.</span><span class="sxs-lookup"><span data-stu-id="1fac6-107">Simple print jobs, such as printing an individual text file.</span></span> <span data-ttu-id="1fac6-108">V takovém případě byste přidali <xref:System.Drawing.Printing.PrintDocument> součásti na formuláři Windows pak přidejte programovací logiky, která vytiskne soubor v <xref:System.Drawing.Printing.PrintDocument.PrintPage> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="1fac6-108">In such a case you would add the <xref:System.Drawing.Printing.PrintDocument> component to a Windows Form, then add programming logic that prints a file in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler.</span></span> <span data-ttu-id="1fac6-109">Programovací logiku by měl případech se <xref:System.Drawing.Printing.PrintDocument.Print%2A> metoda tisk dokumentu.</span><span class="sxs-lookup"><span data-stu-id="1fac6-109">The programming logic should culminate with the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to print the document.</span></span> <span data-ttu-id="1fac6-110">Tato metoda odesílá <xref:System.Drawing.Graphics> objektů, obsažených v <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> třídy tiskárny.</span><span class="sxs-lookup"><span data-stu-id="1fac6-110">This method sends a <xref:System.Drawing.Graphics> object, contained in the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class, to the printer.</span></span> <span data-ttu-id="1fac6-111">Pro příklad, který ukazuje, jak tisk dokumentu text pomocí <xref:System.Drawing.Printing.PrintDocument> součást, najdete v části [postupy: Tisk vícestránkového textového souboru v systému Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="1fac6-111">For an example that shows how to print a text document using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print a Multi-Page Text File in Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="1fac6-112">Složitější tiskové úlohy, jako je například situaci, kde můžete opakovaně použít logiku tisku, který jste napsali.</span><span class="sxs-lookup"><span data-stu-id="1fac6-112">More complex print jobs, such as a situation where you will want to reuse printing logic you have written.</span></span> <span data-ttu-id="1fac6-113">V takovém případě by odvozujete novou součást z <xref:System.Drawing.Printing.PrintDocument> součásti a přepsání (najdete v části [přepsání](~/docs/visual-basic/language-reference/modifiers/overrides.md) jazyka Visual Basic nebo [přepsat](~/docs/csharp/language-reference/keywords/override.md) pro jazyk C#) <xref:System.Drawing.Printing.PrintDocument.PrintPage> událostí.</span><span class="sxs-lookup"><span data-stu-id="1fac6-113">In such a case you would derive a new component from the <xref:System.Drawing.Printing.PrintDocument> component and override (see [Overrides](~/docs/visual-basic/language-reference/modifiers/overrides.md) for Visual Basic or [override](~/docs/csharp/language-reference/keywords/override.md) for C#) the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
 <span data-ttu-id="1fac6-114">Při jejím přidání do formuláře <xref:System.Drawing.Printing.PrintDocument> součást se zobrazí na hlavním panelu v dolní části Návrhář formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="1fac6-114">When it is added to a form, the <xref:System.Drawing.Printing.PrintDocument> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fac6-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="1fac6-115">See Also</span></span>  
 <xref:System.Drawing.Graphics>  
 <xref:System.Drawing.Printing.PrintDocument>  
 [<span data-ttu-id="1fac6-116">Podpora tisku v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1fac6-116">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [<span data-ttu-id="1fac6-117">Komponenta PrintDocument</span><span class="sxs-lookup"><span data-stu-id="1fac6-117">PrintDocument Component</span></span>](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)
