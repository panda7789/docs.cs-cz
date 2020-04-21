---
title: Přehled primitiv synchronizace
description: Informace o primitivech synchronizace vláken .NET, které se používají k synchronizaci přístupu ke sdílenému prostředku nebo interakci podprocesu ovládacího prvku
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization, threads
- threading [.NET],synchronizing threads
- managed threading
ms.assetid: b782bcb8-da6a-4c6a-805f-2eb46d504309
ms.openlocfilehash: 7347c9b40f150febc6a163ae3aa3267123ea0e9d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739369"
---
# <a name="overview-of-synchronization-primitives"></a>Přehled primitiv synchronizace

Rozhraní .NET poskytuje řadu typů, které můžete použít k synchronizaci přístupu ke sdílenému prostředku nebo ke koordinaci interakce podprocesu.

> [!IMPORTANT]
> Použijte stejnou instanci primitivní synchronizace k ochraně přístupu ke sdílenému prostředku. Pokud používáte různé synchronizace primitivní instance k ochraně stejného prostředku, budete obejít ochranu poskytovanou synchronizace primitivní.

## <a name="waithandle-class-and-lightweight-synchronization-types"></a>Třída WaitHandle a zjednodušené typy synchronizace

Více .NET synchronizace primitiv odvozené z <xref:System.Threading.WaitHandle?displayProperty=nameWithType> třídy, která zapouzdřuje nativní operační systém synchronizační popisovač a používá mechanismus signalizace pro interakci podprocesu. Tyto třídy zahrnují:

- <xref:System.Threading.Mutex?displayProperty=nameWithType>, který uděluje výhradní přístup ke sdílenému prostředku. Stav mutex je signalizován, pokud žádné vlákno vlastní.
- <xref:System.Threading.Semaphore?displayProperty=nameWithType>, který omezuje počet podprocesů, které mají současně přístup ke sdílenému prostředku nebo fondu prostředků. Stav semaforu je nastaven na signalizováno, když je jeho počet větší než nula a nesignalizován, když je jeho počet nulový.
- <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>, který představuje událost synchronizace vláken a může být v signalizovaném nebo nesignalizovaném stavu.
- <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType>, který je <xref:System.Threading.EventWaitHandle> odvozen a při signalizaci automaticky resetuje do nesignalizovaného stavu po uvolnění jednoho čekajícího vlákna.
- <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>, který je <xref:System.Threading.EventWaitHandle> odvozen a při signalizaci zůstává v <xref:System.Threading.EventWaitHandle.Reset%2A> signalizovaném stavu, dokud není metoda volána.

V rozhraní .NET <xref:System.Threading.WaitHandle> Framework, <xref:System.MarshalByRefObject?displayProperty=nameWithType>protože je odvozen od , tyto typy lze použít k synchronizaci aktivit podprocesů přes hranice domény aplikace.

V rozhraní .NET Framework a .NET Core mohou některé z těchto typů představovat popisovače synchronizace pojmenovaného systému, které jsou viditelné v celém operačním systému a lze je použít pro meziprocesovou synchronizaci:

- <xref:System.Threading.Mutex>(.NET Framework a .NET Core),
- <xref:System.Threading.Semaphore>(Rozhraní .NET Framework a .NET Core v systému Windows),
- <xref:System.Threading.EventWaitHandle>(.NET Framework a .NET Core v systému Windows).

Další informace naleznete <xref:System.Threading.WaitHandle> v odkazu rozhraní API.

Zjednodušené typy synchronizace nespoléhají na základní popisovače operačního systému a obvykle poskytují lepší výkon. Nelze je však použít pro synchronizaci mezi procesy. Tyto typy použijte pro synchronizaci vláken v rámci jedné aplikace.

Některé z těchto typů jsou alternativy <xref:System.Threading.WaitHandle>k typům odvozeným od . Například <xref:System.Threading.SemaphoreSlim> je lehká <xref:System.Threading.Semaphore>alternativa k .

## <a name="synchronization-of-access-to-a-shared-resource"></a>Synchronizace přístupu ke sdílenému prostředku

Rozhraní .NET poskytuje řadu synchronizačních primitiv pro řízení přístupu ke sdílenému prostředku více vlákny.

