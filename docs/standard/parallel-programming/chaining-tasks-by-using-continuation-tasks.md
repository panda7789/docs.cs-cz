---
title: Řetězení úloh pomocí úloh pokračování
ms.date: 02/11/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, continuations
ms.assetid: 0b45e9a2-de28-46ce-8212-1817280ed42d
ms.openlocfilehash: 7de8c4e44e1866e3df36c666c9ecc210dc6a7d83
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159361"
---
# <a name="chaining-tasks-by-using-continuation-tasks"></a>Řetězení úloh pomocí úloh pokračování
V asynchronním programování je běžné, že jedna asynchronní operace po dokončení vyvolá druhou operaci a předá jí data. Tradičně pokračování byly provedeny pomocí metody zpětného volání. V paralelní knihovně úloh je stejná funkce poskytována *úlohami pokračování*. Úloha pokračování (označovaná také jako pokračování) je asynchronní úloha, která je vyvolána jinou úlohou, která se nazývá *předchůdce*, když předchůdce dokončí.  
  
 Pokračování jsou poměrně snadné použití, ale přesto jsou silné a flexibilní. Můžete například provést následující věci:  
  
- Předá data z předchůdce pokračování.  
  
- Určete přesné podmínky, za kterých bude pokračování vyvoláno nebo není vyvoláno.  
  
- Zrušte pokračování před spuštěním nebo kooperativně, jak je spuštěno.  
  
- Poskytněte rady o tom, jak by mělo být naplánováno pokračování.  
  
- Vyvolat více pokračování ze stejného předchůdce.  
  
- Vyvolat jedno pokračování po dokončení všech nebo některé z více předchůdců.  
  
- Řetěz pokračuje jeden po druhém na libovolnou délku.  
  
- Použijte pokračování pro zpracování výjimek vyzdvižených předchůdcem.  
  
## <a name="about-continuations"></a>Pokračování  
 Pokračování je úkol, který je <xref:System.Threading.Tasks.TaskStatus.WaitingForActivation> vytvořen ve stavu. Aktivuje se automaticky po dokončení předchozího úkolu nebo úkolů. Volání <xref:System.Threading.Tasks.Task.Start%2A?displayProperty=nameWithType> na pokračování v uživatelském <xref:System.InvalidOperationException?displayProperty=nameWithType> kódu vyvolá výjimku.  
  
 Pokračování je samo <xref:System.Threading.Tasks.Task> o sobě a neblokuje vlákno, na kterém je spuštěn. Volání <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metody blokovat, dokud dokončení úkolu pokračování.  
  
## <a name="creating-a-continuation-for-a-single-antecedent"></a>Vytvoření pokračování pro jednu předchozí  
 Můžete vytvořit pokračování, které se spustí po jeho <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> předchůdce dokončil voláním metody. Následující příklad ukazuje základní vzor (pro přehlednost, zpracování výjimek je vynechán). Provede předchozí úlohu , `taskA`která vrací <xref:System.DayOfWeek> objekt, který označuje název aktuálního dne v týdnu. Po dokončení předchůdce je úkol pokračování `continuation`, předán předchozí a zobrazí řetězec, který obsahuje jeho výsledek.

