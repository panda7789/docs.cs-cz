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
ms.openlocfilehash: 859ccb703c6c54c66d6ea7b433c67d156627e25b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187038"
---
# <a name="how-to-remotely-survey-the-status-of-printers"></a><span data-ttu-id="9b7fc-102">Postupy: Vzdálené zjištění stavu tiskáren</span><span class="sxs-lookup"><span data-stu-id="9b7fc-102">How to: Remotely Survey the Status of Printers</span></span>
<span data-ttu-id="9b7fc-103">V daném okamžiku ve středních a velkých společnostech může existovat více tiskáren, které nefungují kvůli uvíznutí papíru nebo nedostatku papíru nebo jiné problematické situaci.</span><span class="sxs-lookup"><span data-stu-id="9b7fc-103">At any given time at medium and large companies there may be multiple printers that are not working due to a paper jam or being out of paper or some other problematic situation.</span></span> <span data-ttu-id="9b7fc-104">Bohatá sada vlastností tiskárny vystavených v rozhraních API rozhraní Microsoft .NET Framework poskytuje prostředky pro provádění rychlého průzkumu stavů tiskáren.</span><span class="sxs-lookup"><span data-stu-id="9b7fc-104">The rich set of printer properties exposed in the APIs of Microsoft .NET Framework provide a means for performing a rapid survey of the states of printers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b7fc-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="9b7fc-105">Example</span></span>  
 <span data-ttu-id="9b7fc-106">Hlavní kroky pro vytvoření tohoto druhu nástroje jsou následující.</span><span class="sxs-lookup"><span data-stu-id="9b7fc-106">The major steps for creating this kind of utility are as follows.</span></span>  
  
1. <span data-ttu-id="9b7fc-107">Získejte seznam všech tiskových serverů.</span><span class="sxs-lookup"><span data-stu-id="9b7fc-107">Obtain a list of all print servers.</span></span>  
  
2. <span data-ttu-id="9b7fc-108">Smyčka prostřednictvím serverů k dotazování jejich tiskové fronty.</span><span class="sxs-lookup"><span data-stu-id="9b7fc-108">Loop through the servers to query their print queues.</span></span>  
  
3. <span data-ttu-id="9b7fc-109">V rámci každého průchodu smyčky serveru projděte všechny fronty serveru a přečtěte si každou vlastnost, která může znamenat, že fronta právě nefunguje.</span><span class="sxs-lookup"><span data-stu-id="9b7fc-109">Within each pass of the server loop, loop through all the server's queues and read each property that might indicate that the queue is not currently working.</span></span>  
  
 <span data-ttu-id="9b7fc-110">Níže uvedený kód je řada výstřižků.</span><span class="sxs-lookup"><span data-stu-id="9b7fc-110">The code below is a series of snippets.</span></span> <span data-ttu-id="9b7fc-111">Pro jednoduchost tento příklad předpokládá, že existuje seznam tiskových serverů oddělený crlf.</span><span class="sxs-lookup"><span data-stu-id="9b7fc-111">For simplicity, this example assumes that there is a CRLF-delimited list of print servers.</span></span> <span data-ttu-id="9b7fc-112">Proměnná `fileOfPrintServers` je <xref:System.IO.StreamReader> objekt pro tento soubor.</span><span class="sxs-lookup"><span data-stu-id="9b7fc-112">The variable `fileOfPrintServers` is a <xref:System.IO.StreamReader> object for this file.</span></span> <span data-ttu-id="9b7fc-113">Vzhledem k tomu, že každý název <xref:System.IO.StreamReader.ReadLine%2A> serveru je na svém vlastním <xref:System.IO.StreamReader>řádku, každé volání získá název dalšího serveru a přesune kurzor 's na začátek dalšího řádku.</span><span class="sxs-lookup"><span data-stu-id="9b7fc-113">Since each server name is on its own line, any call of <xref:System.IO.StreamReader.ReadLine%2A> gets the name of the next server and moves the <xref:System.IO.StreamReader>'s cursor to the beginning of the next line.</span></span>  
  
 <span data-ttu-id="9b7fc-114">V rámci vnější smyčky kód <xref:System.Printing.PrintServer> vytvoří objekt pro nejnovější tiskový server a určuje, že aplikace má mít práva správce k serveru.</span><span class="sxs-lookup"><span data-stu-id="9b7fc-114">Within the outer loop, the code creates a <xref:System.Printing.PrintServer> object for the latest print server and specifies that the application is to have administrative rights to the server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9b7fc-115">Pokud existuje mnoho serverů, můžete zlepšit výkon <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> pomocí konstruktory, které pouze inicializovat vlastnosti, které budete potřebovat.</span><span class="sxs-lookup"><span data-stu-id="9b7fc-115">If there are a lot of servers, you can improve performance by using the <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> constructors that only initialize the properties you are going to need.</span></span>  
  
 <span data-ttu-id="9b7fc-116">Příklad pak <xref:System.Printing.PrintServer.GetPrintQueues%2A> používá k vytvoření kolekce všech front serveru a začne smyčku přes ně.</span><span class="sxs-lookup"><span data-stu-id="9b7fc-116">The example then uses <xref:System.Printing.PrintServer.GetPrintQueues%2A> to create a collection of all of the server's queues and begins to loop through them.</span></span> <span data-ttu-id="9b7fc-117">Tato vnitřní smyčka obsahuje strukturu větvení odpovídající dvěma způsobům kontroly stavu tiskárny:</span><span class="sxs-lookup"><span data-stu-id="9b7fc-117">This inner loop contains a branching structure corresponding to the two ways of checking a printer's status:</span></span>  
  
