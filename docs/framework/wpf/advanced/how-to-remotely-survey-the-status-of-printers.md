---
title: 'Postupy: Vzdálené zjištění stavu tiskáren'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- surveying printer status remotely [WPF]
- printer status [WPF], surveying remotely
- remotely surveying printer status [WPF]
- status [WPF], printers [WPF], surveying remotely
ms.assetid: d6324759-8292-4c23-9584-9c708887dc94
ms.openlocfilehash: eca1720aea1620683ebc9ed08b47a0f5625da9d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545968"
---
# <a name="how-to-remotely-survey-the-status-of-printers"></a><span data-ttu-id="c5bfd-102">Postupy: Vzdálené zjištění stavu tiskáren</span><span class="sxs-lookup"><span data-stu-id="c5bfd-102">How to: Remotely Survey the Status of Printers</span></span>
<span data-ttu-id="c5bfd-103">V každém okamžiku v střední a velké společnosti může být více tiskárny, které nejsou práce z důvodu uvíznutí papíru nebo se z dokumentu nebo jiné problematické situaci.</span><span class="sxs-lookup"><span data-stu-id="c5bfd-103">At any given time at medium and large companies there may be multiple printers that are not working due to a paper jam or being out of paper or some other problematic situation.</span></span> <span data-ttu-id="c5bfd-104">Bohatá sada vlastností tiskárny v [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] Microsoft .NET Framework poskytují způsob pro provádění rychlé dotazník stavů tiskáren.</span><span class="sxs-lookup"><span data-stu-id="c5bfd-104">The rich set of printer properties exposed in the [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] of Microsoft .NET Framework provide a means for performing a rapid survey of the states of printers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5bfd-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="c5bfd-105">Example</span></span>  
 <span data-ttu-id="c5bfd-106">Hlavní kroky pro vytvoření tento druh nástroj jsou následující.</span><span class="sxs-lookup"><span data-stu-id="c5bfd-106">The major steps for creating this kind of utility are as follows.</span></span>  
  
1.  <span data-ttu-id="c5bfd-107">Získejte seznam všech tiskových serverů.</span><span class="sxs-lookup"><span data-stu-id="c5bfd-107">Obtain a list of all print servers.</span></span>  
  
2.  <span data-ttu-id="c5bfd-108">Projděte serverů, které chcete dotazovat jejich tiskové fronty.</span><span class="sxs-lookup"><span data-stu-id="c5bfd-108">Loop through the servers to query their print queues.</span></span>  
  
3.  <span data-ttu-id="c5bfd-109">V každém průchodu smyčky serveru procházení všechny server front a číst každou vlastnost, jež může naznačovat, že není aktuálně funguje fronty.</span><span class="sxs-lookup"><span data-stu-id="c5bfd-109">Within each pass of the server loop, loop through all the server's queues and read each property that might indicate that the queue is not currently working.</span></span>  
  
 <span data-ttu-id="c5bfd-110">Následující kód je řadu fragmenty kódu.</span><span class="sxs-lookup"><span data-stu-id="c5bfd-110">The code below is a series of snippets.</span></span> <span data-ttu-id="c5bfd-111">Pro zjednodušení tento příklad předpokládá, že je seznam s položkami oddělenými Line FEED tiskových serverů.</span><span class="sxs-lookup"><span data-stu-id="c5bfd-111">For simplicity, this example assumes that there is a CRLF-delimited list of print servers.</span></span> <span data-ttu-id="c5bfd-112">Proměnná `fileOfPrintServers` je <xref:System.IO.StreamReader> objekt pro tento soubor.</span><span class="sxs-lookup"><span data-stu-id="c5bfd-112">The variable `fileOfPrintServers` is a <xref:System.IO.StreamReader> object for this file.</span></span> <span data-ttu-id="c5bfd-113">Vzhledem k tomu, že každý název serveru je ve svém vlastním řádku, žádném volání z <xref:System.IO.StreamReader.ReadLine%2A> získá název další server a přejde <xref:System.IO.StreamReader>na kurzor na začátek na další řádek.</span><span class="sxs-lookup"><span data-stu-id="c5bfd-113">Since each server name is on its own line, any call of <xref:System.IO.StreamReader.ReadLine%2A> gets the name of the next server and moves the <xref:System.IO.StreamReader>'s cursor to the beginning of the next line.</span></span>  
  
 <span data-ttu-id="c5bfd-114">V rámci vnějšího smyčky, kód vytvoří <xref:System.Printing.PrintServer> objekt pro nejnovější tiskového serveru a určuje, že aplikace bude mít oprávnění správce k serveru.</span><span class="sxs-lookup"><span data-stu-id="c5bfd-114">Within the outer loop, the code creates a <xref:System.Printing.PrintServer> object for the latest print server and specifies that the application is to have administrative rights to the server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5bfd-115">Pokud existuje mnoho serverů, můžete zlepšit výkon pomocí <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> konstruktory, které pouze inicializace vlastností, kterou budete potřebovat.</span><span class="sxs-lookup"><span data-stu-id="c5bfd-115">If there are a lot of servers, you can improve performance by using the <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> constructors that only initialize the properties you are going to need.</span></span>  
  
 <span data-ttu-id="c5bfd-116">V příkladu se pak použije <xref:System.Printing.PrintServer.GetPrintQueues%2A> můžete vytvořit kolekci všech serveru je fronty a začne procházení je.</span><span class="sxs-lookup"><span data-stu-id="c5bfd-116">The example then uses <xref:System.Printing.PrintServer.GetPrintQueues%2A> to create a collection of all of the server's queues and begins to loop through them.</span></span> <span data-ttu-id="c5bfd-117">Tato vnitřní smyčka obsahuje větvení struktura odpovídající na dva způsoby, jak kontrolovat stav tiskárny:</span><span class="sxs-lookup"><span data-stu-id="c5bfd-117">This inner loop contains a branching structure corresponding to the two ways of checking a printer's status:</span></span>  
  
