---
title: Řetězení úloh pomocí úloh pokračování
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, continuations
ms.assetid: 0b45e9a2-de28-46ce-8212-1817280ed42d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14c046094db52f2db55bb095839d354c7e6c691e
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2018
ms.locfileid: "42912039"
---
# <a name="chaining-tasks-by-using-continuation-tasks"></a>Řetězení úloh pomocí úloh pokračování
V asynchronním programování je velmi běžné, že jedna asynchronní operace při dokončení vyvolá druhou operaci a předá jí data. Tradičně se to stalo pomocí metod zpětného volání. V Task Parallel Library je stejná funkčnost zajištěna pomocí *pokračujících úloh*. Pokračující úloha (nazývaná také pouze pokračování) je asynchronní úloha, která je vyvolána jinou úlohou, která se nazývá *předchůdce*, jakmile je předchůdce dokončen.  
  
 Pokračování jsou relativně snadno použitelná, ale přesto jsou velmi výkonná a flexibilní. Například můžete:  
  
-   Předejte data z předchůdce do pokračování.  
  
-   Určete přesné podmínky, za kterých bude vyvolána pokračování nebo není vyvolána.  
  
-   Zrušte pokračování před spuštěním nebo kooperativně za běhu.  
  
-   Poskytnout nápovědu, jak by měl být pokračování naplánováno.  
  
-   Vyvolejte ze stejného předchůdce více pokračování.  
  
-   Vyvolejte jedno pokračování, až skončí všichni nebo jeden z více předchůdců.  
  
-   Zřetězit pokračování jedno po druhém do jakékoli libovolné délky.  
  
-   Použijte pokračování pro zpracování výjimek vyvolaných předchůdcem.  
  
## <a name="about-continuations"></a>Informace o pokračování  
 Pokračování je úkol, který je vytvořen v <xref:System.Threading.Tasks.TaskStatus.WaitingForActivation> stavu. Je aktivována automaticky po dokončení jeho předchozí úlohy nebo úlohy. Volání <xref:System.Threading.Tasks.Task.Start%2A?displayProperty=nameWithType> na pokračování v uživatelském kódu vyvolá <xref:System.InvalidOperationException?displayProperty=nameWithType> výjimky.  
  
 Pokračování je samo o sobě <xref:System.Threading.Tasks.Task> a neblokuje vlákno, na kterém je spuštěno. Volání <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metoda blokuje, dokud neskončí úloha pokračování.  
  
