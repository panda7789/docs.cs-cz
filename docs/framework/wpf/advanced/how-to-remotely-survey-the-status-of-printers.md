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
---
# <a name="how-to-remotely-survey-the-status-of-printers"></a>Postupy: Vzdálené zjištění stavu tiskáren
V každém okamžiku v střední a velké společnosti může být více tiskárny, které nejsou práce z důvodu uvíznutí papíru nebo se z dokumentu nebo jiné problematické situaci. Bohatá sada vlastností tiskárny v [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] Microsoft .NET Framework poskytují způsob pro provádění rychlé dotazník stavů tiskáren.  
  
## <a name="example"></a>Příklad  
 Hlavní kroky pro vytvoření tento druh nástroj jsou následující.  
  
1.  Získejte seznam všech tiskových serverů.  
  
2.  Projděte serverů, které chcete dotazovat jejich tiskové fronty.  
  
3.  V každém průchodu smyčky serveru procházení všechny server front a číst každou vlastnost, jež může naznačovat, že není aktuálně funguje fronty.  
  
 Následující kód je řadu fragmenty kódu. Pro zjednodušení tento příklad předpokládá, že je seznam s položkami oddělenými Line FEED tiskových serverů. Proměnná `fileOfPrintServers` je <xref:System.IO.StreamReader> objekt pro tento soubor. Vzhledem k tomu, že každý název serveru je ve svém vlastním řádku, žádném volání z <xref:System.IO.StreamReader.ReadLine%2A> získá název další server a přejde <xref:System.IO.StreamReader>na kurzor na začátek na další řádek.  
  
 V rámci vnějšího smyčky, kód vytvoří <xref:System.Printing.PrintServer> objekt pro nejnovější tiskového serveru a určuje, že aplikace bude mít oprávnění správce k serveru.  
  
> [!NOTE]
>  Pokud existuje mnoho serverů, můžete zlepšit výkon pomocí <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> konstruktory, které pouze inicializace vlastností, kterou budete potřebovat.  
  
 V příkladu se pak použije <xref:System.Printing.PrintServer.GetPrintQueues%2A> můžete vytvořit kolekci všech serveru je fronty a začne procházení je. Tato vnitřní smyčka obsahuje větvení struktura odpovídající na dva způsoby, jak kontrolovat stav tiskárny:  
  
-   Příznaky systému si můžete přečíst <xref:System.Printing.PrintQueue.QueueStatus%2A> vlastnost, která je typu <xref:System.Printing.PrintQueueStatus>.  
  
-   Můžete si přečíst každé příslušné vlastnosti, jako <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, a <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.  
  
 Tento příklad ukazuje obě metody tak, aby byl uživatel dříve zobrazí výzva, kterou metodu použít a odpověděla s "y", pokud mu chtěli použít příznaky z <xref:System.Printing.PrintQueue.QueueStatus%2A> vlastnost. Níže naleznete podrobnosti o tyto dvě metody.  
  
 Nakonec výsledky se zobrazí uživateli.  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 Zkontrolujte stav tiskárny s použitím příznaků z <xref:System.Printing.PrintQueue.QueueStatus%2A> vlastnost, zkontrolujte každý relevantní příznak, pokud je nastavena. Standardní způsob, jak zobrazit, pokud je v sadě bitové příznaky nastavit jeden bit je logické a operace sadou příznaky jako jeden operand a příznak sám sebe jako na druhý. Vzhledem k tomu, že příznak samotné má jenom jeden bit, nastavit, výsledek logické a je, že, maximálně Tento stejný bit nastavený. Pokud chcete zjistit, zda je nebo není, porovnejte právě výsledek logické a s příznakem sám sebe. Další informace najdete v tématu <xref:System.Printing.PrintQueueStatus>, [& – operátor (referenční dokumentace jazyka C#)](~/docs/csharp/language-reference/operators/and-operator.md), a <xref:System.FlagsAttribute>.  
  
 Pro každý atribut, jehož bit nastaven přidá kód oznámení závěrečnou zprávu, která bude zobrazovat uživatelům. ( **ReportAvailabilityAtThisTime** metoda, která je volána na konci tohoto kódu je popsána níže.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 Pokud chcete zkontrolovat stav tiskárny pomocí každou vlastnost, jednoduše přečíst si každou vlastnost a přidání poznámky do konečné sestavy, které budou zobrazovat uživateli, pokud je vlastnost `true`. ( **ReportAvailabilityAtThisTime** metoda, která je volána na konci tohoto kódu je popsána níže.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 **ReportAvailabilityAtThisTime** metoda byla vytvořena v případě, že budete muset určit, zda je fronta k dispozici v aktuální denní čas.  
  
 Metoda se nic nestane. Pokud <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> a <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> vlastnosti jsou stejné; protože v takovém případě tiskárna není k dispozici za všech okolností. Pokud se liší, metoda získá aktuální čas, který pak musí být převeden do celkový počet minut po půlnoci, protože <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> a <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> vlastnosti jsou <xref:System.Int32>s představující minut po půlnoc, není <xref:System.DateTime> objekty. Nakonec metodu zkontroluje, pokud je aktuální čas mezi začátkem a "do" časy.  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a>Viz také  
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
 [& – Operátor (referenční dokumentace jazyka C#)](~/docs/csharp/language-reference/operators/and-operator.md)  
 [Dokumenty v platformě WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Přehled tisku](../../../../docs/framework/wpf/advanced/printing-overview.md)