-   <span data-ttu-id="c5bfd-118">Příznaky systému si můžete přečíst <xref:System.Printing.PrintQueue.QueueStatus%2A> vlastnost, která je typu <xref:System.Printing.PrintQueueStatus>.</span><span class="sxs-lookup"><span data-stu-id="c5bfd-118">You can read the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property which is of type <xref:System.Printing.PrintQueueStatus>.</span></span>  
  
-   <span data-ttu-id="c5bfd-119">Můžete si přečíst každé příslušné vlastnosti, jako <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, a <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.</span><span class="sxs-lookup"><span data-stu-id="c5bfd-119">You can read each relevant property such as <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, and <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.</span></span>  
  
 <span data-ttu-id="c5bfd-120">Tento příklad ukazuje obě metody tak, aby byl uživatel dříve zobrazí výzva, kterou metodu použít a odpověděla s "y", pokud mu chtěli použít příznaky z <xref:System.Printing.PrintQueue.QueueStatus%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c5bfd-120">This example demonstrates both methods, so the user was previously prompted as to which method to use and responded with "y" if he or she wanted to use the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property.</span></span> <span data-ttu-id="c5bfd-121">Níže naleznete podrobnosti o tyto dvě metody.</span><span class="sxs-lookup"><span data-stu-id="c5bfd-121">See below for the details of the two methods.</span></span>  
  
 <span data-ttu-id="c5bfd-122">Nakonec výsledky se zobrazí uživateli.</span><span class="sxs-lookup"><span data-stu-id="c5bfd-122">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 <span data-ttu-id="c5bfd-123">Zkontrolujte stav tiskárny s použitím příznaků z <xref:System.Printing.PrintQueue.QueueStatus%2A> vlastnost, zkontrolujte každý relevantní příznak, pokud je nastavena.</span><span class="sxs-lookup"><span data-stu-id="c5bfd-123">To check printer status using the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property, you check each relevant flag to see if it is set.</span></span> <span data-ttu-id="c5bfd-124">Standardní způsob, jak zobrazit, pokud je v sadě bitové příznaky nastavit jeden bit je logické a operace sadou příznaky jako jeden operand a příznak sám sebe jako na druhý.</span><span class="sxs-lookup"><span data-stu-id="c5bfd-124">The standard way to see if one bit is set in a set of bit flags is to perform a logical AND operation with the set of flags as one operand and the flag itself as the other.</span></span> <span data-ttu-id="c5bfd-125">Vzhledem k tomu, že příznak samotné má jenom jeden bit, nastavit, výsledek logické a je, že, maximálně Tento stejný bit nastavený.</span><span class="sxs-lookup"><span data-stu-id="c5bfd-125">Since the flag itself has only one bit set, the result of the logical AND is that, at most, that same bit is set.</span></span> <span data-ttu-id="c5bfd-126">Pokud chcete zjistit, zda je nebo není, porovnejte právě výsledek logické a s příznakem sám sebe.</span><span class="sxs-lookup"><span data-stu-id="c5bfd-126">To find out whether it is or not, just compare the result of the logical AND with the flag itself.</span></span> <span data-ttu-id="c5bfd-127">Další informace najdete v tématu <xref:System.Printing.PrintQueueStatus>, [& – operátor (referenční dokumentace jazyka C#)](~/docs/csharp/language-reference/operators/and-operator.md), a <xref:System.FlagsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c5bfd-127">For more information, see <xref:System.Printing.PrintQueueStatus>, the [& Operator (C# Reference)](~/docs/csharp/language-reference/operators/and-operator.md), and <xref:System.FlagsAttribute>.</span></span>  
  
 <span data-ttu-id="c5bfd-128">Pro každý atribut, jehož bit nastaven přidá kód oznámení závěrečnou zprávu, která bude zobrazovat uživatelům.</span><span class="sxs-lookup"><span data-stu-id="c5bfd-128">For each attribute whose bit is set, the code adds a notice to the final report that will be presented to the user.</span></span> <span data-ttu-id="c5bfd-129">( **ReportAvailabilityAtThisTime** metoda, která je volána na konci tohoto kódu je popsána níže.)</span><span class="sxs-lookup"><span data-stu-id="c5bfd-129">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 <span data-ttu-id="c5bfd-130">Pokud chcete zkontrolovat stav tiskárny pomocí každou vlastnost, jednoduše přečíst si každou vlastnost a přidání poznámky do konečné sestavy, které budou zobrazovat uživateli, pokud je vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="c5bfd-130">To check printer status using each property, you simply read each property and add a note to the final report that will be presented to the user if the property is `true`.</span></span> <span data-ttu-id="c5bfd-131">( **ReportAvailabilityAtThisTime** metoda, která je volána na konci tohoto kódu je popsána níže.)</span><span class="sxs-lookup"><span data-stu-id="c5bfd-131">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 <span data-ttu-id="c5bfd-132">**ReportAvailabilityAtThisTime** metoda byla vytvořena v případě, že budete muset určit, zda je fronta k dispozici v aktuální denní čas.</span><span class="sxs-lookup"><span data-stu-id="c5bfd-132">The **ReportAvailabilityAtThisTime** method was created in case you need to determine if the queue is available at the current time of day.</span></span>  
  
 <span data-ttu-id="c5bfd-133">Metoda se nic nestane. Pokud <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> a <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> vlastnosti jsou stejné; protože v takovém případě tiskárna není k dispozici za všech okolností.</span><span class="sxs-lookup"><span data-stu-id="c5bfd-133">The method will do nothing if the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are equal; because in that case the printer is available at all times.</span></span> <span data-ttu-id="c5bfd-134">Pokud se liší, metoda získá aktuální čas, který pak musí být převeden do celkový počet minut po půlnoci, protože <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> a <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> vlastnosti jsou <xref:System.Int32>s představující minut po půlnoc, není <xref:System.DateTime> objekty.</span><span class="sxs-lookup"><span data-stu-id="c5bfd-134">If they are different, the method gets the current time which then has to be converted into total minutes past midnight because the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are <xref:System.Int32>s representing minutes-after-midnight, not <xref:System.DateTime> objects.</span></span> <span data-ttu-id="c5bfd-135">Nakonec metodu zkontroluje, pokud je aktuální čas mezi začátkem a "do" časy.</span><span class="sxs-lookup"><span data-stu-id="c5bfd-135">Finally, the method checks to see if the current time is between the start and "until" times.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a><span data-ttu-id="c5bfd-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5bfd-136">See Also</span></span>  
 <xref:System.Printing.PrintQueue.StartTimeOfDay%2A>  
 <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>  
 <xref:System.DateTime>  
 <xref:System.Printing.PrintQueueStatus>  
 <xref:System.FlagsAttribute>  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 [<span data-ttu-id="c5bfd-137">& – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c5bfd-137">& Operator (C# Reference)</span></span>](~/docs/csharp/language-reference/operators/and-operator.md)  
 [<span data-ttu-id="c5bfd-138">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="c5bfd-138">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="c5bfd-139">Přehled tisku</span><span class="sxs-lookup"><span data-stu-id="c5bfd-139">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)
