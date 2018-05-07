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
ms.openlocfilehash: 27d97d38c903cbb33097db0e109758d98527e00f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="chaining-tasks-by-using-continuation-tasks"></a>Řetězení úloh pomocí úloh pokračování
V asynchronní programování, je velmi běžné jeden asynchronní operaci na dokončení pro vyvolání druhá operace a předat data. Obvyklým byla provedena pomocí metody zpětného volání. V Task Parallel Library stejné funkce poskytované *úloh pokračování*. Úloha pokračování (známou taky stejně jako pokračování) je asynchronní úkol, který je vyvolán jiná úloha, která se označuje jako *předchůdce*, až se dokončí předchůdce.  
  
 Pokračování jsou poměrně snadno použitelný, ale přesto jsou velmi výkonný a flexibilní. Například můžete:  
  
-   Předejte data z předchůdce pokračování.  
  
-   Zadejte přesné podmínky, za kterých pokračování bude či není vyvolána.  
  
-   Zrušení pokračování buď před spuštěním nebo spolupráce při spuštěné.  
  
-   Poskytnout nápovědu, jak má být naplánováno pokračování.  
  
-   Vyvolání více pokračování ze stejného předchůdce.  
  
-   Po dokončení všech nebo jakoukoli jednu z více předchůdců vyvolejte jedno pokračování.  
  
-   Zřetězené pokračování za sebou žádné libovolné délce.  
  
-   Zpracování výjimek vyvolaných předchůdcem pomocí pokračování.  
  
## <a name="about-continuations"></a>O pokračování  
 Pokračování je úkol, který je vytvořen v <xref:System.Threading.Tasks.TaskStatus.WaitingForActivation> stavu. Je aktivovaná automaticky po dokončení jeho předchozí úlohou nebo úlohy. Volání metody <xref:System.Threading.Tasks.Task.Start%2A?displayProperty=nameWithType> na pokračování v uživatelském kódu vyvolá <xref:System.InvalidOperationException?displayProperty=nameWithType> výjimka.  
  
 Pokračování je sám <xref:System.Threading.Tasks.Task> a neblokuje vláken, na kterém je spuštěná. Volání <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metoda blokování, dokud nebude dokončeno úkolů pokračování.  
  
