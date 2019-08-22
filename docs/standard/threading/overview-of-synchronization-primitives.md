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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31d5df6521b7c420943a7d3d0efcf6e4bee2d3a2
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666280"
---
# <a name="overview-of-synchronization-primitives"></a>Přehled primitiv synchronizace

Rozhraní .NET poskytuje rozsah typů, které můžete použít k synchronizaci přístupu ke sdílenému prostředku nebo k interakci s vlákny pro koordinaci.

> [!IMPORTANT]
> Pro ochranu přístupu ke sdílenému prostředku použijte stejnou instanci primitiva synchronizace. Pokud k ochraně stejného prostředku používáte různé primitivní instance synchronizace, obejít ochranu poskytovanou primitivním primitivem.

## <a name="waithandle-class-and-lightweight-synchronization-types"></a>Třídy WaitHandle a zjednodušené typy synchronizace

Několik primitiv synchronizace rozhraní .NET je odvozeno <xref:System.Threading.WaitHandle?displayProperty=nameWithType> od třídy, která zapouzdřuje nativní popisovač synchronizace operačního systému a používá mechanismus signalizace pro interakci s vlákny. Tyto třídy zahrnují:

- <xref:System.Threading.Mutex?displayProperty=nameWithType>, který uděluje exkluzivní přístup ke sdílenému prostředku. Stav mutex je signalizována, pokud není vlastníkem vlákna.
- <xref:System.Threading.Semaphore?displayProperty=nameWithType>, což omezuje počet vláken, která mají souběžný přístup ke sdílenému prostředku nebo fondu prostředků. Stav semaforu je nastaven na signalizaci, pokud je jeho počet větší než nula a nesignálný, pokud je jeho počet nula.
- <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>, který představuje událost synchronizace vlákna a může být buď v signalizačním, nebo nesignalizacém stavu.
- <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType>, která je odvozena <xref:System.Threading.EventWaitHandle> z a, při signalizaci, je automaticky nastavena na nesignálný stav po uvolnění jediného čekajícího vlákna.
- <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>, která je odvozena <xref:System.Threading.EventWaitHandle> z a, je-li signalizována, zůstane v signalizačním stavu, <xref:System.Threading.EventWaitHandle.Reset%2A> dokud není volána metoda.

V .NET Framework, vzhledem k <xref:System.Threading.WaitHandle> tomu, že <xref:System.MarshalByRefObject?displayProperty=nameWithType>jsou odvozeny z, lze tyto typy použít k synchronizaci aktivit vláken napříč hranicemi aplikační domény.

V .NET Framework a .NET Core mohou některé z těchto typů představovat pojmenované popisovače synchronizace systému, které jsou viditelné v celém operačním systému a lze je použít pro synchronizaci mezi procesy:

- <xref:System.Threading.Mutex>(.NET Framework a .NET Core),
- <xref:System.Threading.Semaphore>(.NET Framework a .NET Core ve Windows),
- <xref:System.Threading.EventWaitHandle>(.NET Framework a .NET Core ve Windows).

Další informace najdete v referenčních <xref:System.Threading.WaitHandle> informacích k rozhraní API.

Odlehčené typy synchronizace nespoléhají na základní obslužné rutiny operačního systému a obvykle poskytují lepší výkon. Nelze je však použít pro synchronizaci mezi procesy. Tyto typy použijte pro synchronizaci vláken v rámci jedné aplikace.

Některé z těchto typů jsou alternativy k typům odvozeným <xref:System.Threading.WaitHandle>z. Například <xref:System.Threading.SemaphoreSlim> je odlehčená alternativa k <xref:System.Threading.Semaphore>.

## <a name="synchronization-of-access-to-a-shared-resource"></a>Synchronizace přístupu ke sdílenému prostředku

.NET poskytuje řadu synchronizačních primitiv pro řízení přístupu ke sdílenému prostředku více vlákny.

### <a name="monitor-class"></a>Monitor – třída

