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
ms.openlocfilehash: f3deaba0c8589eaa0ba24bc66669f5a76e60467f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877804"
---
# <a name="exception-handling-task-parallel-library"></a>Zpracování výjimek (Task Parallel Library)
Neošetřené výjimky, které jsou vyvolány uživatelským kódem spuštěným uvnitř úkolu jsou šířeny zpět do volajícího vlákna, s výjimkou zvláštních situací, které jsou popsány dále v tomto tématu. Výjimky jsou šířeny, pokud použijete jednu ze statických nebo instance <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> nebo <!--zz <xref:System.Threading.Tasks.Task%601.Wait%2A?displayProperty=nameWithType>  --> `Wait` metody a zpracujete je uzavřením volání `try` / `catch` příkazu. Pokud je úloha nadřazené připojených podřízených úloh, nebo pokud čekáte na více úkolů, může být vyvoláno více výjimek.  
  
 Aby bylo možné šířit všechny výjimky zpět do hlavního vlákna, infrastruktura úkolů je zabaluje do instance <xref:System.AggregateException>. <xref:System.AggregateException> Výjimek má <xref:System.AggregateException.InnerExceptions%2A> vlastnost, která může být přezkoumána za účelem zjištění původních výjimek, které byly vyvolány a zpracovat (nebo Nezpracovat) každé z nich samostatně. Původní výjimky může také zpracovávat pomocí <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> metody.  
  
 I v případě, že je vyvolána pouze jednou výjimkou, je stále zabalena do <xref:System.AggregateException> výjimky, jak ukazuje následující příklad.  
  
 [!code-csharp[TPL_Exceptions#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling21.cs#21)]
 [!code-vb[TPL_Exceptions#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling21.vb#21)]  
  
 Nezpracované výjimce se můžete vyhnout zachycením instance <xref:System.AggregateException> a ignorováním jakýchkoli vnitřních výjimek. Doporučujeme však, že jste neprovádějte tuto akci, protože je analogické k zachytávaní základní <xref:System.Exception> typ v neparalelních situacích. Pokud zachytíte výjimku, a potom neprovedete žádnou konkrétní akci zotavení, bude program ponechán v neurčitém stavu.  
  
 Pokud nechcete k volání <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> nebo <!--zz <xref:System.Threading.Tasks.Task%601.Wait%2A?displayProperty=nameWithType>  --> `Wait` metoda počkat na dokončení úkolu, můžete také načíst <xref:System.AggregateException> výjimku z úkolu <xref:System.Threading.Tasks.Task.Exception%2A> vlastnost, jak ukazuje následující příklad. Další informace najdete v tématu [pozorování výjimek pomocí vlastnosti Task.Exception](#ExceptionProp) v tomto tématu.  
  
 [!code-csharp[TPL_Exceptions#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling22.cs#29)]
 [!code-vb[TPL_Exceptions#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling22.vb#29)]  
  
 Pokud není čekání na úkol, který šíří výjimku, nebo přístup k jeho <xref:System.Threading.Tasks.Task.Exception%2A> vlastnost, výjimka je eskalován podle zásad výjimky .NET, když je úkol uklizena modulem.  
  
 Pokud je výjimkám umožněn návrat zpět do spojovacího vlákna pokračovala, je možné, že úloha bude pokračovat ve zpracování některých položek poté, co je vyvolána výjimka.  
  
> [!NOTE]
>  Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“. Tato chyba je neškodná. Můžete pokračovat stisknutím klávesy F5 a zjistit, jakým způsobem jsou zpracovaný výjimky, což je znázorněno v těchto příkladech. Abyste zabránili přerušení nebo první chybě sady Visual Studio, zrušte zaškrtnutí **povolit volbu pouze vlastní kód** zaškrtávací políčko **nástroje, možnosti, ladění, Obecné**.  
  
## <a name="attached-child-tasks-and-nested-aggregateexceptions"></a>Připojené podřízené úkoly a vnořené výjimky AggregateExceptions  
 Pokud úloha obsahuje připojené podřízené úlohy, které způsobí výjimku, je tato výjimka zabalená do instance <xref:System.AggregateException> předtím, než je postoupena do nadřazené úlohy, která zabalí tuto výjimku do vlastní instance <xref:System.AggregateException> dříve, než ji postoupí zpět do volajícího vlákna. V takových případech <xref:System.AggregateException.InnerExceptions%2A> vlastnost <xref:System.AggregateException> výjimku, která je zachycena v <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> nebo <!--zz <xref:System.Threading.Tasks.Task%601.Wait%2A?displayProperty=nameWithType>  --> `Wait` nebo <xref:System.Threading.Tasks.Task.WaitAny%2A> nebo <xref:System.Threading.Tasks.Task.WaitAll%2A> metoda obsahuje jeden nebo více <xref:System.AggregateException> instance není původní výjimky, které chybu způsobily. Abyste se vyhnuli nutnosti k iteraci přes vnořené <xref:System.AggregateException> výjimky, můžete použít <xref:System.AggregateException.Flatten%2A> metoda odebrat všechny vnořeného <xref:System.AggregateException> výjimky, tak, aby <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> vlastnost obsahovala původní výjimky. V následujícím příkladu jsou vnořené instance <xref:System.AggregateException> zploštěny a zpracovávány pouze v jednom průchodu.  
  
 [!code-csharp[TPL_Exceptions#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/flatten2.cs#22)]
 [!code-vb[TPL_Exceptions#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/flatten2.vb#22)]  
  
 Můžete také použít <xref:System.AggregateException.Flatten%2A?displayProperty=nameWithType> metody pro funkci opětovného vyvolání vnitřních výjimek z několika <xref:System.AggregateException> instance vyvolané více úloh v jediném <xref:System.AggregateException> instance, jak ukazuje následující příklad.  
  
 [!code-csharp[TPL_Exceptions#13](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions2.cs#13)]
 [!code-vb[TPL_Exceptions#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions2.vb#13)]  
  
## <a name="exceptions-from-detached-child-tasks"></a>Výjimky z odpojených podřízených úkolů  
 Ve výchozím nastavení jsou podřízené úkoly vytvořeny jako odpojené. Výjimky vyvolané z odpojených úkolů musí být zpracovány nebo znovu vyvolány ihned v nadřazeném úkolu. Tyto výjimky nejsou šířeny zpět do volajícího vlákna stejným způsobem jako připojené úkoly. Nejvyšší nadřazený úkol může ručně znovu vyvolat výjimku z odpojeného podřízeného způsobit, že bude zabalena do <xref:System.AggregateException> a postoupena zpět do volajícího vlákna.  
  
 [!code-csharp[TPL_Exceptions#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/detached21.cs#23)]
 [!code-vb[TPL_Exceptions#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/detached21.vb#23)]  
  
 I pokud používáte pokračování pro sledování výjimky v podřízeném úkolu, musí být výjimka stále sledována nadřazeným úkolem.  
  
## <a name="exceptions-that-indicate-cooperative-cancellation"></a>Výjimky, které určují kooperativní zrušení  
 Pokud uživatelský kód v rámci úkolu odpoví na požadavek zrušení, mělo by správně dojít k vyvolání výjimky <xref:System.OperationCanceledException> a předání v tokenu zrušení, na kterém byl požadavek sdělen. Dříve než se pokusí o postoupení výjimky, porovná úkol token ve výjimce s tokenem, který byl předán při vytváření. Pokud se shodují, daný úkol postoupí výjimku <xref:System.Threading.Tasks.TaskCanceledException> zabalenou v instanci <xref:System.AggregateException> a lze ji zobrazit při ověřování vnořené výjimky. Ale pokud volající vlákno není čekání na úlohu, nebude tato konkrétní výjimka postoupena. Další informace najdete v tématu [zrušení úlohy](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
 [!code-csharp[TPL_Exceptions#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#4)]
 [!code-vb[TPL_Exceptions#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/tpl_exceptions.vb#4)]  
  
## <a name="using-the-handle-method-to-filter-inner-exceptions"></a>Používání metody Handle k filtrování vnitřních výjimek  
 Metodu <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> můžete použít k filtrování výjimek, které lze považovat jako „zpracované“ bez použití jakékoli další logiky. V uživatelském delegátu poskytnutém metodě <xref:System.AggregateException.Handle%28System.Func%7BSystem.Exception%2CSystem.Boolean%7D%29?displayProperty=nameWithType> metodu, můžete prověřit typ výjimky, jeho <xref:System.Exception.Message%2A> vlastnost nebo nějakých jiných informací o tom, která umožní zjistit, zda je výjimka neškodná. Všechny výjimky, pro které delegát vrátí `false` jsou znovu vyvolány v nové <xref:System.AggregateException> instance okamžitě po <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> metoda vrátí hodnotu.  
  
 Následující příklad je funkčně srovnatelný s první příklad v tomto tématu, který zkoumá vlastnost jednotlivých výjimkách v <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> kolekce.  Místo toho tato obslužná rutina výjimky zavolá <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> objekt metody pro každou výjimku a pouze znovu vyvolá výjimky, které nejsou `CustomException` instancí.  
  
 [!code-csharp[TPL_Exceptions#26](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handlemethod21.cs#26)]
 [!code-vb[TPL_Exceptions#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handlemethod21.vb#26)]  
  
 Následuje Úplnější příklad, který používá <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> metodu k dispozici zvláštní zacházení <xref:System.UnauthorizedAccessException> při vytváření výčtu souborů došlo k výjimce.  
  
 [!code-csharp[TPL_Exceptions#12](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions.cs#12)]
 [!code-vb[TPL_Exceptions#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions.vb#12)]  
  
<a name="ExceptionProp"></a>   
## <a name="observing-exceptions-by-using-the-taskexception-property"></a>Pozorování výjimek pomocí vlastnosti Task.Exception  
 Pokud úkol skončí ve stavu <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType>, může být její vlastnost <xref:System.Threading.Tasks.Task.Exception%2A> přezkoumána a zjištěna výjimka, která chybu způsobila. Vhodným způsobem sledování vlastnosti <xref:System.Threading.Tasks.Task.Exception%2A> je použití pokračování, které se spouští pouze v případě selhání předchozího úkolu, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[TPL_Exceptions#27](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptionprop21.cs#27)]
 [!code-vb[TPL_Exceptions#27](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionprop21.vb#27)]  
  
 V reálné aplikaci může delegát pokračování protokolovat podrobné informace o výjimce a případně spustit nový úkol zotavení z výjimky.  
  
## <a name="unobservedtaskexception-event"></a>Událost UnobservedTaskException  
 V některých situacích, jako je například hostování nedůvěryhodných zásuvných modulů, mohou být neškodné výjimky běžné a může být příliš obtížné je všechny sledovat ručně. V těchto případech je možné zpracovat událost <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=nameWithType>. Instance <xref:System.Threading.Tasks.UnobservedTaskExceptionEventArgs?displayProperty=nameWithType>, která je předána obslužné rutině, může být použita k zamezení šíření nesledovaných výjimek zpět do spojovacího vlákna.  
  
## <a name="see-also"></a>Viz také:

- [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
