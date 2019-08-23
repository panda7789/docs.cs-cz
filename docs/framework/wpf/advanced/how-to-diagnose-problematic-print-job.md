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
ms.openlocfilehash: 181248f69684860fd43648952ef4eb3cced1c0ba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944637"
---
# <a name="how-to-diagnose-problematic-print-job"></a>Postupy: Diagnostika problematické tiskové úlohy
Správci sítě často používají stížnosti od uživatelů k tiskovým úlohám, které nefungují pomalu ani netisknou. Bohatá sada vlastností tiskové úlohy zveřejněná v rozhraní API Microsoft .NET Framework poskytuje způsob, jak rychle provést rychlou vzdálenou diagnostiku tiskových úloh.  
  
## <a name="example"></a>Příklad  
 Hlavní kroky pro vytvoření tohoto typu nástroje jsou následující.  
  
1. Určete tiskovou úlohu, o které uživatel nastížností. Uživatelé to často nemůžou dělat přesně. Nemusí znát názvy tiskových serverů nebo tiskáren. Můžou popsat umístění tiskárny v jiné terminologii, než se použila při nastavení její <xref:System.Printing.PrintQueue.Location%2A> vlastnosti. V důsledku toho je vhodné vygenerovat seznam aktuálně odeslaných úloh uživatele. Pokud je k dispozici více než jedna, je možné použít komunikaci mezi uživatelem a správcem tiskového systému k určení úlohy, u které dochází k problémům. Níže jsou uvedené podkroky.  
  
    1. Získejte seznam všech tiskových serverů.  
  
    2. Projděte servery a Dotazujte tiskové fronty.  
  
    3. V rámci každého průchodu smyčky serveru projdete všemi frontami serveru dotazování na úlohy.  
  
    4. V rámci každého průchodu smyčky frontu prochází úlohy a shromažďují se informace o těch, které poslal uživatel stížnosti.  
  