## <a name="creating-a-continuation-for-a-single-antecedent"></a>Vytváření pokračování pro jeden předchůdce  
 Vytvoření pokračování, které se spustí po dokončení jeho předchůdce voláním <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> metoda. Následující příklad ukazuje základní vzor, (pro přehlednost, je vynechaný zpracování výjimek). Se provede předchozí úlohou, `taskA`, který vrátí <xref:System.DayOfWeek> objekt, který označuje název aktuální den v týdnu. Po dokončení předchůdce úlohu pokračování `taskB`, je předaná předchůdce a zobrazí řetězec, který zahrnuje její výsledek.  
  
 [!code-csharp[TPL_Continuations#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/simple1.cs#1)]
 [!code-vb[TPL_Continuations#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/simple1.vb#1)]  
  
## <a name="creating-a-continuation-for-multiple-antecedents"></a>Vytváření pokračování pro více předchůdců  
 Můžete také vytvořit pokračování, který se spustí po dokončení některé nebo všechny skupiny úloh. Provést pokračování, když byly dokončeny všechny předchozí úlohy, zavolejte statickou (`Shared` v jazyce Visual Basic) <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> metodu nebo instanci <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> metoda. Provést pokračování některé z předchozích úloh po dokončení, zavolejte statickou (`Shared` v jazyce Visual Basic) <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> metodu nebo instanci <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType> metoda.  
  
 Všimněte si, že volá, aby se <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> přetížení neblokují volající vlákno.  Však obvykle volání všechny ale na <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.WhenAll%28System.Threading.Tasks.Task%5B%5D%29?displayProperty=nameWithType> metody načíst vrácený <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> vlastnosti, která blokují volající vlákno.  
  
 Následující příklad volání <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> metodu pro vytvoření pokračování úlohu, která zobrazuje výsledky jeho deset předchozí úlohy. Každý předchozí úlohou Umocní druhou hodnotu indexu, které rozsahy od 1 do 10. Pokud předchůdců úspěšně dokončit (jejich <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> vlastnost je <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>), <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> vlastnost pokračování je pole <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> hodnot vrácených každý předchůdce. V příkladu se přidají do výpočetní součet kvadratických hodnot pro všechna čísla mezi jeden a 10.  
  
 [!code-csharp[TPL_Continuations#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/whenall1.cs#5)]
 [!code-vb[TPL_Continuations#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/whenall1.vb#5)]  
  
## <a name="continuation-options"></a>Možnosti pokračování  
 Když vytvoříte pokračování jedné úlohy, můžete použít <xref:System.Threading.Tasks.Task.ContinueWith%2A> přetížení, které přijímá <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> hodnota výčtu k určení podmínek, za kterých se spustí o pokračování. Například můžete určit, že pokračování bude spustit jenom v případě, že je předchůdce dokončen úspěšně, nebo jenom v případě, že dokončení v chybovém stavu. Pokud podmínka není true, pokud předchůdce je připraven k vyvolání pokračování, pokračování přejde přímo na <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> stavu a nemůže být dále spuštěno.  
  
 Počet pokračování metody, jako jsou přetížení <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> metoda, také zahrnovat <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> parametr. Pouze podmnožinu všech <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> členy výčtu je platný, ale. Můžete zadat <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> hodnoty, které mají svými protějšky v <xref:System.Threading.Tasks.TaskCreationOptions?displayProperty=nameWithType> výčtu, například <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType>, <xref:System.Threading.Tasks.TaskContinuationOptions.LongRunning?displayProperty=nameWithType>, a <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness?displayProperty=nameWithType>. Pokud je zadána některá z `NotOn` nebo `OnlyOn` možnosti pokračování, <xref:System.ArgumentOutOfRangeException> v době běhu bude vyvolána výjimka.  
  
 Další informace o možnostech úkolů pokračování najdete v tématu <xref:System.Threading.Tasks.TaskContinuationOptions> tématu.  
  
## <a name="passing-data-to-a-continuation"></a>Předání dat pokračování  
 <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> Metoda předá reference na předchůdce uživatelskému delegátovi pokračování jako argument. Pokud je předchůdce <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> objekt a úlohy spustili dokud byla dokončena, je k pokračování přístup <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> vlastnosti úlohy.  
  
 <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> Vlastnost blokuje až po dokončení úlohy. Ale pokud úloha byla zrušena nebo došlo k chybě, pokusu o přístup k <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost vyvolává <xref:System.AggregateException> výjimka. Tento problém můžete vyhnout použitím <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnRanToCompletion> možnost, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[TPL_Continuations#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result1.cs#2)]
 [!code-vb[TPL_Continuations#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result1.vb#2)]  
  
 Pokud chcete o pokračování spustit i v případě, že předchůdce nebyl spuštěn na úspěšné dokončení, musíte chránit proti výjimku. Jeden z přístupů je k testování <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> vlastnost předchozí a pouze pokusí o přístup <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost Pokud stav není <xref:System.Threading.Tasks.TaskStatus.Faulted> nebo <xref:System.Threading.Tasks.TaskStatus.Canceled>. Můžete také zkontrolovat <xref:System.Threading.Tasks.Task.Exception%2A> vlastnost předchozího kroku. Další informace najdete v tématu [zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md). Následující příklad změní předchozí příklad pro předchůdce přístup <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> vlastnost pouze v případě, že má stav <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>.  
  
 [!code-csharp[TPL_Continuations#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result2.cs#7)]
 [!code-vb[TPL_Continuations#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result2.vb#7)]  
  
## <a name="canceling-a-continuation"></a>Zrušení pokračování  
 <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> Pokračování je nastavena na <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> v následujících situacích:  
  
-   Vyvolá <xref:System.OperationCanceledException> výjimka v reakci na žádost o zrušení. Stejně jako u jakékoli jiné úlohy, pokud výjimka obsahuje stejný token, který byl předán pokračování, bude považován za potvrzení o spolupráci zrušení.  
  
-   Pokračování je předána <xref:System.Threading.CancellationToken?displayProperty=nameWithType> jejichž <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost je `true`. V takovém případě pokračování se nespustí a přechází na <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> stavu.  
  
-   Pokračování nikdy nespustí, protože podmínka nastavena podle jeho <xref:System.Threading.Tasks.TaskContinuationOptions> argument nebyl splněn. Například, pokud předchůdce přejde do <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> stavu, který byl předán pokračování <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnFaulted?displayProperty=nameWithType> možnost nespustí, ale přejde do <xref:System.Threading.Tasks.TaskStatus.Canceled> stavu.  
  
 Pokud úlohy a její pokračování představují dvě části stejné logické operace, můžete předat stejný token zrušení pro obě úlohy, jak je znázorněno v následujícím příkladu. Skládá se z předchůdce, který generuje seznam celých čísel, které jsou dělitelná 33, který předává do pokračování. Pokračování pak zobrazí v seznamu. Předchůdce a pokračování pozastavit pravidelně v náhodných intervalech. Kromě toho <xref:System.Threading.Timer?displayProperty=nameWithType> objekt se používá k provedení `Elapsed` metoda po vypršení časového limitu pěti sekund intervalu. Volá <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metoda, což způsobí, že aktuálně prováděné úlohy k volání <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A?displayProperty=nameWithType> metoda. Jestli <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metoda je volána, když je prováděna předchůdce nebo jeho pokračování závisí na dobu trvání náhodně generované pozastaví. Pokud je předchůdce zrušen, pokračování se nespustí. Pokud není předchůdce zrušen, token pořád můžou použít pro zrušení pokračování.  
  
 [!code-csharp[TPL_Continuations#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation1.cs#3)]
 [!code-vb[TPL_Continuations#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation1.vb#3)]  
  
 Můžete také zabránit spuštění, pokud je zrušen předchůdce bez nutnosti zadávat pokračování pokračování token zrušení zadáním <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled?displayProperty=nameWithType> při vytváření pokračování. Zde je jednoduchý příklad.  
  
 [!code-csharp[TPL_Continuations#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation2.cs#8)]
 [!code-vb[TPL_Continuations#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation2.vb#8)]  
  
 Přechod do pokračování <xref:System.Threading.Tasks.TaskStatus.Canceled> stavu, může to mít vliv pokračování, které následují, v závislosti na <xref:System.Threading.Tasks.TaskContinuationOptions> které bylo zadáno pro tyto pokračování.  
  
 Pokračování, které jsou zapomenuty se nespustí.  
  
## <a name="continuations-and-child-tasks"></a>Pokračování a podřízené úlohy  
 Pokračování nespustí dokud předchůdce a všech jeho podřízených úloh byly dokončeny. Pokračování nečeká odpojené podřízené úlohy ukončíte. Následující dva příklady ilustrují podřízené úlohy, které jsou připojeny k a odpojený od předchůdce, který vytvoří pokračování. V následujícím příkladu spustí pokračování až poté, co byly dokončeny všechny podřízené úlohy, a spuštění příkladu vícekrát vytváří identické výstupní pokaždé, když. Všimněte si, že v příkladu spustí předchůdce voláním <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metoda, protože ve výchozím nastavení <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metoda vytvoří nadřazené úlohu, jejíž výchozí možnost vytváření úloh je <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>.  
  
 [!code-csharp[TPL_Continuations#9](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/attached1.cs#9)]
 [!code-vb[TPL_Continuations#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/attached1.vb#9)]  
  
 Pokud z předchůdce jsou odpojené podřízené úlohy, ale o pokračování spustí, jakmile předchůdce ukončilo bez ohledu na stav podřízené úlohy. V důsledku toho více běží v následujícím příkladu může vytvářet proměnné výstupu, který závisí na způsob Plánovač úloh zpracování každé podřízené úlohy.  
  
 [!code-csharp[TPL_Continuations#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/detached1.cs#10)]
 [!code-vb[TPL_Continuations#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/detached1.vb#10)]  
  
 Poslední stav předchozí úlohou závisí na konečného stavu všech podřízených úloh. Stav odpojené podřízené úlohy nemá vliv na nadřazený. Další informace najdete v tématu [připojené a odpojené podřízené úlohy](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## <a name="associating-state-with-continuations"></a>Stav přidružení k pokračování  
 Libovolný stavu můžete přidružit úkolů pokračování. <xref:System.Threading.Tasks.Task.ContinueWith%2A> Metoda nabízí přetížené verze, která každý proveďte <xref:System.Object> hodnotu, která představuje stav pokračování. Můžete později přístup k tomuto objektu stavu pomocí <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> vlastnost. Tento objekt stavu je `null` Pokud nezadáte hodnotu.  
  
 Pokračování stavu je užitečné, když převést stávající kód, který používá [asynchronní programování modelu (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) použití TPL. V APM, je obvykle zadat stav objektu v **začít *** metoda* metoda a později přístup, který stavu pomocí <xref:System.IAsyncResult.AsyncState%2A?displayProperty=nameWithType> vlastnost. Pomocí <xref:System.Threading.Tasks.Task.ContinueWith%2A> metodu, můžete zachovat tento stav při převodu kód, který používá APM použití TPL.  
  
 Pokračování stavu může být také užitečná při práci s <xref:System.Threading.Tasks.Task> objekty v ladicím programu sady Visual Studio. Například v **paralelních úloh** okně **úloh** sloupec zobrazuje řetězcovou reprezentaci objektu stav pro každý úkol. Další informace o **paralelních úloh** okně najdete v části [používání okna úloh](/visualstudio/debugger/using-the-tasks-window).  
  
 Následující příklad ukazuje, jak se používání stavu pokračování. Vytvoří řetězec úloh pokračování. Každý úkol poskytuje aktuální čas <xref:System.DateTime> objekt, pro `state` parametr <xref:System.Threading.Tasks.Task.ContinueWith%2A> metoda. Každý <xref:System.DateTime> objekt představuje čas, kdy bude úloha pokračování vytvořena. Každý úkol vytváří jako výsledek a sekundu <xref:System.DateTime> objekt, který představuje čas, kdy na dokončení úlohy. Po dokončení všech úloh tento příklad zobrazuje čas vytvoření a čas, na které každý pokračování úkol dokončí.  
  
 [!code-csharp[TPL_ContinuationState#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuationstate/cs/continuationstate.cs#1)]
 [!code-vb[TPL_ContinuationState#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuationstate/vb/continuationstate.vb#1)]  
  
## <a name="handling-exceptions-thrown-from-continuations"></a>Zpracování výjimek vyvolaných z pokračování  
 Relaci předchůdce pokračování se nejedná o relaci nadřazený podřízený. Výjimky vyvolané pokračováním nebudou rozšířeny na předchůdce. Proto zpracování výjimky vyvolané pokračováním, jako je v jiné úlohy, následujícím způsobem:  
  
-   Můžete použít <xref:System.Threading.Tasks.Task.Wait%2A>, <xref:System.Threading.Tasks.Task.WaitAll%2A>, nebo <xref:System.Threading.Tasks.Task.WaitAny%2A> metoda nebo jeho obecný protějšek k čekání na pokračování. Počkejte, až předchůdce a jeho pokračování ve stejné `try` příkaz, jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[TPL_Continuations#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception1.cs#6)]
     [!code-vb[TPL_Continuations#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception1.vb#6)]  
  
-   Druhý pokračování můžete sledovat <xref:System.Threading.Tasks.Task.Exception%2A> vlastnost prvního pokračování. V následujícím příkladu úloha pokusí číst z neexistující soubor. Pokračování pak zobrazí informace o výjimce v předchozí úlohou.  
  
     [!code-csharp[TPL_Continuations#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#4)]
     [!code-vb[TPL_Continuations#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#4)]  
  
     Vzhledem k tomu, že byla spuštěna s <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnFaulted?displayProperty=nameWithType> možnost pokračování provádí pouze v případě, že dojde k výjimce předchůdce, a proto ji můžete předpokládat, že je předchůdce <xref:System.Threading.Tasks.Task.Exception%2A> vlastnost není `null`. Pokud se o pokračování provede, zda je vyvolána výjimka předchůdce, by mělo zkontrolujte, zda je předchůdce <xref:System.Threading.Tasks.Task.Exception%2A> vlastnost není `null` před pokusem o zpracování výjimky, jako následující fragment kódu ukazuje.  
  
     [!code-csharp[TPL_Continuations#11](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#11)]
     [!code-vb[TPL_Continuations#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#11)]  
  
     Další informace najdete v tématu [zpracování výjimek](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md) a [NIB: postupy: zpracování výjimek vyvolaných úlohami](https://msdn.microsoft.com/library/d6c47ec8-9de9-4880-beb3-ff19ae51565d).  
  
-   Pokud se o pokračování je připojená úloha, která byla vytvořena pomocí <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType> možnost, se rozšíří jeho výjimky nadřízený objekt zpět do volající vlákno, jako je tomu v jiných připojené podřízené. Další informace najdete v tématu [připojené a odpojené podřízené úlohy](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## <a name="see-also"></a>Viz také  
 [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