> [!NOTE]
> C# ukázky v tomto článku `async` použít modifikátor na metodu. `Main` Tato funkce je k dispozici v C# 7.1 a novější. Předchozí verze [`CS5001`](../../csharp/misc/cs5001.md) generovat při kompilaci tohoto ukázkového kódu. Budete muset nastavit jazykovou verzi C# 7.1 nebo novější. Jak nakonfigurovat jazykovou verzi, najdete v článku o [konfiguraci jazykové verze](../../csharp/language-reference/configure-language-version.md).
  
 [!code-csharp[TPL_Continuations#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/simple1.cs#1)]
 [!code-vb[TPL_Continuations#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/simple1.vb#1)]  
  
## <a name="creating-a-continuation-for-multiple-antecedents"></a>Vytvoření pokračování pro více předchůdců  
 Můžete také vytvořit pokračování, které bude spuštěno po dokončení některé nebo všechny skupiny úkolů. Chcete-li provést pokračování po dokončení všech předchozích úloh, volání statické (`Shared` v jazyce Visual Basic) <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> metoda nebo metodu instance. <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> Chcete-li provést pokračování po dokončení některého z předchozích`Shared` úloh, volání <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> statické ( <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType> v jazyce Visual Basic) metoda nebo metodu instance.  
  
 Všimněte si, <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> že volání a přetížení neblokují volající vlákno.  Obvykle však voláte všechny, ale <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.WhenAll%28System.Threading.Tasks.Task%5B%5D%29?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> metody k načtení vrácené vlastnosti, která blokuje volající vlákno.  
  
 Následující příklad volá <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> metodu k vytvoření úlohy pokračování, která odráží výsledky jeho 10 předchozích úkolů. Každý předchozí úkol čtverce hodnotu indexu, která se pohybuje od jedné do 10. Pokud předchůdce úspěšně dokončena (jejich <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> vlastnost <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>je <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> ), vlastnost pokračování je <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> pole hodnoty vrácené každý předchůdce. Příklad je přidá k výpočtu součtu čtverců pro všechna čísla od jedné do deseti.  
  
 [!code-csharp[TPL_Continuations#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/whenall1.cs#5)]
 [!code-vb[TPL_Continuations#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/whenall1.vb#5)]  
  
## <a name="continuation-options"></a>Možnosti pokračování  
 Při vytváření pokračování jedné úlohy můžete <xref:System.Threading.Tasks.Task.ContinueWith%2A> použít přetížení, <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> které trvá hodnotu výčtu k určení podmínek, za kterých začíná pokračování. Můžete například určit, že pokračování má být spuštěno pouze v případě, že předchůdce bude úspěšně dokončen, nebo pouze v případě, že se dokončí v chybném stavu. Pokud podmínka není true, když předchůdce je připraven k vyvolání pokračování, <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> pokračování přechody přímo do stavu a následně nelze spustit.  
  
 Počet víceúloha pokračování metody, jako je <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> například přetížení <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> metody, také parametr. Je však platná <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> pouze podmnožina všech členů výčtu. Můžete zadat <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> hodnoty, které mají <xref:System.Threading.Tasks.TaskCreationOptions?displayProperty=nameWithType> protějšky ve <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType>výčtu, například , <xref:System.Threading.Tasks.TaskContinuationOptions.LongRunning?displayProperty=nameWithType>a <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness?displayProperty=nameWithType>. Pokud zadáte některou `NotOn` `OnlyOn` z možností nebo s pokračováním více úkolů, bude vyvolána <xref:System.ArgumentOutOfRangeException> výjimka za běhu.  
  
 Další informace o možnostech pokračování <xref:System.Threading.Tasks.TaskContinuationOptions> úkolu naleznete v tématu.  
  
## <a name="passing-data-to-a-continuation"></a>Předávání dat pokračování  
 Metoda <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> předá odkaz na předchůdce uživateli delegátpokračování jako argument. Pokud předchůdce je <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> objekt a úloha byla spuštěna, dokud nebyla <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> dokončena, pak pokračování přístup k vlastnost úkolu.  
  
 Vlastnost <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> blokuje, dokud úkol nebyl dokončen. Pokud však byla úloha zrušena nebo došlo k <xref:System.Threading.Tasks.Task%601.Result%2A> chybě, <xref:System.AggregateException> pokus o přístup k vlastnosti vyvolá výjimku. Tomuto problému se můžete <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnRanToCompletion> vyhnout pomocí možnosti, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[TPL_Continuations#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result1.cs#2)]
 [!code-vb[TPL_Continuations#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result1.vb#2)]  
  
 Pokud chcete pokračování spustit i v případě, že předchůdce neběžel k úspěšnému dokončení, je nutné chránit před výjimkou. Jedním z přístupů <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> je otestovat vlastnost předchůdce a pouze <xref:System.Threading.Tasks.Task%601.Result%2A> pokus o přístup <xref:System.Threading.Tasks.TaskStatus.Faulted> <xref:System.Threading.Tasks.TaskStatus.Canceled>k vlastnosti, pokud stav není nebo . Můžete také prozkoumat <xref:System.Threading.Tasks.Task.Exception%2A> vlastnost předchůdce. Další informace naleznete v [tématu Zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md). Následující příklad upravuje předchozí příklad pro přístup k <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> vlastnosti antecedent <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>pouze v případě, že jeho stav je .  
  
 [!code-csharp[TPL_Continuations#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result2.cs#7)]
 [!code-vb[TPL_Continuations#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result2.vb#7)]  
  
## <a name="canceling-a-continuation"></a>Zrušení pokračování  
 Vlastnost <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> pokračování je nastavena <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> na v následujících situacích:  
  
- Vyvolá výjimku <xref:System.OperationCanceledException> v reakci na požadavek na zrušení. Stejně jako u jakékoli úlohy, pokud výjimka obsahuje stejný token, který byl předán pokračování, je považován za potvrzení zrušení spolupráce.  
  
- Pokračování je <xref:System.Threading.CancellationToken?displayProperty=nameWithType> předán, <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> jehož vlastnost je `true`. V tomto případě pokračování nespustí a přechody <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> do stavu.  
  
- Pokračování nikdy spustí, protože podmínka <xref:System.Threading.Tasks.TaskContinuationOptions> nastavená jeho argument nebyla splněna. Například pokud předchůdce přejde do <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> stavu, jeho pokračování, <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnFaulted?displayProperty=nameWithType> které bylo předáno možnost <xref:System.Threading.Tasks.TaskStatus.Canceled> nebude spuštěna, ale bude přechod do stavu.  
  
 Pokud úkol a jeho pokračování představují dvě části stejné logické operace, můžete předat stejný token zrušení pro oba úkoly, jak je znázorněno v následujícím příkladu. Skládá se z předchůdce, který generuje seznam celá čísla, která jsou dělitelná 33, které přejde na pokračování. Pokračování zase zobrazí seznam. Předchůdce i pokračování se pravidelně pozastavují v náhodných intervalech. Kromě toho <xref:System.Threading.Timer?displayProperty=nameWithType> objekt se používá `Elapsed` ke spuštění metody po pětisekundový časový interval. Tento příklad <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> volá metodu, která způsobí, že <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A?displayProperty=nameWithType> aktuálně spuštěná úloha volá metodu. Zda <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> je metoda volána při předchůdce nebo jeho pokračování je provádění závisí na dobu trvání náhodně generované pauzy. Pokud předchůdce je zrušena, pokračování se nespustí. Pokud předchůdce není zrušena, token lze stále použít ke zrušení pokračování.  
  
 [!code-csharp[TPL_Continuations#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation1.cs#3)]
 [!code-vb[TPL_Continuations#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation1.vb#3)]  
  
 Můžete také zabránit pokračování v provádění, pokud jeho předchůdce je zrušena bez poskytnutí pokračování <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled?displayProperty=nameWithType> token zrušení zadáním možnosti při vytváření pokračování. Následuje jednoduchý příklad.  
  
 [!code-csharp[TPL_Continuations#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation2.cs#8)]
 [!code-vb[TPL_Continuations#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation2.vb#8)]  
  
 Po pokračování přejde <xref:System.Threading.Tasks.TaskStatus.Canceled> do stavu, může ovlivnit pokračování, <xref:System.Threading.Tasks.TaskContinuationOptions> které následují, v závislosti na které byly určeny pro tyto pokračování.  
  
 Pokračování, které jsou uvolněny nespustí.  
  
## <a name="continuations-and-child-tasks"></a>Pokračování a podřízené úkoly  
 Pokračování nespustí, dokud předchůdce a všechny jeho připojené podřízené úkoly byly dokončeny. Pokračování nečeká na dokončení odpojených podřízených úloh. Následující dva příklady ilustrují podřízené úkoly, které jsou připojeny k předchůdce, který vytváří pokračování a odnímaly je od předchozího. V následujícím příkladu pokračování spustí pouze po dokončení všech podřízených úloh a spuštění příkladu vícekrát vytvoří stejný výstup pokaždé. Příklad spustí předchůdce voláním <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metody, protože ve výchozím <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> nastavení metoda vytvoří nadřazený úkol, jehož výchozí možnost vytvoření úkolu je <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>.  
  
 [!code-csharp[TPL_Continuations#9](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/attached1.cs#9)]
 [!code-vb[TPL_Continuations#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/attached1.vb#9)]  
  
 Pokud podřízené úkoly jsou odpojeny od předchůdce, ale pokračování spustí, jakmile předchůdce byl ukončen, bez ohledu na stav podřízené úkoly. V důsledku toho více spuštění v následujícím příkladu můžete vytvořit variabilní výstup, který závisí na tom, jak plánovač úloh zpracovány každé podřízené úlohy.  
  
 [!code-csharp[TPL_Continuations#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/detached1.cs#10)]
 [!code-vb[TPL_Continuations#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/detached1.vb#10)]  
  
 Konečný stav předchozí úlohy závisí na konečném stavu všech připojených podřízených úkolů. Stav odpojených podřízených úkolů nemá vliv na nadřazenou položku. Další informace naleznete v [tématu Attached and Detached Child Tasks](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## <a name="associating-state-with-continuations"></a>Soupozování státu s pokračováním  
 K pokračování úkolu můžete přidružit libovolný stav. Metoda <xref:System.Threading.Tasks.Task.ContinueWith%2A> poskytuje přetížené verze, které <xref:System.Object> každý trvat hodnotu, která představuje stav pokračování. Později můžete přistupovat k <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> tomuto objektu stavu pomocí vlastnosti. Tento objekt `null` stavu je, pokud nezadáte hodnotu.  
  
 Stav pokračování je užitečný při převodu existujícího kódu, který používá [asynchronní programovací model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) k použití TPL. V APM obvykle poskytujete stav objektu v **metodě Begin**_Method_ a <xref:System.IAsyncResult.AsyncState%2A?displayProperty=nameWithType> později přistupujete k tomuto stavu pomocí vlastnosti. Pomocí <xref:System.Threading.Tasks.Task.ContinueWith%2A> metody můžete zachovat tento stav při převodu kódu, který používá APM pro použití TPL.  
  
 Stav pokračování může být také <xref:System.Threading.Tasks.Task> užitečné při práci s objekty v ladicím programu sady Visual Studio. Například v okně **Paralelní úkoly** se ve sloupci **Úkol** zobrazí řetězcová reprezentace objektu stavu pro každou úlohu. Další informace o okně **Paralelní úkoly** naleznete [v tématu Použití okna Úkoly](/visualstudio/debugger/using-the-tasks-window).  
  
 Následující příklad ukazuje, jak použít stav pokračování. Vytvoří řetězec pokračování úlohy. Každý úkol poskytuje aktuální <xref:System.DateTime> čas, objekt, `state` pro <xref:System.Threading.Tasks.Task.ContinueWith%2A> parametr metody. Každý <xref:System.DateTime> objekt představuje čas, kdy je vytvořena úloha pokračování. Každý úkol vytvoří jako svůj <xref:System.DateTime> výsledek druhý objekt, který představuje čas dokončení úkolu. Po dokončení všech úkolů se v tomto příkladu zobrazí čas vytvoření a čas dokončení každé úlohy pokračování.  
  
 [!code-csharp[TPL_ContinuationState#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuationstate/cs/continuationstate.cs#1)]
 [!code-vb[TPL_ContinuationState#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuationstate/vb/continuationstate.vb#1)]  
  
## <a name="handling-exceptions-thrown-from-continuations"></a>Zpracování výjimek vyzdvižených z pokračování  
 Vztah předchůdce a pokračování není vztah nadřazený podřízený. Výjimky vyzývané pokračováním nejsou šířeny do předchůdce. Proto zpracovat výjimky vyvoláné pokračování jako byste je zpracovat v jakékoli jiné úlohy, takto:  
  
- Můžete použít <xref:System.Threading.Tasks.Task.Wait%2A>, <xref:System.Threading.Tasks.Task.WaitAll%2A>nebo <xref:System.Threading.Tasks.Task.WaitAny%2A> metoda nebo jeho obecný protějšek, čekat na pokračování. Můžete počkat na předchůdce a jeho pokračování `try` ve stejném příkazu, jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[TPL_Continuations#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception1.cs#6)]
     [!code-vb[TPL_Continuations#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception1.vb#6)]  
  
- Můžete použít druhé pokračování sledovat <xref:System.Threading.Tasks.Task.Exception%2A> vlastnost první pokračování. V následujícím příkladu se úloha pokusí číst z neexistujícího souboru. Pokračování pak zobrazí informace o výjimce v předchozí úloze.  
  
     [!code-csharp[TPL_Continuations#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#4)]
     [!code-vb[TPL_Continuations#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#4)]  
  
     Vzhledem k tomu, že byla spuštěna s <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnFaulted?displayProperty=nameWithType> možností, pokračování provede pouze v případě, že dojde k <xref:System.Threading.Tasks.Task.Exception%2A> výjimce v předchůdce, a proto lze předpokládat, že vlastnost předchůdce není `null`. Pokud pokračování provede, zda je vyvolána výjimka v předchůdce, bude muset zkontrolovat, zda <xref:System.Threading.Tasks.Task.Exception%2A> předchůdce vlastnost `null` není před pokusem o zpracování výjimky, jak ukazuje následující fragment kódu.  
  
     [!code-csharp[TPL_Continuations#11](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#11)]
     [!code-vb[TPL_Continuations#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#11)]  
  
     Další informace naleznete v [tématu Zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
- Pokud pokračování je připojen podřízený úkol, který <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType> byl vytvořen pomocí možnosti, jeho výjimky budou rozšířeny nadřazené zpět do volajícího vlákna, jako je tomu v případě jakékoli jiné připojené podřízené. Další informace naleznete v [tématu Attached and Detached Child Tasks](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## <a name="see-also"></a>Viz také

- [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
