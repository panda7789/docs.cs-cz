---
title: 'Postupy: Vyčíslení dílčí sady tiskové fronty'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- enumerating [WPF], subset of print queues
- print queues [WPF], enumerating subset of
ms.assetid: cc4a1b5b-d46f-4c5e-bc26-22c226e4bee0
ms.openlocfilehash: aae41931f012f6d34fc057fdd6ee9fc9baab6e7b
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094537"
---
# <a name="how-to-enumerate-a-subset-of-print-queues"></a><span data-ttu-id="d7267-102">Postupy: Vyčíslení dílčí sady tiskové fronty</span><span class="sxs-lookup"><span data-stu-id="d7267-102">How to: Enumerate a Subset of Print Queues</span></span>
<span data-ttu-id="d7267-103">Běžnou situací, kterou čelí odborníci na informační technologie (IT), která spravuje sadu tiskáren v rámci podnikové sítě, je vygenerovat seznam tiskáren, které mají určité charakteristiky.</span><span class="sxs-lookup"><span data-stu-id="d7267-103">A common situation faced by information technology (IT) professionals managing a company-wide set of printers is to generate a list of printers having certain characteristics.</span></span> <span data-ttu-id="d7267-104">Tato funkce je k dispozici pomocí metody <xref:System.Printing.PrintServer.GetPrintQueues%2A> objektu <xref:System.Printing.PrintServer> a výčtu <xref:System.Printing.EnumeratedPrintQueueTypes>.</span><span class="sxs-lookup"><span data-stu-id="d7267-104">This functionality is provided by the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method of a <xref:System.Printing.PrintServer> object and the <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7267-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="d7267-105">Example</span></span>  
 <span data-ttu-id="d7267-106">V následujícím příkladu kód začíná vytvořením pole příznaků, které určují charakteristiky tiskových front, které chceme zobrazit.</span><span class="sxs-lookup"><span data-stu-id="d7267-106">In the example below, the code begins by creating an array of flags that specify the characteristics of the print queues we want to list.</span></span> <span data-ttu-id="d7267-107">V tomto příkladu hledáme tiskové fronty, které jsou nainstalované místně na tiskovém serveru a jsou sdílené.</span><span class="sxs-lookup"><span data-stu-id="d7267-107">In this example, we are looking for print queues that are installed locally on the print server and are shared.</span></span> <span data-ttu-id="d7267-108">Výčet <xref:System.Printing.EnumeratedPrintQueueTypes> poskytuje mnoho dalších možností.</span><span class="sxs-lookup"><span data-stu-id="d7267-108">The <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration provides many other possibilities.</span></span>  
  
 <span data-ttu-id="d7267-109">Kód poté vytvoří objekt <xref:System.Printing.LocalPrintServer>, třídu odvozenou z <xref:System.Printing.PrintServer>.</span><span class="sxs-lookup"><span data-stu-id="d7267-109">The code then creates a <xref:System.Printing.LocalPrintServer> object, a class derived from <xref:System.Printing.PrintServer>.</span></span> <span data-ttu-id="d7267-110">Místní tiskový server je počítač, na kterém je aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="d7267-110">The local print server is the computer on which the application is running.</span></span>  
  
 <span data-ttu-id="d7267-111">Posledním krokem je předat pole do metody <xref:System.Printing.PrintServer.GetPrintQueues%2A>.</span><span class="sxs-lookup"><span data-stu-id="d7267-111">The last significant step is to pass the array to the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method.</span></span>  
  
 <span data-ttu-id="d7267-112">Nakonec se výsledky zobrazí uživateli.</span><span class="sxs-lookup"><span data-stu-id="d7267-112">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 <span data-ttu-id="d7267-113">Tento příklad můžete rozšířit tím, že zadáte `foreach` smyčkou, kterou jednotlivé tiskové fronty provedou k dalšímu prověřování.</span><span class="sxs-lookup"><span data-stu-id="d7267-113">You could extend this example by having the `foreach` loop that steps through each print queue do further screening.</span></span> <span data-ttu-id="d7267-114">Můžete například umístit tiskárny, které nepodporují oboustranný tisk, voláním každé <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> metody tiskové fronty a otestovat vrácenou hodnotu pro přítomnost duplexního přenosu.</span><span class="sxs-lookup"><span data-stu-id="d7267-114">For example, you could screen out printers that do not support two-sided printing by having the loop call each print queue's <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method and test the returned value for the presence of duplexing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7267-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7267-115">See also</span></span>

- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [<span data-ttu-id="d7267-116">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="d7267-116">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="d7267-117">Přehled tisku</span><span class="sxs-lookup"><span data-stu-id="d7267-117">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="d7267-118">Zapisovač dokumentů Microsoft XPS</span><span class="sxs-lookup"><span data-stu-id="d7267-118">Microsoft XPS Document Writer</span></span>](/windows/win32/printdocs/microsoft-xps-document-writer)
