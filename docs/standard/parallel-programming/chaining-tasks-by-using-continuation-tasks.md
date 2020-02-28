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
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159361"
---
# <a name="chaining-tasks-by-using-continuation-tasks"></a>Řetězení úloh pomocí úloh pokračování
V asynchronním programování je běžné pro jednu asynchronní operaci po dokončení, k vyvolání druhé operace a předání dat do ní. Pokračování je tradičně prováděno pomocí metod zpětného volání. V knihovně Task Parallel Library jsou stejné funkce poskytovány *pokračujícími úkoly*. Pokračující úkol (označuje se také jako pokračování) je asynchronní úloha, která je vyvolána jinou úlohou, která se označuje jako *předchůdce*po dokončení předchůdce.  
  
 Pokračování je poměrně snadné použít, ale jsou ale výkonné a flexibilní. Můžete například provést následující věci:  
  
- Předat data z předchůdce do pokračování.  
  
- Určete přesné podmínky, za kterých bude pokračování vyvoláno nebo není vyvoláno.  
  
- Zrušení pokračování buď před jeho spuštěním, nebo ve spolupráci s tím, jak běží.  
  
- Poskytněte nápovědu, jak má být pokračování naplánováno.  
  
- Vyvolá několik pokračování ze stejného předchůdce.  
  
- Vyvolat jedno pokračování, až se dokončí všechny nebo některé z více předchůdců.  
  
- Zřetězit pokračování jedno po druhém do jakékoli libovolné délky.  
  
- Použijte pokračování pro zpracování výjimek vyvolaných předchůdcem.  
  
## <a name="about-continuations"></a>O pokračování  
 Pokračování je úkol, který je vytvořen ve stavu <xref:System.Threading.Tasks.TaskStatus.WaitingForActivation>. Aktivuje se automaticky po dokončení jeho předchozí úlohy nebo úkolů. Volání <xref:System.Threading.Tasks.Task.Start%2A?displayProperty=nameWithType> při pokračování v uživatelském kódu vyvolá výjimku <xref:System.InvalidOperationException?displayProperty=nameWithType>.  
  
 Pokračování je samo <xref:System.Threading.Tasks.Task> a neblokuje vlákno, ve kterém je spuštěno. Zavolejte metodu <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> pro blokování, dokud neskončí pokračování úlohy.  
  
## <a name="creating-a-continuation-for-a-single-antecedent"></a>Vytvoření pokračování pro jeden předchůdce  
 Můžete vytvořit pokračování, které se provede po dokončení jeho předchůdce voláním metody <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>. Následující příklad znázorňuje základní vzorek (pro přehlednost, vynechává se zpracování výjimek). Spustí předchozí úlohu, `taskA`, která vrátí objekt <xref:System.DayOfWeek>, který označuje název aktuálního dne v týdnu. Po dokončení předchůdce se úkol pokračování, `continuation`, předává předchůdci a zobrazí řetězec, který obsahuje jeho výsledek.

