---
title: Zpracování výjimek (Task Parallel Library)
description: Prozkoumejte zpracování výjimek pomocí Task Parallel Library (TPL) v rozhraní .NET. Viz vnořené agregované výjimky, vnitřní výjimky, nepozorované výjimky úloh & další.
ms.date: 04/20/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, exceptions
ms.assetid: beb51e50-9061-4d3d-908c-56a4f7c2e8c1
ms.openlocfilehash: f1c1a994f4b3a8df0556a0190bc4eacb63f2921e
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662534"
---
# <a name="exception-handling-task-parallel-library"></a>Zpracování výjimek (Task Parallel Library)

Neošetřené výjimky, které jsou vyvolány uživatelským kódem, který je spuštěn v rámci úlohy, jsou šířeny zpět do volajícího vlákna, s výjimkou některých scénářů, které jsou popsány dále v tomto tématu. Výjimky jsou šířeny při použití jedné ze statických nebo instančních <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metod a jejich zpracování uzavřením volání do `try` / `catch` příkazu. Pokud je úkol nadřazený k připojeným podřízeným úkolům nebo pokud čekáte na více úloh, může být vyvoláno více výjimek.

Aby bylo možné šířit všechny výjimky zpět do hlavního vlákna, infrastruktura úkolů je zabaluje do instance <xref:System.AggregateException>. <xref:System.AggregateException>Výjimka má <xref:System.AggregateException.InnerExceptions%2A> vlastnost, která může být vytvořena výčtem, aby prověřila všechny původní výjimky, které byly vyvolány, a zpracovala (nebo nezpracovává) každou z nich jednotlivě. Původní výjimky lze také zpracovat pomocí <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> metody.

I v případě, že je vyvolána pouze jedna výjimka, je stále zabalena do <xref:System.AggregateException> výjimky, jak ukazuje následující příklad.