2. Když je zjištěna problematická tisková úloha, prostudujte si příslušné vlastnosti, abyste zjistili, co by mohlo být problém. Například úloha je v chybovém stavu nebo tiskárna obsluhuje, že fronta přejde do režimu offline, aby mohla úloha tisknout?  
  
 Níže uvedený kód je série příkladů kódu. První příklad kódu obsahuje smyčku prostřednictvím tiskových front. (Krok 1C výše.) `myPrintQueues` Proměnná<xref:System.Printing.PrintQueueCollection> je objekt aktuálního tiskového serveru.  
  
 Příklad kódu začíná aktualizací aktuálního objektu tiskové fronty pomocí <xref:System.Printing.PrintQueue.Refresh%2A?displayProperty=nameWithType>. Tím se zajistí, že vlastnosti objektu přesně reprezentují stav fyzické tiskárny, kterou představuje. Pak aplikace získá kolekci tiskových úloh, které jsou aktuálně v tiskové frontě, <xref:System.Printing.PrintQueue.GetPrintJobInfoCollection%2A>pomocí.  
  
 V dalším cyklu aplikace projde <xref:System.Printing.PrintSystemJobInfo> kolekce a porovná každou <xref:System.Printing.PrintSystemJobInfo.Submitter%2A> vlastnost s aliasem uživatele, který je stěžovatel. Pokud se shodují, aplikace přidá identifikační informace o úloze do řetězce, který se zobrazí. (Proměnné `jobList` a jsou inicializovány dříve v aplikaci.) `userName`  
  
 [!code-cpp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#enumeratejobsinqueues)]
 [!code-csharp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#enumeratejobsinqueues)]
 [!code-vb[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#enumeratejobsinqueues)]  
  
 Následující příklad kódu v kroku 2 vybere aplikaci. (Viz výše.) Byla zjištěna problematická úloha a aplikace zobrazí výzvu k zadání informací, které ji identifikují. Z těchto informací vytvoří <xref:System.Printing.PrintServer>objekty, <xref:System.Printing.PrintQueue>a. <xref:System.Printing.PrintSystemJobInfo>  
  
 V tomto okamžiku aplikace obsahuje strukturu větvení odpovídající dvěma způsobům kontroly stavu tiskové úlohy:  
  
- Můžete číst příznaky <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> vlastnosti, která je typu <xref:System.Printing.PrintJobStatus>.  
  
- Můžete číst jednotlivé relevantní vlastnosti, jako jsou <xref:System.Printing.PrintSystemJobInfo.IsBlocked%2A> a <xref:System.Printing.PrintSystemJobInfo.IsInError%2A>.  
  
 Tento příklad ukazuje obě metody, takže uživatel byl dříve vyzván, aby se použila metoda a odpovídala "Y", pokud chtěla použít příznaky <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> vlastnosti. Podrobnosti o těchto dvou metodách najdete níže. Nakonec aplikace používá metodu nazvanou **ReportQueueAndJobAvailability** k tomu, aby nahlásila, zda lze úlohu v této denní době vytisknout. Tato metoda je popsána v tématu [zjištění, zda lze vytisknout tiskovou úlohu v této denní době](how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day.md).  
  
 [!code-cpp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#identifyanddiagnoseproblematicjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#identifyanddiagnoseproblematicjob)]
 [!code-vb[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#identifyanddiagnoseproblematicjob)]  
  
 Chcete-li kontrolovat stav tiskových úloh pomocí příznaků <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> vlastnosti, zkontrolujte každý příslušný příznak, abyste viděli, zda je nastavena. Standardní způsob, jak zjistit, zda je jeden bit nastaven v sadě bitových příznaků, je provést logickou operaci a s množinou příznaků jako jeden operand a příznak jako druhý. Vzhledem k tomu, že příznak samotný má pouze jednu bitovou sadu, výsledek logického typu a je, který je nanejvýš stejný jako bit nastaven. Chcete-li zjistit, zda je nebo není, stačí porovnat výsledek logického operátoru a samotného příznaku. Další informace naleznete v tématu <xref:System.Printing.PrintJobStatus>, [operátor & (C# Referenční dokumentace)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)a. <xref:System.FlagsAttribute>  
  
 Pro každý atribut, jehož bit je nastaven, kód hlásí obrazovku konzoly a někdy navrhuje způsob, jak reagovat. (Metoda **HandlePausedJob** , která je volána, pokud je úloha nebo fronta pozastavena, je popsána níže.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobattributes)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobattributes)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobattributes)]  
  
 Chcete-li kontrolovat stav tiskové úlohy pomocí samostatných vlastností, jednoduše si přečtete jednotlivé vlastnosti a pokud je `true`vlastnost, nahlaste obrazovku konzoly a pravděpodobně navrhnete způsob, jak reagovat. (Metoda **HandlePausedJob** , která je volána, pokud je úloha nebo fronta pozastavena, je popsána níže.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobproperties)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobproperties)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobproperties)]  
  
 Metoda **HandlePausedJob** umožňuje uživateli aplikace vzdáleně obnovit pozastavené úlohy. Vzhledem k tomu, že existuje dobrý důvod, proč se tisková fronta pozastavila, metoda začíná dotazem na rozhodnutí uživatele o tom, jestli se má obnovit. Pokud je odpověď "Y", pak <xref:System.Printing.PrintQueue.Resume%2A?displayProperty=nameWithType> je volána metoda.  
  
 V dalším kroku se zobrazí výzva k rozhodnutí, zda by měla být úloha obnovena, a to pouze v případě, že je pozastavena nezávisle na tiskové frontě. (Porovnat <xref:System.Printing.PrintQueue.IsPaused%2A?displayProperty=nameWithType> a <xref:System.Printing.PrintSystemJobInfo.IsPaused%2A?displayProperty=nameWithType>.) Pokud je odpověď "Y", pak <xref:System.Printing.PrintSystemJobInfo.Resume%2A?displayProperty=nameWithType> je volána; jinak <xref:System.Printing.PrintSystemJobInfo.Cancel%2A> je volána.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#handlepausedjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#handlepausedjob)]
 [!code-vb[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#handlepausedjob)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Printing.PrintJobStatus>
- <xref:System.Printing.PrintSystemJobInfo>
- <xref:System.FlagsAttribute>
- <xref:System.Printing.PrintQueue>
- [Operátor & (C# Referenční dokumentace)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)
- [Dokumenty v platformě WPF](documents-in-wpf.md)
- [Přehled tisku](printing-overview.md)
