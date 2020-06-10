---
title: Řetězení úloh pomocí úloh pokračování
description: Naučte se řetězit úkol pomocí úloh pokračování v .NET. Pokračující úkol je asynchronní úloha, která je vyvolána jinou úlohou.
ms.date: 02/11/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, continuations
ms.assetid: 0b45e9a2-de28-46ce-8212-1817280ed42d
ms.openlocfilehash: 90317f3db5bcf2371494e14a1ca1dd16d049e0bd
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662469"
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
 Pokračování je úkol, který je vytvořen ve <xref:System.Threading.Tasks.TaskStatus.WaitingForActivation> stavu. Aktivuje se automaticky po dokončení jeho předchozí úlohy nebo úkolů. Volání <xref:System.Threading.Tasks.Task.Start%2A?displayProperty=nameWithType> při pokračování v uživatelském kódu vyvolá <xref:System.InvalidOperationException?displayProperty=nameWithType> výjimku.  
  
 Pokračování je samo <xref:System.Threading.Tasks.Task> a neblokuje vlákno, ve kterém je spuštěno. Zavolejte <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metodu pro blokování do dokončení pokračování úlohy.  
  
## <a name="creating-a-continuation-for-a-single-antecedent"></a>Vytvoření pokračování pro jeden předchůdce  
 Můžete vytvořit pokračování, které se provede po dokončení jeho předchůdce voláním <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> metody. Následující příklad znázorňuje základní vzorek (pro přehlednost, vynechává se zpracování výjimek). Spustí předchozí úlohu, `taskA` která vrátí <xref:System.DayOfWeek> objekt, který označuje název aktuálního dne v týdnu. Po dokončení předchůdce se úkol pokračování předá `continuation` do předchůdce a zobrazí řetězec, který obsahuje jeho výsledek.

