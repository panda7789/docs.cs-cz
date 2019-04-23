---
title: 'Postupy: Ověření a sloučení PrintTickets'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- merging PrintTickets [WPF]
- PrintTicket [WPF], merging
- validation of PrintTickets [WPF]
- PrintTicket [WPF], validation
ms.assetid: 4fe2d501-d0b0-4fef-86af-6ffe6c162532
ms.openlocfilehash: be8b299c99515394bc676cfd7a715cb82ac4d58c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59301149"
---
# <a name="how-to-validate-and-merge-printtickets"></a><span data-ttu-id="533f8-102">Postupy: Ověření a sloučení PrintTickets</span><span class="sxs-lookup"><span data-stu-id="533f8-102">How to: Validate and Merge PrintTickets</span></span>
<span data-ttu-id="533f8-103">[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [Tisk schématu](https://go.microsoft.com/fwlink/?LinkId=186397) zahrnuje flexibilní a rozšiřitelné <xref:System.Printing.PrintCapabilities> a <xref:System.Printing.PrintTicket> elementy.</span><span class="sxs-lookup"><span data-stu-id="533f8-103">The [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [Print Schema](https://go.microsoft.com/fwlink/?LinkId=186397) includes the flexible and extensible <xref:System.Printing.PrintCapabilities> and <xref:System.Printing.PrintTicket> elements.</span></span> <span data-ttu-id="533f8-104">Předchozí najdete výčet možností zařízení pro tisk a druhá možnost určuje, jak zařízení používali tyto možnosti s ohledem na konkrétní pořadí dokumentů, jednotlivý dokument nebo jednotlivých stránek.</span><span class="sxs-lookup"><span data-stu-id="533f8-104">The former itemizes the capabilities of a print device and the latter specifies how the device should use those capabilities with respect to a particular sequence of documents, individual document, or individual page.</span></span>  
  
 <span data-ttu-id="533f8-105">Typická posloupnost úloh pro aplikace, která podporuje tisk by měl vypadat takto.</span><span class="sxs-lookup"><span data-stu-id="533f8-105">A typical sequence of tasks for an application that supports printing would be as follows.</span></span>  
  
1. <span data-ttu-id="533f8-106">Určení možnosti tiskárny.</span><span class="sxs-lookup"><span data-stu-id="533f8-106">Determine a printer's capabilities.</span></span>  
  
2. <span data-ttu-id="533f8-107">Konfigurace <xref:System.Printing.PrintTicket> používání těchto možností.</span><span class="sxs-lookup"><span data-stu-id="533f8-107">Configure a <xref:System.Printing.PrintTicket> to use those capabilities.</span></span>  
  
3. <span data-ttu-id="533f8-108">Ověření <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="533f8-108">Validate the <xref:System.Printing.PrintTicket>.</span></span>  
  
 <span data-ttu-id="533f8-109">Tento článek ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="533f8-109">This article shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="533f8-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="533f8-110">Example</span></span>  
 <span data-ttu-id="533f8-111">V následujícím jednoduchém příkladu nás zajímají pouze určuje, zda tiskárnu může podporovat duplexní – oboustranný tisk.</span><span class="sxs-lookup"><span data-stu-id="533f8-111">In the simple example below, we are interested only in whether a printer can support duplexing — two-sided printing.</span></span> <span data-ttu-id="533f8-112">Hlavní kroky jsou následující.</span><span class="sxs-lookup"><span data-stu-id="533f8-112">The major steps are as follows.</span></span>  
  
1. <span data-ttu-id="533f8-113">Získat <xref:System.Printing.PrintCapabilities> objektu <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="533f8-113">Get a <xref:System.Printing.PrintCapabilities> object with the <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method.</span></span>  
  
2. <span data-ttu-id="533f8-114">Testovat přítomnost schopností, který chcete.</span><span class="sxs-lookup"><span data-stu-id="533f8-114">Test for the presence of the capability you want.</span></span> <span data-ttu-id="533f8-115">V následujícím příkladu testujeme <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> vlastnost <xref:System.Printing.PrintCapabilities> objektu přítomnost možnosti tisku na obou stranách list papíru s měnící"stránky" po dlouhé straně stylů.</span><span class="sxs-lookup"><span data-stu-id="533f8-115">In the example below, we test the <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> property of the <xref:System.Printing.PrintCapabilities> object for the presence of the capability of printing on both sides of a sheet of paper with the "page turning" along the long side of the sheet.</span></span> <span data-ttu-id="533f8-116">Protože <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> je kolekce, můžeme použít `Contains` metoda <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="533f8-116">Since <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> is a collection, we use the `Contains` method of <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="533f8-117">Tento krok není nezbytně nutné.</span><span class="sxs-lookup"><span data-stu-id="533f8-117">This step is not strictly necessary.</span></span> <span data-ttu-id="533f8-118"><xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> Metoda používá pod kontrola za každý požadavek <xref:System.Printing.PrintTicket> s možnostmi tiskárny.</span><span class="sxs-lookup"><span data-stu-id="533f8-118">The <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method used below will check each request in the <xref:System.Printing.PrintTicket> against the capabilities of the printer.</span></span> <span data-ttu-id="533f8-119">Pokud požadované funkce nepodporuje tiskárny, ovladač tiskárny nahradí alternativní žádosti v <xref:System.Printing.PrintTicket> vrácený metodou.</span><span class="sxs-lookup"><span data-stu-id="533f8-119">If the requested capability is not supported by printer, the printer driver will substitute an alternative request in the <xref:System.Printing.PrintTicket> returned by the method.</span></span>  
  
3. <span data-ttu-id="533f8-120">Pokud je podpora duplexní, ukázkový kód vytvoří <xref:System.Printing.PrintTicket> , která požádá o duplexní.</span><span class="sxs-lookup"><span data-stu-id="533f8-120">If the printer supports duplexing, the sample code creates a <xref:System.Printing.PrintTicket> that asks for duplexing.</span></span> <span data-ttu-id="533f8-121">Aplikace, nemůžou ale zadat nastavení k dispozici v každé možné tiskárny <xref:System.Printing.PrintTicket> elementu.</span><span class="sxs-lookup"><span data-stu-id="533f8-121">But the application does not specify every possible printer setting available in the <xref:System.Printing.PrintTicket> element.</span></span> <span data-ttu-id="533f8-122">Bylo by plýtváním programátorů i čas programu.</span><span class="sxs-lookup"><span data-stu-id="533f8-122">That would be wasteful of both programmer and program time.</span></span> <span data-ttu-id="533f8-123">Místo toho kód nastaví pouze duplexní požadavek a pak sloučí to <xref:System.Printing.PrintTicket> s existujícím, plně nakonfigurované a ověřit, <xref:System.Printing.PrintTicket>, v tomto případě výchozí uživatele <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="533f8-123">Instead, the code sets only the duplexing request and then merges this <xref:System.Printing.PrintTicket> with an existing, fully configured and validated, <xref:System.Printing.PrintTicket>, in this case, the user's default <xref:System.Printing.PrintTicket>.</span></span>  
  
4. <span data-ttu-id="533f8-124">Odpovídajícím způsobem, ukázka zavolá <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> metoda sloučit nové, minimal, <xref:System.Printing.PrintTicket> s výchozí uživatele <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="533f8-124">Accordingly, the sample calls the <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method to merge the new, minimal, <xref:System.Printing.PrintTicket> with the user's default <xref:System.Printing.PrintTicket>.</span></span> <span data-ttu-id="533f8-125">Tím se vrátí <xref:System.Printing.ValidationResult> , který obsahuje novou <xref:System.Printing.PrintTicket> jako jedna z jeho vlastností.</span><span class="sxs-lookup"><span data-stu-id="533f8-125">This returns a <xref:System.Printing.ValidationResult> that includes the new <xref:System.Printing.PrintTicket> as one of its properties.</span></span>  
  
5. <span data-ttu-id="533f8-126">Ukázka pak testy, které nový <xref:System.Printing.PrintTicket> požadavků duplexní.</span><span class="sxs-lookup"><span data-stu-id="533f8-126">The sample then tests that the new <xref:System.Printing.PrintTicket> requests duplexing.</span></span> <span data-ttu-id="533f8-127">Pokud ano, pak vzorku umožňuje nový lístek výchozí tisku pro daného uživatele.</span><span class="sxs-lookup"><span data-stu-id="533f8-127">If it does, then the sample makes it the new default print ticket for the user.</span></span> <span data-ttu-id="533f8-128">Bylo vynecháno kroku 2 výše a tiskárny nepodporuje duplexní po dlouhé straně a pak test by vznikla `false`.</span><span class="sxs-lookup"><span data-stu-id="533f8-128">If step 2 above had been left out and the printer did not support duplexing along the long side, then the test would have resulted in `false`.</span></span> <span data-ttu-id="533f8-129">(Viz poznámka výše.)</span><span class="sxs-lookup"><span data-stu-id="533f8-129">(See the note above.)</span></span>  
  
6. <span data-ttu-id="533f8-130">Je poslední významný krok k potvrzení změn do <xref:System.Printing.PrintQueue.UserPrintTicket%2A> vlastnost <xref:System.Printing.PrintQueue> s <xref:System.Printing.PrintQueue.Commit%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="533f8-130">The last significant step is to commit the change to the <xref:System.Printing.PrintQueue.UserPrintTicket%2A> property of the <xref:System.Printing.PrintQueue> with the <xref:System.Printing.PrintQueue.Commit%2A> method.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 <span data-ttu-id="533f8-131">Takže můžete rychle otestovat v tomto příkladu, zbytek je uveden níže.</span><span class="sxs-lookup"><span data-stu-id="533f8-131">So that you can quickly test this example, the remainder of it is presented below.</span></span> <span data-ttu-id="533f8-132">Vytvoření projektu a obor názvů a pak vložte fragmenty kódu v tomto článku do bloku oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="533f8-132">Create a project and a namespace and then paste both the code snippets in this article into the namespace block.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a><span data-ttu-id="533f8-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="533f8-133">See also</span></span>

- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [<span data-ttu-id="533f8-134">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="533f8-134">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="533f8-135">Přehled tisku</span><span class="sxs-lookup"><span data-stu-id="533f8-135">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="533f8-136">Tisk schématu</span><span class="sxs-lookup"><span data-stu-id="533f8-136">Print Schema</span></span>](https://go.microsoft.com/fwlink/?LinkId=186397)
