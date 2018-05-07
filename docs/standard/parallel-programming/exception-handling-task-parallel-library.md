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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16ab0b8967ac394540f201fcc9098024faaccaa7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="exception-handling-task-parallel-library"></a>Zpracování výjimek (Task Parallel Library)
Nezpracované výjimky, které jsou vyvolány pomocí uživatelského kódu, které běží uvnitř úlohy rozšířeny zpět do volající vlákno, s výjimkou v některých scénářích, které jsou popsány dále v tomto tématu. Výjimky rozšířeny při použití statický nebo instance <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> nebo <!--zz <xref:System.Threading.Tasks.Task%601.Wait%2A?displayProperty=nameWithType>  --> `Wait` metody a zpracování je zachytávají v `try` / `catch` příkaz. Pokud úloha je nadřazená připojené podřízené úlohy, nebo pokud čekáte na více úloh, může být vyvolána více výjimek.  
  
 Aby bylo možné šířit všechny výjimky zpět do hlavního vlákna, infrastruktura úkolů je zabaluje do instance <xref:System.AggregateException>. <xref:System.AggregateException> Výjimka má <xref:System.AggregateException.InnerExceptions%2A> vlastnosti, které mohou být uvedené prozkoumat původní výjimky, které byly vyvolány zpracování (nebo není zpracování) každé z nich jednotlivě. Můžete také zpracovat původní výjimky pomocí <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> metoda.  
  
 I když je vyvolána výjimka pouze jeden, je stále uzavřen do <xref:System.AggregateException> výjimky, jak ukazuje následující příklad.  
  
 [!code-csharp[TPL_Exceptions#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling21.cs#21)]
 [!code-vb[TPL_Exceptions#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling21.vb#21)]  
  
 Nezpracované výjimce se můžete vyhnout zachycením instance <xref:System.AggregateException> a ignorováním jakýchkoli vnitřních výjimek. Doporučujeme však, že jste neprovádějte tuto akci, protože je to analogie zachytávání základní <xref:System.Exception> typu v jiné paralelní scénáře. Pokud zachytíte výjimku, a potom neprovedete žádnou konkrétní akci zotavení, bude program ponechán v neurčitém stavu.  
  
 Pokud nechcete volání <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> nebo <!--zz <xref:System.Threading.Tasks.Task%601.Wait%2A?displayProperty=nameWithType>  --> `Wait` metoda čekání na dokončení úkolu, můžete také načíst <xref:System.AggregateException> výjimky z úkolu <xref:System.Threading.Tasks.Task.Exception%2A> vlastnost, jak ukazuje následující příklad. Další informace najdete v tématu [sledování výjimek pomocí vlastnosti Task.Exception](#ExceptionProp) v tomto tématu.  
  
 [!code-csharp[TPL_Exceptions#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling22.cs#29)]
 [!code-vb[TPL_Exceptions#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling22.vb#29)]  
  
 Pokud není počkat na úlohu, který rozšíří výjimku, nebo přístup k jeho <xref:System.Threading.Tasks.Task.Exception%2A> vlastnost, výjimka je eskalovat podle zásad výjimky .NET, když je úlohu uvolňování paměti.  
  
 Když výjimky jsou povoleny pro třídění zpět do spojovacího vlákna, je možné, že úloha bude pokračovat ve zpracování některých položek po je vyvolána výjimka.  
  
> [!NOTE]
>  Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“. Tato chyba je neškodná. Můžete pokračovat stisknutím klávesy F5 a zjistit, jakým způsobem jsou zpracovaný výjimky, což je znázorněno v těchto příkladech. Chcete-li zabránit Visual Studio v zastavení na první chyba, zrušte **povolit volbu pouze vlastní kód** políčko pod **nástroje, možnosti, ladění, Obecné**.  
  
## <a name="attached-child-tasks-and-nested-aggregateexceptions"></a>Připojené podřízené úkoly a vnořené výjimky AggregateExceptions  
 Pokud úloha obsahuje připojené podřízené úlohy, které způsobí výjimku, je tato výjimka zabalená do instance <xref:System.AggregateException> předtím, než je postoupena do nadřazené úlohy, která zabalí tuto výjimku do vlastní instance <xref:System.AggregateException> dříve, než ji postoupí zpět do volajícího vlákna. V takových případech <xref:System.AggregateException.InnerExceptions%2A> vlastnost <xref:System.AggregateException> výjimka, která je zachycena v <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> nebo <!--zz <xref:System.Threading.Tasks.Task%601.Wait%2A?displayProperty=nameWithType>  --> `Wait` nebo <xref:System.Threading.Tasks.Task.WaitAny%2A> nebo <xref:System.Threading.Tasks.Task.WaitAll%2A> metoda obsahuje jeden nebo více <xref:System.AggregateException> instance není původní výjimky, které způsobily chybu. Abyste se vyhnuli nutnosti Iterujte přes vnořený <xref:System.AggregateException> výjimky, můžete použít <xref:System.AggregateException.Flatten%2A> a odebrat všechny vnořeného <xref:System.AggregateException> výjimky, tak, aby <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> vlastnost obsahuje původní výjimky. V následujícím příkladu jsou vnořené instance <xref:System.AggregateException> zploštěny a zpracovávány pouze v jednom průchodu.  
  
 [!code-csharp[TPL_Exceptions#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/flatten2.cs#22)]
 [!code-vb[TPL_Exceptions#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/flatten2.vb#22)]  
  
 Můžete také <xref:System.AggregateException.Flatten%2A?displayProperty=nameWithType> metoda pro opětovné vnitřní výjimky z více <xref:System.AggregateException> instance vyvolané více úloh v jediném <xref:System.AggregateException> instance, jak ukazuje následující příklad.  
  
 [!code-csharp[TPL_Exceptions#13](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions2.cs#13)]
 [!code-vb[TPL_Exceptions#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions2.vb#13)]  
  
## <a name="exceptions-from-detached-child-tasks"></a>Výjimky z odpojených podřízených úkolů  
 Ve výchozím nastavení jsou podřízené úkoly vytvořeny jako odpojené. Výjimky vyvolané z odpojených úkolů musí být zpracovány nebo znovu vyvolány ihned v nadřazeném úkolu. Tyto výjimky nejsou šířeny zpět do volajícího vlákna stejným způsobem jako připojené úkoly. Nejhornější nadřazená můžete ručně opětovné výjimku z odpojené podřízené způsobit mohla být uzavřen do <xref:System.AggregateException> a rozšíří volající vlákno.  
  
 [!code-csharp[TPL_Exceptions#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/detached21.cs#23)]
 [!code-vb[TPL_Exceptions#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/detached21.vb#23)]  
  
 I pokud používáte pokračování pro sledování výjimky v podřízeném úkolu, musí být výjimka stále sledována nadřazeným úkolem.  
  
## <a name="exceptions-that-indicate-cooperative-cancellation"></a>Výjimky, které určují kooperativní zrušení  
 Pokud uživatelský kód v rámci úkolu odpoví na požadavek zrušení, mělo by správně dojít k vyvolání výjimky <xref:System.OperationCanceledException> a předání v tokenu zrušení, na kterém byl požadavek sdělen. Dříve než se pokusí o postoupení výjimky, porovná úkol token ve výjimce s tokenem, který byl předán při vytváření. Pokud se shodují, daný úkol postoupí výjimku <xref:System.Threading.Tasks.TaskCanceledException> zabalenou v instanci <xref:System.AggregateException> a lze ji zobrazit při ověřování vnořené výjimky. Ale pokud volající vlákno nečeká na úlohy, nebude tato konkrétní výjimka rozšířeny. Další informace najdete v tématu [zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
 [!code-csharp[TPL_Exceptions#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#4)]
 [!code-vb[TPL_Exceptions#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/tpl_exceptions.vb#4)]  
  
## <a name="using-the-handle-method-to-filter-inner-exceptions"></a>Používání metody Handle k filtrování vnitřních výjimek  
 Metodu <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> můžete použít k filtrování výjimek, které lze považovat jako „zpracované“ bez použití jakékoli další logiky. V uživatele delegáta, který je součástí <xref:System.AggregateException.Handle%28System.Func%7BSystem.Exception%2CSystem.Boolean%7D%29?displayProperty=nameWithType> metoda, typ výjimky, můžete zkontrolovat jeho <xref:System.Exception.Message%2A> vlastnost nebo Další informace o tom, které vám umožní určit, zda je neškodné. Jakékoli výjimky, pro které se vrátí delegáta `false` jsou znovu vyvolány v nové <xref:System.AggregateException> instance okamžitě po <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> metoda vrátí.  
  
 V následujícím příkladu je funkčně srovnatelný v prvním příkladu v tomto tématu, který zkoumá jednotlivých výjimkách v <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> kolekce.  Místo toho tato obslužná rutina výjimky volá <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> objekt metoda pro každou výjimky a pouze znovu vyvolá výjimky, které nejsou `CustomException` instance.  
  
 [!code-csharp[TPL_Exceptions#26](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handlemethod21.cs#26)]
 [!code-vb[TPL_Exceptions#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handlemethod21.vb#26)]  
  
 Tady je více kompletní příklad, který používá <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> metody můžete zajistit zvláštní zpracování pro <xref:System.UnauthorizedAccessException> výjimka při vytváření výčtu souborů.  
  
 [!code-csharp[TPL_Exceptions#12](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions.cs#12)]
 [!code-vb[TPL_Exceptions#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions.vb#12)]  
  
<a name="ExceptionProp"></a>   
## <a name="observing-exceptions-by-using-the-taskexception-property"></a>Sledování výjimek pomocí Task.Exception vlastnosti.  
 Pokud úkol skončí ve stavu <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType>, může být její vlastnost <xref:System.Threading.Tasks.Task.Exception%2A> přezkoumána a zjištěna výjimka, která chybu způsobila. Vhodným způsobem sledování vlastnosti <xref:System.Threading.Tasks.Task.Exception%2A> je použití pokračování, které se spouští pouze v případě selhání předchozího úkolu, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[TPL_Exceptions#27](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptionprop21.cs#27)]
 [!code-vb[TPL_Exceptions#27](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionprop21.vb#27)]  
  
 V reálné aplikaci může delegát pokračování protokolovat podrobné informace o výjimce a případně spustit nový úkol zotavení z výjimky.  
  
## <a name="unobservedtaskexception-event"></a>Událost UnobservedTaskException  
 V některých situacích, jako je například hostování nedůvěryhodných zásuvných modulů, mohou být neškodné výjimky běžné a může být příliš obtížné je všechny sledovat ručně. V těchto případech je možné zpracovat událost <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=nameWithType>. Instance <xref:System.Threading.Tasks.UnobservedTaskExceptionEventArgs?displayProperty=nameWithType>, která je předána obslužné rutině, může být použita k zamezení šíření nesledovaných výjimek zpět do spojovacího vlákna.  
  
## <a name="see-also"></a>Viz také  
 [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