- <span data-ttu-id="9b7fc-118">Můžete si přečíst <xref:System.Printing.PrintQueue.QueueStatus%2A> příznaky vlastnosti, <xref:System.Printing.PrintQueueStatus>která je typu .</span><span class="sxs-lookup"><span data-stu-id="9b7fc-118">You can read the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property which is of type <xref:System.Printing.PrintQueueStatus>.</span></span>  
  
- <span data-ttu-id="9b7fc-119">Můžete si přečíst každou <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>příslušnou <xref:System.Printing.PrintQueue.IsPaperJammed%2A>vlastnost, například . a .</span><span class="sxs-lookup"><span data-stu-id="9b7fc-119">You can read each relevant property such as <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, and <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.</span></span>  
  
 <span data-ttu-id="9b7fc-120">Tento příklad ukazuje obě metody, takže uživatel byl dříve vyzván, jakou metodu použít a odpověděl "y", pokud chtěli použít příznaky <xref:System.Printing.PrintQueue.QueueStatus%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9b7fc-120">This example demonstrates both methods, so the user was previously prompted as to which method to use and responded with "y" if they wanted to use the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property.</span></span> <span data-ttu-id="9b7fc-121">Podrobnosti o těchto dvou metodách naleznete níže.</span><span class="sxs-lookup"><span data-stu-id="9b7fc-121">See below for the details of the two methods.</span></span>  
  
 <span data-ttu-id="9b7fc-122">Nakonec jsou výsledky prezentovány uživateli.</span><span class="sxs-lookup"><span data-stu-id="9b7fc-122">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 <span data-ttu-id="9b7fc-123">Chcete-li zkontrolovat stav tiskárny pomocí příznaků vlastnosti, <xref:System.Printing.PrintQueue.QueueStatus%2A> zkontrolujte každý příslušný příznak a zjistěte, zda je nastaven.</span><span class="sxs-lookup"><span data-stu-id="9b7fc-123">To check printer status using the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property, you check each relevant flag to see if it is set.</span></span> <span data-ttu-id="9b7fc-124">Standardní způsob, jak zjistit, zda jeden bit je nastaven v sadě příznaků bitů je provést logickou operaci and se sadou příznaků jako jeden operand a příznak sám jako druhý.</span><span class="sxs-lookup"><span data-stu-id="9b7fc-124">The standard way to see if one bit is set in a set of bit flags is to perform a logical AND operation with the set of flags as one operand and the flag itself as the other.</span></span> <span data-ttu-id="9b7fc-125">Vzhledem k tomu, že příznak sám má pouze jeden bit nastavit, výsledkem logické and je, že nanejvýš, že stejný bit je nastaven.</span><span class="sxs-lookup"><span data-stu-id="9b7fc-125">Since the flag itself has only one bit set, the result of the logical AND is that, at most, that same bit is set.</span></span> <span data-ttu-id="9b7fc-126">Chcete-li zjistit, zda je či není, stačí porovnat výsledek logické and s příznakem sám.</span><span class="sxs-lookup"><span data-stu-id="9b7fc-126">To find out whether it is or not, just compare the result of the logical AND with the flag itself.</span></span> <span data-ttu-id="9b7fc-127">Další informace naleznete <xref:System.Printing.PrintQueueStatus>v [tématech operátor& (C# Reference)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)a <xref:System.FlagsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9b7fc-127">For more information, see <xref:System.Printing.PrintQueueStatus>, the [& Operator (C# Reference)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-), and <xref:System.FlagsAttribute>.</span></span>  
  
 <span data-ttu-id="9b7fc-128">Pro každý atribut, jehož bit je nastaven, kód přidá oznámení do závěrečné sestavy, která bude předložena uživateli.</span><span class="sxs-lookup"><span data-stu-id="9b7fc-128">For each attribute whose bit is set, the code adds a notice to the final report that will be presented to the user.</span></span> <span data-ttu-id="9b7fc-129">(Metoda **ReportAvailabilityAtThisTime,** která je volána na konci kódu, je popsána níže.)</span><span class="sxs-lookup"><span data-stu-id="9b7fc-129">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 <span data-ttu-id="9b7fc-130">Chcete-li zkontrolovat stav tiskárny pomocí jednotlivých vlastností, jednoduše si přečtěte každou vlastnost a `true`přidejte poznámku do závěrečné sestavy, která bude uživateli předložena, pokud je vlastnost .</span><span class="sxs-lookup"><span data-stu-id="9b7fc-130">To check printer status using each property, you simply read each property and add a note to the final report that will be presented to the user if the property is `true`.</span></span> <span data-ttu-id="9b7fc-131">(Metoda **ReportAvailabilityAtThisTime,** která je volána na konci kódu, je popsána níže.)</span><span class="sxs-lookup"><span data-stu-id="9b7fc-131">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 <span data-ttu-id="9b7fc-132">**Metoda ReportAvailabilityAtThisTime** byla vytvořena v případě, že potřebujete zjistit, zda je fronta k dispozici v aktuální denní době.</span><span class="sxs-lookup"><span data-stu-id="9b7fc-132">The **ReportAvailabilityAtThisTime** method was created in case you need to determine if the queue is available at the current time of day.</span></span>  
  
 <span data-ttu-id="9b7fc-133">Metoda nebude dělat <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> nic, <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> pokud a vlastnosti jsou stejné; protože v takovém případě je tiskárna vždy k dispozici.</span><span class="sxs-lookup"><span data-stu-id="9b7fc-133">The method will do nothing if the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are equal; because in that case the printer is available at all times.</span></span> <span data-ttu-id="9b7fc-134">Pokud se liší, metoda získá aktuální čas, který pak musí být převedeny na celkový počet minut po půlnoci, <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> protože vlastnosti a <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> představují <xref:System.Int32>minuty po půlnoci, nikoli <xref:System.DateTime> objekty.</span><span class="sxs-lookup"><span data-stu-id="9b7fc-134">If they are different, the method gets the current time which then has to be converted into total minutes past midnight because the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are <xref:System.Int32>s representing minutes-after-midnight, not <xref:System.DateTime> objects.</span></span> <span data-ttu-id="9b7fc-135">Nakonec metoda zkontroluje, zda aktuální čas je mezi počáteční a "do" časy.</span><span class="sxs-lookup"><span data-stu-id="9b7fc-135">Finally, the method checks to see if the current time is between the start and "until" times.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a><span data-ttu-id="9b7fc-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="9b7fc-136">See also</span></span>

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
- [<span data-ttu-id="9b7fc-137">operátor& (odkaz jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9b7fc-137">& Operator (C# Reference)</span></span>](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)
- [<span data-ttu-id="9b7fc-138">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="9b7fc-138">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="9b7fc-139">Přehled tisku</span><span class="sxs-lookup"><span data-stu-id="9b7fc-139">Printing Overview</span></span>](printing-overview.md)
