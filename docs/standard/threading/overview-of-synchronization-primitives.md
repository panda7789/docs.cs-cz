---
title: Přehled primitiv synchronizace
description: Přečtěte si o primitivech synchronizace vláken .NET používaných k synchronizaci přístupu ke sdílenému vláknu nebo k interakci řídicího vlákna.
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization, threads
- threading [.NET],synchronizing threads
- managed threading
ms.assetid: b782bcb8-da6a-4c6a-805f-2eb46d504309
ms.openlocfilehash: 43f78c914b7cb01f9b0de4c258d5882548e52790
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73106595"
---
# <a name="overview-of-synchronization-primitives"></a>Přehled primitiv synchronizace

Rozhraní .NET poskytuje rozsah typů, které můžete použít k synchronizaci přístupu ke sdílenému prostředku nebo k interakci s vlákny pro koordinaci.

> [!IMPORTANT]
> Pro ochranu přístupu ke sdílenému prostředku použijte stejnou instanci primitiva synchronizace. Pokud k ochraně stejného prostředku používáte různé primitivní instance synchronizace, obejít ochranu poskytovanou primitivním primitivem.

## <a name="waithandle-class-and-lightweight-synchronization-types"></a>Třídy WaitHandle a zjednodušené typy synchronizace

Několik primitiv synchronizace rozhraní .NET je odvozeno od třídy <xref:System.Threading.WaitHandle?displayProperty=nameWithType>, která zapouzdřuje nativní popisovač synchronizace operačního systému a používá mechanismus signalizace pro interakci s vlákny. Tyto třídy zahrnují:

- <xref:System.Threading.Mutex?displayProperty=nameWithType>, která uděluje exkluzivní přístup ke sdílenému prostředku. Stav mutex je signalizována, pokud není vlastníkem vlákna.
- <xref:System.Threading.Semaphore?displayProperty=nameWithType>, která omezuje počet vláken, která mají souběžný přístup ke sdílenému prostředku nebo fondu prostředků. Stav semaforu je nastaven na signalizaci, pokud je jeho počet větší než nula a nesignálný, pokud je jeho počet nula.
- <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>, který představuje událost synchronizace vlákna a může být buď v signalizačním, nebo nesignalizacém stavu.
- <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType>, která je odvozena z <xref:System.Threading.EventWaitHandle> a, při signalizaci, je automaticky nastavena na nesignálný stav po uvolnění jediného čekajícího vlákna.
- <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>, která je odvozena z <xref:System.Threading.EventWaitHandle> a v případě signalizace zůstane v signalizačním stavu, dokud nebude volána metoda <xref:System.Threading.EventWaitHandle.Reset%2A>.

V .NET Framework, protože <xref:System.Threading.WaitHandle> jsou odvozeny z <xref:System.MarshalByRefObject?displayProperty=nameWithType>, lze tyto typy použít k synchronizaci aktivit vláken napříč hranicemi aplikační domény.

V .NET Framework a .NET Core mohou některé z těchto typů představovat pojmenované popisovače synchronizace systému, které jsou viditelné v celém operačním systému a lze je použít pro synchronizaci mezi procesy:

- <xref:System.Threading.Mutex> (.NET Framework a .NET Core),
- <xref:System.Threading.Semaphore> (.NET Framework a .NET Core ve Windows),
- <xref:System.Threading.EventWaitHandle> (.NET Framework a .NET Core ve Windows).

Další informace najdete v referenčních informacích k rozhraní <xref:System.Threading.WaitHandle> API.

Odlehčené typy synchronizace nespoléhají na základní obslužné rutiny operačního systému a obvykle poskytují lepší výkon. Nelze je však použít pro synchronizaci mezi procesy. Tyto typy použijte pro synchronizaci vláken v rámci jedné aplikace.

Některé z těchto typů jsou alternativy k typům odvozeným od <xref:System.Threading.WaitHandle>. Například <xref:System.Threading.SemaphoreSlim> je zjednodušenou alternativou pro <xref:System.Threading.Semaphore>.

## <a name="synchronization-of-access-to-a-shared-resource"></a>Synchronizace přístupu ke sdílenému prostředku

.NET poskytuje řadu synchronizačních primitiv pro řízení přístupu ke sdílenému prostředku více vlákny.

