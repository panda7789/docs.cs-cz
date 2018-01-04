---
title: "Postupy: Vyčíslení dílčí sady tiskové fronty"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- enumerating [WPF], subset of print queues
- print queues [WPF], enumerating subset of
ms.assetid: cc4a1b5b-d46f-4c5e-bc26-22c226e4bee0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 397ec40e2d8a0694e208296593687e9268546fc7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enumerate-a-subset-of-print-queues"></a><span data-ttu-id="05eb1-102">Postupy: Vyčíslení dílčí sady tiskové fronty</span><span class="sxs-lookup"><span data-stu-id="05eb1-102">How to: Enumerate a Subset of Print Queues</span></span>
<span data-ttu-id="05eb1-103">Běžné situace Odborníci v oblasti technologií (IT) informace o správě společnosti sadu tiskárny, jimž je vygenerovat seznam tiskárny, které mají určité charakteristické vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="05eb1-103">A common situation faced by information technology (IT) professionals managing a company-wide set of printers is to generate a list of printers having certain characteristics.</span></span> <span data-ttu-id="05eb1-104">Tato funkce poskytuje <xref:System.Printing.PrintServer.GetPrintQueues%2A> metodu <xref:System.Printing.PrintServer> objektu a <xref:System.Printing.EnumeratedPrintQueueTypes> výčtu.</span><span class="sxs-lookup"><span data-stu-id="05eb1-104">This functionality is provided by the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method of a <xref:System.Printing.PrintServer> object and the <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05eb1-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="05eb1-105">Example</span></span>  
 <span data-ttu-id="05eb1-106">V následujícím příkladu kódu začíná vytvořením pole příznaky, které určují vlastnosti tiskové fronty, které chcete zobrazit seznam.</span><span class="sxs-lookup"><span data-stu-id="05eb1-106">In the example below, the code begins by creating an array of flags that specify the characteristics of the print queues we want to list.</span></span> <span data-ttu-id="05eb1-107">V tomto příkladu jsme hledáte tiskové fronty, které jsou nainstalovány místně na tiskovém serveru a sdílejí.</span><span class="sxs-lookup"><span data-stu-id="05eb1-107">In this example, we are looking for print queues that are installed locally on the print server and are shared.</span></span> <span data-ttu-id="05eb1-108"><xref:System.Printing.EnumeratedPrintQueueTypes> Výčet obsahuje mnoho dalších možností.</span><span class="sxs-lookup"><span data-stu-id="05eb1-108">The <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration provides many other possibilities.</span></span>  
  
 <span data-ttu-id="05eb1-109">Kód vytvoří <xref:System.Printing.LocalPrintServer> objektu třída odvozená z <xref:System.Printing.PrintServer>.</span><span class="sxs-lookup"><span data-stu-id="05eb1-109">The code then creates a <xref:System.Printing.LocalPrintServer> object, a class derived from <xref:System.Printing.PrintServer>.</span></span> <span data-ttu-id="05eb1-110">Místní tiskový server je počítač, na kterém je aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="05eb1-110">The local print server is the computer on which the application is running.</span></span>  
  
 <span data-ttu-id="05eb1-111">Posledním krokem významné je předat pole do <xref:System.Printing.PrintServer.GetPrintQueues%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="05eb1-111">The last significant step is to pass the array to the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method.</span></span>  
  
 <span data-ttu-id="05eb1-112">Nakonec výsledky se zobrazí uživateli.</span><span class="sxs-lookup"><span data-stu-id="05eb1-112">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 <span data-ttu-id="05eb1-113">Tento příklad šlo rozšířit tak, že `foreach` smyčky, že kroky prostřednictvím každou tiskovou frontu provádět další blokování.</span><span class="sxs-lookup"><span data-stu-id="05eb1-113">You could extend this example by having the `foreach` loop that steps through each print queue do further screening.</span></span> <span data-ttu-id="05eb1-114">Například je může vyloučit tiskárny, které nepodporují oboustranný tisk tak, že volání smyčky každou tiskovou frontu <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> metoda a testování vrácená hodnota přítomnost duplexní.</span><span class="sxs-lookup"><span data-stu-id="05eb1-114">For example, you could screen out printers that do not support two-sided printing by having the loop call each print queue's <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method and test the returned value for the presence of duplexing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05eb1-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="05eb1-115">See Also</span></span>  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>  
 [<span data-ttu-id="05eb1-116">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="05eb1-116">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="05eb1-117">Přehled tisku</span><span class="sxs-lookup"><span data-stu-id="05eb1-117">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [<span data-ttu-id="05eb1-118">Zapisovací modul dokumentů Microsoft XPS</span><span class="sxs-lookup"><span data-stu-id="05eb1-118">Microsoft XPS Document Writer</span></span>](http://go.microsoft.com/fwlink/?LinkId=147319)
