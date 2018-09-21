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
ms.openlocfilehash: 37abcb6b3a8fdf4ef91d5e946a97db7ca1428ce8
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46532737"
---
# <a name="overview-of-synchronization-primitives"></a>Přehled primitiv synchronizace
<a name="top"></a> Rozhraní .NET Framework poskytuje celou řadu primitiv synchronizace pro řízení interakce vláken a jak se vyhnout konfliktům časování. Ty je možné zhruba rozdělit do tří kategorií: zamykání, signalizační a propojené operace.  
  
 Kategorie nejsou uklizený ani jasně definované: Některé mechanismy synchronizace mají charakteristiky v několika kategoriích; události, které verze jedním vláknem a současně jsou funkčně jako zámky; verze žádný zámek si lze představit jako signál; a propojené operace lze použít k sestavení kompletních zámky. Kategorie jsou však stále užitečná.  
  
 Je dobré si uvědomit, že je kooperativní synchronizaci vláken. Pokud ani jedno vlákno obchází synchronizační mechanismus a přistupuje k chráněnému prostředku přímo, tento synchronizační mechanismus nemůže být účinné.  
  
 Tento přehled obsahuje následující části:  
  
-   [Uzamčení](#locking)  
  
-   [Signalizace](#signaling)  
  
-   [Typy zjednodušené synchronizace](#lightweight_synchronization_types)  
  
-   [SpinWait](#spinwait)  
  
-   [Propojené operace](#interlocked_operations)  
  
<a name="locking"></a>   
## <a name="locking"></a>Uzamčení  
 Zámky poskytují kontrolu prostředku na jedno vlákno najednou, nebo zadaný počet vláken. Vlákna, která vyžaduje výhradní zámek při zámek je používán bloky dokud nebude k dispozici zámek.  
  
### <a name="exclusive-locks"></a>Výhradní zámků  
 Nejjednodušší forma uzamčení se `lock` příkaz v jazyce C# a `SyncLock` v sadě Visual Studio, které řídí přístup k bloku kódu. Takové bloku se často označuje jako kritickou sekci. `lock` Příkazu je implementovaný s využitím <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> a <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> metody a používá `try…finally` blok k Ujistěte se, že zámek je uvolněn.  
  
 Obecně platí, pomocí `lock` nebo `SyncLock` příkaz k ochraně malé bloky kódu, nikdy pokrývající více než jedné metody, je nejlepší způsob, jak používat <xref:System.Threading.Monitor> třídy. I když výkonné, <xref:System.Threading.Monitor> třídy je náchylný na zámků osamocené a zablokování.  
  
#### <a name="monitor-class"></a>Monitor – třída  
 <xref:System.Threading.Monitor> Třída poskytuje další funkce, které lze použít ve spojení s `lock` – příkaz:  
  
-   <xref:System.Threading.Monitor.TryEnter%2A> Metoda umožňuje podproces, který je blokovaný čekání na prostředek, který chcete vzdát po uplynutí zadaného intervalu. Vrátí logickou hodnotu udávající úspěch nebo selhání, který slouží ke zjišťování a zabránilo potenciální zablokování.  
  
-   <xref:System.Threading.Monitor.Wait%2A> Metoda je volána vláknem v kritický oddíl. Nabízí řízení prostředků a bloky, dokud prostředek je opět k dispozici.  
  
-   <xref:System.Threading.Monitor.Pulse%2A> a <xref:System.Threading.Monitor.PulseAll%2A> povolit vlákno, které chcete uvolnit zámek nebo volání metody <xref:System.Threading.Monitor.Wait%2A> umístit jeden nebo více vláken do fronty, připravené tak, aby jejich získání zámku.  
  
 Časové limity u <xref:System.Threading.Monitor.Wait%2A> přetížení metody umožňují čekajících vláken k návratu do fronty připravené.  
  
 <xref:System.Threading.Monitor> Třída může poskytnout uzamčení v víc aplikačních doménách, pokud objekt použitý pro zámek je odvozena z <xref:System.MarshalByRefObject>.  
  
 <xref:System.Threading.Monitor> má spřažení vláken. To znamená, vlákna, které zadaný monitor ukončíte zavoláním <xref:System.Threading.Monitor.Exit%2A> nebo <xref:System.Threading.Monitor.Wait%2A>.  
  
 <xref:System.Threading.Monitor> Třída není instantiable. Její metody jsou statické (`Shared` v jazyce Visual Basic), dokážete na základě instantiable zámek objektu.  
  
 Koncepční přehled najdete v tématu [monitorování](https://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).  
  
#### <a name="mutex-class"></a>Mutex – třída  
 Požadavek vlákna <xref:System.Threading.Mutex> voláním přetížení jeho <xref:System.Threading.WaitHandle.WaitOne%2A> metoda. Přetížení s vypršení časového limitu jsou k dispozici, aby vlákna uvolňovat čekání. Na rozdíl od <xref:System.Threading.Monitor> třídě mutex může být místní nebo globální. Globální objekty mutex, také nazývané objekty pojmenované mutex, jsou viditelné v celém operačním systému a slouží k synchronizaci vláken ve více doménách aplikace nebo procesy. Místní mutexů odvozovat <xref:System.MarshalByRefObject>a můžete použít přes hranice aplikačních domén.  
  
 Kromě toho <xref:System.Threading.Mutex> je odvozena z <xref:System.Threading.WaitHandle>, což znamená, že lze použít s signalizační mechanismy poskytované <xref:System.Threading.WaitHandle>, například <xref:System.Threading.WaitHandle.WaitAll%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, a <xref:System.Threading.WaitHandle.SignalAndWait%2A> metody.  
  
 Stejně jako <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex> má spřažení vláken. Na rozdíl od <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex> je instantiable objekt.  
  
 Koncepční přehled najdete v tématu [mutexů](../../../docs/standard/threading/mutexes.md).  
  
#### <a name="spinlock-class"></a>Třída struktuře SpinLock  
 Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], můžete použít <xref:System.Threading.SpinLock> třídy, pokud to vyžaduje režii <xref:System.Threading.Monitor> snižuje výkon. Když <xref:System.Threading.SpinLock> zaznamená uzamčené kritický oddíl, ho jednoduše přede ve smyčce dokud nebude k dispozici zámek. Pokud je pro velmi krátké době zámek, pokryjte může poskytovat lepší výkon než blokování. Nicméně, pokud je zámek je uložena pro více než několik desítek cykly, <xref:System.Threading.SpinLock> provádí stejně, jako <xref:System.Threading.Monitor>, ale bude používat další Procesorové cykly a proto může snížit výkon jiných vláknech či procesy.  
  
### <a name="other-locks"></a>Další zámky  
 Zámky nemusí být exkluzivní. Často je užitečné umožnit omezenému počtu vláken souběžný přístup k prostředku. Semaforů a zámky pro čtení a zápis jsou určeny k řízení tento druh přístupu k prostředkům ve fondu.  
  
#### <a name="readerwriterlock-class"></a>ReaderWriterLock – třída  
 <xref:System.Threading.ReaderWriterLockSlim> Třídy řeší případ, kdy vlákno, které mění data, modul pro zápis musí exkluzivní přístup k prostředku. Pokud modul pro zápis není aktivní, můžete libovolný počet čtenářů přístup k prostředku (například voláním <xref:System.Threading.ReaderWriterLockSlim.EnterReadLock%2A> metoda). Pokud vlákno vyžaduje výhradní přístup (například voláním <xref:System.Threading.ReaderWriterLockSlim.EnterWriteLock%2A> metoda), následné čtečky požadavky bloku, dokud všechny existující čtenáři odpojili zámek a zapisovač, který má zadaný a byla ukončena, zámek.  
  
 <xref:System.Threading.ReaderWriterLockSlim> má spřažení vláken.  
  
 Koncepční přehled najdete v tématu [čtení a zápis uzamkne](../../../docs/standard/threading/reader-writer-locks.md).  
  
#### <a name="semaphore-class"></a>Semaphore – třída  
 <xref:System.Threading.Semaphore> Třída umožňuje zadaný počet vláken pro přístup k prostředku. Žádosti o prostředku bloku, dokud vlákno uvolní semafor další vlákna.  
  
 Podobně jako <xref:System.Threading.Mutex> třídy <xref:System.Threading.Semaphore> je odvozena z <xref:System.Threading.WaitHandle>. Také jako <xref:System.Threading.Mutex>, <xref:System.Threading.Semaphore> může být místní nebo globální. Je možné přes hranice aplikačních domén.  
  
 Na rozdíl od <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex>, a <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Semaphore> nemá spřažení vláken. To znamená, že je možné použít v situacích, kdy jedno vlákno získává semafor a jiné verze.  
  
 Koncepční přehled najdete v tématu [Semaphore a SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md).  
  
 <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> je zjednodušené semafor pro synchronizaci v rámci jednoho procesu hranice.  
  
 [Zpět na začátek](#top)  
  
<a name="signaling"></a>   
## <a name="signaling"></a>Signálů  
 Nejjednodušší způsob, jak čekání na signál z jiného vlákna je zavolat <xref:System.Threading.Thread.Join%2A> metodu, která blokuje, dokud se nedokončí jiného podprocesu. <xref:System.Threading.Thread.Join%2A> má dvě přetížení, které umožňují zablokování vlákna, aby čekání po uplynutí zadaného intervalu.  
  
 Obslužné rutiny čekání poskytují mnohem širší nabídku sad signalizace možnosti a čekání.  
  
### <a name="wait-handles"></a>Obslužné rutiny čekání  
 Obslužné rutiny čekání odvozovat <xref:System.Threading.WaitHandle> třídu, která je dále odvozeno z <xref:System.MarshalByRefObject>. Díky tomu se obslužné rutiny čekání slouží k synchronizaci činností vlákna přes hranice aplikačních domén.  
  
 Blokování vlákna na čekací zpracovává zavoláním metody instance <xref:System.Threading.WaitHandle.WaitOne%2A> nebo statických metod <xref:System.Threading.WaitHandle.WaitAll%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, nebo <xref:System.Threading.WaitHandle.SignalAndWait%2A>. Jak se vydávají závisí na byla volána metoda a na druhu obslužné rutiny čekání.  
  
 Koncepční přehled najdete v tématu [počkejte zpracovává](https://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489).  
  
#### <a name="event-wait-handles"></a>Událost obslužné rutiny čekání  
 Zahrnout události obslužné rutiny čekání <xref:System.Threading.EventWaitHandle> třída a odvozené třídy, <xref:System.Threading.AutoResetEvent> a <xref:System.Threading.ManualResetEvent>. Vlákna se vydávají z popisovače čekání události při popisovač čekání události signalizován voláním jeho <xref:System.Threading.EventWaitHandle.Set%2A> metody nebo pomocí <xref:System.Threading.WaitHandle.SignalAndWait%2A> metoda.  
  
 Událost obslužné rutiny, buď resetovat sami automaticky, jako je Turniket, který umožňuje pouze jedno vlákno prostřednictvím pokaždé, když je signalizována, nebo musí být v továrním ručně, jako je brána je zavřít, dokud není signalizována a pak otevřete, dokud uživatel nezavře čekání. Jak naznačují jejich názvy <xref:System.Threading.AutoResetEvent> a <xref:System.Threading.ManualResetEvent> představují bývalého a druhá možnost, v uvedeném pořadí. <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> je zjednodušené událost synchronizace v rámci jednoho procesu hranice.  
  
 <xref:System.Threading.EventWaitHandle> Může představovat buď typ události a může být místní nebo globální. Odvozené třídy <xref:System.Threading.AutoResetEvent> a <xref:System.Threading.ManualResetEvent> jsou vždy místní.  
  
 Obslužné rutiny události čekání nemají spřažení vláken. Jakékoli vlákno může signalizuje, že popisovač čekání událost.  
  
 Koncepční přehled najdete v tématu [eventwaithandle –, autoresetevent –, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md).  
  
#### <a name="mutex-and-semaphore-classes"></a>Vzájemně vyloučený přístup a třídy Semaphore  
 Vzhledem k tomu, <xref:System.Threading.Mutex> a <xref:System.Threading.Semaphore> třídy odvozovat z <xref:System.Threading.WaitHandle>, je možné pomocí statické metody z <xref:System.Threading.WaitHandle>. Například můžete použít vlákno <xref:System.Threading.WaitHandle.WaitAll%2A> metoda počkat, dokud jsou splněny všechny tři z následujících akcí: <xref:System.Threading.EventWaitHandle> signalizován, <xref:System.Threading.Mutex> vydání a <xref:System.Threading.Semaphore> vydání. Podobně můžete použít vlákno <xref:System.Threading.WaitHandle.WaitAny%2A> metoda počkat, až některou z těchto podmínek má hodnotu true.  
  
 Pro <xref:System.Threading.Mutex> nebo <xref:System.Threading.Semaphore>, probíhá signalizován znamená, že se vydávají. Pokud se buď typ používá jako první argument <xref:System.Threading.WaitHandle.SignalAndWait%2A> metoda, se uvolní. V případě třídy <xref:System.Threading.Mutex>, který obsahuje spřažení vláken, je vyvolána výjimka, pokud volající vlákno nevlastní mutex. Jak bylo uvedeno dříve, nemají semafory spřažení vláken.  
  
#### <a name="barrier"></a>Bariéra  
 <xref:System.Threading.Barrier> Třída poskytuje způsob, jak cyklicky synchronizovat více vláken, aby se všechny blok na stejný bod a počkat na všechna vlákna, k dokončení. Bariéra je užitečné, když jeden nebo více vláken vyžadují výsledky z jiného vlákna než budete pokračovat v další fázi algoritmus. Další informace najdete v tématu [bariéry](../../../docs/standard/threading/barrier.md).  
  
 [Zpět na začátek](#top)  
  
<a name="lightweight_synchronization_types"></a>   
## <a name="lightweight-synchronization-types"></a>Typy zjednodušené synchronizace  
 Počínaje [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], můžete použít primitiv synchronizace, které poskytují rychlý výkon zabráněním nákladné závislost na Win32 jádra objekty, jako je obslužné rutiny, kdykoli je to možné čekání. Obecně platí abyste používali tyto typy po krátkou dobu čekání a pouze v případě, že původní typy synchronizace jste se pokusili a vyhodnocený jako nevyhovující. Jednoduché typy nelze používat ve scénářích, které vyžadují komunikace mezi procesy.  
  
-   <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> je Odlehčená verze <xref:System.Threading.Semaphore?displayProperty=nameWithType>.  
  
-   <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> je Odlehčená verze <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>.  
  
-   <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> představuje událost, která se stane signalizováno při její vlastnosti count je nula.  
  
-   <xref:System.Threading.Barrier?displayProperty=nameWithType> umožňuje více vláken, k synchronizaci mezi sebou bez použití ovládacího prvku hlavní vlákno. Bariéry brání každé vlákno pokračovat, dokud všechna vlákna dosáhli Zadaný bod.  
  
 [Zpět na začátek](#top)  
  
<a name="spinwait"></a>   
## <a name="spinwait"></a>SpinWait  
 Počínaje [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], můžete použít <xref:System.Threading.SpinWait?displayProperty=nameWithType> struktury, pokud vlákno obsahuje čekání na událost má být signalizován nebo podmínku splnit, ale v případě, že skutečné čekací doba má být menší než doba čekání pomocí popisovač čekání nebo otherwi se blokuje aktuální vlákno. S použitím <xref:System.Threading.SpinWait>, můžete zadat krátké doby k aktivaci při čekání a potom yield (třeba podle čekání nebo v režimu spánku) pouze v případě, že nebyla splněna podmínka v určený čas.  
  
 [Zpět na začátek](#top)  
  
<a name="interlocked_operations"></a>   
## <a name="interlocked-operations"></a>Propojené operace  
 Propojené operace jsou jednoduché atomické operace provedené na umístění v paměti pomocí statických metod <xref:System.Threading.Interlocked> třídy. Atomických operací zahrnují přidání, zvýšení a snížení, exchange, podmíněné exchange v závislosti na tom, porovnání a operace čtení pro hodnoty 64-bit na 32bitových platformách.  
  
> [!NOTE]
>  Zárukou atomicitu je omezená na jednotlivé operace; Když jako jednotka se musí provádět více operací, musí být použita více hrubých synchronizační mechanismus.  
  
 I když žádné z těchto operací se zámky nebo signály, můžete použít k sestavení kompletních zámky a signálů. Protože jde o nativního pro operační systém Windows, propojené operace jsou velmi rychlé.  
  
 Propojené operace lze s volatile paměti záruky pro psaní aplikací, které vykazují výkonné neblokující souběžnosti. Ale vyžadují sofistikované, nízké úrovně programování, tak pro většinu účelů jsou jednoduché zámky lepší volbou.  
  
 Koncepční přehled najdete v tématu [propojené operace](../../../docs/standard/threading/interlocked-operations.md).  
  
## <a name="see-also"></a>Viz také:

- [Synchronizace dat pro vícevláknové zpracování](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
- [Monitorování](https://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
- [Mutex – třídy](../../../docs/standard/threading/mutexes.md)  
- [Semaphore a SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
- [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
- [Obslužné rutiny čekání](https://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
- [Propojené operace](../../../docs/standard/threading/interlocked-operations.md)  
- [Zámky modulů pro čtení a zápis](../../../docs/standard/threading/reader-writer-locks.md)  
- [Barrier](../../../docs/standard/threading/barrier.md)  
- [SpinWait](../../../docs/standard/threading/spinwait.md)  
- [SpinLock](../../../docs/standard/threading/spinlock.md)
