---
title: Přehled primitiv synchronizace
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization, threads
- threading [.NET Framework],synchronizing threads
- managed threading
ms.assetid: b782bcb8-da6a-4c6a-805f-2eb46d504309
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e35c2337ff7e416cb5f2c869f8ede160e05d369f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592012"
---
# <a name="overview-of-synchronization-primitives"></a>Přehled primitiv synchronizace
<a name="top"></a> Rozhraní .NET Framework poskytuje celou řadu synchronizace primitiv pro řízení interakce vláken a vyloučení časování. To je možné zhruba rozdělit do tří kategorií: zamykání, signalizační a interlocked operace.  
  
 Kategorie nejsou přehledně ani jasně definované: Některé mechanismy synchronizace mají charakteristické vlastnosti třídy více kategorií; události, které verze jedním vláknem a současně jsou funkčně jako zámky; verze všech zámku lze považovat za signál; a propojené operace lze použít k vytvoření zámky. Kategorie jsou však stále užitečné.  
  
 Je důležité si pamatovat, že je synchronizace vláken spolupráci. Pokud ani jedno vlákno obchází synchronizační mechanismus a přistupuje k chráněnému prostředku přímo, nelze tento synchronizační mechanismus efektivní.  
  
 Tento přehled obsahuje následující části:  
  
