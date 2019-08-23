---
title: 'Postupy: Vzdálený průzkum stavu tiskáren'
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
ms.openlocfilehash: 0a7756684d5a133fa9cb014f109d14e413223ea9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945230"
---
# <a name="how-to-remotely-survey-the-status-of-printers"></a><span data-ttu-id="a3a6b-102">Postupy: Vzdálený průzkum stavu tiskáren</span><span class="sxs-lookup"><span data-stu-id="a3a6b-102">How to: Remotely Survey the Status of Printers</span></span>
<span data-ttu-id="a3a6b-103">V jakémkoli okamžiku na středních a velkých společnostech může existovat několik tiskáren, které nefungují z důvodu zaseknutí nebo vystavení papíru nebo některé jiné problematické situace.</span><span class="sxs-lookup"><span data-stu-id="a3a6b-103">At any given time at medium and large companies there may be multiple printers that are not working due to a paper jam or being out of paper or some other problematic situation.</span></span> <span data-ttu-id="a3a6b-104">Bohatá sada vlastností tiskárny zveřejněná v rozhraní API Microsoft .NET Framework poskytují prostředky pro rychlé prošetření stavů tiskáren.</span><span class="sxs-lookup"><span data-stu-id="a3a6b-104">The rich set of printer properties exposed in the APIs of Microsoft .NET Framework provide a means for performing a rapid survey of the states of printers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3a6b-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="a3a6b-105">Example</span></span>  
 <span data-ttu-id="a3a6b-106">Hlavní kroky pro vytvoření tohoto typu nástroje jsou následující.</span><span class="sxs-lookup"><span data-stu-id="a3a6b-106">The major steps for creating this kind of utility are as follows.</span></span>  
  
1. <span data-ttu-id="a3a6b-107">Získejte seznam všech tiskových serverů.</span><span class="sxs-lookup"><span data-stu-id="a3a6b-107">Obtain a list of all print servers.</span></span>  
  
2. <span data-ttu-id="a3a6b-108">Projděte servery a Dotazujte tiskové fronty.</span><span class="sxs-lookup"><span data-stu-id="a3a6b-108">Loop through the servers to query their print queues.</span></span>  
  
3. <span data-ttu-id="a3a6b-109">V rámci každého průchodu smyčky serveru procházejte všemi frontami serveru a přečtěte si jednotlivé vlastnosti, které mohou indikovat, že fronta aktuálně nepracuje.</span><span class="sxs-lookup"><span data-stu-id="a3a6b-109">Within each pass of the server loop, loop through all the server's queues and read each property that might indicate that the queue is not currently working.</span></span>  
  
 <span data-ttu-id="a3a6b-110">Níže uvedený kód je série fragmentů.</span><span class="sxs-lookup"><span data-stu-id="a3a6b-110">The code below is a series of snippets.</span></span> <span data-ttu-id="a3a6b-111">Pro zjednodušení tento příklad předpokládá, že existuje seznam tiskových serverů oddělený znaky CRLF.</span><span class="sxs-lookup"><span data-stu-id="a3a6b-111">For simplicity, this example assumes that there is a CRLF-delimited list of print servers.</span></span> <span data-ttu-id="a3a6b-112">`fileOfPrintServers` Proměnná<xref:System.IO.StreamReader> je objekt pro tento soubor.</span><span class="sxs-lookup"><span data-stu-id="a3a6b-112">The variable `fileOfPrintServers` is a <xref:System.IO.StreamReader> object for this file.</span></span> <span data-ttu-id="a3a6b-113">Vzhledem k tomu, že každý název serveru je na samostatném řádku <xref:System.IO.StreamReader.ReadLine%2A> , jakékoli volání získá název dalšího serveru a <xref:System.IO.StreamReader>přesune kurzor na začátek dalšího řádku.</span><span class="sxs-lookup"><span data-stu-id="a3a6b-113">Since each server name is on its own line, any call of <xref:System.IO.StreamReader.ReadLine%2A> gets the name of the next server and moves the <xref:System.IO.StreamReader>'s cursor to the beginning of the next line.</span></span>  
  
 <span data-ttu-id="a3a6b-114">V rámci vnější smyčky kód vytvoří <xref:System.Printing.PrintServer> objekt pro nejnovější tiskový server a určí, že aplikace má mít práva správce k serveru.</span><span class="sxs-lookup"><span data-stu-id="a3a6b-114">Within the outer loop, the code creates a <xref:System.Printing.PrintServer> object for the latest print server and specifies that the application is to have administrative rights to the server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a3a6b-115">Pokud existuje velký počet serverů, můžete zvýšit výkon pomocí <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> konstruktorů, které inicializují pouze vlastnosti, které budete potřebovat.</span><span class="sxs-lookup"><span data-stu-id="a3a6b-115">If there are a lot of servers, you can improve performance by using the <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> constructors that only initialize the properties you are going to need.</span></span>  
  
 <span data-ttu-id="a3a6b-116">Příklad potom používá <xref:System.Printing.PrintServer.GetPrintQueues%2A> k vytvoření kolekce všech front serveru a zahájí jejich procyklaci.</span><span class="sxs-lookup"><span data-stu-id="a3a6b-116">The example then uses <xref:System.Printing.PrintServer.GetPrintQueues%2A> to create a collection of all of the server's queues and begins to loop through them.</span></span> <span data-ttu-id="a3a6b-117">Tato vnitřní smyčka obsahuje strukturu větvení, která odpovídá dvěma způsobům kontroly stavu tiskárny:</span><span class="sxs-lookup"><span data-stu-id="a3a6b-117">This inner loop contains a branching structure corresponding to the two ways of checking a printer's status:</span></span>  
  
