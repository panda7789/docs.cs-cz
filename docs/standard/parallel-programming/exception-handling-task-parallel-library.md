---
title: Zpracování výjimek (paralelní knihovna úloh)
ms.date: 04/20/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, exceptions
ms.assetid: beb51e50-9061-4d3d-908c-56a4f7c2e8c1
ms.openlocfilehash: aa6d4b706eb11921ffd419402bcf4cf059a29b11
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021508"
---
# <a name="exception-handling-task-parallel-library"></a>Zpracování výjimek (paralelní knihovna úloh)

Neošetřené výjimky, které jsou vyvolány uživatelským kódem, který je spuštěn uvnitř úlohy, jsou šířeny zpět do volajícího vlákna, s výjimkou určitých scénářů, které jsou popsány dále v tomto tématu. Výjimky jsou šířeny při použití jedné ze <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> statických metod nebo metod instance a `try` / `catch` zpracováváte je ohraničujícím volání v příkazu. Pokud je úkol nadřazenou podřízenou úlohou připojených podřízených úloh nebo pokud čekáte na více úkolů, může být vyvoláno více výjimek.

Aby bylo možné šířit všechny výjimky zpět do hlavního vlákna, infrastruktura úkolů je zabaluje do instance <xref:System.AggregateException>. Výjimka <xref:System.AggregateException> má <xref:System.AggregateException.InnerExceptions%2A> vlastnost, která může být výčtu zkoumat všechny původní výjimky, které byly vyvolány a zpracování (nebo nezpracování) každý z nich jednotlivě. Můžete také zpracovat původní výjimky <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> pomocí metody.

I v případě, že je vyvolána pouze <xref:System.AggregateException> jedna výjimka, je stále zabalena do výjimky, jak ukazuje následující příklad.

