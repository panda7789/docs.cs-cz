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
ms.openlocfilehash: 7a2f6cd76cf44a3a6bd431e53ba0c10d3438037e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54665796"
---
# <a name="how-to-diagnose-problematic-print-job"></a>Postupy: Diagnostika problematické tiskové úlohy
Správci sítě často pole stížností od uživatelů o tiskové úlohy, které vytisknout nebo vytisknout pomalu. Bohaté sadě vlastností tiskovou úlohu v [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] Microsoft .NET Framework poskytují způsob pro provádění rychlé vzdálené diagnostiky tiskových úloh.  
  
## <a name="example"></a>Příklad  
 Hlavní kroky pro vytvoření tento druh nástroj jsou následující.  
  
1.  Identifikujte tiskové úlohy, která je stěžovat uživatele. Uživatelé často nelze provést přesně. Názvy tiskáren nebo tiskových serverů, které nemusí znají. Může popisu umístění tiskárny v odlišnou terminologii, než se používá v nastavení jeho <xref:System.Printing.PrintQueue.Location%2A> vlastnost. Proto je vhodné vytvořit seznam uživatele aktuálně odeslaných úloh. Pokud existuje více než jeden, pak komunikace mezi uživatelem a správce tiskovém systému slouží ke kotvícímu bodu na úlohu, problémy. Dílčí kroky jsou následující.  
  
    1.  Získáte seznam všech tiskových serverů.  
  
    2.  Projít servery, které chcete dotazovat jejich tiskové fronty.  
  
    3.  V každém průchodu server smyčky projděte všechny server fronty a dotazování svých úloh  
  
    4.  V každém průchodu fronty smyčky projít jeho úlohy a shromážděte identifikační informace o těch, které byly předány žalující uživatelem.  
  
