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
ms.openlocfilehash: dc187a4ea120661e8118ce79a966d3d4a3b40711
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768498"
---
# <a name="how-to-remotely-survey-the-status-of-printers"></a><span data-ttu-id="7edbc-102">Postupy: Vzdálený průzkum stavu tiskáren</span><span class="sxs-lookup"><span data-stu-id="7edbc-102">How to: Remotely Survey the Status of Printers</span></span>
<span data-ttu-id="7edbc-103">V každém okamžiku u středně velkých a velkých společností může být více tiskárny, které nejsou práce z důvodu zaseknutý papír nebo jsou mimo papír nebo jiné problematické situaci.</span><span class="sxs-lookup"><span data-stu-id="7edbc-103">At any given time at medium and large companies there may be multiple printers that are not working due to a paper jam or being out of paper or some other problematic situation.</span></span> <span data-ttu-id="7edbc-104">Bohaté sadě vlastností tiskárny v [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] Microsoft .NET Framework poskytují způsob pro provádění rychlé zjišťování stavu tiskárny.</span><span class="sxs-lookup"><span data-stu-id="7edbc-104">The rich set of printer properties exposed in the [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] of Microsoft .NET Framework provide a means for performing a rapid survey of the states of printers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7edbc-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="7edbc-105">Example</span></span>  
 <span data-ttu-id="7edbc-106">Hlavní kroky pro vytvoření tento druh nástroj jsou následující.</span><span class="sxs-lookup"><span data-stu-id="7edbc-106">The major steps for creating this kind of utility are as follows.</span></span>  
  
1. <span data-ttu-id="7edbc-107">Získáte seznam všech tiskových serverů.</span><span class="sxs-lookup"><span data-stu-id="7edbc-107">Obtain a list of all print servers.</span></span>  
  
2. <span data-ttu-id="7edbc-108">Projít servery, které chcete dotazovat jejich tiskové fronty.</span><span class="sxs-lookup"><span data-stu-id="7edbc-108">Loop through the servers to query their print queues.</span></span>  
  
3. <span data-ttu-id="7edbc-109">V každém průchodu server smyčky projít všechny serveru front a čtení každou vlastnost, která můžou značit, že fronta není aktuálně funguje.</span><span class="sxs-lookup"><span data-stu-id="7edbc-109">Within each pass of the server loop, loop through all the server's queues and read each property that might indicate that the queue is not currently working.</span></span>  
  
 <span data-ttu-id="7edbc-110">Následující kód je posloupnost fragmenty kódu.</span><span class="sxs-lookup"><span data-stu-id="7edbc-110">The code below is a series of snippets.</span></span> <span data-ttu-id="7edbc-111">Pro zjednodušení tento příklad předpokládá, že je seznam tiskových serverů oddělených znaky CRLF.</span><span class="sxs-lookup"><span data-stu-id="7edbc-111">For simplicity, this example assumes that there is a CRLF-delimited list of print servers.</span></span> <span data-ttu-id="7edbc-112">Proměnná `fileOfPrintServers` je <xref:System.IO.StreamReader> objekt pro tento soubor.</span><span class="sxs-lookup"><span data-stu-id="7edbc-112">The variable `fileOfPrintServers` is a <xref:System.IO.StreamReader> object for this file.</span></span> <span data-ttu-id="7edbc-113">Každý název serveru je na samostatném řádku, některé volání <xref:System.IO.StreamReader.ReadLine%2A> získá název dalšího serveru a přesune <xref:System.IO.StreamReader>od kurzoru na začátek dalšího řádku.</span><span class="sxs-lookup"><span data-stu-id="7edbc-113">Since each server name is on its own line, any call of <xref:System.IO.StreamReader.ReadLine%2A> gets the name of the next server and moves the <xref:System.IO.StreamReader>'s cursor to the beginning of the next line.</span></span>  
  
 <span data-ttu-id="7edbc-114">V rámci vnější smyčky, vytvoří kód <xref:System.Printing.PrintServer> objekt pro nejnovější tiskového serveru a určuje, že aplikace je mít práva správce k serveru.</span><span class="sxs-lookup"><span data-stu-id="7edbc-114">Within the outer loop, the code creates a <xref:System.Printing.PrintServer> object for the latest print server and specifies that the application is to have administrative rights to the server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7edbc-115">Pokud existuje mnoho serverů, můžete zlepšit výkon pomocí <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> konstruktory, které inicializovat pouze vlastnosti, kterou budete potřebovat.</span><span class="sxs-lookup"><span data-stu-id="7edbc-115">If there are a lot of servers, you can improve performance by using the <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> constructors that only initialize the properties you are going to need.</span></span>  
  
 <span data-ttu-id="7edbc-116">Příklad poté použije <xref:System.Printing.PrintServer.GetPrintQueues%2A> můžete vytvořit kolekci všech serveru je zařadí do fronty a spustí se ve smyčce projde.</span><span class="sxs-lookup"><span data-stu-id="7edbc-116">The example then uses <xref:System.Printing.PrintServer.GetPrintQueues%2A> to create a collection of all of the server's queues and begins to loop through them.</span></span> <span data-ttu-id="7edbc-117">Tento vnitřní smyčka obsahuje strukturu větvení odpovídající na dva způsoby, jak kontroluje se stav tiskárny:</span><span class="sxs-lookup"><span data-stu-id="7edbc-117">This inner loop contains a branching structure corresponding to the two ways of checking a printer's status:</span></span>  
  
