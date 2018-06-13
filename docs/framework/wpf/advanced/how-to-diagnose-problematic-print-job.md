---
title: 'Postupy: Diagnostika problematické tiskové úlohy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- troubleshooting print job problems [WPF]
- print jobs [WPF], troubleshooting
- print jobs [WPF], diagnosing problems
ms.assetid: b081a170-84c6-48f9-a487-5766a8d58a82
ms.openlocfilehash: 2010c911bd164570a82f23a939622f342810761f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546738"
---
# <a name="how-to-diagnose-problematic-print-job"></a>Postupy: Diagnostika problematické tiskové úlohy
Správci sítě často pole stížností od uživatelů o tiskové úlohy, které vytisknout nebo vytisknout pomalu. Bohatá sada vlastností tiskových úloh v [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] Microsoft .NET Framework poskytují způsob pro provádění rychlé vzdálenou diagnostiku tiskových úloh.  
  
## <a name="example"></a>Příklad  
 Hlavní kroky pro vytvoření tento druh nástroj jsou následující.  
  
1.  Identifikujte tiskovou úlohu, která je stěžovat uživatele. Uživatelé často nelze provést přesněji. Se nemusí znát názvy tiskáren nebo tiskových serverů. Oproti nastavení může popisují umístění tiskárny v odlišnou terminologii jeho <xref:System.Printing.PrintQueue.Location%2A> vlastnost. Proto je vhodné vytvořit seznam uživatele aktuálně předat úlohy. Pokud existuje více než jeden, můžete komunikace mezi uživatelem a tiskový systém správce použít ke kotvícímu bodu na úlohu, která má potíže. Dílčích kroků jsou následujícím způsobem.  
  
    1.  Získejte seznam všech tiskových serverů.  
  
    2.  Projděte serverů, které chcete dotazovat jejich tiskové fronty.  
  
    3.  V každém průchodu smyčky serveru projděte všechny server fronty k dotazování svou práci  
  
    4.  V každém průchodu smyčky fronty procházení jeho úlohy a shromážděte identifikační informace o ty, které byly odeslány žalující uživatelem.  
  