### <a name="monitor-class"></a>Monitor – třída

Třída <xref:System.Threading.Monitor?displayProperty=nameWithType> uděluje vzájemně exkluzivní přístup ke sdílenému prostředku získáním nebo uvolněním zámku objektu, který identifikuje prostředek. I když je držen zámek, vlákno, které obsahuje zámek, může znovu načíst a uvolnit zámek. Jakékoli jiné vlákno zablokovalo získání zámku a <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> metoda počká, dokud se zámek neuvolní. Metoda <xref:System.Threading.Monitor.Enter%2A> získá uvolněný zámek. Pomocí metody <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> lze také určit dobu, během které se vlákno pokusí získat zámek. Vzhledem k tomu, že třída <xref:System.Threading.Monitor> má spřažení vlákna, vlákno, které získalo zámek, musí uvolnit zámek voláním metody <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType>.

Můžete koordinovat interakci vláken, která získávají zámek na stejný objekt pomocí metod <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType>a <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType>.

Další informace najdete v referenčních informacích k rozhraní <xref:System.Threading.Monitor> API.

> [!NOTE]
> Použijte příkaz [Lock](../../csharp/language-reference/keywords/lock-statement.md) v C# a příkaz [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) v Visual Basic pro synchronizaci přístupu ke sdílenému prostředku místo přímého použití třídy <xref:System.Threading.Monitor>. Tyto příkazy jsou implementovány pomocí metod <xref:System.Threading.Monitor.Enter%2A> a <xref:System.Threading.Monitor.Exit%2A> a `try…finally` bloku, aby bylo zajištěno, že se získaný zámek vždy uvolňuje.

### <a name="mutex-class"></a>Mutex – třída

Třída <xref:System.Threading.Mutex?displayProperty=nameWithType>, jako je <xref:System.Threading.Monitor>, uděluje exkluzivní přístup ke sdílenému prostředku. Použijte jedno z přetížení metod [mutex. WaitOne](<xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>) pro vyžádání vlastnictví mutexu. Stejně jako <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex> má spřažení vlákna a vlákno, které získalo mutex, je musí uvolnit voláním metody <xref:System.Threading.Mutex.ReleaseMutex%2A?displayProperty=nameWithType>.

Na rozdíl od <xref:System.Threading.Monitor>lze třídu <xref:System.Threading.Mutex> použít pro synchronizaci mezi procesy. K tomu použijte pojmenovaný mutex, který je viditelný v celém operačním systému. Chcete-li vytvořit pojmenovanou instanci mutex, použijte [konstruktor Mutex](<xref:System.Threading.Mutex.%23ctor%2A>) , který určuje název. Můžete také volat metodu <xref:System.Threading.Mutex.OpenExisting%2A?displayProperty=nameWithType> pro otevření existujícího objektu mutex s názvem systému.
  
Další informace najdete v článku věnovaném [mutexům](mutexes.md) a v referenčních informacích k rozhraní <xref:System.Threading.Mutex> API.

### <a name="spinlock-structure"></a>Struktura struktuře SpinLock

Struktura <xref:System.Threading.SpinLock?displayProperty=nameWithType>, jako je <xref:System.Threading.Monitor>, uděluje exkluzivní přístup ke sdílenému prostředku na základě dostupnosti zámku. Když se <xref:System.Threading.SpinLock> pokusí získat zámek, který není k dispozici, čeká ve smyčce a opakovaně kontroluje, dokud zámek nebude k dispozici.

Další informace o výhodách a nevýhodách použití zámku získáte v článku o [struktuře SpinLock](spinlock.md) a v referenčních informacích k rozhraní API <xref:System.Threading.SpinLock>.

### <a name="readerwriterlockslim-class"></a>ReaderWriterLockSlim – třída

Třída <xref:System.Threading.ReaderWriterLockSlim?displayProperty=nameWithType> uděluje exkluzivní přístup ke sdílenému prostředku pro zápis a umožňuje více vláknům přistupovat k prostředku současně pro čtení. Můžete chtít použít <xref:System.Threading.ReaderWriterLockSlim> k synchronizaci přístupu ke sdílené datové struktuře, která podporuje operace čtení bezpečné pro přístup z více vláken, ale vyžaduje výhradní přístup k provedení operace zápisu. Když vlákno požaduje výhradní přístup (například voláním metody <xref:System.Threading.ReaderWriterLockSlim.EnterWriteLock%2A?displayProperty=nameWithType>), pak další požadavky na čtečku a zapisovač, dokud všichni stávající čtenáři neukončí zámek, a zapisovač zadal a ukončil zámek.
  