- <span data-ttu-id="a3a6b-118">Můžete číst příznaky <xref:System.Printing.PrintQueue.QueueStatus%2A> vlastnosti, která je typu <xref:System.Printing.PrintQueueStatus>.</span><span class="sxs-lookup"><span data-stu-id="a3a6b-118">You can read the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property which is of type <xref:System.Printing.PrintQueueStatus>.</span></span>  
  
- <span data-ttu-id="a3a6b-119">Můžete číst jednotlivé relevantní vlastnosti <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, například, a. <xref:System.Printing.PrintQueue.IsPaperJammed%2A></span><span class="sxs-lookup"><span data-stu-id="a3a6b-119">You can read each relevant property such as <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, and <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.</span></span>  
  
 <span data-ttu-id="a3a6b-120">Tento příklad ukazuje obě metody, takže uživatel byl dříve vyzván, aby se použila metoda a odpovídala "y", pokud chtěla použít příznaky <xref:System.Printing.PrintQueue.QueueStatus%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a3a6b-120">This example demonstrates both methods, so the user was previously prompted as to which method to use and responded with "y" if he or she wanted to use the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property.</span></span> <span data-ttu-id="a3a6b-121">Podrobnosti o těchto dvou metodách najdete níže.</span><span class="sxs-lookup"><span data-stu-id="a3a6b-121">See below for the details of the two methods.</span></span>  
  
 <span data-ttu-id="a3a6b-122">Nakonec se výsledky zobrazí uživateli.</span><span class="sxs-lookup"><span data-stu-id="a3a6b-122">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 <span data-ttu-id="a3a6b-123">Chcete-li kontrolovat stav tiskárny pomocí příznaků <xref:System.Printing.PrintQueue.QueueStatus%2A> vlastnosti, zkontrolujte každý příslušný příznak, abyste viděli, zda je nastavena.</span><span class="sxs-lookup"><span data-stu-id="a3a6b-123">To check printer status using the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property, you check each relevant flag to see if it is set.</span></span> <span data-ttu-id="a3a6b-124">Standardní způsob, jak zjistit, zda je jeden bit nastaven v sadě bitových příznaků, je provést logickou operaci a s množinou příznaků jako jeden operand a příznak jako druhý.</span><span class="sxs-lookup"><span data-stu-id="a3a6b-124">The standard way to see if one bit is set in a set of bit flags is to perform a logical AND operation with the set of flags as one operand and the flag itself as the other.</span></span> <span data-ttu-id="a3a6b-125">Vzhledem k tomu, že příznak samotný má pouze jednu bitovou sadu, výsledek logického typu a je, který je nanejvýš stejný jako bit nastaven.</span><span class="sxs-lookup"><span data-stu-id="a3a6b-125">Since the flag itself has only one bit set, the result of the logical AND is that, at most, that same bit is set.</span></span> <span data-ttu-id="a3a6b-126">Chcete-li zjistit, zda je nebo není, stačí porovnat výsledek logického operátoru a samotného příznaku.</span><span class="sxs-lookup"><span data-stu-id="a3a6b-126">To find out whether it is or not, just compare the result of the logical AND with the flag itself.</span></span> <span data-ttu-id="a3a6b-127">Další informace naleznete v tématu <xref:System.Printing.PrintQueueStatus>, [operátor & (C# Referenční dokumentace)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)a. <xref:System.FlagsAttribute></span><span class="sxs-lookup"><span data-stu-id="a3a6b-127">For more information, see <xref:System.Printing.PrintQueueStatus>, the [& Operator (C# Reference)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-), and <xref:System.FlagsAttribute>.</span></span>  
  
 <span data-ttu-id="a3a6b-128">Pro každý atribut, jehož bit je nastaven, kód přidá oznámení konečné sestavě, která bude prezentována uživateli.</span><span class="sxs-lookup"><span data-stu-id="a3a6b-128">For each attribute whose bit is set, the code adds a notice to the final report that will be presented to the user.</span></span> <span data-ttu-id="a3a6b-129">(Metoda **ReportAvailabilityAtThisTime** , která je volána na konci kódu, je popsána níže.)</span><span class="sxs-lookup"><span data-stu-id="a3a6b-129">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 <span data-ttu-id="a3a6b-130">Chcete-li kontrolovat stav tiskárny pomocí jednotlivých vlastností, stačí načíst jednotlivé vlastnosti a přidat poznámku do konečné sestavy, která bude prezentována uživateli, pokud je `true`vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a3a6b-130">To check printer status using each property, you simply read each property and add a note to the final report that will be presented to the user if the property is `true`.</span></span> <span data-ttu-id="a3a6b-131">(Metoda **ReportAvailabilityAtThisTime** , která je volána na konci kódu, je popsána níže.)</span><span class="sxs-lookup"><span data-stu-id="a3a6b-131">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 <span data-ttu-id="a3a6b-132">Metoda **ReportAvailabilityAtThisTime** byla vytvořena pro případ, že je třeba určit, zda je fronta k dispozici v aktuálním denním okamžiku.</span><span class="sxs-lookup"><span data-stu-id="a3a6b-132">The **ReportAvailabilityAtThisTime** method was created in case you need to determine if the queue is available at the current time of day.</span></span>  
  
 <span data-ttu-id="a3a6b-133">Tato metoda neprovede žádnou akci, pokud <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> jsou <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> vlastnosti a stejné; protože v takovém případě je tiskárna k dispozici v tuto dobu.</span><span class="sxs-lookup"><span data-stu-id="a3a6b-133">The method will do nothing if the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are equal; because in that case the printer is available at all times.</span></span> <span data-ttu-id="a3a6b-134">Pokud se liší, metoda získá aktuální čas, který je pak nutné převést na celkový počet <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> minut po půlnoci, protože vlastnosti a <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> jsou <xref:System.Int32>představující minuty-po půlnoci, ne <xref:System.DateTime> objekty.</span><span class="sxs-lookup"><span data-stu-id="a3a6b-134">If they are different, the method gets the current time which then has to be converted into total minutes past midnight because the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are <xref:System.Int32>s representing minutes-after-midnight, not <xref:System.DateTime> objects.</span></span> <span data-ttu-id="a3a6b-135">Nakonec metoda zkontroluje, zda je aktuální čas mezi začátkem a časem.</span><span class="sxs-lookup"><span data-stu-id="a3a6b-135">Finally, the method checks to see if the current time is between the start and "until" times.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a><span data-ttu-id="a3a6b-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3a6b-136">See also</span></span>

- <xref:System.Printing.PrintQueue.StartTimeOfDay%2A>
- <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>
- <xref:System.DateTime>
- <xref:System.Printing.PrintQueueStatus>
- <xref:System.FlagsAttribute>
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- [<span data-ttu-id="a3a6b-137">Operátor & (C# Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="a3a6b-137">& Operator (C# Reference)</span></span>](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)
- [<span data-ttu-id="a3a6b-138">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="a3a6b-138">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="a3a6b-139">Přehled tisku</span><span class="sxs-lookup"><span data-stu-id="a3a6b-139">Printing Overview</span></span>](printing-overview.md)