### <a name="monitor-class"></a>Monitor – třída

Třída <xref:System.Threading.Monitor?displayProperty=nameWithType> uděluje vzájemně vylučující přístup ke sdílenému prostředku získáním nebo uvolněním zámku na objekt, který identifikuje prostředek. Zatímco zámek je držen, podproces, který drží zámek můžete znovu získat a uvolnit zámek. Jakékoli jiné vlákno je blokován o <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> získání zámku a metoda čeká, dokud zámek je uvolněna. Metoda <xref:System.Threading.Monitor.Enter%2A> získá uvolněný zámek. Metodu <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> můžete také použít k určení doby, po kterou se vlákno pokusí získat zámek. Vzhledem <xref:System.Threading.Monitor> k tomu, že třída má spřažení podprocesů, <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> podproces, který získal zámek musí uvolnit zámek voláním metody.

Můžete koordinovat interakci podprocesů, které získávají zámek na <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType>stejný <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType>objekt <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> pomocí , a metody.

Další informace naleznete <xref:System.Threading.Monitor> v odkazu rozhraní API.

> [!NOTE]
> Použijte příkaz [lock](../../csharp/language-reference/keywords/lock-statement.md) v jazyce C# a příkaz [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) v jazyce <xref:System.Threading.Monitor> Visual Basic k synchronizaci přístupu ke sdílenému prostředku namísto přímého použití třídy. Tyto příkazy jsou <xref:System.Threading.Monitor.Enter%2A> implementovány pomocí metody a <xref:System.Threading.Monitor.Exit%2A> `try…finally` blok, aby bylo zajištěno, že získané zámek je vždy uvolněna.

### <a name="mutex-class"></a>Mutex – třída

Třída, <xref:System.Threading.Mutex?displayProperty=nameWithType> jako <xref:System.Threading.Monitor>je , uděluje výhradní přístup ke sdílenému prostředku. Použijte jeden z přetížení metody [Mutex.WaitOne](<xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>) požádat o vlastnictví mutex. Stejně jako <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex> má spřažení podprocesů a vlákno, <xref:System.Threading.Mutex.ReleaseMutex%2A?displayProperty=nameWithType> které získalo mutex musí uvolnit voláním metody.

Na <xref:System.Threading.Monitor>rozdíl <xref:System.Threading.Mutex> od , třídy lze použít pro synchronizaci mezi procesy. Chcete-li to provést, použijte pojmenovaný objekt mutex, který je viditelný v celém operačním systému. Chcete-li vytvořit pojmenovanou instanci mutex, použijte [konstruktor Mutex,](<xref:System.Threading.Mutex.%23ctor%2A>) který určuje název. Můžete také volat <xref:System.Threading.Mutex.OpenExisting%2A?displayProperty=nameWithType> metodu otevřít existující pojmenovaný systém mutex.
  
Další informace naleznete v článku [Mutexes](mutexes.md) a odkaz na <xref:System.Threading.Mutex> rozhraní API.

### <a name="spinlock-structure"></a>Struktura SpinLock

Struktura, <xref:System.Threading.SpinLock?displayProperty=nameWithType> jako <xref:System.Threading.Monitor>je , uděluje výhradní přístup ke sdílenému prostředku na základě dostupnosti zámku. Při <xref:System.Threading.SpinLock> pokusech o získání zámku, který není k dispozici, čeká ve smyčce, opakovaně kontroluje, dokud zámek k dispozici.

Další informace o výhodách a nevýhodách použití spin lock, naleznete <xref:System.Threading.SpinLock> v článku [SpinLock](spinlock.md) a odkaz na rozhraní API.

### <a name="readerwriterlockslim-class"></a>Třída ReaderWriterLockSlim

Třída <xref:System.Threading.ReaderWriterLockSlim?displayProperty=nameWithType> uděluje výhradní přístup ke sdílenému prostředku pro zápis a umožňuje více vláken pro přístup k prostředku současně pro čtení. Můžete chtít použít <xref:System.Threading.ReaderWriterLockSlim> k synchronizaci přístupu ke sdílené datové struktuře, která podporuje operace čtení bezpečné pro přístup z více vláken, ale vyžaduje výhradní přístup k provedení operace zápisu. Když vlákno požaduje výhradní přístup (například <xref:System.Threading.ReaderWriterLockSlim.EnterWriteLock%2A?displayProperty=nameWithType> voláním metody), následné požadavky pro čtenáře a zapisovatele blokují, dokud všechny existující čtenáři neukončí zámek a zapisovatel nezadal a neukončil zámek.
  
