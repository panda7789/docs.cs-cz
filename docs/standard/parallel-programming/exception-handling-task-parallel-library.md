---
title: Zpracování výjimek (Task Parallel Library)
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, exceptions
ms.assetid: beb51e50-9061-4d3d-908c-56a4f7c2e8c1
ms.openlocfilehash: 12777a5f34b8aadcc80977b8796fc2cd53c626a8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134254"
---
# <a name="exception-handling-task-parallel-library"></a>Zpracování výjimek (Task Parallel Library)

Neošetřené výjimky, které jsou vyvolány uživatelským kódem, který je spuštěn v rámci úlohy, jsou šířeny zpět do volajícího vlákna, s výjimkou některých scénářů, které jsou popsány dále v tomto tématu. Výjimky jsou šířeny při použití jedné z metod <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> statického typu nebo instance a jejich zpracování uzavřením volání do `try`/`catch`m příkazu. Pokud je úkol nadřazený k připojeným podřízeným úkolům nebo pokud čekáte na více úloh, může být vyvoláno více výjimek.

Aby bylo možné šířit všechny výjimky zpět do hlavního vlákna, infrastruktura úkolů je zabaluje do instance <xref:System.AggregateException>. Výjimka <xref:System.AggregateException> má vlastnost <xref:System.AggregateException.InnerExceptions%2A>, která může být vytvořena výčtem, aby prozkoumala všechny původní výjimky, které byly vyvolány, a zpracovala (nebo nezpracovává) každou z nich jednotlivě. Původní výjimky lze také zpracovat pomocí metody <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType>.

I v případě, že je vyvolána pouze jedna výjimka, je stále zabalena v <xref:System.AggregateException> výjimka, jak ukazuje následující příklad.