<xref:System.Threading.Monitor?displayProperty=nameWithType> Třída uděluje vzájemně exkluzivní přístup ke sdílenému prostředku získáním nebo uvolněním zámku objektu, který identifikuje prostředek. I když je držen zámek, vlákno, které obsahuje zámek, může znovu načíst a uvolnit zámek. Jakékoli jiné vlákno zablokovalo získání zámku a <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> metoda počká, dokud se zámek neuvolní. <xref:System.Threading.Monitor.Enter%2A> Metoda získá uvolněný zámek. Můžete také použít <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> metodu k určení doby, během které se vlákno pokusí získat zámek. Vzhledem k <xref:System.Threading.Monitor> tomu, že třída má spřažení vláken, vlákno, které získalo zámek, musí uvolnit zámek <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> voláním metody.

Můžete koordinovat interakci vláken, která získají zámek na stejném objektu pomocí <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType>metod, <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType>a <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> .

Další informace najdete v referenčních <xref:System.Threading.Monitor> informacích k rozhraní API.

> [!NOTE]
> Použijte příkaz [Lock](../../csharp/language-reference/keywords/lock-statement.md) v C# a příkaz [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) v Visual Basic pro synchronizaci přístupu ke sdílenému <xref:System.Threading.Monitor> prostředku místo přímého použití třídy. Tyto příkazy jsou implementovány pomocí <xref:System.Threading.Monitor.Enter%2A> metod a <xref:System.Threading.Monitor.Exit%2A> a `try…finally` bloku, aby bylo zajištěno, že se načtený zámek vždy uvolňuje.

### <a name="mutex-class"></a>Mutex – třída

<xref:System.Threading.Mutex?displayProperty=nameWithType> Třída ,například,udělujeexkluzivnípřístup<xref:System.Threading.Monitor>ke sdílenému prostředku. Použijte jedno z přetížení metod [mutex. WaitOne](<xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>) pro vyžádání vlastnictví mutexu. Podobně <xref:System.Threading.Monitor>jako <xref:System.Threading.Mutex> , má spřažení vlákna a vlákno, které získalo mutex, musí <xref:System.Threading.Mutex.ReleaseMutex%2A?displayProperty=nameWithType> uvolnit voláním metody.

<xref:System.Threading.Monitor> Na<xref:System.Threading.Mutex> rozdíl od, třída může být použita pro synchronizaci mezi procesy. K tomu použijte pojmenovaný mutex, který je viditelný v celém operačním systému. Chcete-li vytvořit pojmenovanou instanci mutex, použijte [konstruktor Mutex](<xref:System.Threading.Mutex.%23ctor%2A>) , který určuje název. Můžete také zavolat <xref:System.Threading.Mutex.OpenExisting%2A?displayProperty=nameWithType> metodu a otevřít existující objekt mutex s názvem systému.
  
Další informace najdete v článku věnovaném [mutexům](mutexes.md) a v <xref:System.Threading.Mutex> referenčních informacích k rozhraní API.

### <a name="spinlock-structure"></a>Struktura struktuře SpinLock

Struktura, jako <xref:System.Threading.Monitor>je, uděluje exkluzivní přístup ke sdílenému prostředku na základě dostupnosti zámku. <xref:System.Threading.SpinLock?displayProperty=nameWithType> Když <xref:System.Threading.SpinLock> se pokusí získat zámek, který není k dispozici, čeká ve smyčce a opakovaně kontroluje, dokud zámek nebude k dispozici.

Další informace o výhodách a nevýhodách použití zámku získáte v článku [struktuře SpinLock](spinlock.md) a v referenčních informacích k <xref:System.Threading.SpinLock> rozhraní API.

### <a name="readerwriterlockslim-class"></a>ReaderWriterLockSlim – třída

<xref:System.Threading.ReaderWriterLockSlim?displayProperty=nameWithType> Třída uděluje exkluzivní přístup ke sdílenému prostředku pro zápis a umožňuje více vláknům přistupovat ke zdroji současně pro čtení. Můžete chtít použít <xref:System.Threading.ReaderWriterLockSlim> pro synchronizaci přístupu ke sdílené datové struktuře, která podporuje operace čtení bezpečné pro přístup z více vláken, ale vyžaduje výhradní přístup k provádění operací zápisu. Když vlákno požaduje výhradní přístup (například voláním <xref:System.Threading.ReaderWriterLockSlim.EnterWriteLock%2A?displayProperty=nameWithType> metody), pak další požadavky na čtečku a zapisovač, dokud všichni stávající čtenáři neukončí zámek, a zapisovač zadal a ukončil zámek.
  