- <span data-ttu-id="7edbc-118">Můžete si přečíst příznaky z <xref:System.Printing.PrintQueue.QueueStatus%2A> vlastnost, která je typu <xref:System.Printing.PrintQueueStatus>.</span><span class="sxs-lookup"><span data-stu-id="7edbc-118">You can read the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property which is of type <xref:System.Printing.PrintQueueStatus>.</span></span>  
  
- <span data-ttu-id="7edbc-119">Můžete si přečíst každý relevantní vlastnosti, jako <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, a <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.</span><span class="sxs-lookup"><span data-stu-id="7edbc-119">You can read each relevant property such as <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, and <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.</span></span>  
  
 <span data-ttu-id="7edbc-120">Tento příklad ukazuje obě metody, uživateli se zobrazí výzva, jakou metodu použít a odpověděl zprávou "y", pokud uživatel chce použít příznaky z <xref:System.Printing.PrintQueue.QueueStatus%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7edbc-120">This example demonstrates both methods, so the user was previously prompted as to which method to use and responded with "y" if he or she wanted to use the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property.</span></span> <span data-ttu-id="7edbc-121">Níže naleznete podrobnosti ze dvou způsobů.</span><span class="sxs-lookup"><span data-stu-id="7edbc-121">See below for the details of the two methods.</span></span>  
  
 <span data-ttu-id="7edbc-122">A konečně výsledky se zobrazí uživateli.</span><span class="sxs-lookup"><span data-stu-id="7edbc-122">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 <span data-ttu-id="7edbc-123">Ke kontrole stavu tiskárny pomocí příznaků z <xref:System.Printing.PrintQueue.QueueStatus%2A> vlastnost, zkontrolujte každý relevantní příznak zobrazíte, pokud je nastavena.</span><span class="sxs-lookup"><span data-stu-id="7edbc-123">To check printer status using the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property, you check each relevant flag to see if it is set.</span></span> <span data-ttu-id="7edbc-124">K provedení logické operace a sadu příznaků jako jeden operand a příznak samotný jako druhý je standardní způsob, jak zobrazit, pokud jeden bit nastaven sadu bitových příznaků.</span><span class="sxs-lookup"><span data-stu-id="7edbc-124">The standard way to see if one bit is set in a set of bit flags is to perform a logical AND operation with the set of flags as one operand and the flag itself as the other.</span></span> <span data-ttu-id="7edbc-125">Protože příznak samotný má pouze jeden bit nastaven, výsledek logické a je to, že, maximálně Tento stejný bit nastaven.</span><span class="sxs-lookup"><span data-stu-id="7edbc-125">Since the flag itself has only one bit set, the result of the logical AND is that, at most, that same bit is set.</span></span> <span data-ttu-id="7edbc-126">Pokud chcete zjistit, jestli je nebo není, stačí porovnání výsledku logické a s příznakem samotný.</span><span class="sxs-lookup"><span data-stu-id="7edbc-126">To find out whether it is or not, just compare the result of the logical AND with the flag itself.</span></span> <span data-ttu-id="7edbc-127">Další informace najdete v tématu <xref:System.Printing.PrintQueueStatus>, [& – operátor (C# odkaz)](~/docs/csharp/language-reference/operators/and-operator.md), a <xref:System.FlagsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7edbc-127">For more information, see <xref:System.Printing.PrintQueueStatus>, the [& Operator (C# Reference)](~/docs/csharp/language-reference/operators/and-operator.md), and <xref:System.FlagsAttribute>.</span></span>  
  
 <span data-ttu-id="7edbc-128">Pro každý atribut, jehož bit nastaven kód přidá upozornění na konečná sestava, která se zobrazí uživateli.</span><span class="sxs-lookup"><span data-stu-id="7edbc-128">For each attribute whose bit is set, the code adds a notice to the final report that will be presented to the user.</span></span> <span data-ttu-id="7edbc-129">( **ReportAvailabilityAtThisTime** metodu, která je volána na konci kód, jsou popsány níže.)</span><span class="sxs-lookup"><span data-stu-id="7edbc-129">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 <span data-ttu-id="7edbc-130">Pokud chcete zkontrolovat stav tiskárny pomocí každou vlastnost, jednoduše čtení každou vlastnost a přidání poznámky ke Konečná sestava, která budou zobrazovat uživateli, pokud je vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="7edbc-130">To check printer status using each property, you simply read each property and add a note to the final report that will be presented to the user if the property is `true`.</span></span> <span data-ttu-id="7edbc-131">( **ReportAvailabilityAtThisTime** metodu, která je volána na konci kód, jsou popsány níže.)</span><span class="sxs-lookup"><span data-stu-id="7edbc-131">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 <span data-ttu-id="7edbc-132">**ReportAvailabilityAtThisTime** metoda byl vytvořen v případě, že je potřeba určit, zda je fronta dostupná v současné době den.</span><span class="sxs-lookup"><span data-stu-id="7edbc-132">The **ReportAvailabilityAtThisTime** method was created in case you need to determine if the queue is available at the current time of day.</span></span>  
  
 <span data-ttu-id="7edbc-133">Metoda neudělá Pokud <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> a <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> vlastnosti jsou stejné; protože v takovém případě tiskárna není k dispozici po celou dobu.</span><span class="sxs-lookup"><span data-stu-id="7edbc-133">The method will do nothing if the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are equal; because in that case the printer is available at all times.</span></span> <span data-ttu-id="7edbc-134">Pokud se liší, metoda získá aktuální čas, který má být převeden do celkový počet minut po půlnoci, protože nemá <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> a <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> vlastnosti jsou <xref:System.Int32>s představující minut po půlnoc, ne <xref:System.DateTime> objekty.</span><span class="sxs-lookup"><span data-stu-id="7edbc-134">If they are different, the method gets the current time which then has to be converted into total minutes past midnight because the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are <xref:System.Int32>s representing minutes-after-midnight, not <xref:System.DateTime> objects.</span></span> <span data-ttu-id="7edbc-135">Nakonec metoda zkontroluje, pokud je aktuální čas mezi začátky a "až" časy.</span><span class="sxs-lookup"><span data-stu-id="7edbc-135">Finally, the method checks to see if the current time is between the start and "until" times.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a><span data-ttu-id="7edbc-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7edbc-136">See also</span></span>

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
- [<span data-ttu-id="7edbc-137">& – Operátor (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="7edbc-137">& Operator (C# Reference)</span></span>](~/docs/csharp/language-reference/operators/and-operator.md)
- [<span data-ttu-id="7edbc-138">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="7edbc-138">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="7edbc-139">Přehled tisku</span><span class="sxs-lookup"><span data-stu-id="7edbc-139">Printing Overview</span></span>](printing-overview.md)