[!code-csharp[TPL_Exceptions#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling21.cs#21)]
[!code-vb[TPL_Exceptions#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling21.vb#21)]

Nezpracované výjimce se můžete vyhnout zachycením instance <xref:System.AggregateException> a ignorováním jakýchkoli vnitřních výjimek. Nicméně doporučujeme, abyste to provedli, protože se podobá zachycení základního <xref:System.Exception>ho typu v neparalelních scénářích. Pokud zachytíte výjimku, a potom neprovedete žádnou konkrétní akci zotavení, bude program ponechán v neurčitém stavu.

Pokud nechcete volat metodu <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> pro čekání na dokončení úlohy, můžete také načíst výjimku <xref:System.AggregateException> z vlastnosti <xref:System.Threading.Tasks.Task.Exception%2A> úlohy, jak ukazuje následující příklad. Další informace naleznete v části [sledování výjimek pomocí vlastnosti Task. Exception](#observing-exceptions-by-using-the-taskexception-property) v tomto tématu.

[!code-csharp[TPL_Exceptions#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling22.cs#29)]
[!code-vb[TPL_Exceptions#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling22.vb#29)]

Pokud nečekáte na úlohu, která šíří výjimku, nebo ke své vlastnosti <xref:System.Threading.Tasks.Task.Exception%2A> přistupovat, je výjimka předávána v souladu se zásadami výjimky rozhraní .NET, pokud je úloha uvolněna z paměti.

Pokud jsou výjimky povoleny k bublinám zpět do spojovacího vlákna, je možné, že úloha může pokračovat ve zpracování některých položek poté, co je vyvolána výjimka.

> [!NOTE]
> Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“. Tato chyba je neškodná. Můžete pokračovat stisknutím klávesy F5 a zjistit, jakým způsobem jsou zpracovaný výjimky, což je znázorněno v těchto příkladech. Chcete-li aplikaci Visual Studio zabránit v přerušení první chyby, zrušte zaškrtnutí políčka **povolit pouze můj kód** v části **nástroje, možnosti, ladění, obecné**.

## <a name="attached-child-tasks-and-nested-aggregateexceptions"></a>Připojené podřízené úlohy a vnořené AggregateExceptions

Pokud úloha obsahuje připojené podřízené úlohy, které způsobí výjimku, je tato výjimka zabalená do instance <xref:System.AggregateException> předtím, než je postoupena do nadřazené úlohy, která zabalí tuto výjimku do vlastní instance <xref:System.AggregateException> dříve, než ji postoupí zpět do volajícího vlákna. V takových případech vlastnost <xref:System.AggregateException.InnerExceptions%2A> <xref:System.AggregateException> výjimka, která je zachycena v metodě <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAny%2A>nebo <xref:System.Threading.Tasks.Task.WaitAll%2A>, obsahuje jednu nebo více instancí <xref:System.AggregateException>, nikoli původní výjimky, které způsobily chybu. Chcete-li se vyhnout nutnosti iterovat vnořené výjimky <xref:System.AggregateException>, můžete použít metodu <xref:System.AggregateException.Flatten%2A> k odebrání všech vnořených <xref:System.AggregateException> výjimek, aby vlastnost <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> obsahovala původní výjimky. V následujícím příkladu jsou vnořené instance <xref:System.AggregateException> zploštěny a zpracovávány pouze v jednom průchodu.

[!code-csharp[TPL_Exceptions#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/flatten2.cs#22)]
[!code-vb[TPL_Exceptions#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/flatten2.vb#22)]

Můžete také použít metodu <xref:System.AggregateException.Flatten%2A?displayProperty=nameWithType> k opětovnému vyvolání vnitřních výjimek z více instancí <xref:System.AggregateException> vyvolaných více úlohami v rámci jedné instance <xref:System.AggregateException>, jak ukazuje následující příklad.

[!code-csharp[TPL_Exceptions#13](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions2.cs#13)]
[!code-vb[TPL_Exceptions#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions2.vb#13)]

## <a name="exceptions-from-detached-child-tasks"></a>Výjimky z odpojených podřízených úloh

Ve výchozím nastavení jsou podřízené úkoly vytvořeny jako odpojené. Výjimky vyvolané z odpojených úkolů musí být zpracovány nebo znovu vyvolány ihned v nadřazeném úkolu. Tyto výjimky nejsou šířeny zpět do volajícího vlákna stejným způsobem jako připojené úkoly. Nejvyšší nadřazený prvek může ručně znovu vyvolat výjimku z odpojeného podřízeného objektu, aby mohl být zabalen do <xref:System.AggregateException> a šířen zpět do volajícího vlákna.

[!code-csharp[TPL_Exceptions#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/detached21.cs#23)]
[!code-vb[TPL_Exceptions#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/detached21.vb#23)]

I pokud používáte pokračování pro sledování výjimky v podřízeném úkolu, musí být výjimka stále sledována nadřazeným úkolem.

## <a name="exceptions-that-indicate-cooperative-cancellation"></a>Výjimky indikující kooperativní zrušení

Pokud uživatelský kód v rámci úkolu odpoví na požadavek zrušení, mělo by správně dojít k vyvolání výjimky <xref:System.OperationCanceledException> a předání v tokenu zrušení, na kterém byl požadavek sdělen. Dříve než se pokusí o postoupení výjimky, porovná úkol token ve výjimce s tokenem, který byl předán při vytváření. Pokud se shodují, daný úkol postoupí výjimku <xref:System.Threading.Tasks.TaskCanceledException> zabalenou v instanci <xref:System.AggregateException> a lze ji zobrazit při ověřování vnořené výjimky. Nicméně pokud volající vlákno nečeká na úlohu, tato specifická výjimka nebude šířena. Další informace najdete v tématu [zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md).

[!code-csharp[TPL_Exceptions#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#4)]
[!code-vb[TPL_Exceptions#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/tpl_exceptions.vb#4)]

## <a name="using-the-handle-method-to-filter-inner-exceptions"></a>Použití metody Handle k filtrování vnitřních výjimek

Metodu <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> můžete použít k filtrování výjimek, které lze považovat jako „zpracované“ bez použití jakékoli další logiky. V uživatelském delegátu, který je dodán metodě <xref:System.AggregateException.Handle%28System.Func%7BSystem.Exception%2CSystem.Boolean%7D%29?displayProperty=nameWithType>, můžete prověřit typ výjimky, její vlastnost <xref:System.Exception.Message%2A> nebo jakékoli jiné informace, které vám umožní určit, zda je neškodný. Jakékoli výjimky, pro které delegát vrací `false` jsou znovu vyvolány v nové instanci <xref:System.AggregateException> ihned po návratu metody <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType>.

Následující příklad je funkčně ekvivalentní k prvnímu příkladu v tomto tématu, který prověřuje každou výjimku v kolekci <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType>.  Místo toho tato obslužná rutina výjimky volá objekt <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> metody pro každou výjimku a znovu vyvolá výjimky, které nejsou `CustomException` instancí.

[!code-csharp[TPL_Exceptions#26](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handlemethod21.cs#26)]
[!code-vb[TPL_Exceptions#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handlemethod21.vb#26)]

Následuje Úplnější příklad, který používá metodu <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> k poskytnutí speciálního zpracování výjimky <xref:System.UnauthorizedAccessException> při vytváření výčtu souborů.

[!code-csharp[TPL_Exceptions#12](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions.cs#12)]
[!code-vb[TPL_Exceptions#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions.vb#12)]

## <a name="observing-exceptions-by-using-the-taskexception-property"></a>Pozorování výjimek pomocí vlastnosti Task. Exception

Pokud úkol skončí ve stavu <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType>, může být její vlastnost <xref:System.Threading.Tasks.Task.Exception%2A> přezkoumána a zjištěna výjimka, která chybu způsobila. Vhodným způsobem sledování vlastnosti <xref:System.Threading.Tasks.Task.Exception%2A> je použití pokračování, které se spouští pouze v případě selhání předchozího úkolu, jak je znázorněno v následujícím příkladu.

[!code-csharp[TPL_Exceptions#27](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptionprop21.cs#27)]
[!code-vb[TPL_Exceptions#27](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionprop21.vb#27)]

V reálné aplikaci může delegát pokračování protokolovat podrobné informace o výjimce a případně spustit nový úkol zotavení z výjimky.

## <a name="unobservedtaskexception-event"></a>Událost UnobservedTaskException

V některých situacích, jako je například hostování nedůvěryhodných zásuvných modulů, mohou být neškodné výjimky běžné a může být příliš obtížné je všechny sledovat ručně. V těchto případech je možné zpracovat událost <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=nameWithType>. Instance <xref:System.Threading.Tasks.UnobservedTaskExceptionEventArgs?displayProperty=nameWithType>, která je předána obslužné rutině, může být použita k zamezení šíření nesledovaných výjimek zpět do spojovacího vlákna.

## <a name="see-also"></a>Viz také:

- [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