Další informace najdete v referenčních <xref:System.Threading.ReaderWriterLockSlim> informacích k rozhraní API.

### <a name="semaphore-and-semaphoreslim-classes"></a>Semafor a třídy SemaphoreSlim

Třídy <xref:System.Threading.Semaphore?displayProperty=nameWithType> a<xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> omezují počet vláken, která mají souběžný přístup ke sdílenému prostředku nebo fondu prostředků. Další vlákna, která vyžádají prostředek, počkejte, dokud jakékoli vlákno neuvolní semafor. Vzhledem k tomu, že semafor nemá spřažení vláken, vlákno může získat semafor a další ho může uvolnit.

<xref:System.Threading.SemaphoreSlim>je odlehčená alternativa <xref:System.Threading.Semaphore> k a lze ji použít pouze pro synchronizaci v rámci jedné hranice procesu.

Ve Windows můžete použít <xref:System.Threading.Semaphore> pro synchronizaci mezi procesy. K tomu je třeba vytvořit <xref:System.Threading.Semaphore> instanci, která představuje pojmenovaný systémový semafor pomocí jednoho z konstruktorů [semaforu](<xref:System.Threading.Semaphore.%23ctor%2A>) , který určuje název nebo <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType> metodu. <xref:System.Threading.SemaphoreSlim>nepodporuje pojmenované systémové semafory.

Další informace najdete v článku [semafor a SemaphoreSlim](semaphore-and-semaphoreslim.md) a v referenčních <xref:System.Threading.Semaphore> informacích k <xref:System.Threading.SemaphoreSlim> rozhraní API.

## <a name="thread-interaction-or-signaling"></a>Interakce vlákna nebo signalizace

Interakce vlákna (nebo signalizace vlákna) znamená, že vlákno musí čekat na oznámení nebo signál, z jednoho nebo více vláken, aby bylo možné pokračovat. Například pokud vlákno a volá <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> metodu vlákna B, vlákno a je blokováno, dokud vlákno b nedokončí. Prvky synchronizace popsané v předchozí části poskytují jiný mechanismus pro signalizaci: uvolněním zámku vlákno upozorní jiné vlákno, že může pokračovat získáním zámku.

Tato část popisuje další konstrukce signalizace poskytované rozhraním .NET.

### <a name="eventwaithandle-autoresetevent-manualresetevent-and-manualreseteventslim-classes"></a>Třídy EventWaitHandle, AutoResetEvent, ManualResetEvent a ManualResetEventSlim

<xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> Třída představuje událost synchronizace vlákna.

Událost synchronizace může být buď v nesignalizacém, nebo ve stavu signalizace. Při nesignalizaci stavu události je vlákno, které volá <xref:System.Threading.WaitHandle.WaitOne%2A?> přetížení události, blokováno, dokud událost není signalizována. <xref:System.Threading.EventWaitHandle.Set%2A?displayProperty=nameWithType> Metoda nastaví stav události k signalizaci.

Chování <xref:System.Threading.EventWaitHandle> , které bylo signalizaci, závisí na režimu obnovení:

- <xref:System.Threading.EventWaitHandle> Vytvořený<xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> pomocí příznaku se automaticky obnoví po uvolnění jediného čekajícího vlákna. Vypadá to jako Turnstile, který umožňuje pouze jedno vlákno přes pokaždé, když je signál. Třída, která je odvozena z <xref:System.Threading.EventWaitHandle>, představuje toto chování. <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType>
- Vytvořená pomocí příznaku zůstane signalizována do chvíle <xref:System.Threading.EventWaitHandle.Reset%2A> , kdy se zavolá jeho metoda. <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> <xref:System.Threading.EventWaitHandle> Je to jako brána, která je zavřená, dokud není signalizována, a pak zůstane otevřená, dokud ji někdo neuzavře. Třída, která je odvozena z <xref:System.Threading.EventWaitHandle>, představuje toto chování. <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> Třída je odlehčená alternativa k <xref:System.Threading.ManualResetEvent>. <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>