2.  Pokud byla zjištěna problematické tiskové úlohy, podívejte se na relevantní vlastnosti chcete zobrazit, co může být problém. Například je úloha ve stavu chyby nebo nebyla Údržba tiskárny fronty přejít do režimu offline, než má úloha může vytisknout?  
  
 Následující kód je řada příklady kódu. První příklad kódu obsahuje projděte tiskové fronty. (Krok 1c výše). Proměnná `myPrintQueues` je <xref:System.Printing.PrintQueueCollection> objektů pro aktuální tiskový server.  
  
 Příklad kódu začíná aktualizací aktuální objekt tiskové fronty s <xref:System.Printing.PrintQueue.Refresh%2A?displayProperty=nameWithType>. Tím se zajistí, že vlastnosti objektu přesně reprezentovat stav fyzické tiskárny, který představuje. Potom aplikace získá kolekci tiskových úloh aktuálně v tiskové frontě pomocí <xref:System.Printing.PrintQueue.GetPrintJobInfoCollection%2A>.  
  
 Další aplikace prochází <xref:System.Printing.PrintSystemJobInfo> kolekce a porovná <xref:System.Printing.PrintSystemJobInfo.Submitter%2A> vlastnost s aliasem žalující uživatele. Pokud se shodují, aplikace přidá identifikační informace o úloze řetězec, který se zobrazí. ( `userName` a `jobList` proměnné jsou inicializovány dříve v aplikaci.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#enumeratejobsinqueues)]
 [!code-csharp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#enumeratejobsinqueues)]
 [!code-vb[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#enumeratejobsinqueues)]  
  
 Následující příklad kódu načte, začne používat tuto aplikaci v kroku 2. (Viz výše). Byla zjištěna problematické úlohy a aplikace vyzve k zadání informací, které bude identifikovat. Z těchto informací vytvoří <xref:System.Printing.PrintServer>, <xref:System.Printing.PrintQueue>, a <xref:System.Printing.PrintSystemJobInfo> objekty.  
  
 V tomto okamžiku aplikace obsahuje strukturu větvení odpovídající na dva způsoby, jak kontroluje se stav tiskové úlohy:  
  
-   Můžete si přečíst příznaky z <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> vlastnost, která je typu <xref:System.Printing.PrintJobStatus>.  
  
-   Můžete si přečíst každý relevantní vlastnosti, jako <xref:System.Printing.PrintSystemJobInfo.IsBlocked%2A> a <xref:System.Printing.PrintSystemJobInfo.IsInError%2A>.  
  
 Tento příklad ukazuje obě metody, uživateli se zobrazí výzva, jakou metodu použít a odpověděl zprávou "Y", pokud uživatel chce použít příznaky z <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> vlastnost. Níže naleznete podrobnosti ze dvou způsobů. A konečně aplikace používá metodu nazvanou **ReportQueueAndJobAvailability** zprávu o tom, jestli lze vytisknout úlohy v této denní době. Tato metoda je popsána v [zjistit, jestli tisk úlohy můžete být vytisknout na tento denní dobu](../../../../docs/framework/wpf/advanced/how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day.md).  
  
 [!code-cpp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#identifyanddiagnoseproblematicjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#identifyanddiagnoseproblematicjob)]
 [!code-vb[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#identifyanddiagnoseproblematicjob)]  
  
 Ke kontrole stavu úlohy pomocí příznaky z <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> vlastnost, zkontrolujte každý relevantní příznak zobrazíte, pokud je nastavena. K provedení logické operace a sadu příznaků jako jeden operand a příznak samotný jako druhý je standardní způsob, jak zobrazit, pokud jeden bit nastaven sadu bitových příznaků. Protože příznak samotný má pouze jeden bit nastaven, výsledek logické a je to, že, maximálně Tento stejný bit nastaven. Pokud chcete zjistit, jestli je nebo není, stačí porovnání výsledku logické a s příznakem samotný. Další informace najdete v tématu <xref:System.Printing.PrintJobStatus>, [& – operátor (C# odkaz)](~/docs/csharp/language-reference/operators/and-operator.md), a <xref:System.FlagsAttribute>.  
  
 Kód pro každý atribut, jehož bit nastaven, to hlásí do okna konzoly a někdy navrhuje způsob, jak reagovat. ( **HandlePausedJob** metodu, která je volána, pokud úlohy nebo fronta je pozastavená, jsou popsány níže.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobattributes)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobattributes)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobattributes)]  
  
 Ke kontrole stavu tiskové úlohy pomocí samostatné vlastnosti, jednoduše načíst každou vlastnost a, pokud je vlastnost `true`zprávu do okna konzoly a pravděpodobně navrhnout způsob, jak reagovat. ( **HandlePausedJob** metodu, která je volána, pokud úlohy nebo fronta je pozastavená, jsou popsány níže.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobproperties)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobproperties)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobproperties)]  
  
 **HandlePausedJob** metoda umožňuje uživatelům vaší aplikace vzdáleně obnovit pozastavené úlohy. Protože můžou existovat dobrý důvod, proč byla pozastavena tiskovou frontu, metoda začíná vás vyzve k zadání uživatele rozhodnutí o tom, jestli ho obnovit. Pokud je odpověď "Y", pak bude <xref:System.Printing.PrintQueue.Resume%2A?displayProperty=nameWithType> metoda je volána.  
  
 Dále bude uživatel vyzván k rozhodování, pokud by měl být obnoveno samotnou úlohu, jen v případě, že je pozastavený nezávisle na tiskovou frontu. (Porovnání <xref:System.Printing.PrintQueue.IsPaused%2A?displayProperty=nameWithType> a <xref:System.Printing.PrintSystemJobInfo.IsPaused%2A?displayProperty=nameWithType>.) Pokud je odpověď "Y", pak <xref:System.Printing.PrintSystemJobInfo.Resume%2A?displayProperty=nameWithType> volané; v opačném <xref:System.Printing.PrintSystemJobInfo.Cancel%2A> je volána.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#HandlePausedJob](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#handlepausedjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#HandlePausedJob](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#handlepausedjob)]
 [!code-vb[DiagnoseProblematicPrintJob#HandlePausedJob](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#handlepausedjob)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Printing.PrintJobStatus>
- <xref:System.Printing.PrintSystemJobInfo>
- <xref:System.FlagsAttribute>
- <xref:System.Printing.PrintQueue>
- [& – Operátor (C# odkaz)](~/docs/csharp/language-reference/operators/and-operator.md)
- [Dokumenty v platformě WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
- [Přehled tisku](../../../../docs/framework/wpf/advanced/printing-overview.md)
