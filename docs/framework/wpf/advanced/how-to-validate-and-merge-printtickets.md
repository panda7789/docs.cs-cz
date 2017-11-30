---
title: "Postupy: Ověření a sloučení PrintTickets"
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
helpviewer_keywords:
- merging PrintTickets [WPF]
- PrintTicket [WPF], merging
- validation of PrintTickets [WPF]
- PrintTicket [WPF], validation
ms.assetid: 4fe2d501-d0b0-4fef-86af-6ffe6c162532
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a2c2929f37895f0dee5529a5bf90f84146585032
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-validate-and-merge-printtickets"></a><span data-ttu-id="9e4d3-102">Postupy: Ověření a sloučení PrintTickets</span><span class="sxs-lookup"><span data-stu-id="9e4d3-102">How to: Validate and Merge PrintTickets</span></span>
<span data-ttu-id="9e4d3-103">[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [Tiskových schématu](http://go.microsoft.com/fwlink/?LinkId=186397) zahrnuje flexibilní a rozšiřitelný <xref:System.Printing.PrintCapabilities> a <xref:System.Printing.PrintTicket> elementy.</span><span class="sxs-lookup"><span data-stu-id="9e4d3-103">The [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [Print Schema](http://go.microsoft.com/fwlink/?LinkId=186397) includes the flexible and extensible <xref:System.Printing.PrintCapabilities> and <xref:System.Printing.PrintTicket> elements.</span></span> <span data-ttu-id="9e4d3-104">První rozepisuje možností zařízení pro tisk a druhá možnost určuje, jak má zařízení použít tyto možnosti s ohledem na konkrétní pořadí dokumenty, jednotlivý dokument nebo jednotlivých stránek.</span><span class="sxs-lookup"><span data-stu-id="9e4d3-104">The former itemizes the capabilities of a print device and the latter specifies how the device should use those capabilities with respect to a particular sequence of documents, individual document, or individual page.</span></span>  
  
 <span data-ttu-id="9e4d3-105">Typické pořadí úloh pro aplikace, která podporuje tisk vypadat takto.</span><span class="sxs-lookup"><span data-stu-id="9e4d3-105">A typical sequence of tasks for an application that supports printing would be as follows.</span></span>  
  
1.  <span data-ttu-id="9e4d3-106">Určení možnosti tiskárny.</span><span class="sxs-lookup"><span data-stu-id="9e4d3-106">Determine a printer's capabilities.</span></span>  
  
2.  <span data-ttu-id="9e4d3-107">Konfigurace <xref:System.Printing.PrintTicket> využívá tyto možnosti.</span><span class="sxs-lookup"><span data-stu-id="9e4d3-107">Configure a <xref:System.Printing.PrintTicket> to use those capabilities.</span></span>  
  
3.  <span data-ttu-id="9e4d3-108">Ověření <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="9e4d3-108">Validate the <xref:System.Printing.PrintTicket>.</span></span>  
  
 <span data-ttu-id="9e4d3-109">Tento článek ukazuje, jak to udělat.</span><span class="sxs-lookup"><span data-stu-id="9e4d3-109">This article shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e4d3-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="9e4d3-110">Example</span></span>  
 <span data-ttu-id="9e4d3-111">V jednoduchém příkladu níže jsme zajímá pouze v tom, jestli tiskárnu může podporovat duplexní – oboustranný tisk.</span><span class="sxs-lookup"><span data-stu-id="9e4d3-111">In the simple example below, we are interested only in whether a printer can support duplexing — two-sided printing.</span></span> <span data-ttu-id="9e4d3-112">Hlavní kroky jsou následující.</span><span class="sxs-lookup"><span data-stu-id="9e4d3-112">The major steps are as follows.</span></span>  
  
1.  <span data-ttu-id="9e4d3-113">Získání <xref:System.Printing.PrintCapabilities> objektu s <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="9e4d3-113">Get a <xref:System.Printing.PrintCapabilities> object with the <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method.</span></span>  
  
2.  <span data-ttu-id="9e4d3-114">Test na přítomnost schopností, které chcete.</span><span class="sxs-lookup"><span data-stu-id="9e4d3-114">Test for the presence of the capability you want.</span></span> <span data-ttu-id="9e4d3-115">V následujícím příkladu jsme testovat <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> vlastnost <xref:System.Printing.PrintCapabilities> objektu přítomnost možnosti tisku na obou stranách papíru s "stránka měnící" delší strana stylů.</span><span class="sxs-lookup"><span data-stu-id="9e4d3-115">In the example below, we test the <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> property of the <xref:System.Printing.PrintCapabilities> object for the presence of the capability of printing on both sides of a sheet of paper with the "page turning" along the long side of the sheet.</span></span> <span data-ttu-id="9e4d3-116">Vzhledem k tomu <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> je kolekce, použijeme `Contains` metodu <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="9e4d3-116">Since <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> is a collection, we use the `Contains` method of <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9e4d3-117">Tento krok není nezbytně nutné.</span><span class="sxs-lookup"><span data-stu-id="9e4d3-117">This step is not strictly necessary.</span></span> <span data-ttu-id="9e4d3-118"><xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> Metodu použitou níže zkontroluje každé žádosti <xref:System.Printing.PrintTicket> s možnostmi tiskárny.</span><span class="sxs-lookup"><span data-stu-id="9e4d3-118">The <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method used below will check each request in the <xref:System.Printing.PrintTicket> against the capabilities of the printer.</span></span> <span data-ttu-id="9e4d3-119">Pokud požadovaná funkce není podporovaná tiskárny, ovladač tiskárny budou nahrazeny alternativní požadavku v <xref:System.Printing.PrintTicket> vrácený metodou.</span><span class="sxs-lookup"><span data-stu-id="9e4d3-119">If the requested capability is not supported by printer, the printer driver will substitute an alternative request in the <xref:System.Printing.PrintTicket> returned by the method.</span></span>  
  
3.  <span data-ttu-id="9e4d3-120">Pokud je podpora duplexní, ukázkový kód vytvoří <xref:System.Printing.PrintTicket> , požádá o duplexní.</span><span class="sxs-lookup"><span data-stu-id="9e4d3-120">If the printer supports duplexing, the sample code creates a <xref:System.Printing.PrintTicket> that asks for duplexing.</span></span> <span data-ttu-id="9e4d3-121">Ale aplikace neurčuje nastavení k dispozici v každé možné tiskárny <xref:System.Printing.PrintTicket> elementu.</span><span class="sxs-lookup"><span data-stu-id="9e4d3-121">But the application does not specify every possible printer setting available in the <xref:System.Printing.PrintTicket> element.</span></span> <span data-ttu-id="9e4d3-122">Který by plýtvání programátory a program čas.</span><span class="sxs-lookup"><span data-stu-id="9e4d3-122">That would be wasteful of both programmer and program time.</span></span> <span data-ttu-id="9e4d3-123">Místo toho nastaví pouze požadavek duplexní kód a pak sloučí to <xref:System.Printing.PrintTicket> s existujícími, plně nakonfigurované a ověřit, <xref:System.Printing.PrintTicket>, v takovém případě výchozí uživatele <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="9e4d3-123">Instead, the code sets only the duplexing request and then merges this <xref:System.Printing.PrintTicket> with an existing, fully configured and validated, <xref:System.Printing.PrintTicket>, in this case, the user's default <xref:System.Printing.PrintTicket>.</span></span>  
  
4.  <span data-ttu-id="9e4d3-124">Podle toho, ukázka volá <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> metoda sloučit nové, minimální, <xref:System.Printing.PrintTicket> výchozí uživatele <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="9e4d3-124">Accordingly, the sample calls the <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method to merge the new, minimal, <xref:System.Printing.PrintTicket> with the user's default <xref:System.Printing.PrintTicket>.</span></span> <span data-ttu-id="9e4d3-125">Tento příkaz vrátí <xref:System.Printing.ValidationResult> , který obsahuje nové <xref:System.Printing.PrintTicket> jako jednu ze svých vlastností.</span><span class="sxs-lookup"><span data-stu-id="9e4d3-125">This returns a <xref:System.Printing.ValidationResult> that includes the new <xref:System.Printing.PrintTicket> as one of its properties.</span></span>  
  
5.  <span data-ttu-id="9e4d3-126">Ukázka pak testů, který nové <xref:System.Printing.PrintTicket> požadavky duplexní.</span><span class="sxs-lookup"><span data-stu-id="9e4d3-126">The sample then tests that the new <xref:System.Printing.PrintTicket> requests duplexing.</span></span> <span data-ttu-id="9e4d3-127">Pokud ano, pak ukázce je nový výchozí tiskové lístek pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="9e4d3-127">If it does, then the sample makes it the new default print ticket for the user.</span></span> <span data-ttu-id="9e4d3-128">Pokud krok 2 výše byly ponechány a tiskárny nepodporuje duplexní delší strana, pak by vznikla test `false`.</span><span class="sxs-lookup"><span data-stu-id="9e4d3-128">If step 2 above had been left out and the printer did not support duplexing along the long side, then the test would have resulted in `false`.</span></span> <span data-ttu-id="9e4d3-129">(Viz poznámka výše).</span><span class="sxs-lookup"><span data-stu-id="9e4d3-129">(See the note above.)</span></span>  
  
6.  <span data-ttu-id="9e4d3-130">Posledním krokem významné je Potvrdit změnu <xref:System.Printing.PrintQueue.UserPrintTicket%2A> vlastnost <xref:System.Printing.PrintQueue> s <xref:System.Printing.PrintQueue.Commit%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="9e4d3-130">The last significant step is to commit the change to the <xref:System.Printing.PrintQueue.UserPrintTicket%2A> property of the <xref:System.Printing.PrintQueue> with the <xref:System.Printing.PrintQueue.Commit%2A> method.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 <span data-ttu-id="9e4d3-131">Tak, aby v tomto příkladu můžete rychle otestovat, zbývající části je uveden níže.</span><span class="sxs-lookup"><span data-stu-id="9e4d3-131">So that you can quickly test this example, the remainder of it is presented below.</span></span> <span data-ttu-id="9e4d3-132">Vytvoření projektu a obor názvů a vložte fragmenty kódu v tomto článku do bloku oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="9e4d3-132">Create a project and a namespace and then paste both the code snippets in this article into the namespace block.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a><span data-ttu-id="9e4d3-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e4d3-133">See Also</span></span>  
 <xref:System.Printing.PrintCapabilities>  
 <xref:System.Printing.PrintTicket>  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>  
 [<span data-ttu-id="9e4d3-134">Dokumenty v grafickém subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="9e4d3-134">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="9e4d3-135">Tisk – přehled</span><span class="sxs-lookup"><span data-stu-id="9e4d3-135">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [<span data-ttu-id="9e4d3-136">Tisk – schéma</span><span class="sxs-lookup"><span data-stu-id="9e4d3-136">Print Schema</span></span>](http://go.microsoft.com/fwlink/?LinkId=186397)