[!code-csharp[TPL_Exceptions#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling21.cs#21)]
[!code-vb[TPL_Exceptions#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling21.vb#21)]

Nezpracované výjimce se můžete vyhnout zachycením instance <xref:System.AggregateException> a ignorováním jakýchkoli vnitřních výjimek. Doporučujeme však nedělat to, protože je obdobou zachycení <xref:System.Exception> základní typ v neparalelní scénáře. Pokud zachytíte výjimku, a potom neprovedete žádnou konkrétní akci zotavení, bude program ponechán v neurčitém stavu.

Pokud nechcete volat metodu <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> čekat na dokončení úkolu, můžete také <xref:System.AggregateException> načíst výjimku <xref:System.Threading.Tasks.Task.Exception%2A> z vlastnosti úkolu, jak ukazuje následující příklad. Další informace naleznete [v části Sledování výjimek pomocí části Vlastnost Task.Exception](#observing-exceptions-by-using-the-taskexception-property) v tomto tématu.

[!code-csharp[TPL_Exceptions#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling22.cs#29)]
[!code-vb[TPL_Exceptions#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling22.vb#29)]

Pokud nečekáte na úlohu, která šíří výjimku, nebo přístup k jeho <xref:System.Threading.Tasks.Task.Exception%2A> vlastnosti, výjimka je eskalována podle zásady výjimky .NET při uvolňování úlohy.

Pokud jsou povoleny výjimky bubliny zpět do spojovacího vlákna, je možné, že úkol může pokračovat ve zpracování některých položek po vyvolání výjimky.

> [!NOTE]
> Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“. Tato chyba je neškodná. Můžete pokračovat stisknutím klávesy F5 a zjistit, jakým způsobem jsou zpracovaný výjimky, což je znázorněno v těchto příkladech. Chcete-li zabránit visual studio z rozdělení na první chybu, stačí zrušit zaškrtnutí políčka **Povolit pouze můj kód** v části **Nástroje, možnosti, ladění, obecné**.

## <a name="attached-child-tasks-and-nested-aggregateexceptions"></a>Připojené podřízené úkoly a vnořené aggregateExceptions

Pokud úloha obsahuje připojené podřízené úlohy, které způsobí výjimku, je tato výjimka zabalená do instance <xref:System.AggregateException> předtím, než je postoupena do nadřazené úlohy, která zabalí tuto výjimku do vlastní instance <xref:System.AggregateException> dříve, než ji postoupí zpět do volajícího vlákna. V takových případech <xref:System.AggregateException.InnerExceptions%2A> vlastnost <xref:System.AggregateException> výjimky, která <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>je <xref:System.Threading.Tasks.Task.WaitAny%2A>zachycena v , nebo <xref:System.Threading.Tasks.Task.WaitAll%2A> metoda obsahuje jednu nebo více <xref:System.AggregateException> instancí, nikoli původní výjimky, které způsobily chybu. Chcete-li se vyhnout nutnosti <xref:System.AggregateException> iterát přes <xref:System.AggregateException.Flatten%2A> vnořené výjimky, můžete použít metodu k odebrání všech vnořených <xref:System.AggregateException> výjimek tak, aby <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> vlastnost obsahuje původní výjimky. V následujícím příkladu jsou vnořené instance <xref:System.AggregateException> zploštěny a zpracovávány pouze v jednom průchodu.

[!code-csharp[TPL_Exceptions#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/flatten2.cs#22)]
[!code-vb[TPL_Exceptions#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/flatten2.vb#22)]

Můžete také použít <xref:System.AggregateException.Flatten%2A?displayProperty=nameWithType> metodu znovu vyvolat vnitřní <xref:System.AggregateException> výjimky z více instancí <xref:System.AggregateException> vyvolána více úkolů v jedné instanci, jak ukazuje následující příklad.

[!code-csharp[TPL_Exceptions#13](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions2.cs#13)]
[!code-vb[TPL_Exceptions#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions2.vb#13)]

## <a name="exceptions-from-detached-child-tasks"></a>Výjimky z odpojených podřízených úkolů

Ve výchozím nastavení jsou podřízené úkoly vytvořeny jako odpojené. Výjimky vyvolané z odpojených úkolů musí být zpracovány nebo znovu vyvolány ihned v nadřazeném úkolu. Tyto výjimky nejsou šířeny zpět do volajícího vlákna stejným způsobem jako připojené úkoly. Nejvyšší nadřazený může ručně znovu vyvolat výjimku z odpojené <xref:System.AggregateException> podřízené způsobit, že má být zabalen a šířen zpět do volajícího vlákna.

[!code-csharp[TPL_Exceptions#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/detached21.cs#23)]
[!code-vb[TPL_Exceptions#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/detached21.vb#23)]

I pokud používáte pokračování pro sledování výjimky v podřízeném úkolu, musí být výjimka stále sledována nadřazeným úkolem.

## <a name="exceptions-that-indicate-cooperative-cancellation"></a>Výjimky, které označují zrušení spolupráce

Pokud uživatelský kód v rámci úkolu odpoví na požadavek zrušení, mělo by správně dojít k vyvolání výjimky <xref:System.OperationCanceledException> a předání v tokenu zrušení, na kterém byl požadavek sdělen. Dříve než se pokusí o postoupení výjimky, porovná úkol token ve výjimce s tokenem, který byl předán při vytváření. Pokud se shodují, daný úkol postoupí výjimku <xref:System.Threading.Tasks.TaskCanceledException> zabalenou v instanci <xref:System.AggregateException> a lze ji zobrazit při ověřování vnořené výjimky. Pokud však volající vlákno na úlohu nečeká, nebude tato konkrétní výjimka rozšířena. Další informace naleznete v [tématu Zrušení úkolu](../../../docs/standard/parallel-programming/task-cancellation.md).

[!code-csharp[TPL_Exceptions#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#4)]
[!code-vb[TPL_Exceptions#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/tpl_exceptions.vb#4)]

## <a name="using-the-handle-method-to-filter-inner-exceptions"></a>Použití metody popisovače k filtrování vnitřních výjimek

Metodu <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> můžete použít k filtrování výjimek, které lze považovat jako „zpracované“ bez použití jakékoli další logiky. V delegáta uživatele, který <xref:System.AggregateException.Handle%28System.Func%7BSystem.Exception%2CSystem.Boolean%7D%29?displayProperty=nameWithType> je dodáván k metodě, <xref:System.Exception.Message%2A> můžete zkontrolovat typ výjimky, jeho vlastnost nebo jakékoli jiné informace o něm, které vám umožní určit, zda je neškodný. Všechny výjimky, pro `false` které delegát vrátí jsou <xref:System.AggregateException> znovu vyvolány v nové instanci ihned po <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> vrátí metoda.

Následující příklad je funkčně ekvivalentní prvnímu příkladu v tomto <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> tématu, který zkoumá každou výjimku v kolekci.  Místo toho tato obslužná rutina výjimky volá objekt <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> metody `CustomException` pro každou výjimku a pouze znovu vyvolá výjimky, které nejsou instancemi.

[!code-csharp[TPL_Exceptions#26](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handlemethod21.cs#26)]
[!code-vb[TPL_Exceptions#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handlemethod21.vb#26)]

Následuje úplnější příklad, který <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> používá metodu k <xref:System.UnauthorizedAccessException> poskytnutí zvláštního zpracování výjimky při výčtu souborů.

[!code-csharp[TPL_Exceptions#12](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions.cs#12)]
[!code-vb[TPL_Exceptions#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions.vb#12)]

## <a name="observing-exceptions-by-using-the-taskexception-property"></a>Pozorování výjimek pomocí vlastnosti Task.Exception

Pokud úkol skončí ve stavu <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType>, může být její vlastnost <xref:System.Threading.Tasks.Task.Exception%2A> přezkoumána a zjištěna výjimka, která chybu způsobila. Vhodným způsobem sledování vlastnosti <xref:System.Threading.Tasks.Task.Exception%2A> je použití pokračování, které se spouští pouze v případě selhání předchozího úkolu, jak je znázorněno v následujícím příkladu.

[!code-csharp[TPL_Exceptions#27](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptionprop21.cs#27)]
[!code-vb[TPL_Exceptions#27](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionprop21.vb#27)]

Ve smysluplné aplikaci může delegát pokračování protokolovat podrobné informace o výjimce a případně vytvořit nové úkoly, které se z výjimky zotaví. Pokud úloha chyby, následující výrazy vyvolat výjimku:

- `await task`
- `task.Wait()`
- `task.Result`
- `task.GetAwaiter().GetResult()`

Použijte [`try-catch`](../../csharp/language-reference/keywords/try-catch.md) příkaz pro zpracování a sledování vyzdvižené výjimky. Případně dodržujte výjimku přístupem <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> k vlastnosti.

## <a name="unobservedtaskexception-event"></a>Událost UnobservedTaskException

V některých situacích, jako je například hostování nedůvěryhodných zásuvných modulů, mohou být neškodné výjimky běžné a může být příliš obtížné je všechny sledovat ručně. V těchto případech je možné zpracovat událost <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=nameWithType>. Instance <xref:System.Threading.Tasks.UnobservedTaskExceptionEventArgs?displayProperty=nameWithType>, která je předána obslužné rutině, může být použita k zamezení šíření nesledovaných výjimek zpět do spojovacího vlákna.

## <a name="see-also"></a>Viz také

- [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