> [!NOTE]
> C# Ukázky v tomto článku využívají modifikátor `async` na metodě `Main`. Tato funkce je k dispozici v C# 7,1 a novějších verzích. Předchozí verze generují [`CS5001`](../../csharp/misc/cs5001.md) při kompilování tohoto ukázkového kódu. Je nutné nastavit jazykovou verzi na C# 7,1 nebo novější. Informace o tom, jak nakonfigurovat jazykovou verzi, najdete v článku o [konfiguraci jazykové verze](../../csharp/language-reference/configure-language-version.md).
  
 [!code-csharp[TPL_Continuations#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/simple1.cs#1)]
 [!code-vb[TPL_Continuations#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/simple1.vb#1)]  
  
## <a name="creating-a-continuation-for-multiple-antecedents"></a>Vytváření pokračování pro více předchůdců  
 Můžete také vytvořit pokračování, které se spustí, když se dokončí kterákoli nebo celá skupina úkolů. Chcete-li provést pokračování po dokončení všech předchozích úloh, zavoláte metodu static (`Shared` in Visual Basic) <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> nebo metodu instance <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>. Chcete-li provést pokračování po dokončení kteréhokoliv z předchozích úloh, zavoláte metodu static (`Shared` in Visual Basic) <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> nebo metodu instance <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType>.  
  
 Všimněte si, že volání <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> přetížení neblokují volající vlákno.  Nicméně obvykle zavoláte všechny metody, ale <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.WhenAll%28System.Threading.Tasks.Task%5B%5D%29?displayProperty=nameWithType>, abyste načetli vrácenou vlastnost <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType>, která zablokuje volající vlákno.  
  
 V následujícím příkladu je volána metoda <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> pro vytvoření pokračování úlohy, která odráží výsledky jeho 10 předchozích úloh. Každý předchozí úkol napředá hodnotu indexu, která je v rozsahu od 1 do 10. Pokud se předchůdce úspěšně dokončí (vlastnost <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> je <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>), vlastnost <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> pokračování je pole hodnot <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> vrácených jednotlivými předchůdci. Tento příklad je přidá k výpočtu součtu čtverců pro všechna čísla od 1 do 10.  
  
 [!code-csharp[TPL_Continuations#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/whenall1.cs#5)]
 [!code-vb[TPL_Continuations#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/whenall1.vb#5)]  
  
## <a name="continuation-options"></a>Možnosti pokračování  
 Když vytvoříte pokračování jedné úlohy, můžete použít <xref:System.Threading.Tasks.Task.ContinueWith%2A> přetížení, které přebírá hodnotu <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> výčtu k určení podmínek, za kterých se pokračování spustí. Můžete například určit, že pokračování bude spuštěno pouze v případě, že se předchůdce úspěšně dokončí, nebo pouze v případě, že se dokončí v chybovém stavu. Pokud podmínka není pravdivá, pokud je předchůdce připraven k vyvolání pokračování, pokračování přejde přímo do stavu <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> a následně nemůže být spuštěno.  
  
 Několik metod pokračování více úloh, jako je například přetížení metody <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>, zahrnuje také parametr <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType>. Platná je však pouze podmnožina všech členů výčtu <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType>. Můžete určit <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> hodnoty, které mají protějšky ve výčtu <xref:System.Threading.Tasks.TaskCreationOptions?displayProperty=nameWithType>, například <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType>, <xref:System.Threading.Tasks.TaskContinuationOptions.LongRunning?displayProperty=nameWithType>a <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness?displayProperty=nameWithType>. Pokud zadáte některou z `NotOn` nebo `OnlyOn` možnosti s pokračováním více úloh, bude vyvolána výjimka <xref:System.ArgumentOutOfRangeException> v době běhu.  
  
 Další informace o možnostech pokračování úlohy najdete v tématu <xref:System.Threading.Tasks.TaskContinuationOptions>.  
  
## <a name="passing-data-to-a-continuation"></a>Předávání dat do pokračování  
 Metoda <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> předá odkaz na předchůdce jako argument pro uživatele pokračování. Pokud je předchůdce objekt <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> a úloha byla spuštěna až do dokončení, pokračování může získat přístup k vlastnosti <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> úlohy.  
  
 Vlastnost <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> zablokuje, dokud se úloha nedokončí. Pokud se ale úloha zrušila nebo došlo k chybě, pokus o přístup k vlastnosti <xref:System.Threading.Tasks.Task%601.Result%2A> vyvolá výjimku <xref:System.AggregateException>. Tomuto problému se můžete vyhnout pomocí možnosti <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnRanToCompletion>, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[TPL_Continuations#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result1.cs#2)]
 [!code-vb[TPL_Continuations#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result1.vb#2)]  
  
 Pokud chcete pokračovat v běhu i v případě, že předchůdce nebyl úspěšně dokončen, je nutné před výjimkou provést ochranu. Jedním z přístupů je otestování vlastnosti <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> předchůdce a pokus o přístup k vlastnosti <xref:System.Threading.Tasks.Task%601.Result%2A> pouze v případě, že stav není <xref:System.Threading.Tasks.TaskStatus.Faulted> nebo <xref:System.Threading.Tasks.TaskStatus.Canceled>. Můžete také prostudovat vlastnost <xref:System.Threading.Tasks.Task.Exception%2A> předchůdce. Další informace naleznete v tématu [zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md). Následující příklad upravuje předchozí příklad pro přístup k vlastnosti <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> předchůdce pouze v případě, že je jeho stav <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>.  
  
 [!code-csharp[TPL_Continuations#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result2.cs#7)]
 [!code-vb[TPL_Continuations#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result2.vb#7)]  
  
## <a name="canceling-a-continuation"></a>Zrušení pokračování  
 Vlastnost <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> pokračování je nastavena na <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> v následujících situacích:  
  
- Vyvolá výjimku <xref:System.OperationCanceledException> v reakci na žádost o zrušení. Stejně jako u jakékoli úlohy, pokud výjimka obsahuje stejný token, který byl předán pokračování, je považována za potvrzení kooperativního zrušení.  
  
- Pokračování je předáno <xref:System.Threading.CancellationToken?displayProperty=nameWithType>, jehož vlastnost <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> je `true`. V takovém případě se pokračování nespustí a přejde do stavu <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType>.  
  
- Pokračování se nikdy nespustí, protože nebyla splněna podmínka nastavená argumentem <xref:System.Threading.Tasks.TaskContinuationOptions>. Například pokud předchůdce přejde do stavu <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType>, jeho pokračování, které bylo předáno <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnFaulted?displayProperty=nameWithType> možnost, nebude spuštěno, ale převede do stavu <xref:System.Threading.Tasks.TaskStatus.Canceled>.  
  
 Pokud úloha a její pokračování reprezentují dvě části stejné logické operace, můžete stejný token zrušení předat oběma úkolům, jak je znázorněno v následujícím příkladu. Skládá se z předchůdce, který generuje seznam celých čísel, která jsou dělitelná 33, která je předána pokračování. Pokračování zobrazí seznam. Předchůdce i pokračování v pravidelných intervalech se v náhodných intervalech pozastaví. Kromě toho se <xref:System.Threading.Timer?displayProperty=nameWithType> objekt používá ke spuštění metody `Elapsed` po pěti sekundách intervalu časového limitu. Tento příklad volá metodu <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType>, která způsobuje, že aktuálně vykonávaná úloha volá metodu <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A?displayProperty=nameWithType>. Určuje, zda je volána metoda <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType>, když předchůdce nebo jeho pokračování provádí, závisí na době trvání náhodně generovaných pozastavení. Pokud je předchůdce zrušen, pokračování nebude zahájeno. Pokud předchůdce není zrušen, token lze nadále použít k zrušení pokračování.  
  
 [!code-csharp[TPL_Continuations#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation1.cs#3)]
 [!code-vb[TPL_Continuations#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation1.vb#3)]  
  
 Můžete také zabránit spuštění pokračování, pokud je jeho předchůdce zrušen bez zadání pokračování tokenu zrušení zadáním možnosti <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled?displayProperty=nameWithType> při vytváření pokračování. Následuje jednoduchý příklad.  
  
 [!code-csharp[TPL_Continuations#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation2.cs#8)]
 [!code-vb[TPL_Continuations#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation2.vb#8)]  
  
 Po pokračování přejde do stavu <xref:System.Threading.Tasks.TaskStatus.Canceled>, může ovlivnit pokračování, která následují, v závislosti na <xref:System.Threading.Tasks.TaskContinuationOptions>, které byly pro tyto pokračování zadány.  
  
 Pokračování, která jsou uvolněna, se nespustí.  
  
## <a name="continuations-and-child-tasks"></a>Pokračování a podřízené úlohy  
 Pokračování není spuštěno, dokud předchůdce a všechny jeho připojené podřízené úlohy nebyly dokončeny. Pokračování nečeká na dokončení odpojených podřízených úloh. Následující dva příklady ilustrují podřízené úlohy, které jsou připojeny k a odpojeny od předchůdce, který vytváří pokračování. V následujícím příkladu se pokračování spustí až po dokončení všech podřízených úloh a spuštění příkladu několikrát vytvoří stejný výstup. V příkladu se spustí předchůdce voláním metody <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType>, protože ve výchozím nastavení metoda <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> vytvoří nadřazenou úlohu, jejíž výchozí možnost vytvoření úlohy je <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>.  
  
 [!code-csharp[TPL_Continuations#9](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/attached1.cs#9)]
 [!code-vb[TPL_Continuations#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/attached1.vb#9)]  
  
 Pokud se ale podřízené úlohy odpojí od předchůdce, pokračování se spustí hned po ukončení předchůdce, a to bez ohledu na stav podřízených úloh. V důsledku toho může více spuštění z následujícího příkladu vytvořit proměnnou výstup, který závisí na tom, jak Plánovač úloh zpracoval každou podřízenou úlohu.  
  
 [!code-csharp[TPL_Continuations#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/detached1.cs#10)]
 [!code-vb[TPL_Continuations#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/detached1.vb#10)]  
  
 Konečný stav předchozí úlohy závisí na konečném stavu všech připojených podřízených úloh. Stav odpojených podřízených úloh nemá vliv na nadřazenou položku. Další informace najdete v tématu [připojené a odpojené podřízené úlohy](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## <a name="associating-state-with-continuations"></a>Přidružení stavu k pokračováním  
 Můžete přidružit libovolný stav pokračování úlohy. Metoda <xref:System.Threading.Tasks.Task.ContinueWith%2A> poskytuje přetížené verze, které každá z nich převezme hodnotu <xref:System.Object>, která představuje stav pokračování. Později můžete přistupovat k tomuto objektu stavu pomocí vlastnosti <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType>. Tento objekt stavu je `null`, pokud nezadáte hodnotu.  
  
 Pokračování stavu je užitečné, pokud převedete existující kód, který používá [asynchronní programovací model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) pro použití rozhraní TPL. V APM obvykle poskytujete stav objektu v metodě **Begin**_metody_ a později získáte přístup k tomuto stavu pomocí vlastnosti <xref:System.IAsyncResult.AsyncState%2A?displayProperty=nameWithType>. Pomocí metody <xref:System.Threading.Tasks.Task.ContinueWith%2A> můžete zachovat tento stav při převodu kódu, který používá APM k použití rozhraní TPL.  
  
 Stav pokračování může být užitečné také při práci s <xref:System.Threading.Tasks.Task> objekty v ladicím programu sady Visual Studio. Například v okně **Paralelní úlohy** zobrazuje sloupec **úkoly** řetězcovou reprezentaci objektu State pro každý úkol. Další informace o okně **Paralelní úlohy** najdete v tématu [použití okna úlohy](/visualstudio/debugger/using-the-tasks-window).  
  
 Následující příklad ukazuje, jak použít stav pokračování. Vytvoří řetězec pokračujících úloh. Každý úkol poskytuje aktuální čas, objekt <xref:System.DateTime> pro parametr `state` metody <xref:System.Threading.Tasks.Task.ContinueWith%2A>. Každý objekt <xref:System.DateTime> představuje čas, kdy se vytvoří úkol pokračování. Každý úkol vytváří jako výsledek druhý objekt <xref:System.DateTime>, který představuje čas, kdy se úkol dokončí. Po dokončení všech úloh v tomto příkladu se zobrazí čas vytvoření a čas, kdy se Každá úloha pokračování dokončí.  
  
 [!code-csharp[TPL_ContinuationState#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuationstate/cs/continuationstate.cs#1)]
 [!code-vb[TPL_ContinuationState#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuationstate/vb/continuationstate.vb#1)]  
  
## <a name="handling-exceptions-thrown-from-continuations"></a>Zpracování výjimek vyvolaných z pokračování  
 Vztah předchůdce-pokračování není relace typu nadřazený-podřízený. Výjimky vyvolané pokračováním nejsou šířeny do předchůdce. Proto zpracujte výjimky vyvolané pokračováním, protože byste je měli zpracovat v jakékoli jiné úloze, a to následujícím způsobem:  
  
- Pro čekání na pokračování lze použít metodu <xref:System.Threading.Tasks.Task.Wait%2A>, <xref:System.Threading.Tasks.Task.WaitAll%2A>nebo <xref:System.Threading.Tasks.Task.WaitAny%2A> nebo její obecné protějšky. Můžete počkat na předchůdce a jeho pokračování ve stejném příkazu `try`, jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[TPL_Continuations#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception1.cs#6)]
     [!code-vb[TPL_Continuations#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception1.vb#6)]  
  
- Druhé pokračování můžete použít ke sledování vlastnosti <xref:System.Threading.Tasks.Task.Exception%2A> prvního pokračování. V následujícím příkladu se úloha pokusí o čtení z neexistujícího souboru. Pokračování potom zobrazí informace o výjimce v předchozí úloze.  
  
     [!code-csharp[TPL_Continuations#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#4)]
     [!code-vb[TPL_Continuations#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#4)]  
  
     Protože byl spuštěn s možností <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnFaulted?displayProperty=nameWithType>, pokračování se spustí pouze v případě, že v předchůdci dojde k výjimce, a proto může předpokládat, že vlastnost <xref:System.Threading.Tasks.Task.Exception%2A> předchůdce není `null`. Pokud se pokračování provede bez ohledu na to, zda je vyvolána výjimka v předchůdci, bude nutné ověřit, zda je před pokusem o zpracování výjimky ne`null`á vlastnost <xref:System.Threading.Tasks.Task.Exception%2A> předchůdce, jak ukazuje následující fragment kódu.  
  
     [!code-csharp[TPL_Continuations#11](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#11)]
     [!code-vb[TPL_Continuations#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#11)]  
  
     Další informace naleznete v tématu [zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
- Pokud je pokračování připojená podřízená úloha, která byla vytvořena pomocí možnosti <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType>, jejich výjimky budou rozšířeny nadřazeným objektem zpět do volajícího vlákna, jako je případ v jakémkoli jiném připojeném podřízeném prvku. Další informace najdete v tématu [připojené a odpojené podřízené úlohy](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## <a name="see-also"></a>Viz také

- [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
