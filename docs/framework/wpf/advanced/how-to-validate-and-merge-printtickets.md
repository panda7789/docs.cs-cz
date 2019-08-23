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
ms.openlocfilehash: 9e5242c07179501e6b39840a36f8dd6364d65b84
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918349"
---
# <a name="how-to-validate-and-merge-printtickets"></a><span data-ttu-id="0781b-102">Postupy: Ověření a sloučení PrintTickets</span><span class="sxs-lookup"><span data-stu-id="0781b-102">How to: Validate and Merge PrintTickets</span></span>
<span data-ttu-id="0781b-103">Schéma tisku zahrnuje flexibilní a rozšiřitelnost <xref:System.Printing.PrintCapabilities> a <xref:System.Printing.PrintTicket> prvky. [](https://go.microsoft.com/fwlink/?LinkId=186397) [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0781b-103">The [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [Print Schema](https://go.microsoft.com/fwlink/?LinkId=186397) includes the flexible and extensible <xref:System.Printing.PrintCapabilities> and <xref:System.Printing.PrintTicket> elements.</span></span> <span data-ttu-id="0781b-104">Předchozí rozepisuje možnosti tiskového zařízení a druhého nastavení určují, jak by mělo zařízení používat tyto možnosti s ohledem na konkrétní posloupnost dokumentů, jednotlivé dokumenty nebo jednotlivé stránky.</span><span class="sxs-lookup"><span data-stu-id="0781b-104">The former itemizes the capabilities of a print device and the latter specifies how the device should use those capabilities with respect to a particular sequence of documents, individual document, or individual page.</span></span>  
  
 <span data-ttu-id="0781b-105">Typická posloupnost úloh pro aplikaci, která podporuje tisk, by byla následující.</span><span class="sxs-lookup"><span data-stu-id="0781b-105">A typical sequence of tasks for an application that supports printing would be as follows.</span></span>  
  
1. <span data-ttu-id="0781b-106">Určete schopnosti tiskárny.</span><span class="sxs-lookup"><span data-stu-id="0781b-106">Determine a printer's capabilities.</span></span>  
  
2. <span data-ttu-id="0781b-107">Nakonfigurujte, <xref:System.Printing.PrintTicket> aby se tyto možnosti používaly.</span><span class="sxs-lookup"><span data-stu-id="0781b-107">Configure a <xref:System.Printing.PrintTicket> to use those capabilities.</span></span>  
  
3. <span data-ttu-id="0781b-108"><xref:System.Printing.PrintTicket>Ověřte.</span><span class="sxs-lookup"><span data-stu-id="0781b-108">Validate the <xref:System.Printing.PrintTicket>.</span></span>  
  
 <span data-ttu-id="0781b-109">Tento článek ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="0781b-109">This article shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0781b-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="0781b-110">Example</span></span>  
 <span data-ttu-id="0781b-111">V následujícím příkladu vás zajímá pouze to, jestli tiskárna podporuje oboustranný tisk – oboustranný tisk.</span><span class="sxs-lookup"><span data-stu-id="0781b-111">In the simple example below, we are interested only in whether a printer can support duplexing — two-sided printing.</span></span> <span data-ttu-id="0781b-112">Hlavní kroky jsou následující.</span><span class="sxs-lookup"><span data-stu-id="0781b-112">The major steps are as follows.</span></span>  
  
1. <span data-ttu-id="0781b-113"><xref:System.Printing.PrintCapabilities> Získat objekt<xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> s metodou.</span><span class="sxs-lookup"><span data-stu-id="0781b-113">Get a <xref:System.Printing.PrintCapabilities> object with the <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method.</span></span>  
  
2. <span data-ttu-id="0781b-114">Otestujte přítomnost požadované schopnosti.</span><span class="sxs-lookup"><span data-stu-id="0781b-114">Test for the presence of the capability you want.</span></span> <span data-ttu-id="0781b-115">V následujícím příkladu testujeme <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> vlastnost <xref:System.Printing.PrintCapabilities> objektu pro přítomnost možnosti tisku na obou stranách listu papíru s "otáčením stránky" podél pravé strany listu.</span><span class="sxs-lookup"><span data-stu-id="0781b-115">In the example below, we test the <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> property of the <xref:System.Printing.PrintCapabilities> object for the presence of the capability of printing on both sides of a sheet of paper with the "page turning" along the long side of the sheet.</span></span> <span data-ttu-id="0781b-116">Vzhledem <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> k tomu, že `Contains` je kolekce, používáme <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>metodu.</span><span class="sxs-lookup"><span data-stu-id="0781b-116">Since <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> is a collection, we use the `Contains` method of <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="0781b-117">Tento krok není nezbytně nezbytný.</span><span class="sxs-lookup"><span data-stu-id="0781b-117">This step is not strictly necessary.</span></span> <span data-ttu-id="0781b-118"><xref:System.Printing.PrintTicket> Níže uvedená <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> metoda zkontroluje všechny požadavky v s funkcemi tiskárny.</span><span class="sxs-lookup"><span data-stu-id="0781b-118">The <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method used below will check each request in the <xref:System.Printing.PrintTicket> against the capabilities of the printer.</span></span> <span data-ttu-id="0781b-119">Pokud není požadovaná schopnost tiskárny podporována, ovladač tiskárny nahradí alternativní požadavek <xref:System.Printing.PrintTicket> vrácený metodou.</span><span class="sxs-lookup"><span data-stu-id="0781b-119">If the requested capability is not supported by printer, the printer driver will substitute an alternative request in the <xref:System.Printing.PrintTicket> returned by the method.</span></span>  
  
3. <span data-ttu-id="0781b-120">Pokud tiskárna podporuje duplexní režim, vzorový kód vytvoří a <xref:System.Printing.PrintTicket> požádá o oboustranný přenos.</span><span class="sxs-lookup"><span data-stu-id="0781b-120">If the printer supports duplexing, the sample code creates a <xref:System.Printing.PrintTicket> that asks for duplexing.</span></span> <span data-ttu-id="0781b-121">Aplikace ale neurčuje všechna možná nastavení tiskárny, která jsou k dispozici v <xref:System.Printing.PrintTicket> elementu.</span><span class="sxs-lookup"><span data-stu-id="0781b-121">But the application does not specify every possible printer setting available in the <xref:System.Printing.PrintTicket> element.</span></span> <span data-ttu-id="0781b-122">To by bylo wasteful programátora i času programu.</span><span class="sxs-lookup"><span data-stu-id="0781b-122">That would be wasteful of both programmer and program time.</span></span> <span data-ttu-id="0781b-123">Místo toho kód nastaví pouze duplexní požadavek a pak ho sloučí <xref:System.Printing.PrintTicket> s existujícím, plně nakonfigurovaným a <xref:System.Printing.PrintTicket>ověřeným, v tomto případě jako výchozí nastavení <xref:System.Printing.PrintTicket>uživatele.</span><span class="sxs-lookup"><span data-stu-id="0781b-123">Instead, the code sets only the duplexing request and then merges this <xref:System.Printing.PrintTicket> with an existing, fully configured and validated, <xref:System.Printing.PrintTicket>, in this case, the user's default <xref:System.Printing.PrintTicket>.</span></span>  
  
4. <span data-ttu-id="0781b-124">Proto ukázka volá <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> metodu pro sloučení nového, <xref:System.Printing.PrintTicket> minimálního s výchozím nastavením <xref:System.Printing.PrintTicket>uživatele.</span><span class="sxs-lookup"><span data-stu-id="0781b-124">Accordingly, the sample calls the <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method to merge the new, minimal, <xref:System.Printing.PrintTicket> with the user's default <xref:System.Printing.PrintTicket>.</span></span> <span data-ttu-id="0781b-125">Vrátí <xref:System.Printing.ValidationResult> , který obsahuje nový <xref:System.Printing.PrintTicket> jako jednu z jeho vlastností.</span><span class="sxs-lookup"><span data-stu-id="0781b-125">This returns a <xref:System.Printing.ValidationResult> that includes the new <xref:System.Printing.PrintTicket> as one of its properties.</span></span>  
  
5. <span data-ttu-id="0781b-126">Ukázka potom testuje, zda nové <xref:System.Printing.PrintTicket> požadavky přibyly duplexní.</span><span class="sxs-lookup"><span data-stu-id="0781b-126">The sample then tests that the new <xref:System.Printing.PrintTicket> requests duplexing.</span></span> <span data-ttu-id="0781b-127">V takovém případě ukázka vytvoří nový výchozí tiskový lístek pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="0781b-127">If it does, then the sample makes it the new default print ticket for the user.</span></span> <span data-ttu-id="0781b-128">Pokud byl krok 2 výše popsaný a tiskárna nepodporovala oboustranně, pak test by byl výsledkem `false`.</span><span class="sxs-lookup"><span data-stu-id="0781b-128">If step 2 above had been left out and the printer did not support duplexing along the long side, then the test would have resulted in `false`.</span></span> <span data-ttu-id="0781b-129">(Viz poznámka výše.)</span><span class="sxs-lookup"><span data-stu-id="0781b-129">(See the note above.)</span></span>  
  
6. <span data-ttu-id="0781b-130">Posledním významným krokem je potvrzení změny <xref:System.Printing.PrintQueue.UserPrintTicket%2A> vlastnosti <xref:System.Printing.PrintQueue> <xref:System.Printing.PrintQueue.Commit%2A> metody s metodou.</span><span class="sxs-lookup"><span data-stu-id="0781b-130">The last significant step is to commit the change to the <xref:System.Printing.PrintQueue.UserPrintTicket%2A> property of the <xref:System.Printing.PrintQueue> with the <xref:System.Printing.PrintQueue.Commit%2A> method.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 <span data-ttu-id="0781b-131">Aby bylo možné rychle otestovat tento příklad, zbývající část je uvedena níže.</span><span class="sxs-lookup"><span data-stu-id="0781b-131">So that you can quickly test this example, the remainder of it is presented below.</span></span> <span data-ttu-id="0781b-132">Vytvořte projekt a obor názvů a vložte oba fragmenty kódu v tomto článku do bloku oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0781b-132">Create a project and a namespace and then paste both the code snippets in this article into the namespace block.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a><span data-ttu-id="0781b-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0781b-133">See also</span></span>

- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [<span data-ttu-id="0781b-134">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="0781b-134">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="0781b-135">Přehled tisku</span><span class="sxs-lookup"><span data-stu-id="0781b-135">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="0781b-136">Tisk schématu</span><span class="sxs-lookup"><span data-stu-id="0781b-136">Print Schema</span></span>](https://go.microsoft.com/fwlink/?LinkId=186397)