Další informace najdete v referenčních informacích k rozhraní <xref:System.Threading.ReaderWriterLockSlim> API.

### <a name="semaphore-and-semaphoreslim-classes"></a>Semafor a třídy SemaphoreSlim

Třídy <xref:System.Threading.Semaphore?displayProperty=nameWithType> a <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> omezují počet vláken, která mají souběžný přístup ke sdílenému prostředku nebo fondu prostředků. Další vlákna, která vyžádají prostředek, počkejte, dokud jakékoli vlákno neuvolní semafor. Vzhledem k tomu, že semafor nemá spřažení vláken, vlákno může získat semafor a další ho může uvolnit.

<xref:System.Threading.SemaphoreSlim> je odlehčená alternativa k <xref:System.Threading.Semaphore> a lze ji použít pouze pro synchronizaci v rámci jedné hranice procesu.

Ve Windows můžete použít <xref:System.Threading.Semaphore> pro synchronizaci mezi procesy. K tomu je třeba vytvořit instanci <xref:System.Threading.Semaphore>, která představuje pojmenovaný systémový semafor pomocí jednoho z [konstruktorů semaforu](<xref:System.Threading.Semaphore.%23ctor%2A>) , který určuje název nebo metodu <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType>. <xref:System.Threading.SemaphoreSlim> nepodporuje pojmenované systémové semafory.

Další informace najdete v článku [semafor a SemaphoreSlim](semaphore-and-semaphoreslim.md) a referenční informace k rozhraní API pro <xref:System.Threading.Semaphore> nebo <xref:System.Threading.SemaphoreSlim>.

## <a name="thread-interaction-or-signaling"></a>Interakce vlákna nebo signalizace

Interakce vlákna (nebo signalizace vlákna) znamená, že vlákno musí čekat na oznámení nebo signál, z jednoho nebo více vláken, aby bylo možné pokračovat. Například pokud vlákno A zavolá metodu <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> vlákna B, vlákno A je blokováno, dokud není vlákno B dokončeno. Prvky synchronizace popsané v předchozí části poskytují jiný mechanismus pro signalizaci: uvolněním zámku vlákno upozorní jiné vlákno, že může pokračovat získáním zámku.

Tato část popisuje další konstrukce signalizace poskytované rozhraním .NET.

### <a name="eventwaithandle-autoresetevent-manualresetevent-and-manualreseteventslim-classes"></a>Třídy EventWaitHandle, AutoResetEvent, ManualResetEvent a ManualResetEventSlim

Třída <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> představuje událost synchronizace vlákna.

Událost synchronizace může být buď v nesignalizacém, nebo ve stavu signalizace. Při nesignalizaci stavu události je vlákno, které volá přetížení události <xref:System.Threading.WaitHandle.WaitOne%2A?>, blokováno, dokud událost není signalizována. Metoda <xref:System.Threading.EventWaitHandle.Set%2A?displayProperty=nameWithType> nastaví stav události, která má být signalizována.

Chování <xref:System.Threading.EventWaitHandle>, které bylo signalizaci, závisí na režimu obnovení:

- <xref:System.Threading.EventWaitHandle> vytvořené pomocí příznaku <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> se automaticky obnoví po uvolnění jediného čekajícího vlákna. Vypadá to jako Turnstile, který umožňuje pouze jedno vlákno přes pokaždé, když je signál. Třída <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType>, která je odvozena z <xref:System.Threading.EventWaitHandle>, představuje toto chování.
- <xref:System.Threading.EventWaitHandle> vytvořené pomocí příznaku <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> zůstává signalizována, dokud není volána jeho metoda <xref:System.Threading.EventWaitHandle.Reset%2A>. Je to jako brána, která je zavřená, dokud není signalizována, a pak zůstane otevřená, dokud ji někdo neuzavře. Třída <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>, která je odvozena z <xref:System.Threading.EventWaitHandle>, představuje toto chování. Třída <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> je zjednodušenou alternativou pro <xref:System.Threading.ManualResetEvent>.

