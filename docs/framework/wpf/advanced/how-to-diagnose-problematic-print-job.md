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
ms.openlocfilehash: 15de5d9ec8dc4016753b9d4cbed6fb0c64571774
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186046"
---
# <a name="how-to-diagnose-problematic-print-job"></a>Postupy: Diagnostika problematické tiskové úlohy
Správci sítě často vyčleňují stížnosti uživatelů na tiskové úlohy, které se netisknou ani netisknou pomalu. Bohatá sada vlastností tiskové úlohy vystavených v rozhraních API rozhraní Microsoft .NET Framework poskytuje prostředky pro provádění rychlé vzdálené diagnostiky tiskových úloh.  
  
## <a name="example"></a>Příklad  
 Hlavní kroky pro vytvoření tohoto druhu nástroje jsou následující.  
  
1. Identifikujte tiskovou úlohu, na kterou si uživatel stěžuje. Uživatelé to často nemohou udělat přesně. Pravděpodobně neznají názvy tiskových serverů nebo tiskáren. Mohou popisovat umístění tiskárny v jiné terminologii, <xref:System.Printing.PrintQueue.Location%2A> než byla použita při nastavování její vlastnosti. Proto je vhodné vytvořit seznam aktuálně odeslaných úloh uživatele. Pokud existuje více než jeden, pak komunikace mezi uživatelem a správce tiskového systému lze určit úlohu, která má problémy. Dílčí kroky jsou následující.  
  
    1. Získejte seznam všech tiskových serverů.  
  
    2. Smyčka prostřednictvím serverů k dotazování jejich tiskové fronty.  
  
    3. V rámci každého průchodu serversmyčky, smyčka přes všechny fronty serveru k dotazu jejich úlohy  
  
    4. V rámci každého průchodu smyčky fronty, smyčka prostřednictvím svých úloh a shromažďovat identifikační informace o těch, které byly odeslány stěžující si uživatele.  
  