[!code-csharp[TPL_Exceptions#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling21.cs#21)]
[!code-vb[TPL_Exceptions#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling21.vb#21)]

Nezpracované výjimce se můžete vyhnout zachycením instance <xref:System.AggregateException> a ignorováním jakýchkoli vnitřních výjimek. Nicméně doporučujeme, abyste to provedli, protože se podobá zachycení základního <xref:System.Exception> typu v neparalelních scénářích. Pokud zachytíte výjimku, a potom neprovedete žádnou konkrétní akci zotavení, bude program ponechán v neurčitém stavu.

Pokud nechcete volat <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metodu pro čekání na dokončení úlohy, můžete také načíst <xref:System.AggregateException> výjimku z <xref:System.Threading.Tasks.Task.Exception%2A> vlastnosti úkolu, jak ukazuje následující příklad. Další informace naleznete v části [sledování výjimek pomocí vlastnosti Task. Exception](#observing-exceptions-by-using-the-taskexception-property) v tomto tématu.

[!code-csharp[TPL_Exceptions#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling22.cs#29)]
[!code-vb[TPL_Exceptions#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling22.vb#29)]

Pokud nečekáte na úlohu, která šíří výjimku, nebo ke své <xref:System.Threading.Tasks.Task.Exception%2A> vlastnosti, je výjimka předávána v souladu se zásadami výjimky rozhraní .NET, pokud je úloha uvolněna z paměti.

Pokud jsou výjimky povoleny k bublinám zpět do spojovacího vlákna, je možné, že úloha může pokračovat ve zpracování některých položek poté, co je vyvolána výjimka.

> [!NOTE]
> Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“. Tato chyba je neškodná. Můžete pokračovat stisknutím klávesy F5 a zjistit, jakým způsobem jsou zpracovaný výjimky, což je znázorněno v těchto příkladech. Chcete-li aplikaci Visual Studio zabránit v přerušení první chyby, zrušte zaškrtnutí políčka **povolit pouze můj kód** v části **nástroje, možnosti, ladění, obecné**.

## <a name="attached-child-tasks-and-nested-aggregateexceptions"></a>Připojené podřízené úlohy a vnořené AggregateExceptions

Pokud úloha obsahuje připojené podřízené úlohy, které způsobí výjimku, je tato výjimka zabalená do instance <xref:System.AggregateException> předtím, než je postoupena do nadřazené úlohy, která zabalí tuto výjimku do vlastní instance <xref:System.AggregateException> dříve, než ji postoupí zpět do volajícího vlákna. V takových případech <xref:System.AggregateException.InnerExceptions%2A> vlastnost <xref:System.AggregateException> výjimky, která je zachycena v <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task.WaitAny%2A> metodě, nebo <xref:System.Threading.Tasks.Task.WaitAll%2A> obsahuje jednu nebo více <xref:System.AggregateException> instancí, nikoli původní výjimky, které způsobily chybu. Chcete-li se vyhnout nutnosti iterovat vnořené <xref:System.AggregateException> výjimky, můžete použít <xref:System.AggregateException.Flatten%2A> metodu k odebrání všech vnořených <xref:System.AggregateException> výjimek, takže <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> vlastnost obsahuje původní výjimky. V následujícím příkladu jsou vnořené instance <xref:System.AggregateException> zploštěny a zpracovávány pouze v jednom průchodu.

[!code-csharp[TPL_Exceptions#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/flatten2.cs#22)]
[!code-vb[TPL_Exceptions#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/flatten2.vb#22)]

Můžete také použít <xref:System.AggregateException.Flatten%2A?displayProperty=nameWithType> metodu k opětovnému vyvolání vnitřních výjimek z více <xref:System.AggregateException> instancí vyvolaných více úlohami v rámci jedné <xref:System.AggregateException> instance, jak ukazuje následující příklad.

[!code-csharp[TPL_Exceptions#13](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions2.cs#13)]
[!code-vb[TPL_Exceptions#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions2.vb#13)]

## <a name="exceptions-from-detached-child-tasks"></a>Výjimky z odpojených podřízených úloh

Ve výchozím nastavení jsou podřízené úkoly vytvořeny jako odpojené. Výjimky vyvolané z odpojených úkolů musí být zpracovány nebo znovu vyvolány ihned v nadřazeném úkolu. Tyto výjimky nejsou šířeny zpět do volajícího vlákna stejným způsobem jako připojené úkoly. Nejvyšší nadřazený prvek může ručně znovu vyvolat výjimku z odpojeného podřízeného objektu, aby mohl být zabalen do <xref:System.AggregateException> a šířen zpět do volajícího vlákna.

[!code-csharp[TPL_Exceptions#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/detached21.cs#23)]
[!code-vb[TPL_Exceptions#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/detached21.vb#23)]

I pokud používáte pokračování pro sledování výjimky v podřízeném úkolu, musí být výjimka stále sledována nadřazeným úkolem.

## <a name="exceptions-that-indicate-cooperative-cancellation"></a>Výjimky indikující kooperativní zrušení

Pokud uživatelský kód v rámci úkolu odpoví na požadavek zrušení, mělo by správně dojít k vyvolání výjimky <xref:System.OperationCanceledException> a předání v tokenu zrušení, na kterém byl požadavek sdělen. Dříve než se pokusí o postoupení výjimky, porovná úkol token ve výjimce s tokenem, který byl předán při vytváření. Pokud se shodují, daný úkol postoupí výjimku <xref:System.Threading.Tasks.TaskCanceledException> zabalenou v instanci <xref:System.AggregateException> a lze ji zobrazit při ověřování vnořené výjimky. Nicméně pokud volající vlákno nečeká na úlohu, tato specifická výjimka nebude šířena. Další informace najdete v tématu [zrušení úlohy](task-cancellation.md).

[!code-csharp[TPL_Exceptions#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#4)]
[!code-vb[TPL_Exceptions#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/tpl_exceptions.vb#4)]

## <a name="using-the-handle-method-to-filter-inner-exceptions"></a>Použití metody Handle k filtrování vnitřních výjimek

Metodu <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> můžete použít k filtrování výjimek, které lze považovat jako „zpracované“ bez použití jakékoli další logiky. V uživatelském delegátu, který je dodán <xref:System.AggregateException.Handle%28System.Func%7BSystem.Exception%2CSystem.Boolean%7D%29?displayProperty=nameWithType> metodě, můžete prověřit typ výjimky, jeho <xref:System.Exception.Message%2A> vlastnost nebo jakékoli jiné informace, které vám umožní určit, zda je neškodný. Jakékoli výjimky, pro které se delegát vrátí, `false` se znovu vyvolají v nové <xref:System.AggregateException> instanci hned po <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> návratu metody.

Následující příklad je funkčně ekvivalentní k prvnímu příkladu v tomto tématu, který prověřuje každou výjimku v <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> kolekci.  Místo toho tato obslužná rutina výjimky volá <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> objekt metody pro každou výjimku a znovu vyvolá výjimky, které nejsou `CustomException` instancemi.

[!code-csharp[TPL_Exceptions#26](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handlemethod21.cs#26)]
[!code-vb[TPL_Exceptions#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handlemethod21.vb#26)]

Následuje příklad kompletního příkladu, který používá <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> metodu k poskytnutí speciálního zpracování <xref:System.UnauthorizedAccessException> výjimky při vytváření výčtu souborů.

[!code-csharp[TPL_Exceptions#12](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions.cs#12)]
[!code-vb[TPL_Exceptions#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions.vb#12)]

## <a name="observing-exceptions-by-using-the-taskexception-property"></a>Pozorování výjimek pomocí vlastnosti Task. Exception

Pokud úkol skončí ve stavu <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType>, může být její vlastnost <xref:System.Threading.Tasks.Task.Exception%2A> přezkoumána a zjištěna výjimka, která chybu způsobila. Vhodným způsobem sledování vlastnosti <xref:System.Threading.Tasks.Task.Exception%2A> je použití pokračování, které se spouští pouze v případě selhání předchozího úkolu, jak je znázorněno v následujícím příkladu.

[!code-csharp[TPL_Exceptions#27](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptionprop21.cs#27)]
[!code-vb[TPL_Exceptions#27](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionprop21.vb#27)]

V smysluplné aplikaci může delegát pokračování Protokolovat podrobné informace o výjimce a případně vytvořit nové úlohy pro zotavení z výjimky. Pokud chyby úlohy, vyvolají následující výrazy výjimku:

- `await task`
- `task.Wait()`
- `task.Result`
- `task.GetAwaiter().GetResult()`

Použijte [`try-catch`](../../csharp/language-reference/keywords/try-catch.md) příkaz pro zpracování a sledování vyvolaných výjimek. Případně můžete pozorovat výjimku přístupem k <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> Vlastnosti.

## <a name="unobservedtaskexception-event"></a>Událost UnobservedTaskException

V některých situacích, jako je například hostování nedůvěryhodných zásuvných modulů, mohou být neškodné výjimky běžné a může být příliš obtížné je všechny sledovat ručně. V těchto případech je možné zpracovat událost <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=nameWithType>. Instance <xref:System.Threading.Tasks.UnobservedTaskExceptionEventArgs?displayProperty=nameWithType>, která je předána obslužné rutině, může být použita k zamezení šíření nesledovaných výjimek zpět do spojovacího vlákna.

## <a name="see-also"></a>Viz také

- [Task Parallel Library (TPL)](task-parallel-library-tpl.md)