Ve Windows můžete použít <xref:System.Threading.EventWaitHandle> pro synchronizaci mezi procesy. Chcete-li to provést, vytvořte instanci <xref:System.Threading.EventWaitHandle>, která představuje pojmenovanou událost synchronizace systému pomocí jednoho z [konstruktorů EventWaitHandle](<xref:System.Threading.EventWaitHandle.%23ctor%2A>) , které určují název nebo metodu <xref:System.Threading.EventWaitHandle.OpenExisting%2A?displayProperty=nameWithType>.

Další informace najdete v článku [EventWaitHandle](eventwaithandle.md) . Referenční informace k rozhraní API naleznete v tématu <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.AutoResetEvent>, <xref:System.Threading.ManualResetEvent>a <xref:System.Threading.ManualResetEventSlim>.

### <a name="countdownevent-class"></a>CountdownEvent – třída

Třída <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> představuje událost, která se nastaví, když je její počet nula. I když je <xref:System.Threading.CountdownEvent.CurrentCount?displayProperty=nameWithType> větší než nula, vlákno, které volá <xref:System.Threading.CountdownEvent.Wait%2A?displayProperty=nameWithType>, je blokované. Zavolejte <xref:System.Threading.CountdownEvent.Signal%2A?displayProperty=nameWithType> pro snížení počtu událostí.

Na rozdíl od <xref:System.Threading.ManualResetEvent> nebo <xref:System.Threading.ManualResetEventSlim>, které lze použít k odblokování více vláken pomocí signálu z jednoho vlákna, můžete použít <xref:System.Threading.CountdownEvent> k odblokování jednoho nebo více podprocesů s signály z více vláken.

Další informace najdete v článku [CountdownEvent](countdownevent.md) a v referenčních informacích k rozhraní API <xref:System.Threading.CountdownEvent>.

### <a name="barrier-class"></a>Bariéra – třída

Třída <xref:System.Threading.Barrier?displayProperty=nameWithType> představuje bariéru spuštění vlákna. Vlákno, které volá metodu <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType>, signalizuje, že dosáhla bariéry a čeká, dokud ostatní vlákna účastníka dosáhnou bariéry. Když všechna vlákna účastníka dosáhnou bariéry, budou pokračovat a bariéra se resetuje a dá se použít znovu.

Můžete použít <xref:System.Threading.Barrier> v případě, že jeden nebo více vláken vyžaduje výsledky jiných vláken před pokračováním do další fáze výpočtu.

Další informace najdete v článku o [bariérě](barrier.md) a v referenčních informacích k rozhraní <xref:System.Threading.Barrier> API.

## <a name="interlocked-class"></a>Interlocked – třída

Třída <xref:System.Threading.Interlocked?displayProperty=nameWithType> poskytuje statické metody, které provádějí jednoduché atomické operace na proměnné. Tyto atomické operace zahrnují sčítání, zvýšení a snížení, Exchange a podmíněný Exchange, které závisí na porovnání a operace čtení z 64 celočíselné hodnoty.

Další informace najdete v referenčních informacích k rozhraní <xref:System.Threading.Interlocked> API.

## <a name="spinwait-structure"></a>Struktura objektu SpinWait

Struktura <xref:System.Threading.SpinWait?displayProperty=nameWithType> poskytuje podporu pro čekání na číselník. Můžete ji chtít použít, když vlákno musí počkat na signalizaci události nebo podmínku, která má být splněna, ale pokud se očekává, že doba čekání bude menší než čekací doba potřebná při použití popisovače čekání nebo jiným způsobem blokování vlákna. Pomocí <xref:System.Threading.SpinWait>můžete zadat krátkou dobu, kdy se má při čekání čekat, a pak (například čekáním nebo v režimu spánku), a to pouze v případě, že podmínka nebyla v zadaném čase splněna.

Další informace najdete v článku [objektu SpinWait](spinwait.md) a v referenčních informacích k rozhraní API <xref:System.Threading.SpinWait>.

## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Kolekce bezpečné pro přístup z více vláken](../collections/thread-safe/index.md)
- [Dělení objektů a funkcí](threading-objects-and-features.md)
