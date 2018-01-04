---
title: "PrintDialog – přehled komponenty (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b90d94165de6985b43d47809ae57bfcae204f0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="printdialog-component-overview-windows-forms"></a><span data-ttu-id="84b27-102">PrintDialog – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="84b27-102">PrintDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="84b27-103">Windows Forms [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) součást je předem nakonfigurovaný dialogové okno umožňuje vybrat tiskárnu, zvolte stránky tisknout a určit další nastavení související s tiskem v aplikacích založených na systému Windows.</span><span class="sxs-lookup"><span data-stu-id="84b27-103">The Windows Forms [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) component is a pre-configured dialog box used to select a printer, choose the pages to print, and determine other print-related settings in Windows-based applications.</span></span> <span data-ttu-id="84b27-104">Použijte jako jednoduchým řešením pro tiskárny a výběr nastavení související s tiskem místo dialogové okno Vlastní konfigurace.</span><span class="sxs-lookup"><span data-stu-id="84b27-104">Use it as a simple solution for printer and print-related settings selection in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="84b27-105">Můžete povolit uživatelům tisknout mnoho částí své dokumenty: všechny vytisknout, vytisknout rozsah zvolené stránky nebo Tisk výběru.</span><span class="sxs-lookup"><span data-stu-id="84b27-105">You can enable users to print many parts of their documents: print all, print a selected page range, or print a selection.</span></span> <span data-ttu-id="84b27-106">Podle standardní dialogová okna Windows, můžete vytvořit aplikace, jehož základní funkce je dobře obeznámeni uživatele.</span><span class="sxs-lookup"><span data-stu-id="84b27-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span> <span data-ttu-id="84b27-107"><xref:System.Windows.Forms.PrintDialog> Komponenta dědí z <xref:System.Windows.Forms.CommonDialog> třídy.</span><span class="sxs-lookup"><span data-stu-id="84b27-107">The <xref:System.Windows.Forms.PrintDialog> component inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>  
  
## <a name="working-with-the-component"></a><span data-ttu-id="84b27-108">Práce s komponentou</span><span class="sxs-lookup"><span data-stu-id="84b27-108">Working with the Component</span></span>  
 <span data-ttu-id="84b27-109">Použití <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro zobrazení dialogu za běhu.</span><span class="sxs-lookup"><span data-stu-id="84b27-109">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="84b27-110">Tato součást obsahuje vlastnosti, které se vztahují k buď jednu tiskovou úlohu (<xref:System.Drawing.Printing.PrintDocument> třída) nebo nastavení jednotlivých tiskáren (<xref:System.Drawing.Printing.PrinterSettings> třídy).</span><span class="sxs-lookup"><span data-stu-id="84b27-110">This component has properties that relate to either a single print job (<xref:System.Drawing.Printing.PrintDocument> class) or the settings of an individual printer (<xref:System.Drawing.Printing.PrinterSettings> class).</span></span> <span data-ttu-id="84b27-111">Jedna z těchto, pak může sdílet více tiskáren.</span><span class="sxs-lookup"><span data-stu-id="84b27-111">Either of these, in turn, may be shared by multiple printers.</span></span>  
  
 <span data-ttu-id="84b27-112">Při jejím přidání do formuláře <xref:System.Windows.Forms.PrintDialog> součást se zobrazí na hlavním panelu v dolní části Návrhář formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="84b27-112">When it is added to a form, the <xref:System.Windows.Forms.PrintDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84b27-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="84b27-113">See Also</span></span>  
 <xref:System.Windows.Forms.PrintDialog>  
 [<span data-ttu-id="84b27-114">Komponenta PrintDialog</span><span class="sxs-lookup"><span data-stu-id="84b27-114">PrintDialog Component</span></span>](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)
