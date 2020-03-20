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
# <a name="how-to-remotely-survey-the-status-of-printers"></a>Postupy: Vzdálené zjištění stavu tiskáren
V daném okamžiku ve středních a velkých společnostech může existovat více tiskáren, které nefungují kvůli uvíznutí papíru nebo nedostatku papíru nebo jiné problematické situaci. Bohatá sada vlastností tiskárny vystavených v rozhraních API rozhraní Microsoft .NET Framework poskytuje prostředky pro provádění rychlého průzkumu stavů tiskáren.  
  
## <a name="example"></a>Příklad  
 Hlavní kroky pro vytvoření tohoto druhu nástroje jsou následující.  
  
1. Získejte seznam všech tiskových serverů.  
  
2. Smyčka prostřednictvím serverů k dotazování jejich tiskové fronty.  
  
3. V rámci každého průchodu smyčky serveru projděte všechny fronty serveru a přečtěte si každou vlastnost, která může znamenat, že fronta právě nefunguje.  
  
 Níže uvedený kód je řada výstřižků. Pro jednoduchost tento příklad předpokládá, že existuje seznam tiskových serverů oddělený crlf. Proměnná `fileOfPrintServers` je <xref:System.IO.StreamReader> objekt pro tento soubor. Vzhledem k tomu, že každý název <xref:System.IO.StreamReader.ReadLine%2A> serveru je na svém vlastním <xref:System.IO.StreamReader>řádku, každé volání získá název dalšího serveru a přesune kurzor 's na začátek dalšího řádku.  
  
 V rámci vnější smyčky kód <xref:System.Printing.PrintServer> vytvoří objekt pro nejnovější tiskový server a určuje, že aplikace má mít práva správce k serveru.  
  
> [!NOTE]
> Pokud existuje mnoho serverů, můžete zlepšit výkon <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> pomocí konstruktory, které pouze inicializovat vlastnosti, které budete potřebovat.  
  
 Příklad pak <xref:System.Printing.PrintServer.GetPrintQueues%2A> používá k vytvoření kolekce všech front serveru a začne smyčku přes ně. Tato vnitřní smyčka obsahuje strukturu větvení odpovídající dvěma způsobům kontroly stavu tiskárny:  
  
- Můžete si přečíst <xref:System.Printing.PrintQueue.QueueStatus%2A> příznaky vlastnosti, <xref:System.Printing.PrintQueueStatus>která je typu .  
  
- Můžete si přečíst každou <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>příslušnou <xref:System.Printing.PrintQueue.IsPaperJammed%2A>vlastnost, například . a .  
  
 Tento příklad ukazuje obě metody, takže uživatel byl dříve vyzván, jakou metodu použít a odpověděl "y", pokud chtěli použít příznaky <xref:System.Printing.PrintQueue.QueueStatus%2A> vlastnosti. Podrobnosti o těchto dvou metodách naleznete níže.  
  
 Nakonec jsou výsledky prezentovány uživateli.  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 Chcete-li zkontrolovat stav tiskárny pomocí příznaků vlastnosti, <xref:System.Printing.PrintQueue.QueueStatus%2A> zkontrolujte každý příslušný příznak a zjistěte, zda je nastaven. Standardní způsob, jak zjistit, zda jeden bit je nastaven v sadě příznaků bitů je provést logickou operaci and se sadou příznaků jako jeden operand a příznak sám jako druhý. Vzhledem k tomu, že příznak sám má pouze jeden bit nastavit, výsledkem logické and je, že nanejvýš, že stejný bit je nastaven. Chcete-li zjistit, zda je či není, stačí porovnat výsledek logické and s příznakem sám. Další informace naleznete <xref:System.Printing.PrintQueueStatus>v [tématech operátor& (C# Reference)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)a <xref:System.FlagsAttribute>.  
  
 Pro každý atribut, jehož bit je nastaven, kód přidá oznámení do závěrečné sestavy, která bude předložena uživateli. (Metoda **ReportAvailabilityAtThisTime,** která je volána na konci kódu, je popsána níže.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 Chcete-li zkontrolovat stav tiskárny pomocí jednotlivých vlastností, jednoduše si přečtěte každou vlastnost a `true`přidejte poznámku do závěrečné sestavy, která bude uživateli předložena, pokud je vlastnost . (Metoda **ReportAvailabilityAtThisTime,** která je volána na konci kódu, je popsána níže.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 **Metoda ReportAvailabilityAtThisTime** byla vytvořena v případě, že potřebujete zjistit, zda je fronta k dispozici v aktuální denní době.  
  
 Metoda nebude dělat <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> nic, <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> pokud a vlastnosti jsou stejné; protože v takovém případě je tiskárna vždy k dispozici. Pokud se liší, metoda získá aktuální čas, který pak musí být převedeny na celkový počet minut po půlnoci, <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> protože vlastnosti a <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> představují <xref:System.Int32>minuty po půlnoci, nikoli <xref:System.DateTime> objekty. Nakonec metoda zkontroluje, zda aktuální čas je mezi počáteční a "do" časy.  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a>Viz také

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
- [operátor& (odkaz jazyka C#)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)
- [Dokumenty v platformě WPF](documents-in-wpf.md)
- [Přehled tisku](printing-overview.md)