Další informace naleznete <xref:System.Threading.ReaderWriterLockSlim> v odkazu rozhraní API.

### <a name="semaphore-and-semaphoreslim-classes"></a>Třídy Semafor a SemaforSlim

<xref:System.Threading.Semaphore?displayProperty=nameWithType> Třídy <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> a omezit počet podprocesů, které mohou přistupovat ke sdílenému prostředku nebo fondu prostředků současně. Další vlákna, která požadují prostředek, počkejte, dokud žádné vlákno neuvolní semafor. Vzhledem k tomu, že semafor nemá spřažení vláken, vlákno může získat semafor a jiný ho může uvolnit.

<xref:System.Threading.SemaphoreSlim>je zjednodušenou <xref:System.Threading.Semaphore> alternativou k a lze ji použít pouze pro synchronizaci v rámci jedné hranice procesu.

V systému Windows <xref:System.Threading.Semaphore> můžete použít pro synchronizaci mezi procesy. Chcete-li to <xref:System.Threading.Semaphore> provést, vytvořte instanci, která představuje pojmenovaný systémový semafor pomocí jednoho <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType> z [konstruktorů Semafor,](<xref:System.Threading.Semaphore.%23ctor%2A>) který určuje název nebo metodu. <xref:System.Threading.SemaphoreSlim>nepodporuje pojmenované systémové semafory.

Další informace naleznete v článku [Semafor a SemaphoreSlim](semaphore-and-semaphoreslim.md) a <xref:System.Threading.Semaphore> odkaz na rozhraní API nebo. <xref:System.Threading.SemaphoreSlim>

## <a name="thread-interaction-or-signaling"></a>Interakce závitu nebo signalizace

Interakce vlákna (nebo signalizace vlákna) znamená, že vlákno musí čekat na oznámení nebo signál z jednoho nebo více vláken, aby bylo možné pokračovat. Například pokud vlákno A <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> volá metodu vlákna B, vlákno A je blokován, dokud vlákno B nedokončí. Synchronizační primitiva popsaná v předchozí části poskytují jiný mechanismus pro signalizaci: uvolněním zámku vlákno upozorní jiné vlákno, které může pokračovat získáním zámku.

Tato část popisuje další signalizační konstrukce poskytované rozhraním .NET.

### <a name="eventwaithandle-autoresetevent-manualresetevent-and-manualreseteventslim-classes"></a>Třída EventWaitHandle, AutoResetEvent, ManualResetEvent a ManualResetEventSlim

Třída <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> představuje událost synchronizace vláken.

Událost synchronizace může být v nesignalizovaném nebo signalizovaném stavu. Pokud je stav události nesignalizován, vlákno, které volá <xref:System.Threading.WaitHandle.WaitOne%2A?> přetížení události, je blokováno, dokud není signalizována událost. Metoda <xref:System.Threading.EventWaitHandle.Set%2A?displayProperty=nameWithType> nastaví stav události signalizované.

Chování signalizovaného objektu <xref:System.Threading.EventWaitHandle> závisí na jeho režimu resetování:

- Vytvořené <xref:System.Threading.EventWaitHandle> s <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> příznakem resetuje automaticky po uvolnění jednoho čekajícího vlákna. Je to jako turniket, který umožňuje pouze jedno vlákno, když je signalizováno. Třída, <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType> která je <xref:System.Threading.EventWaitHandle>odvozena od , představuje toto chování.
- Vytvořené <xref:System.Threading.EventWaitHandle> s <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> příznakem zůstane signalizováno, dokud není volána jeho <xref:System.Threading.EventWaitHandle.Reset%2A> metoda. Je to jako brána, která je zavřená, dokud není signalizována, a pak zůstane otevřená, dokud ji někdo nezavře. Třída, <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> která je <xref:System.Threading.EventWaitHandle>odvozena od , představuje toto chování. Třída <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> je lehká <xref:System.Threading.ManualResetEvent>alternativa k .