Ve Windows můžete použít <xref:System.Threading.EventWaitHandle> pro synchronizaci mezi procesy. K tomu je třeba vytvořit <xref:System.Threading.EventWaitHandle> instanci, která představuje pojmenovanou událost synchronizace systému pomocí jednoho z konstruktorů [EventWaitHandle](<xref:System.Threading.EventWaitHandle.%23ctor%2A>) , které určují název nebo <xref:System.Threading.EventWaitHandle.OpenExisting%2A?displayProperty=nameWithType> metodu.

Další informace najdete v článku [EventWaitHandle](eventwaithandle.md) . Referenční informace k rozhraní API naleznete <xref:System.Threading.EventWaitHandle>v <xref:System.Threading.AutoResetEvent>tématech <xref:System.Threading.ManualResetEvent>,, <xref:System.Threading.ManualResetEventSlim>a.

### <a name="countdownevent-class"></a>CountdownEvent – třída

<xref:System.Threading.CountdownEvent?displayProperty=nameWithType> Třída představuje událost, která se nastaví, když je její počet nula. Zatímco <xref:System.Threading.CountdownEvent.CurrentCount?displayProperty=nameWithType> je větší než nula, vlákno, které volá <xref:System.Threading.CountdownEvent.Wait%2A?displayProperty=nameWithType> , je blokované. Volání <xref:System.Threading.CountdownEvent.Signal%2A?displayProperty=nameWithType> k odečtení počtu událostí.

Na rozdíl <xref:System.Threading.ManualResetEvent> od nebo <xref:System.Threading.ManualResetEventSlim>, které lze použít k odblokování více vláken pomocí signálu z jednoho vlákna, můžete použít <xref:System.Threading.CountdownEvent> k odblokování jednoho nebo více podprocesů s signály z více vláken.

Další informace najdete v článku [CountdownEvent](countdownevent.md) a v referenčních <xref:System.Threading.CountdownEvent> informacích k rozhraní API.

### <a name="barrier-class"></a>Bariéra – třída

<xref:System.Threading.Barrier?displayProperty=nameWithType> Třída představuje bariéru spuštění vlákna. Vlákno, které volá <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> metodu, signalizuje, že dosáhla bariéry a čeká, dokud ostatní vlákna účastníka dosáhnou bariéry. Když všechna vlákna účastníka dosáhnou bariéry, budou pokračovat a bariéra se resetuje a dá se použít znovu.

V případě, <xref:System.Threading.Barrier> že jeden nebo více vláken vyžaduje výsledky jiných vláken, než budete pokračovat do další fáze výpočtu, můžete použít.

Další informace najdete v článku o [bariérách](barrier.md) a v <xref:System.Threading.Barrier> referenčních informacích k rozhraní API.

## <a name="interlocked-class"></a>Interlocked – třída

<xref:System.Threading.Interlocked?displayProperty=nameWithType> Třída poskytuje statické metody, které provádějí jednoduché atomické operace na proměnné. Tyto atomické operace zahrnují sčítání, zvýšení a snížení, Exchange a podmíněný Exchange, které závisí na porovnání a operace čtení z 64 celočíselné hodnoty.

Další informace najdete v referenčních <xref:System.Threading.Interlocked> informacích k rozhraní API.

## <a name="spinwait-structure"></a>Struktura objektu SpinWait

<xref:System.Threading.SpinWait?displayProperty=nameWithType> Struktura poskytuje podporu pro čekání na číselník. Můžete ji chtít použít, když vlákno musí počkat na signalizaci události nebo podmínku, která má být splněna, ale pokud se očekává, že doba čekání bude menší než čekací doba potřebná při použití popisovače čekání nebo jiným způsobem blokování vlákna. Pomocí <xref:System.Threading.SpinWait>můžete zadat krátkou dobu, kdy se má při čekání čekat, a pak (například čekáním nebo v režimu spánku), a to pouze v případě, že v určeném čase nebyla splněna podmínka.

Další informace najdete v článku [objektu SpinWait](spinwait.md) a v referenčních <xref:System.Threading.SpinWait> informacích k rozhraní API.

## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Kolekce bezpečné pro přístup z více vláken](../collections/thread-safe/index.md)
- [Dělení objektů a funkcí](threading-objects-and-features.md)