2.  Pokud byla zjištěna problematické tiskové úlohy, podívejte se na relevantní vlastnosti chcete zobrazit, co může být problém. Například je úloha ve stavu chyby nebo nebyla tiskárny obsluhy fronty přejít do režimu offline dříve, než může tisknout úlohu?  
  
 Následující kód je řadu příklady kódu. V prvním příkladu kódu obsahuje cyklus prostřednictvím tiskové fronty. (Krok 1c výše). Proměnná `myPrintQueues` je <xref:System.Printing.PrintQueueCollection> objekt pro aktuální tiskový server.  
  
 Příklad kódu začne aktualizujte aktuální objekt tiskové fronty s <xref:System.Printing.PrintQueue.Refresh%2A?displayProperty=nameWithType>. Tím se zajistí, že vlastností objektu přesně reprezentovat stav fyzické tiskárny, který reprezentuje. Pak aplikace získá kolekci tiskové úlohy aktuálně v tiskové frontě pomocí <xref:System.Printing.PrintQueue.GetPrintJobInfoCollection%2A>.  
  
 Další aplikace projde <xref:System.Printing.PrintSystemJobInfo> kolekce a porovnává <xref:System.Printing.PrintSystemJobInfo.Submitter%2A> vlastnost s aliasem žalující uživatele. Pokud se shodují, aplikace přidá řetězec, který zobrazí identifikační informace o úloze. ( `userName` a `jobList` proměnné se inicializují dříve v aplikaci.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#enumeratejobsinqueues)]
 [!code-csharp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#enumeratejobsinqueues)]
 [!code-vb[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#enumeratejobsinqueues)]  
  
 Další příklad kódu převezme aplikace v kroku 2. (Viz výše). Byla zjištěna problematické úlohy a aplikace vyzve k zadání informací, které bude identifikovat. Z těchto informací vytvoří <xref:System.Printing.PrintServer>, <xref:System.Printing.PrintQueue>, a <xref:System.Printing.PrintSystemJobInfo> objekty.  
  
 V tomto okamžiku aplikace obsahuje větvení struktura odpovídající na dva způsoby, jak kontrolovat stav tiskové úlohy:  
  
-   Příznaky systému si můžete přečíst <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> vlastnost, která je typu <xref:System.Printing.PrintJobStatus>.  
  
-   Můžete si přečíst každé příslušné vlastnosti, jako <xref:System.Printing.PrintSystemJobInfo.IsBlocked%2A> a <xref:System.Printing.PrintSystemJobInfo.IsInError%2A>.  
  
 Tento příklad ukazuje obě metody tak, aby byl uživatel dříve zobrazí výzva, kterou metodu použít a odpověděla s "Y", pokud mu chtěli použít příznaky z <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> vlastnost. Níže naleznete podrobnosti o tyto dvě metody. Nakonec aplikace používá metodu s názvem **ReportQueueAndJobAvailability** zprávu o tom, jestli může úloha vytištěna v tuto chvíli den. Tato metoda je popsána v [zjistit, jestli tiskových úlohy můžete být vytisknout v tento čas z den](../../../../docs/framework/wpf/advanced/how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day.md).  
  
 [!code-cpp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#identifyanddiagnoseproblematicjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#identifyanddiagnoseproblematicjob)]
 [!code-vb[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#identifyanddiagnoseproblematicjob)]  
  
 Zkontrolujte stav tiskové úlohy s použitím příznaků z <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> vlastnost, zkontrolujte každý relevantní příznak, pokud je nastavena. Standardní způsob, jak zobrazit, pokud je v sadě bitové příznaky nastavit jeden bit je logické a operace sadou příznaky jako jeden operand a příznak sám sebe jako na druhý. Vzhledem k tomu, že příznak samotné má jenom jeden bit, nastavit, výsledek logické a je, že, maximálně Tento stejný bit nastavený. Pokud chcete zjistit, zda je nebo není, porovnejte právě výsledek logické a s příznakem sám sebe. Další informace najdete v tématu <xref:System.Printing.PrintJobStatus>, [& – operátor (referenční dokumentace jazyka C#)](~/docs/csharp/language-reference/operators/and-operator.md), a <xref:System.FlagsAttribute>.  
  
 Pro každý atribut, jehož bit nastaven kód to sestavy k obrazovce konzoly a někdy navrhne způsob, jak reagovat. ( **HandlePausedJob** metoda, která je volána, když je pozastavená úloha nebo fronty jsou uvedeny níže.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobattributes)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobattributes)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobattributes)]  
  
 Ke kontrole stavu tiskové úlohy pomocí samostatných vlastnosti, jednoduše číst každou vlastnost a pokud je vlastnost `true`, sestavy k obrazovce konzoly a případně Navrhněte způsob, jak reagovat. ( **HandlePausedJob** metoda, která je volána, když je pozastavená úloha nebo fronty jsou uvedeny níže.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobproperties)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobproperties)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobproperties)]  
  
 **HandlePausedJob** metoda umožňuje uživatelům aplikace vzdáleně obnovit pozastavené úlohy. Vzhledem k tomu může být dobrým důvod, proč byla pozastavena tiskové fronty, metoda začíná výzvy pro uživatele rozhodnutí o tom, jestli ho obnoví. Je-li odpověď "Y", pak se <xref:System.Printing.PrintQueue.Resume%2A?displayProperty=nameWithType> metoda je volána.  
  
 Potom bude uživatel vyzván k rozhodování, pokud úlohy sám by byl obnoven, jen v případě, že je pozastavený nezávisle na tiskovou frontu. (Porovnat <xref:System.Printing.PrintQueue.IsPaused%2A?displayProperty=nameWithType> a <xref:System.Printing.PrintSystemJobInfo.IsPaused%2A?displayProperty=nameWithType>.) Pokud je odpověď "Y", pak <xref:System.Printing.PrintSystemJobInfo.Resume%2A?displayProperty=nameWithType> je jinak <xref:System.Printing.PrintSystemJobInfo.Cancel%2A> je volána.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#HandlePausedJob](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#handlepausedjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#HandlePausedJob](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#handlepausedjob)]
 [!code-vb[DiagnoseProblematicPrintJob#HandlePausedJob](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#handlepausedjob)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Printing.PrintJobStatus>  
 <xref:System.Printing.PrintSystemJobInfo>  
 <xref:System.FlagsAttribute>  
 <xref:System.Printing.PrintQueue>  
 [& – Operátor (referenční dokumentace jazyka C#)](~/docs/csharp/language-reference/operators/and-operator.md)  
 [Dokumenty v platformě WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Přehled tisku](../../../../docs/framework/wpf/advanced/printing-overview.md)