> [!NOTE]
> Ukázky v jazyce C# v tomto článku využívají `async` Modifikátor `Main` metody. Tato funkce je k dispozici v C# 7,1 a novějších. Předchozí verze vygenerovaly [`CS5001`](../../csharp/misc/cs5001.md) při kompilování tohoto ukázkového kódu. Je nutné nastavit jazykovou verzi na C# 7,1 nebo novější. Informace o tom, jak nakonfigurovat jazykovou verzi, najdete v článku o [konfiguraci jazykové verze](../../csharp/language-reference/configure-language-version.md).
  
 [!code-csharp[TPL_Continuations#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/simple1.cs#1)]
 [!code-vb[TPL_Continuations#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/simple1.vb#1)]  
  
## <a name="creating-a-continuation-for-multiple-antecedents"></a>Vytváření pokračování pro více předchůdců  
 Můžete také vytvořit pokračování, které se spustí, když se dokončí kterákoli nebo celá skupina úkolů. Chcete-li provést pokračování po dokončení všech předchozích úloh, zavoláte statickou `Shared` metodu (v Visual Basic) <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> nebo metodu instance <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> . Chcete-li provést pokračování po dokončení kteréhokoliv z předchozích úloh, zavoláte statickou metodu ( `Shared` v Visual Basic) <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> nebo <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType> metodu instance.  
  
 Všimněte si, že volání <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> přetížení neblokují volající vlákno.  Nicméně obvykle zavoláte <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> metodu a, <xref:System.Threading.Tasks.Task.WhenAll%28System.Threading.Tasks.Task%5B%5D%29?displayProperty=nameWithType> která načte vrácenou <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> vlastnost, která zablokuje volající vlákno.  
  
 Následující příklad volá <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> metodu pro vytvoření úlohy pokračování, která odráží výsledky jeho 10 předchozích úloh. Každý předchozí úkol napředá hodnotu indexu, která je v rozsahu od 1 do 10. Pokud se předchůdce úspěšně dokončí (jejich <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> vlastnost je <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType> ), <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> vlastnost pokračování je pole <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> hodnot vrácených jednotlivými předchůdci. Tento příklad je přidá k výpočtu součtu čtverců pro všechna čísla od 1 do 10.  
  
 [!code-csharp[TPL_Continuations#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/whenall1.cs#5)]
 [!code-vb[TPL_Continuations#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/whenall1.vb#5)]  
  
## <a name="continuation-options"></a>Možnosti pokračování  
 Když vytvoříte pokračování jedné úlohy, můžete použít <xref:System.Threading.Tasks.Task.ContinueWith%2A> přetížení, které přebírá <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> hodnotu výčtu, a určit podmínky, za kterých se spustí pokračování. Můžete například určit, že pokračování bude spuštěno pouze v případě, že se předchůdce úspěšně dokončí, nebo pouze v případě, že se dokončí v chybovém stavu. Pokud podmínka není pravdivá, pokud je předchůdce připraven k vyvolání pokračování, přechod pokračování přímo do <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> stavu a následně nemůže být spuštěn.  
  
 Několik metod pokračování více úloh, jako jsou například přetížení <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> metody, zahrnují také <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> parametr. Platná je však pouze podmnožina všech <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> členů výčtu. Můžete zadat <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> hodnoty, které mají protějšky ve <xref:System.Threading.Tasks.TaskCreationOptions?displayProperty=nameWithType> výčtu, například <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType> , <xref:System.Threading.Tasks.TaskContinuationOptions.LongRunning?displayProperty=nameWithType> a <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness?displayProperty=nameWithType> . Pokud zadáte některou z `NotOn` možností nebo v případě `OnlyOn` pokračování s více úlohami, <xref:System.ArgumentOutOfRangeException> bude vyvolána výjimka v době běhu.  
  
 Další informace o možnostech pokračování úlohy najdete v <xref:System.Threading.Tasks.TaskContinuationOptions> tématu.  
  
## <a name="passing-data-to-a-continuation"></a>Předávání dat do pokračování  
 <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>Metoda předává odkaz na předchůdce uživateli, který by pokračoval jako argument. Pokud je předchůdce <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> objekt a úloha byla spuštěna až do dokončení, pokračování může získat přístup k <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> Vlastnosti úlohy.  
  
 <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType>Vlastnost blokuje až do dokončení úlohy. Pokud se ale úloha zrušila nebo došlo k chybě, pokus o přístup k <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnosti vyvolá <xref:System.AggregateException> výjimku. Tomuto problému se můžete vyhnout pomocí <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnRanToCompletion> Možnosti, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[TPL_Continuations#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result1.cs#2)]
 [!code-vb[TPL_Continuations#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result1.vb#2)]  
  
 Pokud chcete pokračovat v běhu i v případě, že předchůdce nebyl úspěšně dokončen, je nutné před výjimkou provést ochranu. Jedním z přístupů je otestování <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> vlastnosti předchůdce a pokus o přístup k vlastnosti pouze v <xref:System.Threading.Tasks.Task%601.Result%2A> případě, že stav není <xref:System.Threading.Tasks.TaskStatus.Faulted> nebo <xref:System.Threading.Tasks.TaskStatus.Canceled> . Můžete také prostudovat <xref:System.Threading.Tasks.Task.Exception%2A> vlastnost předchůdce. Další informace naleznete v tématu [zpracování výjimek](exception-handling-task-parallel-library.md). Následující příklad upravuje předchozí příklad pro přístup k vlastnosti předchůdce <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> pouze v případě, že je její stav <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType> .  
  
 [!code-csharp[TPL_Continuations#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result2.cs#7)]
 [!code-vb[TPL_Continuations#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result2.vb#7)]  
  
## <a name="canceling-a-continuation"></a>Zrušení pokračování  
 <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType>Vlastnost pokračování je nastavena <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> v následujících situacích:  
  
- Vyvolá <xref:System.OperationCanceledException> výjimku v reakci na žádost o zrušení. Stejně jako u jakékoli úlohy, pokud výjimka obsahuje stejný token, který byl předán pokračování, je považována za potvrzení kooperativního zrušení.  
  
- Pokračování je úspěšné, <xref:System.Threading.CancellationToken?displayProperty=nameWithType> jehož <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost je `true` . V takovém případě se pokračování nespustí a přejde do <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> stavu.  
  
- Pokračování se nikdy nespustí, protože podmínka nastavená podle jeho <xref:System.Threading.Tasks.TaskContinuationOptions> argumentu nebyla splněna. Například pokud předchůdce přejde do <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> stavu, jeho pokračování, které bylo předáno, se <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnFaulted?displayProperty=nameWithType> nespustí, ale převede do <xref:System.Threading.Tasks.TaskStatus.Canceled> stavu.  
  
 Pokud úloha a její pokračování reprezentují dvě části stejné logické operace, můžete stejný token zrušení předat oběma úkolům, jak je znázorněno v následujícím příkladu. Skládá se z předchůdce, který generuje seznam celých čísel, která jsou dělitelná 33, která je předána pokračování. Pokračování zobrazí seznam. Předchůdce i pokračování v pravidelných intervalech se v náhodných intervalech pozastaví. Kromě toho <xref:System.Threading.Timer?displayProperty=nameWithType> se objekt používá ke spuštění `Elapsed` metody po pěti sekundách intervalu časového limitu. Tento příklad volá <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metodu, která způsobí, že aktuálně vykonávaná úloha volá <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A?displayProperty=nameWithType> metodu. Určuje, zda <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> je metoda volána, když předchůdce nebo jeho pokračování probíhá, závisí na době trvání náhodně generovaných pozastavení. Pokud je předchůdce zrušen, pokračování nebude zahájeno. Pokud předchůdce není zrušen, token lze nadále použít k zrušení pokračování.  
  
 [!code-csharp[TPL_Continuations#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation1.cs#3)]
 [!code-vb[TPL_Continuations#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation1.vb#3)]  
  
 Můžete také zabránit spuštění pokračování, pokud je jeho předchůdce zrušen bez zadání pokračování tokenu zrušení zadáním <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled?displayProperty=nameWithType> Možnosti při vytváření pokračování. Následuje jednoduchý příklad.  
  
 [!code-csharp[TPL_Continuations#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation2.cs#8)]
 [!code-vb[TPL_Continuations#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation2.vb#8)]  
  
 Poté, co pokračování přejde do <xref:System.Threading.Tasks.TaskStatus.Canceled> stavu, může ovlivnit pokračování, která následují, v závislosti na <xref:System.Threading.Tasks.TaskContinuationOptions> tom, které byly pro tyto pokračování zadány.  
  
 Pokračování, která jsou uvolněna, se nespustí.  
  
## <a name="continuations-and-child-tasks"></a>Pokračování a podřízené úlohy  
 Pokračování není spuštěno, dokud předchůdce a všechny jeho připojené podřízené úlohy nebyly dokončeny. Pokračování nečeká na dokončení odpojených podřízených úloh. Následující dva příklady ilustrují podřízené úlohy, které jsou připojeny k a odpojeny od předchůdce, který vytváří pokračování. V následujícím příkladu se pokračování spustí až po dokončení všech podřízených úloh a spuštění příkladu několikrát vytvoří stejný výstup. V příkladu se spustí předchůdce voláním <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metody, protože ve výchozím nastavení <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> Metoda vytvoří nadřazený úkol, jehož výchozí možnost vytvoření úlohy je <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> .  
  
 [!code-csharp[TPL_Continuations#9](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/attached1.cs#9)]
 [!code-vb[TPL_Continuations#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/attached1.vb#9)]  
  
 Pokud se ale podřízené úlohy odpojí od předchůdce, pokračování se spustí hned po ukončení předchůdce, a to bez ohledu na stav podřízených úloh. V důsledku toho může více spuštění z následujícího příkladu vytvořit proměnnou výstup, který závisí na tom, jak Plánovač úloh zpracoval každou podřízenou úlohu.  
  
 [!code-csharp[TPL_Continuations#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/detached1.cs#10)]
 [!code-vb[TPL_Continuations#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/detached1.vb#10)]  
  
 Konečný stav předchozí úlohy závisí na konečném stavu všech připojených podřízených úloh. Stav odpojených podřízených úloh nemá vliv na nadřazenou položku. Další informace najdete v tématu [připojené a odpojené podřízené úlohy](attached-and-detached-child-tasks.md).  
  
## <a name="associating-state-with-continuations"></a>Přidružení stavu k pokračováním  
 Můžete přidružit libovolný stav pokračování úlohy. <xref:System.Threading.Tasks.Task.ContinueWith%2A>Metoda poskytuje přetížené verze, které každá z nich vezme <xref:System.Object> hodnotu, která představuje stav pokračování. Později můžete přistupovat k tomuto objektu stavu pomocí <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> Vlastnosti. Tento objekt stavu je `null` v případě, že nezadáte hodnotu.  
  
 Pokračování stavu je užitečné, pokud převedete existující kód, který používá [asynchronní programovací model (APM)](../asynchronous-programming-patterns/asynchronous-programming-model-apm.md) pro použití rozhraní TPL. V APM obvykle poskytujete stav objektu v metodě **Begin**_metody_ a později získáte přístup k tomuto stavu pomocí <xref:System.IAsyncResult.AsyncState%2A?displayProperty=nameWithType> Vlastnosti. Pomocí <xref:System.Threading.Tasks.Task.ContinueWith%2A> metody můžete zachovat tento stav při převodu kódu, který používá APM k použití rozhraní TPL.  
  
 Stav pokračování může být užitečné také při práci s <xref:System.Threading.Tasks.Task> objekty v ladicím programu sady Visual Studio. Například v okně **Paralelní úlohy** zobrazuje sloupec **úkoly** řetězcovou reprezentaci objektu State pro každý úkol. Další informace o okně **Paralelní úlohy** najdete v tématu [použití okna úlohy](/visualstudio/debugger/using-the-tasks-window).  
  
 Následující příklad ukazuje, jak použít stav pokračování. Vytvoří řetězec pokračujících úloh. Každý úkol poskytuje aktuální čas, <xref:System.DateTime> objekt pro `state` parametr <xref:System.Threading.Tasks.Task.ContinueWith%2A> metody. Každý <xref:System.DateTime> objekt představuje čas, kdy je vytvořen úkol pokračování. Každý úkol vytváří jako výsledek druhý <xref:System.DateTime> objekt, který představuje čas, kdy se úkol dokončí. Po dokončení všech úloh v tomto příkladu se zobrazí čas vytvoření a čas, kdy se Každá úloha pokračování dokončí.  
  
 [!code-csharp[TPL_ContinuationState#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuationstate/cs/continuationstate.cs#1)]
 [!code-vb[TPL_ContinuationState#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuationstate/vb/continuationstate.vb#1)]  
  
## <a name="handling-exceptions-thrown-from-continuations"></a>Zpracování výjimek vyvolaných z pokračování  
 Vztah předchůdce-pokračování není relace typu nadřazený-podřízený. Výjimky vyvolané pokračováním nejsou šířeny do předchůdce. Proto zpracujte výjimky vyvolané pokračováním, protože byste je měli zpracovat v jakékoli jiné úloze, a to následujícím způsobem:  
  
- <xref:System.Threading.Tasks.Task.Wait%2A> <xref:System.Threading.Tasks.Task.WaitAll%2A> <xref:System.Threading.Tasks.Task.WaitAny%2A> Pro čekání na pokračování lze použít metodu, nebo nebo její obecné protějšky. Můžete počkat na předchůdce a jeho pokračování v rámci stejného `try` příkazu, jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[TPL_Continuations#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception1.cs#6)]
     [!code-vb[TPL_Continuations#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception1.vb#6)]  
  
- Můžete použít druhé pokračování a sledovat <xref:System.Threading.Tasks.Task.Exception%2A> vlastnost prvního pokračování. V následujícím příkladu se úloha pokusí o čtení z neexistujícího souboru. Pokračování potom zobrazí informace o výjimce v předchozí úloze.  
  
     [!code-csharp[TPL_Continuations#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#4)]
     [!code-vb[TPL_Continuations#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#4)]  
  
     Vzhledem k tomu, že byl spuštěn s <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnFaulted?displayProperty=nameWithType> možností, pokračování se spustí pouze v případě, že v předchůdci dojde k výjimce, a proto může předpokládat, že vlastnost předchůdce není <xref:System.Threading.Tasks.Task.Exception%2A> `null` . Pokud se pokračování provede bez ohledu na to, zda je výjimka vyvolána v předchůdci, bude nutné <xref:System.Threading.Tasks.Task.Exception%2A> před pokusem o zpracování výjimky ověřit, zda je vlastnost předchůdce `null` nepřed pokusem o zpracování výjimky, jak ukazuje následující fragment kódu.  
  
     [!code-csharp[TPL_Continuations#11](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#11)]
     [!code-vb[TPL_Continuations#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#11)]  
  
     Další informace naleznete v tématu [zpracování výjimek](exception-handling-task-parallel-library.md).  
  
- Pokud je pokračování připojená podřízená úloha, která byla vytvořena pomocí <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType> Možnosti, jejich výjimky budou rozšířeny nadřazeným objektem zpět do volajícího vlákna, jako je případ v jakémkoli jiném připojeném podřízeném prvku. Další informace najdete v tématu [připojené a odpojené podřízené úlohy](attached-and-detached-child-tasks.md).  
  
## <a name="see-also"></a>Viz také

- [Task Parallel Library (TPL)](task-parallel-library-tpl.md)
