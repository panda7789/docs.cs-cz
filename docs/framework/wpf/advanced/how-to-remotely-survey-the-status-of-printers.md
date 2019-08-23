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
# <a name="how-to-remotely-survey-the-status-of-printers"></a>Postupy: Vzdálený průzkum stavu tiskáren
V jakémkoli okamžiku na středních a velkých společnostech může existovat několik tiskáren, které nefungují z důvodu zaseknutí nebo vystavení papíru nebo některé jiné problematické situace. Bohatá sada vlastností tiskárny zveřejněná v rozhraní API Microsoft .NET Framework poskytují prostředky pro rychlé prošetření stavů tiskáren.  
  
## <a name="example"></a>Příklad  
 Hlavní kroky pro vytvoření tohoto typu nástroje jsou následující.  
  
1. Získejte seznam všech tiskových serverů.  
  
2. Projděte servery a Dotazujte tiskové fronty.  
  
3. V rámci každého průchodu smyčky serveru procházejte všemi frontami serveru a přečtěte si jednotlivé vlastnosti, které mohou indikovat, že fronta aktuálně nepracuje.  
  
 Níže uvedený kód je série fragmentů. Pro zjednodušení tento příklad předpokládá, že existuje seznam tiskových serverů oddělený znaky CRLF. `fileOfPrintServers` Proměnná<xref:System.IO.StreamReader> je objekt pro tento soubor. Vzhledem k tomu, že každý název serveru je na samostatném řádku <xref:System.IO.StreamReader.ReadLine%2A> , jakékoli volání získá název dalšího serveru a <xref:System.IO.StreamReader>přesune kurzor na začátek dalšího řádku.  
  
 V rámci vnější smyčky kód vytvoří <xref:System.Printing.PrintServer> objekt pro nejnovější tiskový server a určí, že aplikace má mít práva správce k serveru.  
  
> [!NOTE]
> Pokud existuje velký počet serverů, můžete zvýšit výkon pomocí <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> konstruktorů, které inicializují pouze vlastnosti, které budete potřebovat.  
  
 Příklad potom používá <xref:System.Printing.PrintServer.GetPrintQueues%2A> k vytvoření kolekce všech front serveru a zahájí jejich procyklaci. Tato vnitřní smyčka obsahuje strukturu větvení, která odpovídá dvěma způsobům kontroly stavu tiskárny:  
  
- Můžete číst příznaky <xref:System.Printing.PrintQueue.QueueStatus%2A> vlastnosti, která je typu <xref:System.Printing.PrintQueueStatus>.  
  
- Můžete číst jednotlivé relevantní vlastnosti <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, například, a. <xref:System.Printing.PrintQueue.IsPaperJammed%2A>  
  
 Tento příklad ukazuje obě metody, takže uživatel byl dříve vyzván, aby se použila metoda a odpovídala "y", pokud chtěla použít příznaky <xref:System.Printing.PrintQueue.QueueStatus%2A> vlastnosti. Podrobnosti o těchto dvou metodách najdete níže.  
  
 Nakonec se výsledky zobrazí uživateli.  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 Chcete-li kontrolovat stav tiskárny pomocí příznaků <xref:System.Printing.PrintQueue.QueueStatus%2A> vlastnosti, zkontrolujte každý příslušný příznak, abyste viděli, zda je nastavena. Standardní způsob, jak zjistit, zda je jeden bit nastaven v sadě bitových příznaků, je provést logickou operaci a s množinou příznaků jako jeden operand a příznak jako druhý. Vzhledem k tomu, že příznak samotný má pouze jednu bitovou sadu, výsledek logického typu a je, který je nanejvýš stejný jako bit nastaven. Chcete-li zjistit, zda je nebo není, stačí porovnat výsledek logického operátoru a samotného příznaku. Další informace naleznete v tématu <xref:System.Printing.PrintQueueStatus>, [operátor & (C# Referenční dokumentace)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)a. <xref:System.FlagsAttribute>  
  
 Pro každý atribut, jehož bit je nastaven, kód přidá oznámení konečné sestavě, která bude prezentována uživateli. (Metoda **ReportAvailabilityAtThisTime** , která je volána na konci kódu, je popsána níže.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 Chcete-li kontrolovat stav tiskárny pomocí jednotlivých vlastností, stačí načíst jednotlivé vlastnosti a přidat poznámku do konečné sestavy, která bude prezentována uživateli, pokud je `true`vlastnost. (Metoda **ReportAvailabilityAtThisTime** , která je volána na konci kódu, je popsána níže.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 Metoda **ReportAvailabilityAtThisTime** byla vytvořena pro případ, že je třeba určit, zda je fronta k dispozici v aktuálním denním okamžiku.  
  
 Tato metoda neprovede žádnou akci, pokud <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> jsou <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> vlastnosti a stejné; protože v takovém případě je tiskárna k dispozici v tuto dobu. Pokud se liší, metoda získá aktuální čas, který je pak nutné převést na celkový počet <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> minut po půlnoci, protože vlastnosti a <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> jsou <xref:System.Int32>představující minuty-po půlnoci, ne <xref:System.DateTime> objekty. Nakonec metoda zkontroluje, zda je aktuální čas mezi začátkem a časem.  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a>Viz také:

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
- [Operátor & (C# Referenční dokumentace)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)
- [Dokumenty v platformě WPF](documents-in-wpf.md)
- [Přehled tisku](printing-overview.md)