-   [Zamykání](#locking)  
  
-   [Signalizace](#signaling)  
  
-   [Typy zjednodušené synchronizace](#lightweight_synchronization_types)  
  
-   [SpinWait](#spinwait)  
  
-   [Propojené operace](#interlocked_operations)  
  
<a name="locking"></a>   
## <a name="locking"></a>Zamykání  
 Zámky poskytnou kontrolu prostředku jedno vlákno najednou, nebo určený počet vláken. Vlákno, které žádá o výhradní zámek Pokud zámek je používán bloky dokud nebude k dispozici zámek.  
  
### <a name="exclusive-locks"></a>Výhradní zámky.  
 Je nejjednodušší forma uzamčení `lock` příkaz v jazyce C# a `SyncLock` v jazyce Visual Basic, který určuje přístup do bloku kódu. Takové blok se často označuje jako důležitý oddíl. `lock` Příkaz je implementována pomocí <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> a <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> metody a používá `try…catch…finally` blok k zajištění toho, že je vydán zámek.  
  
 Obecně platí, pomocí `lock` nebo `SyncLock` příkaz k ochraně malé bloky kódu, nikdy pokrývání uzlů více než jedné metody, je nejlepší způsob, jak používat <xref:System.Threading.Monitor> – třída. I když výkonné, <xref:System.Threading.Monitor> třídy jsou náchylné na bez synchronní kopie zámků a blokování.  
  
#### <a name="monitor-class"></a>Monitor – třída  
 <xref:System.Threading.Monitor> Třída poskytuje další funkce, který můžete použít ve spojení s `lock` příkaz:  
  
-   <xref:System.Threading.Monitor.TryEnter%2A> Metoda umožňuje vlákno, které se zablokuje čekáním na prostředek, který uvolňovat po určité době. Vrátí logickou hodnotu udávající úspěch nebo selhání, který můžete použít ke zjištění a vyhnout potenciální zablokování.  
  
-   <xref:System.Threading.Monitor.Wait%2A> Metoda je volána metodou vlákna v kritická sekce. Umožňuje až řízení prostředků a bloky, dokud daný prostředek k dispozici znovu.  
  
-   <xref:System.Threading.Monitor.Pulse%2A> a <xref:System.Threading.Monitor.PulseAll%2A> povolit vlákno, které chcete uvolnit zámek, nebo k volání metody <xref:System.Threading.Monitor.Wait%2A> uvést jednu nebo více podprocesů do připravené fronty, tak, aby se můžete získat zámek.  
  
 Časové limity na <xref:System.Threading.Monitor.Wait%2A> přetížení metody povolit čekání vláken, abyste se vyhnuli do připravené fronty.  
  
 <xref:System.Threading.Monitor> Třída může poskytnout zamykání ve více doménách aplikace, pokud je objekt použitý pro zámek odvozena z <xref:System.MarshalByRefObject>.  
  
 <xref:System.Threading.Monitor> má spřažení vláken. To znamená, musí ukončit vlákno, které zadali monitorování voláním <xref:System.Threading.Monitor.Exit%2A> nebo <xref:System.Threading.Monitor.Wait%2A>.  
  
 <xref:System.Threading.Monitor> Třída není instantiable. Její metody jsou statické (`Shared` v jazyce Visual Basic) a provádění akcí na instantiable zámek objektu.  
  
 Koncepční přehled, najdete v části [monitorování](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).  
  
#### <a name="mutex-class"></a>Mutex – třída  
 Žádost o vláken <xref:System.Threading.Mutex> voláním přetížení jeho <xref:System.Threading.WaitHandle.WaitOne%2A> metoda. Přetížení s časové limity jsou uvedeny umožňující vláken uvolňovat čekání. Na rozdíl od <xref:System.Threading.Monitor> třída, mutex může být buď místní nebo globální. Globální mutex – třídy, označované taky jako s názvem mutex – třídy, jsou viditelné v rámci operačního systému a slouží k synchronizaci vláken ve více domén aplikací nebo procesů. Místní mutex – třídy odvozovat od <xref:System.MarshalByRefObject>a lze použít v rámci hranice domény aplikace.  
  
 Kromě toho <xref:System.Threading.Mutex> je odvozena z <xref:System.Threading.WaitHandle>, což znamená, že lze použít s signalizační mechanismy poskytované <xref:System.Threading.WaitHandle>, jako <xref:System.Threading.WaitHandle.WaitAll%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, a <xref:System.Threading.WaitHandle.SignalAndWait%2A> metody.  
  
 Jako <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex> má spřažení vláken. Na rozdíl od <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex> je instantiable objektem.  
  
 Koncepční přehled, najdete v části [mutex – třídy](../../../docs/standard/threading/mutexes.md).  
  
#### <a name="spinlock-class"></a>SpinLock – třída  
 Od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], můžete použít <xref:System.Threading.SpinLock> třídy, pokud to vyžaduje nároky na <xref:System.Threading.Monitor> snižuje výkon. Když <xref:System.Threading.SpinLock> zaznamená uzamčeném kritická sekce ho jednoduše otáčí ve smyčce dokud nebude k dispozici zámek. Pokud pro velmi krátké době je blokován zámek, roztočený může poskytovat lepší výkon než blokování. Ale v případě, že je blokován zámek pro víc než několik desítkami cykly, <xref:System.Threading.SpinLock> provede stejně dobře jako <xref:System.Threading.Monitor>, ale budou používat další cyklů procesoru a proto může snížit výkon jiných vláken nebo procesy.  
  
### <a name="other-locks"></a>Další zámky.  
 Zámky nemusí být výhradní. Je často užitečné povolit omezený počet vláken souběžný přístup k prostředku. Semaforů a čtení a zápis zámky slouží k řízení tento druh přístupu k prostředkům ve fondu.  
  
#### <a name="readerwriterlock-class"></a>ReaderWriterLock – třída  
 <xref:System.Threading.ReaderWriterLockSlim> Třída řeší tento případ, kdy vlákno, které mění data, modul pro zápis, musí mít výhradní přístup k prostředku. Když v modulu pro zápis není aktivní, libovolný počet čtenářů má přístup k prostředku (například voláním <xref:System.Threading.ReaderWriterLockSlim.EnterReadLock%2A> metoda). Pokud vlákno vyžaduje výhradní přístup (například voláním <xref:System.Threading.ReaderWriterLockSlim.EnterWriteLock%2A> metoda), následné čtečky požadavky bloku, dokud všechny existující čtečky se odpojili zámek a zapisovač zadal a byl ukončen zámek.  
  
 <xref:System.Threading.ReaderWriterLockSlim> má spřažení vláken.  
  
 Koncepční přehled, najdete v části [zamkne čtení a zápis](../../../docs/standard/threading/reader-writer-locks.md).  
  
#### <a name="semaphore-class"></a>Semaphore – třída  
 <xref:System.Threading.Semaphore> Třída umožňuje zadaný počet vláken pro přístup k prostředkům. Požaduje bloku prostředků, dokud vlákno uvolní semaforu další vlákna.  
  
 Podobně jako <xref:System.Threading.Mutex> třídy, <xref:System.Threading.Semaphore> je odvozena z <xref:System.Threading.WaitHandle>. Také jako <xref:System.Threading.Mutex>, <xref:System.Threading.Semaphore> může být místní nebo globální. Lze přes hranice domény aplikace.  
  
 Na rozdíl od <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex>, a <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Semaphore> nemá spřažení vláken. To znamená, že je možné ve scénářích, kde jedno vlákno získá semafor a jiné uvolněním.  
  
 Koncepční přehled, najdete v části [semafor a SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md).  
  
 <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> je lightweight semafor pro synchronizaci v jednom procesu hranici.  
  
 [Zpět na začátek](#top)  
  
<a name="signaling"></a>   
## <a name="signaling"></a>Signálů  
 Nejjednodušší způsob, jak Počkejte, než je signál z jiné vlákno k volání <xref:System.Threading.Thread.Join%2A> metoda, která blokuje až do dokončení jiné vlákno. <xref:System.Threading.Thread.Join%2A> má dva přetížení, která umožňují blokované vlákno pro přerušení mimo dobu, po uplynutí zadaného intervalu.  
  
 Obslužné rutiny čekání poskytují mnohem širší čekání a možnosti signalizace.  
  
### <a name="wait-handles"></a>Obslužné rutiny čekání  
 Obslužné rutiny čekání odvozena od <xref:System.Threading.WaitHandle> třída, která naopak je odvozena z <xref:System.MarshalByRefObject>. Proto obslužné rutiny čekání slouží k synchronizaci aktivity vláken napříč hranicemi domény aplikace.  
  
 Blokování vlákna na čekání zpracovává voláním metody instance <xref:System.Threading.WaitHandle.WaitOne%2A> nebo jeden z statických metod <xref:System.Threading.WaitHandle.WaitAll%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, nebo <xref:System.Threading.WaitHandle.SignalAndWait%2A>. Jak jsou vydávány závisí na volala se metoda, která a na druhu obslužné rutiny čekání.  
  
 Koncepční přehled, najdete v části [počkejte zpracovává](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489).  
  
#### <a name="event-wait-handles"></a>Obslužné rutiny čekání na události  
 Obslužné rutiny čekání na událost zahrnují <xref:System.Threading.EventWaitHandle> třída a odvozené třídy, <xref:System.Threading.AutoResetEvent> a <xref:System.Threading.ManualResetEvent>. Vláken vydávají z popisovač čekání událost signalizace událostí popisovač čekání voláním jeho <xref:System.Threading.EventWaitHandle.Set%2A> metoda nebo pomocí <xref:System.Threading.WaitHandle.SignalAndWait%2A> metoda.  
  
 Obslužné rutiny buď sami automaticky resetovat, jako je Turniket, který umožňuje pouze jedno vlákno prostřednictvím pokaždé, když signalizace, nebo musí být ručně, obnovit jako bránu je uzavřen, dokud signál a pak otevřete, dokud ho někdo nezavře čekání událostí. Jak je určeno, jejich názvy, <xref:System.Threading.AutoResetEvent> a <xref:System.Threading.ManualResetEvent> představují bývalé a druhé, v uvedeném pořadí. <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> je lightweight událost pro synchronizaci v jednom procesu hranici.  
  
 <xref:System.Threading.EventWaitHandle> Může představovat buď typ události a může být místní nebo globální. Odvozené třídy <xref:System.Threading.AutoResetEvent> a <xref:System.Threading.ManualResetEvent> jsou vždy místní.  
  
 Obslužné rutiny čekání na událost nemají spřažení vláken. Jakékoli vlákno mohou signalizovat čekání popisovač události.  
  
 Koncepční přehled, najdete v části [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md).  
  
#### <a name="mutex-and-semaphore-classes"></a>Semafor třídy a mutex  
 Protože <xref:System.Threading.Mutex> a <xref:System.Threading.Semaphore> třídy jsou odvozeny od <xref:System.Threading.WaitHandle>, lze pomocí statických metod <xref:System.Threading.WaitHandle>. Například můžete použít vlákna <xref:System.Threading.WaitHandle.WaitAll%2A> metoda počkat, dokud jsou splněny všechny tři z následujících akcí: <xref:System.Threading.EventWaitHandle> signalizace, <xref:System.Threading.Mutex> vydání a <xref:System.Threading.Semaphore> vydání. Podobně můžete použít vlákna <xref:System.Threading.WaitHandle.WaitAny%2A> metoda počkat, dokud platí jedna z těchto podmínek.  
  
 Pro <xref:System.Threading.Mutex> nebo <xref:System.Threading.Semaphore>, probíhá signál znamená vydán. Pokud buď typ se používá jako první argument funkce <xref:System.Threading.WaitHandle.SignalAndWait%2A> metoda, jeho vydání. U <xref:System.Threading.Mutex>, který má spřažení vláken, je vyvolána výjimka, pokud objekt mutex není vlastníkem volající vlákno. Jak je uvedeno dříve, nemají semaforů spřažení vláken.  
  
#### <a name="barrier"></a>Bariéra  
 <xref:System.Threading.Barrier> Třída poskytuje způsob, jak cyklicky synchronizovat více vláken, tak, aby se všechny bloku zároveň bodu a počkat na všechna vlákna k dokončení. Bariéry je užitečné, pokud jeden nebo více podprocesů vyžadují výsledky jiné vlákno před pokračováním do další fáze algoritmu. Další informace najdete v tématu [Barrier](../../../docs/standard/threading/barrier.md).  
  
 [Zpět na začátek](#top)  
  
<a name="lightweight_synchronization_types"></a>   
## <a name="lightweight-synchronization-types"></a>Typy zjednodušené synchronizace  
 Od verze [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], můžete použít primitiv synchronizace, které poskytují vysoký výkon vyhnout nákladné spoléhat na Win32 jádra objekty, například obslužné rutiny, kdykoli je to možné čekání. Obecně platí měli byste použít tyto typy po krátkou dobu čekání a jenom v případě, že jste se pokusili a nevyhovující původní typy synchronizace. Prosté typů nelze použít ve scénářích, které vyžadují komunikaci mezi procesy.  
  
-   <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> je Odlehčená verze <xref:System.Threading.Semaphore?displayProperty=nameWithType>.  
  
-   <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> je Odlehčená verze <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>.  
  
-   <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> představuje událost, která se změní na signál, když jeho počtu nula.  
  
-   <xref:System.Threading.Barrier?displayProperty=nameWithType> Umožňuje synchronizovat sebou bez použití ovládacího prvku hlavní vlákno více vláken. Bariéry brání každé vlákno z budete pokračovat, dokud všechna vlákna dosáhli Zadaný bod.  
  
 [Zpět na začátek](#top)  
  
<a name="spinwait"></a>   
## <a name="spinwait"></a>SpinWait  
 Od verze [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], můžete použít <xref:System.Threading.SpinWait?displayProperty=nameWithType> struktury vlákno musí čekat signál události nebo podmínky, které musí být splněné, ale když skutečné čekací doba musí být menší než doba čekání požadované pomocí popisovač čekání nebo otherwi se blokování aktuální vlákno. Pomocí <xref:System.Threading.SpinWait>, můžete zadat krátké době číselníku při čekání, a pak yield (například podle čekání nebo režimu spánku) pouze v případě, že nebyla splněna podmínka v určeném čase.  
  
 [Zpět na začátek](#top)  
  
<a name="interlocked_operations"></a>   
## <a name="interlocked-operations"></a>Propojené operace  
 Propojené operace jsou jednoduché atomické operací provádí statických metod v umístění v paměti <xref:System.Threading.Interlocked> třídy. Tyto atomická operace zahrnují přidání, zvýšit a snížení, exchange, v závislosti na porovnání, podmíněného exchange a čtení operací pro 64bitové hodnoty na 32bitové platformy.  
  
> [!NOTE]
>  Zárukou toho nedělitelnost je omezený na jednotlivé operace; Při více operací se musí provádět jako jednotku, se musí použít více hrubý synchronizační mechanismus.  
  
 I když žádný z těchto operací jsou zámky nebo signály, jejich lze vytvořit zámků a signály. Protože jsou nativní pro operační systém Windows, jsou velmi rychlé propojené operace.  
  
 Propojené operace lze použít s záruky volatile paměti pro psaní aplikací, které vykazují výkonné neblokující souběžnosti. Ale vyžadují sofistikované, nízké úrovně programování, tak pro většinu účelů jsou jednoduché zámky lepší volbou.  
  
 Koncepční přehled, najdete v části [propojený Operations](../../../docs/standard/threading/interlocked-operations.md).  
  
## <a name="see-also"></a>Viz také  
 [Synchronizace dat pro vícevláknové zpracování](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 [Monitorování](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 [Mutex – třídy](../../../docs/standard/threading/mutexes.md)  
 [Semaphore a SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 [Obslužné rutiny čekání](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 [Propojené operace](../../../docs/standard/threading/interlocked-operations.md)  
 [Zámky modulů pro čtení a zápis](../../../docs/standard/threading/reader-writer-locks.md)  
 [Barrier](../../../docs/standard/threading/barrier.md)  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 [SpinLock](../../../docs/standard/threading/spinlock.md)