V systému Windows <xref:System.Threading.EventWaitHandle> můžete použít pro synchronizaci mezi procesy. Chcete-li to <xref:System.Threading.EventWaitHandle> provést, vytvořte instanci, která představuje událost synchronizace pojmenovaného systému pomocí <xref:System.Threading.EventWaitHandle.OpenExisting%2A?displayProperty=nameWithType> jednoho z [konstruktorů EventWaitHandle,](<xref:System.Threading.EventWaitHandle.%23ctor%2A>) který určuje název nebo metodu.

Další informace naleznete v článku [EventWaitHandle.](eventwaithandle.md) Odkaz na rozhraní <xref:System.Threading.EventWaitHandle>API <xref:System.Threading.AutoResetEvent> <xref:System.Threading.ManualResetEvent>naleznete <xref:System.Threading.ManualResetEventSlim>v tématu , , a .

### <a name="countdownevent-class"></a>Třída CountdownEvent

Třída <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> představuje událost, která se stane nastavena, když je její počet nula. Zatímco <xref:System.Threading.CountdownEvent.CurrentCount?displayProperty=nameWithType> je větší než nula, vlákno, které volá <xref:System.Threading.CountdownEvent.Wait%2A?displayProperty=nameWithType> je blokován. Volání <xref:System.Threading.CountdownEvent.Signal%2A?displayProperty=nameWithType> snížení počtu událostí.

Na rozdíl <xref:System.Threading.ManualResetEvent> <xref:System.Threading.ManualResetEventSlim>od nebo , které můžete použít k odblokování více vláken <xref:System.Threading.CountdownEvent> se signálem z jednoho vlákna, můžete použít k odblokování jednoho nebo více vláken se signály z více vláken.

Další informace naleznete v článku [CountdownEvent](countdownevent.md) a odkaz na <xref:System.Threading.CountdownEvent> rozhraní API.

### <a name="barrier-class"></a>Bariérová třída

Třída <xref:System.Threading.Barrier?displayProperty=nameWithType> představuje bariéru spuštění podprocesu. Podproces, který <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> volá volání metody signály, že dosáhl bariéry a čeká, dokud ostatní účastník podprocesy dosáhnout bariéry. Když všechny účastníky závity dosáhnou bariéry, pokračují a bariéra se resetuje a může být znovu použita.

Můžete použít, <xref:System.Threading.Barrier> když jeden nebo více vláken vyžadují výsledky jiných vláken před pokračováním do další fáze výpočtu.

Další informace naleznete v článku <xref:System.Threading.Barrier> [bariéra](barrier.md) a odkaz na rozhraní API.

## <a name="interlocked-class"></a>Interlocked – třída

Třída <xref:System.Threading.Interlocked?displayProperty=nameWithType> poskytuje statické metody, které provádějí jednoduché atomické operace s proměnnou. Tyto atomické operace zahrnují sčítání, přírůstek a snížení, výměnu a podmíněnou výměnu, která závisí na porovnání, a operace čtení 64bitové celočíselné hodnoty.

Další informace naleznete <xref:System.Threading.Interlocked> v odkazu rozhraní API.

## <a name="spinwait-structure"></a>Struktura SpinWait

<xref:System.Threading.SpinWait?displayProperty=nameWithType> Struktura poskytuje podporu pro spin-based čekání. Můžete chtít použít, když podproces musí čekat na událost, která má být signalizována nebo podmínka, která má být splněna, ale při skutečné čekací doby se očekává, že bude menší než čekací doba požadovaná pomocí popisovač čekání nebo jinak blokování podprocesu. Pomocí <xref:System.Threading.SpinWait>aplikace můžete zadat krátkou dobu, po kterou se má během čekání otáčet, a potom výtěžnost (například čekáním nebo spánkem) pouze v případě, že podmínka nebyla splněna v zadaném čase.

Další informace naleznete v článku [SpinWait](spinwait.md) a odkaz na <xref:System.Threading.SpinWait> rozhraní API.

## <a name="see-also"></a>Viz také

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Kolekce bezpečné pro přístup z více vláken](../collections/thread-safe/index.md)
- [Dělení objektů a funkcí na vlákna](threading-objects-and-features.md)