2. Po identifikaci problematické tiskové úlohy zkontrolujte příslušné vlastnosti, abyste zjistili, v čem může být problém. Je například úloha v chybovém stavu nebo přešel a vypnul a před tiskem úlohy přešel do vypnuté funkce tiskárny obsluhující frontu?  
  
 Níže uvedený kód je řada příkladů kódu. První příklad kódu obsahuje smyčku přes tiskové fronty. (Krok 1c výše.) Proměnná `myPrintQueues` je <xref:System.Printing.PrintQueueCollection> objekt pro aktuální tiskový server.  
  
 Příklad kódu začíná aktualizací aktuálního objektu <xref:System.Printing.PrintQueue.Refresh%2A?displayProperty=nameWithType>tiskové fronty pomocí aplikace . Tím je zajištěno, že vlastnosti objektu přesně představují stav fyzické tiskárny, která představuje. Potom aplikace získá kolekci tiskových úloh aktuálně v <xref:System.Printing.PrintQueue.GetPrintJobInfoCollection%2A>tiskové frontě pomocí .  
  
 Dále aplikace smyčky prostřednictvím <xref:System.Printing.PrintSystemJobInfo> kolekce a <xref:System.Printing.PrintSystemJobInfo.Submitter%2A> porovná každou vlastnost s alias emitující uživatele. Pokud se shodují, aplikace přidá identifikační informace o úloze do řetězce, který bude prezentován. (A `userName` `jobList` proměnné jsou inicializovány dříve v aplikaci.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#enumeratejobsinqueues)]
 [!code-csharp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#enumeratejobsinqueues)]
 [!code-vb[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#enumeratejobsinqueues)]  
  
 Další příklad kódu vyzvedne aplikaci v kroku 2. (Viz výše.) Problematická úloha byla identifikována a aplikace vyzve k zadání informací, které ji identifikují. Z těchto informací <xref:System.Printing.PrintServer> <xref:System.Printing.PrintQueue>vytvoří <xref:System.Printing.PrintSystemJobInfo> , a objekty.  
  
 V tomto okamžiku aplikace obsahuje strukturu větvení odpovídající dvěma způsobům kontroly stavu tiskové úlohy:  
  
- Můžete si přečíst <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> příznaky vlastnosti, <xref:System.Printing.PrintJobStatus>která je typu .  
  
- Můžete si přečíst každou <xref:System.Printing.PrintSystemJobInfo.IsBlocked%2A> <xref:System.Printing.PrintSystemJobInfo.IsInError%2A>relevantní vlastnost, například a .  
  
 Tento příklad ukazuje obě metody, takže uživatel byl dříve vyzván, jakou metodu použít a odpověděl "Y", pokud chtěli použít příznaky <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> vlastnosti. Podrobnosti o těchto dvou metodách naleznete níže. Nakonec aplikace používá metodu s názvem **ReportQueueAndJobAvailability** k hlášení o tom, zda lze úlohu vytisknout v tuto denní dobu. Tato metoda je popsána v [zjistit, zda lze vytisknout tiskovou úlohu v tuto denní dobu](how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day.md).  
  
 [!code-cpp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#identifyanddiagnoseproblematicjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#identifyanddiagnoseproblematicjob)]
 [!code-vb[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#identifyanddiagnoseproblematicjob)]  
  
 Chcete-li zkontrolovat stav tiskové <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> úlohy pomocí příznaků vlastnosti, zkontrolujte každý příslušný příznak a zjistěte, zda je nastaven. Standardní způsob, jak zjistit, zda jeden bit je nastaven v sadě příznaků bitů je provést logickou operaci and se sadou příznaků jako jeden operand a příznak sám jako druhý. Vzhledem k tomu, že příznak sám má pouze jeden bit nastavit, výsledkem logické and je, že nanejvýš, že stejný bit je nastaven. Chcete-li zjistit, zda je či není, stačí porovnat výsledek logické and s příznakem sám. Další informace naleznete <xref:System.Printing.PrintJobStatus>v [tématech operátor& (C# Reference)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)a <xref:System.FlagsAttribute>.  
  
 Pro každý atribut, jehož bit je nastaven, kód hlásí to na obrazovce konzoly a někdy navrhuje způsob, jak reagovat. **(HandlePausedJob** metoda, která je volána, pokud je pozastavena úloha nebo fronty je popsána níže.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobattributes)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobattributes)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobattributes)]  
  
 Chcete-li zkontrolovat stav tiskové úlohy pomocí samostatných vlastností, jednoduše si přečtěte každou vlastnost a pokud je `true`vlastnost , sestavy na obrazovce konzoly a případně navrhnout způsob, jak reagovat. **(HandlePausedJob** metoda, která je volána, pokud je pozastavena úloha nebo fronty je popsána níže.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobproperties)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobproperties)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobproperties)]  
  
 Metoda **HandlePausedJob** umožňuje uživateli aplikace vzdáleně obnovit pozastavené úlohy. Vzhledem k tomu, že může existovat dobrý důvod, proč byla tisková fronta pozastavena, metoda začíná výzvou k rozhodnutí uživatele o tom, zda ji obnovit. Pokud je odpověď "Y", <xref:System.Printing.PrintQueue.Resume%2A?displayProperty=nameWithType> pak je volána metoda.  
  
 Dále je uživatel vyzván k rozhodnutí, zda má být úloha obnovena, pouze v případě, že je pozastavena nezávisle na tiskové frontě. (Porovnat <xref:System.Printing.PrintQueue.IsPaused%2A?displayProperty=nameWithType> <xref:System.Printing.PrintSystemJobInfo.IsPaused%2A?displayProperty=nameWithType>a .) Je-li odpověď "Y", pak <xref:System.Printing.PrintSystemJobInfo.Resume%2A?displayProperty=nameWithType> se nazývá; jinak <xref:System.Printing.PrintSystemJobInfo.Cancel%2A> se nazývá.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#handlepausedjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#handlepausedjob)]
 [!code-vb[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#handlepausedjob)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Printing.PrintJobStatus>
- <xref:System.Printing.PrintSystemJobInfo>
- <xref:System.FlagsAttribute>
- <xref:System.Printing.PrintQueue>
- [operátor& (odkaz jazyka C#)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)
- [Dokumenty v platformě WPF](documents-in-wpf.md)
- [Přehled tisku](printing-overview.md)
