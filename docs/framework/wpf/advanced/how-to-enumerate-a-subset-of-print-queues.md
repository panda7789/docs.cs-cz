---
title: 'Postupy: Výčet podmnožiny tiskových front'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- enumerating [WPF], subset of print queues
- print queues [WPF], enumerating subset of
ms.assetid: cc4a1b5b-d46f-4c5e-bc26-22c226e4bee0
ms.openlocfilehash: adcfff0196bd0430ec1ae563fbd5489062de11f3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217182"
---
# <a name="how-to-enumerate-a-subset-of-print-queues"></a><span data-ttu-id="a5f8a-102">Postupy: Výčet podmnožiny tiskových front</span><span class="sxs-lookup"><span data-stu-id="a5f8a-102">How to: Enumerate a Subset of Print Queues</span></span>
<span data-ttu-id="a5f8a-103">Je běžné situace spojenou s rozšiřováním Odborníci v oblasti technologií (IT) informace o správě pořádaného microsoftem sadu tiskárny pro vygenerování seznamu tiskáren, které mají určité charakteristické vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a5f8a-103">A common situation faced by information technology (IT) professionals managing a company-wide set of printers is to generate a list of printers having certain characteristics.</span></span> <span data-ttu-id="a5f8a-104">Tato funkce je poskytována <xref:System.Printing.PrintServer.GetPrintQueues%2A> metodu <xref:System.Printing.PrintServer> objektu a <xref:System.Printing.EnumeratedPrintQueueTypes> výčtu.</span><span class="sxs-lookup"><span data-stu-id="a5f8a-104">This functionality is provided by the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method of a <xref:System.Printing.PrintServer> object and the <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5f8a-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="a5f8a-105">Example</span></span>  
 <span data-ttu-id="a5f8a-106">V následujícím příkladu kódu začíná tím, že vytvoříte pole příznaky určující vlastnosti tiskové fronty, které chceme seznamu.</span><span class="sxs-lookup"><span data-stu-id="a5f8a-106">In the example below, the code begins by creating an array of flags that specify the characteristics of the print queues we want to list.</span></span> <span data-ttu-id="a5f8a-107">V tomto příkladu hledáme tiskové fronty, které jsou nainstalovány místně na tiskovém serveru a sdílejí.</span><span class="sxs-lookup"><span data-stu-id="a5f8a-107">In this example, we are looking for print queues that are installed locally on the print server and are shared.</span></span> <span data-ttu-id="a5f8a-108"><xref:System.Printing.EnumeratedPrintQueueTypes> Výčet poskytuje mnoho dalších možností.</span><span class="sxs-lookup"><span data-stu-id="a5f8a-108">The <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration provides many other possibilities.</span></span>  
  
 <span data-ttu-id="a5f8a-109">Kód poté vytvoří <xref:System.Printing.LocalPrintServer> objektu, třída odvozená z <xref:System.Printing.PrintServer>.</span><span class="sxs-lookup"><span data-stu-id="a5f8a-109">The code then creates a <xref:System.Printing.LocalPrintServer> object, a class derived from <xref:System.Printing.PrintServer>.</span></span> <span data-ttu-id="a5f8a-110">Místní tiskový server je počítač, na kterém je aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="a5f8a-110">The local print server is the computer on which the application is running.</span></span>  
  
 <span data-ttu-id="a5f8a-111">Poslední významný krok je pole, které chcete předat <xref:System.Printing.PrintServer.GetPrintQueues%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a5f8a-111">The last significant step is to pass the array to the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method.</span></span>  
  
 <span data-ttu-id="a5f8a-112">A konečně výsledky se zobrazí uživateli.</span><span class="sxs-lookup"><span data-stu-id="a5f8a-112">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 <span data-ttu-id="a5f8a-113">V tomto příkladu může rozšířit tak, že `foreach` smyčku, která vás provede každou tiskovou frontu, proveďte další blokování.</span><span class="sxs-lookup"><span data-stu-id="a5f8a-113">You could extend this example by having the `foreach` loop that steps through each print queue do further screening.</span></span> <span data-ttu-id="a5f8a-114">Například jste mohli vyfiltroval tiskárny, které nepodporují oboustranný tisk tím, že volání smyčky každou tiskovou frontu <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> metoda a testování vrácené hodnoty přítomnost duplexní.</span><span class="sxs-lookup"><span data-stu-id="a5f8a-114">For example, you could screen out printers that do not support two-sided printing by having the loop call each print queue's <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method and test the returned value for the presence of duplexing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5f8a-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5f8a-115">See also</span></span>

- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [<span data-ttu-id="a5f8a-116">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="a5f8a-116">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="a5f8a-117">Přehled tisku</span><span class="sxs-lookup"><span data-stu-id="a5f8a-117">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="a5f8a-118">Zapisovací modul dokumentů Microsoft XPS</span><span class="sxs-lookup"><span data-stu-id="a5f8a-118">Microsoft XPS Document Writer</span></span>](https://go.microsoft.com/fwlink/?LinkId=147319)