## <a name="creating-a-continuation-for-a-single-antecedent"></a>Vytváření pro jeden předchůdce pokračování  
 Vytvořit pokračování, který se spustí po dokončení jeho předchůdce voláním <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> metody. Následující příklad zobrazuje základní vzor (pro přehlednost je vynecháno zpracování výjimek). Je spuštěn předchozí úlohy, `taskA`, která vrací <xref:System.DayOfWeek> objekt, který určuje název aktuální den v týdnu. Jakmile je předchůdce dokončen, úkol pokračování `continuation`, je předán předchůdce a zobrazí řetězec, který obsahuje výsledek.  
  
 [!code-csharp[TPL_Continuations#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/simple1.cs#1)]
 [!code-vb[TPL_Continuations#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/simple1.vb#1)]  
  
## <a name="creating-a-continuation-for-multiple-antecedents"></a>Vytváření pokračování pro více předchůdců  
 Můžete také vytvořit pokračování, které se spustí po dokončení některých nebo všech skupiny úkolů. Provést pokračování po dokončení všechny předchozí úkoly, zavolejte statickou (`Shared` v jazyce Visual Basic) <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> metodu nebo instanci <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> metody. Provést pokračování, až všechny předchozí úkoly dokončí, zavolejte statickou (`Shared` v jazyce Visual Basic) <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> metodu nebo instanci <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType> metody.  
  
 Všimněte si, že se volá, aby <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> přetížení nedochází k blokování volajícího vlákna.  Však obvykle volat pouze na <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.WhenAll%28System.Threading.Tasks.Task%5B%5D%29?displayProperty=nameWithType> metody pro načtení vráceného <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> vlastnost, která blokování volajícího vlákna.  
  
 Následující příklad volá <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> metody k vytvoření pokračování úlohy, která odráží výsledky jeho deset předchozí úlohy. Každé předchozí úlohy squares hodnotu indexu, který se pohybuje od jedné až deset. Pokud předchůdců úspěšně dokončit (jejich <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> vlastnost <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>), <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> vlastnost pokračování je pole <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> hodnoty vrácené každou předchůdce. V příkladu se přidají k výpočtu součet kvadratických hodnot pro všechna čísla v rozsahu od 1 do 10.  
  
 [!code-csharp[TPL_Continuations#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/whenall1.cs#5)]
 [!code-vb[TPL_Continuations#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/whenall1.vb#5)]  
  
## <a name="continuation-options"></a>Možnosti pokračování  
 Při vytváření pokračování jedné úlohy, můžete použít <xref:System.Threading.Tasks.Task.ContinueWith%2A> přetížení, které přijímá <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> hodnotu výčtu pro určení podmínek, za kterých pokračování spustí. Například můžete určit, že pokračování má spustit jenom v případě, že je předchůdce dokončen úspěšně, nebo pouze v případě, že dokončení v chybovém stavu. Pokud podmínka není splněna, kdy je předchůdce připraven k vyvolání pokračování, pokračování přechází přímo <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> stavu a nemůže být dále spuštěno.  
  
 Počet metod víceúlohového pokračování, jako jsou přetížení <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> metoda, také zahrnovat <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> parametr. Pouze podmnožinu všech <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> členy výčtu jsou platné, ale. Můžete zadat <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> hodnoty, které mají jejich protějšky v <xref:System.Threading.Tasks.TaskCreationOptions?displayProperty=nameWithType> výčtu, například <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType>, <xref:System.Threading.Tasks.TaskContinuationOptions.LongRunning?displayProperty=nameWithType>, a <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness?displayProperty=nameWithType>. Pokud je zadána některá z `NotOn` nebo `OnlyOn` možnosti s víceúlohovým pokračováním <xref:System.ArgumentOutOfRangeException> v době běhu, bude vyvolána výjimka.  
  
 Další informace o možnosti pokračování úlohy, najdete v článku <xref:System.Threading.Tasks.TaskContinuationOptions> tématu.  
  
## <a name="passing-data-to-a-continuation"></a>Předávání údajů do pokračování  
 <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> Metoda předává reference na předchůdce uživatelskému delegátovi pokračování jako argument. Pokud je předchůdce <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> objekt a tato úloha spustila úspěšně dokončen, pak může pokračování přistupovat <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> vlastnosti úlohy.  
  
 <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> Vlastnost blokuje, dokud není úloha dokončena. Nicméně, pokud byla úloha zrušena nebo došlo k chybě, pokusu o přístup <xref:System.Threading.Tasks.Task%601.Result%2A> vyvolá vlastnost <xref:System.AggregateException> výjimky. Tento problém můžete vyhnout použitím <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnRanToCompletion> možnosti, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[TPL_Continuations#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result1.cs#2)]
 [!code-vb[TPL_Continuations#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result1.vb#2)]  
  
 Pokud chcete, aby pokračování spuštěno i v případě, že předchůdce nebyl spuštěn na úspěšné dokončení, musí se proti výjimce chránit. Jedním z přístupů je otestovat <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> pokus o přístup k vlastnosti předchozí a jenom <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost Pokud stav není <xref:System.Threading.Tasks.TaskStatus.Faulted> nebo <xref:System.Threading.Tasks.TaskStatus.Canceled>. Můžete také prozkoumat <xref:System.Threading.Tasks.Task.Exception%2A> vlastnosti předchůdce. Další informace najdete v tématu [zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md). Následující příklad upravuje předchozí příklad přístup předchůdce <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> vlastnost pouze v případě, že má stav <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>.  
  
 [!code-csharp[TPL_Continuations#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result2.cs#7)]
 [!code-vb[TPL_Continuations#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result2.vb#7)]  
  
## <a name="canceling-a-continuation"></a>Zrušení pokračování  
 <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> Pokračování je nastavena na <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> v následujících situacích:  
  
-   Vyvolá <xref:System.OperationCanceledException> výjimky v reakci na žádost o zrušení. Stejně jako u každého úkolu, pokud výjimka obsahuje stejný token, který byl předán pokračování, je považován za potvrzení kooperativního zrušení.  
  
-   Pokračování je předán <xref:System.Threading.CancellationToken?displayProperty=nameWithType> jehož <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost `true`. V takovém případě pokračování nespustí a přechází do <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> stavu.  
  
-   Pokračování nikdy nespustí, protože podmínka nastavená jeho <xref:System.Threading.Tasks.TaskContinuationOptions> argument nebyl splněn. Například, pokud předchozí přejde do <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> stavu, její pokračování, který byl předán <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnFaulted?displayProperty=nameWithType> možnost se nespustí, ale nahradí <xref:System.Threading.Tasks.TaskStatus.Canceled> stavu.  
  
 Pokud úlohu a její pokračování představují dvě části stejné logické operace, můžete předat stejný token zrušení oběma úkolům, jak je znázorněno v následujícím příkladu. Zahrnuje předchůdce, který generuje seznam celých čísel, která jsou dělitelná 33, který předá do pokračování. Pokračování zase zobrazí v seznamu. Předchůdce a pokračování pozastavení pravidelně náhodných intervalech. Kromě toho <xref:System.Threading.Timer?displayProperty=nameWithType> objekt se používá ke spuštění `Elapsed` metoda po pěti sekundách časový limit. Volá <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metodu, která způsobí, že právě prováděnou úlohu k volání <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A?displayProperty=nameWithType> metody. Zda <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metoda se volá, když je předchůdce nebo jeho pokračování provádí závisí na době trvání náhodně generované pozastaví. Pokud je předchůdce zrušen, pokračování nespustí. Pokud není předchůdce zrušen, token je stále možné pro zrušení pokračování.  
  
 [!code-csharp[TPL_Continuations#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation1.cs#3)]
 [!code-vb[TPL_Continuations#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation1.vb#3)]  
  
 Můžete také zabránit pokračování v provádění, zda je zrušen předchůdce bez poskytnutí pokračování token zrušení tak, že zadáte <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled?displayProperty=nameWithType> při vytváření pokračování možnost. Níže je jednoduchý příklad.  
  
 [!code-csharp[TPL_Continuations#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation2.cs#8)]
 [!code-vb[TPL_Continuations#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation2.vb#8)]  
  
 Přechod pokračování do <xref:System.Threading.Tasks.TaskStatus.Canceled> stavu, může ovlivnit pokračování, které následují, v závislosti na tom <xref:System.Threading.Tasks.TaskContinuationOptions> , které bylo zadáno pro tyto pokračování.  
  
 Pokračování, které jsou odstraněny se nespustí.  
  
## <a name="continuations-and-child-tasks"></a>Pokračování a podřízené úlohy  
 Pokračování nespustí až do předchůdce a všechny jeho připojené podřízené úlohy dokončeny. Pokračování nečeká na dokončení odpojených podřízených úloh. Následující dva příklady ilustrují podřízených úloh, které jsou připojeny k a Odpojit z předchozí, která vytvoří pokračování. V následujícím příkladu se pokračování nespustí až po dokončení všech podřízených úloh a spuštění příkladu vytvoří více než jednou identické výstupu pokaždé, když. Všimněte si, že v příkladu spustí předchůdce voláním <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metody, protože ve výchozím nastavení <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metoda vytvoří nadřazenou úlohu, jejíž výchozí možnost vytváření úloh je <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>.  
  
 [!code-csharp[TPL_Continuations#9](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/attached1.cs#9)]
 [!code-vb[TPL_Continuations#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/attached1.vb#9)]  
  
 Pokud podřízených úloh jsou odpojeny od předchůdce, ale pokračování spustí, jakmile je předchůdce byl ukončen, bez ohledu na stav podřízených úloh. V důsledku toho více běhů v následujícím příkladu může vytvořit výstup proměnné, na kterém závisí způsob zpracování každá podřízená úloha Plánovač úloh.  
  
 [!code-csharp[TPL_Continuations#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/detached1.cs#10)]
 [!code-vb[TPL_Continuations#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/detached1.vb#10)]  
  
 Konečný stav předchozí úlohy závisí na konečném stavu všech připojených podřízených úloh. Stav odpojených podřízených úloh nemá vliv na nadřazený. Další informace najdete v tématu [připojené a odpojené podřízené úlohy](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## <a name="associating-state-with-continuations"></a>Přidružení stavu s pokračováními  
 Pokračování úlohy lze přidružit libovolný stav. <xref:System.Threading.Tasks.Task.ContinueWith%2A> Metoda poskytuje přetížené verze, která každá převezme <xref:System.Object> hodnotu, která představuje stav pokračování. Můžete později přístup k tomuto objektu stavu pomocí <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> vlastnost. Tento objekt stavu je `null` Pokud nezadáte hodnotu.  
  
 Stav pokračování je užitečný při převádění existujícího kódu, který se používá [asynchronního programovacího modelu (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) pro používání TPL. V APM obvykle poskytnete stav objektů v **začít *** metoda* metoda a později získáte přístup k tomuto stavu pomocí <xref:System.IAsyncResult.AsyncState%2A?displayProperty=nameWithType> vlastnost. S použitím <xref:System.Threading.Tasks.Task.ContinueWith%2A> metodu, můžete zachovat tento stav při převodu kódu, který používá APM pro použití TPL.  
  
 Stav pokračování může také být užitečné při práci s <xref:System.Threading.Tasks.Task> objektů v ladicím programu sady Visual Studio. Například v **paralelní úlohy** okně **úloh** sloupec zobrazuje řetězcovou reprezentaci objektu stav pro každý úkol. Další informace o **paralelní úlohy** okna, naleznete v tématu [Using the Tasks Window](/visualstudio/debugger/using-the-tasks-window).  
  
 Následující příklad ukazuje způsob použití stavu pokračování. Vytvoří řetězec pokračujících úloh. Každá úloha obsahuje aktuální čas <xref:System.DateTime> objektu, pro `state` parametr <xref:System.Threading.Tasks.Task.ContinueWith%2A> metody. Každý <xref:System.DateTime> objekt představuje čas, kdy se vytvoří úkol pokračování. Každý úkol vytváří jako svůj výsledek a druhý <xref:System.DateTime> objekt, který představuje čas, kdy úloha dokončí. Po dokončení všech úkolů tento příklad zobrazuje čas vytvoření a čas, ve které každý pokračování neskončí úloha.  
  
 [!code-csharp[TPL_ContinuationState#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuationstate/cs/continuationstate.cs#1)]
 [!code-vb[TPL_ContinuationState#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuationstate/vb/continuationstate.vb#1)]  
  
## <a name="handling-exceptions-thrown-from-continuations"></a>Zpracování výjimek vyvolaných z pokračování  
 Vztah předchůdce pokračování není vztah nadřízenosti a podřízenosti. Výjimky vyvolané pokračováním nejsou šířeny do předchůdce. Proto zpracujte výjimky vyvolané v pokračování stejně jako je v libovolné jiné úloze a následujícím způsobem:  
  
-   Můžete použít <xref:System.Threading.Tasks.Task.Wait%2A>, <xref:System.Threading.Tasks.Task.WaitAll%2A>, nebo <xref:System.Threading.Tasks.Task.WaitAny%2A> metody nebo jejich obecné protějšky pro čekání na pokračování. Můžete počkat předchůdce a jeho pokračování ve stejném `try` příkaz, jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[TPL_Continuations#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception1.cs#6)]
     [!code-vb[TPL_Continuations#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception1.vb#6)]  
  
-   Pomocí druhého pokračování sledovat <xref:System.Threading.Tasks.Task.Exception%2A> vlastnosti prvního pokračování. V následujícím příkladu úlohu pokouší číst ze souboru neexistuje. Pokračování pak zobrazí informace o výjimce v předchozí úlohy.  
  
     [!code-csharp[TPL_Continuations#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#4)]
     [!code-vb[TPL_Continuations#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#4)]  
  
     Vzhledem k tomu, že byla spuštěna s <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnFaulted?displayProperty=nameWithType> možnost, že pokračování spustí pouze v případě, že dojde k výjimce v předchůdce, a proto by ji můžete předpokládat, že je předchůdce <xref:System.Threading.Tasks.Task.Exception%2A> jedná o vlastnost neumožňující `null`. Pokud pokračování spustí, zda je výjimka vyvolána v předchůdce, bude mít ke kontrole, jestli je předchůdce <xref:System.Threading.Tasks.Task.Exception%2A> jedná o vlastnost neumožňující `null` před pokusem o zpracování výjimky, jako následující fragment kódu ukazuje.  
  
     [!code-csharp[TPL_Continuations#11](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#11)]
     [!code-vb[TPL_Continuations#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#11)]  
  
     Další informace najdete v tématu [zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md) a [NIB: postupy: zpracování Exceptions Thrown by Tasks](https://msdn.microsoft.com/library/d6c47ec8-9de9-4880-beb3-ff19ae51565d).  
  
-   Pokud je pokračování připojené podřízené úlohy, který byl vytvořen pomocí <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType> možnost, výjimky se šířeny přes nadřízenou zpět do volajícího vlákna, stejně jako v případě v libovolného jiného připojeného podřízeného. Další informace najdete v tématu [připojené a odpojené podřízené úlohy](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## <a name="see-also"></a>Viz také  
 [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
