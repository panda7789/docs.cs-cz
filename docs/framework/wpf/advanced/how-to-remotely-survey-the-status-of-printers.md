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
# <a name="how-to-remotely-survey-the-status-of-printers"></a>Postupy: Vzdálený průzkum stavu tiskáren
V každém okamžiku u středně velkých a velkých společností může být více tiskárny, které nejsou práce z důvodu zaseknutý papír nebo jsou mimo papír nebo jiné problematické situaci. Bohaté sadě vlastností tiskárny v [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] Microsoft .NET Framework poskytují způsob pro provádění rychlé zjišťování stavu tiskárny.  
  
## <a name="example"></a>Příklad  
 Hlavní kroky pro vytvoření tento druh nástroj jsou následující.  
  
1. Získáte seznam všech tiskových serverů.  
  
2. Projít servery, které chcete dotazovat jejich tiskové fronty.  
  
3. V každém průchodu server smyčky projít všechny serveru front a čtení každou vlastnost, která můžou značit, že fronta není aktuálně funguje.  
  
 Následující kód je posloupnost fragmenty kódu. Pro zjednodušení tento příklad předpokládá, že je seznam tiskových serverů oddělených znaky CRLF. Proměnná `fileOfPrintServers` je <xref:System.IO.StreamReader> objekt pro tento soubor. Každý název serveru je na samostatném řádku, některé volání <xref:System.IO.StreamReader.ReadLine%2A> získá název dalšího serveru a přesune <xref:System.IO.StreamReader>od kurzoru na začátek dalšího řádku.  
  
 V rámci vnější smyčky, vytvoří kód <xref:System.Printing.PrintServer> objekt pro nejnovější tiskového serveru a určuje, že aplikace je mít práva správce k serveru.  
  
> [!NOTE]
>  Pokud existuje mnoho serverů, můžete zlepšit výkon pomocí <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> konstruktory, které inicializovat pouze vlastnosti, kterou budete potřebovat.  
  
 Příklad poté použije <xref:System.Printing.PrintServer.GetPrintQueues%2A> můžete vytvořit kolekci všech serveru je zařadí do fronty a spustí se ve smyčce projde. Tento vnitřní smyčka obsahuje strukturu větvení odpovídající na dva způsoby, jak kontroluje se stav tiskárny:  
  
- Můžete si přečíst příznaky z <xref:System.Printing.PrintQueue.QueueStatus%2A> vlastnost, která je typu <xref:System.Printing.PrintQueueStatus>.  
  
- Můžete si přečíst každý relevantní vlastnosti, jako <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, a <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.  
  
 Tento příklad ukazuje obě metody, uživateli se zobrazí výzva, jakou metodu použít a odpověděl zprávou "y", pokud uživatel chce použít příznaky z <xref:System.Printing.PrintQueue.QueueStatus%2A> vlastnost. Níže naleznete podrobnosti ze dvou způsobů.  
  
 A konečně výsledky se zobrazí uživateli.  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 Ke kontrole stavu tiskárny pomocí příznaků z <xref:System.Printing.PrintQueue.QueueStatus%2A> vlastnost, zkontrolujte každý relevantní příznak zobrazíte, pokud je nastavena. K provedení logické operace a sadu příznaků jako jeden operand a příznak samotný jako druhý je standardní způsob, jak zobrazit, pokud jeden bit nastaven sadu bitových příznaků. Protože příznak samotný má pouze jeden bit nastaven, výsledek logické a je to, že, maximálně Tento stejný bit nastaven. Pokud chcete zjistit, jestli je nebo není, stačí porovnání výsledku logické a s příznakem samotný. Další informace najdete v tématu <xref:System.Printing.PrintQueueStatus>, [& – operátor (C# odkaz)](~/docs/csharp/language-reference/operators/and-operator.md), a <xref:System.FlagsAttribute>.  
  
 Pro každý atribut, jehož bit nastaven kód přidá upozornění na konečná sestava, která se zobrazí uživateli. ( **ReportAvailabilityAtThisTime** metodu, která je volána na konci kód, jsou popsány níže.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 Pokud chcete zkontrolovat stav tiskárny pomocí každou vlastnost, jednoduše čtení každou vlastnost a přidání poznámky ke Konečná sestava, která budou zobrazovat uživateli, pokud je vlastnost `true`. ( **ReportAvailabilityAtThisTime** metodu, která je volána na konci kód, jsou popsány níže.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 **ReportAvailabilityAtThisTime** metoda byl vytvořen v případě, že je potřeba určit, zda je fronta dostupná v současné době den.  
  
 Metoda neudělá Pokud <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> a <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> vlastnosti jsou stejné; protože v takovém případě tiskárna není k dispozici po celou dobu. Pokud se liší, metoda získá aktuální čas, který má být převeden do celkový počet minut po půlnoci, protože nemá <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> a <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> vlastnosti jsou <xref:System.Int32>s představující minut po půlnoc, ne <xref:System.DateTime> objekty. Nakonec metoda zkontroluje, pokud je aktuální čas mezi začátky a "až" časy.  
  
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
- [& – Operátor (C# odkaz)](~/docs/csharp/language-reference/operators/and-operator.md)
- [Dokumenty v platformě WPF](documents-in-wpf.md)
- [Přehled tisku](printing-overview.md)
