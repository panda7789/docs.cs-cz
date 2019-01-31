---
title: Přehled primitiv synchronizace
description: Další informace o .NET vlákno synchronizací primitiv používá k synchronizaci přístupu k sdíleného prostředku nebo vlákna interakce ovládacího prvku
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization, threads
- threading [.NET],synchronizing threads
- managed threading
ms.assetid: b782bcb8-da6a-4c6a-805f-2eb46d504309
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24df4140e515483adb94fa542a7063bd2ae2120b
ms.sourcegitcommit: dcc8feeff4718664087747529638ec9b47e65234
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/31/2019
ms.locfileid: "55479777"
---
# <a name="overview-of-synchronization-primitives"></a>Přehled primitiv synchronizace

.NET poskytuje celou řadu typů, které slouží k synchronizaci přístupu ke sdíleným prostředkům nebo koordinovat interakce vlákna.

> [!IMPORTANT]
> Použijte stejnou instanci primitivní synchronizace můžete chránit každý přístup ke sdíleným prostředkům. Více vláken může současně přístup k prostředku, pokud používáte jiný synchronizace primitivní instance můžete chránit přístup k prostředku nebo některé části kódu, přímý přístup k prostředku.

## <a name="waithandle-class-and-lightweight-synchronization-types"></a>Typy WaitHandle třídy a zjednodušené synchronizace

Více primitiv synchronizace .NET odvozovat <xref:System.Threading.WaitHandle?displayProperty=nameWithType> třídu, která zapouzdřuje popisovač synchronizace nativní operačního systému a používá signalizační mechanismus pro interakci vlákna. Tyto třídy zahrnují:

- <xref:System.Threading.Mutex?displayProperty=nameWithType>, který uděluje exkluzivní přístup ke sdíleným prostředkům. Stav objektu mutex je signál, pokud žádné vlákno jeho vlastníkem.
- <xref:System.Threading.Semaphore?displayProperty=nameWithType>, což omezuje souběžně počet vláken, které můžete přístup ke sdílenému prostředku nebo fond prostředků. Stav semafor je nastaven do signalizovaného, pokud jeho je počet větší než nula a nonsignaled při její vlastnosti count je nula.
- <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>, který představuje událost synchronizace vlákno a může být buď v unsignaled nebo signalizovaného stavu.
- <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType>, která je odvozena z <xref:System.Threading.EventWaitHandle> a při signalizován, obnoví automaticky unsignaled stavu po vydání jedním vláknem a čekání.
- <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>, která je odvozena z <xref:System.Threading.EventWaitHandle> a při signalizován, pořád do signalizovaného stavu, dokud <xref:System.Threading.EventWaitHandle.Reset%2A> metoda je volána.

V rozhraní .NET Framework protože <xref:System.Threading.WaitHandle> je odvozena z <xref:System.MarshalByRefObject?displayProperty=nameWithType>, tyto typy slouží k synchronizaci činností vlákna přes hranice aplikačních domén.

V rozhraní .NET Framework a .NET Core některé z těchto typů představují popisovače synchronizace s názvem systému, které jsou viditelné v celém operačním systému a je možné pro synchronizaci mezi procesy:

- <xref:System.Threading.Mutex> (Rozhraní .NET framework a .NET Core)
- <xref:System.Threading.Semaphore> (Rozhraní .NET framework a .NET Core ve Windows)
- <xref:System.Threading.EventWaitHandle> (.NET framework a .NET Core ve Windows).

Další informace najdete v tématu <xref:System.Threading.WaitHandle> reference k rozhraní API.

Typy zjednodušené synchronizace není využívají podkladového popisovače operačního systému a obvykle poskytují lepší výkon. Jsou však nelze použít pro synchronizaci mezi procesy. Pomocí těchto typů pro synchronizaci vláken v rámci jedné aplikace.

Některé z těchto typů jsou alternativy k typy odvozené od <xref:System.Threading.WaitHandle>. Například <xref:System.Threading.SemaphoreSlim> zjednodušené alternativu, která umožňuje <xref:System.Threading.Semaphore>.

## <a name="synchronization-of-access-to-a-shared-resource"></a>Synchronizace přístup ke sdíleným prostředkům

.NET poskytuje celou řadu primitiv synchronizace pro řízení přístupu ke sdíleným prostředkům ve víc vláknech.

### <a name="monitor-class"></a>Monitor – třída

<xref:System.Threading.Monitor?displayProperty=nameWithType> Třídy uděluje vzájemně vyloučený přístup ke sdíleným prostředkům získávání nebo uvolnění zámku na objektu, který identifikuje prostředek. Dokud je držen zámek, vlákna, která je držitelem zámku znovu získat a uvolní zámek. Jiné vlákno se blokuje získání zámku a <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> metoda čeká na zámek je uvolněn. <xref:System.Threading.Monitor.Enter%2A> Metoda získá vydané zámek. Můžete také použít <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> metody zadejte dobu, během které vlákno pokusy o získání zámku. Protože <xref:System.Threading.Monitor> třída má spřažení vláken, vlákna, která se získat zámek nutné uvolnit zámek voláním <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> metoda.

Můžete koordinovat interakce vlákna, která se pomocí získat zámek na stejný objekt <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType>, a <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> metody.

Další informace najdete v tématu <xref:System.Threading.Monitor> reference k rozhraní API.

> [!NOTE]
> Použití [Zámek](../../csharp/language-reference/keywords/lock-statement.md) příkaz v jazyce C# a [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) v sadě Visual Studio k synchronizaci přístupu ke sdíleným prostředkům namísto použití <xref:System.Threading.Monitor> třídy přímo. Tyto příkazy jsou implementovány pomocí <xref:System.Threading.Monitor.Enter%2A> a <xref:System.Threading.Monitor.Exit%2A> metody a `try…finally` blok k Ujistěte se, že pořízené zámek je uvolněn vždy.

### <a name="mutex-class"></a>Mutex – třída

<xref:System.Threading.Mutex?displayProperty=nameWithType> Třídy, jako je třeba <xref:System.Threading.Monitor>, udělí se výhradní přístup ke sdíleným prostředkům. Použijte jednu z [Mutex.WaitOne](<xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>) přetížení metody pro vlastnictví objektu mutex, na vyžádání. Stejně jako <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex> má spřažení vláken a vlákna, které získali mutex nutné uvolnit voláním <xref:System.Threading.Mutex.ReleaseMutex%2A?displayProperty=nameWithType> metody.

Na rozdíl od <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex> třídu lze použít pro synchronizaci mezi procesy. K tomuto účelu použijte pojmenovaný vzájemně vyloučený přístup, která je viditelná v celém operačním systému. Chcete-li vytvořit instanci pojmenovaný vzájemně vyloučený přístup, použijte [Mutex konstruktor](<xref:System.Threading.Mutex.%23ctor%2A>) , který určuje název. Můžete také volat <xref:System.Threading.Mutex.OpenExisting%2A?displayProperty=nameWithType> metoda otevřít existující pojmenovaný vzájemně vyloučený přístup systému.
  
Další informace najdete v tématu [mutexů](mutexes.md) článku a <xref:System.Threading.Mutex> reference k rozhraní API.

### <a name="spinlock-structure"></a>Struktuře SpinLock

<xref:System.Threading.SpinLock?displayProperty=nameWithType> Struktury, jako je třeba <xref:System.Threading.Monitor>, udělí se výhradní přístup ke sdíleným prostředkům na základě dostupnosti zámek. Když <xref:System.Threading.SpinLock> se pokouší získat zámek, který je k dispozici, počká ve smyčce opakovaně kontrolu, dokud nebude k dispozici zámek.

Další informace o výhody a nevýhody použití uzamčení, najdete v článku [SpinLock](spinlock.md) článku a <xref:System.Threading.SpinLock> reference k rozhraní API.

### <a name="readerwriterlockslim-class"></a>Třída ReaderWriterLockSlim

<xref:System.Threading.ReaderWriterLockSlim?displayProperty=nameWithType> Třídy udělí se výhradní přístup ke sdíleným prostředkům pro zápis a umožňuje více vláken pro přístup k prostředku současně pro čtení. Můžete chtít použít <xref:System.Threading.ReaderWriterLockSlim> k synchronizaci přístupu k sdíleným datům strukturu, která podporuje operace čtení bezpečným pro vlákno, ale vyžaduje výhradní přístup k provedení operace zápisu. Když vlákno vyžaduje výhradní přístup (například voláním <xref:System.Threading.ReaderWriterLockSlim.EnterWriteLock%2A?displayProperty=nameWithType> metoda), následné čtečky a zapisovače požadavky bloku až do všech existujících čtenáři odpojili zámek a zapisovač, který má zadaný a byla ukončena, zámek.
  
Další informace najdete v tématu <xref:System.Threading.ReaderWriterLockSlim> reference k rozhraní API.

### <a name="semaphore-and-semaphoreslim-classes"></a>Třídy Semaphore a SemaphoreSlim

<xref:System.Threading.Semaphore?displayProperty=nameWithType> a <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> třídy současně omezit počet vláken, které můžete přístup ke sdílenému prostředku nebo fond prostředků. Další vlákna, které příslušný prostředek vyžádejte Počkejte, až uvolní semafor libovolného vlákna. Protože semafor nemá spřažení vláken, vlákno může získat semafor a jiný ji uvolnit.

<xref:System.Threading.SemaphoreSlim> zjednodušené alternativu, která umožňuje <xref:System.Threading.Semaphore> a můžou používat jenom pro synchronizaci v rámci jednoho procesu hranice.

Na Windows, můžete použít <xref:System.Threading.Semaphore> synchronizace mezi procesy. K tomuto účelu vytvořte <xref:System.Threading.Semaphore> instanci, která představuje semafor pojmenované systém pomocí jedné z [semafor konstruktory](<xref:System.Threading.Semaphore.%23ctor%2A>) , který určuje název nebo <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType> metody. <xref:System.Threading.SemaphoreSlim> nepodporuje semafory pojmenované systému.

Další informace najdete v tématu [Semaphore a SemaphoreSlim](semaphore-and-semaphoreslim.md) článku a <xref:System.Threading.Semaphore> nebo <xref:System.Threading.SemaphoreSlim> reference k rozhraní API.

## <a name="thread-interaction-or-signaling"></a>Vlákno, nebo interakci signalizace

Vlákno (nebo interakci signalizace vlákno) znamená, že vlákno musí čekat oznámení nebo signál z jednoho nebo více vláken, aby bylo možné pokračovat. Například, pokud vlákna A zavolá <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> vlákna B, vlákna A metoda je blokovaný, dokud vlákno B dokončí. Synchronizace primitiv je popsáno v předchozí části poskytují různé mechanismus pro signalizaci: podle uvolnění zámku, vlákno upozorní jiného vlákna, který můžete přejít o získání zámku.

Tato část popisuje další signalizační konstrukce poskytované rozhraní .NET.

### <a name="eventwaithandle-autoresetevent-manualresetevent-and-manualreseteventslim-classes"></a>Třídy eventwaithandle –, autoresetevent –, ManualResetEvent a ManualResetEventSlim

<xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> Třída představuje událost synchronizace vlákna.

Synchronizace událostí může být buď v unsignaled nebo signalizovaného stavu. Po unsignaled stav události podproces, který volá události <xref:System.Threading.WaitHandle.WaitOne%2A?> přetížení je blokovaný, dokud událost je signalizována. <xref:System.Threading.EventWaitHandle.Set%2A?displayProperty=nameWithType> Metoda nastaví stav události do signalizovaného.

Chování <xref:System.Threading.EventWaitHandle> , který má byl signalizován, závisí na jeho režimu obnovení:

- <xref:System.Threading.EventWaitHandle> Vytvořené pomocí <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> příznak automatické obnovení po uvolnění jedno vlákno čekání. Je to jako Turniket, který umožňuje pouze jedno vlákno prostřednictvím pokaždé, když to bylo signalizováno. <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType> Třída, která je odvozena z <xref:System.Threading.EventWaitHandle>, představuje toto chování.
- <xref:System.Threading.EventWaitHandle> Vytvořené pomocí <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> příznak instalace zůstane až do signalizovaného jeho <xref:System.Threading.EventWaitHandle.Reset%2A> metoda je volána. Je to jako bránu se zavřít, dokud není signalizována a pak zůstane otevřená, dokud uživatel zavře. <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> Třída, která je odvozena z <xref:System.Threading.EventWaitHandle>, představuje toto chování. <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> Třídy je zjednodušené alternativou k <xref:System.Threading.ManualResetEvent>.

Na Windows, můžete použít <xref:System.Threading.EventWaitHandle> synchronizace mezi procesy. K tomuto účelu vytvořte <xref:System.Threading.EventWaitHandle> instanci, která představuje událost synchronizace s názvem systému pomocí jedné z [eventwaithandle – konstruktory](<xref:System.Threading.EventWaitHandle.%23ctor%2A>) , který určuje název nebo <xref:System.Threading.EventWaitHandle.OpenExisting%2A?displayProperty=nameWithType> metoda.

Další informace najdete v tématu [eventwaithandle –](eventwaithandle.md) článku. Reference k rozhraní API, najdete v části <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.AutoResetEvent>, <xref:System.Threading.ManualResetEvent>, a <xref:System.Threading.ManualResetEventSlim>.

### <a name="countdownevent-class"></a>Třída CountdownEvent

<xref:System.Threading.CountdownEvent?displayProperty=nameWithType> Třída představuje událost, která se stane nastavit, pokud její vlastnosti count je nula. Zatímco <xref:System.Threading.CountdownEvent.CurrentCount?displayProperty=nameWithType> je větší než nula, vlákna, která volá <xref:System.Threading.CountdownEvent.Wait%2A?displayProperty=nameWithType> blokovaný. Volání <xref:System.Threading.CountdownEvent.Signal%2A?displayProperty=nameWithType> se sníží počet události.

Rozdíl od <xref:System.Threading.ManualResetEvent> nebo <xref:System.Threading.ManualResetEventSlim>, který můžete použít k odblokování více vláken s signál z jednoho vlákna, můžete použít <xref:System.Threading.CountdownEvent> odblokujete jedno nebo více vláken s signály z více vláken.

Další informace najdete v tématu [CountdownEvent](countdownevent.md) článku a <xref:System.Threading.CountdownEvent> reference k rozhraní API.

### <a name="barrier-class"></a>Třídy Barrier

<xref:System.Threading.Barrier?displayProperty=nameWithType> Třída reprezentuje barrier spuštění vlákna. Vlákno, které volá <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> metoda signalizuje, že se dosáhlo odbourejte překážky bránící a počká až do jiných účastníka vláken oslovit odbourejte překážky bránící. Pokud všechna vlákna účastníka dosáhnou bariéry, jejich pokračovat a odbourejte překážky bránící se resetuje a je možné znovu.

Můžete použít <xref:System.Threading.Barrier> když jeden nebo více vláken, aby výsledky z jiných vláken před pokračováním na další fázi výpočtu.

Další informace najdete v tématu [bariéry](barrier.md) článku a <xref:System.Threading.Barrier> reference k rozhraní API.

## <a name="interlocked-class"></a>Interlocked – třída

<xref:System.Threading.Interlocked?displayProperty=nameWithType> Třída poskytuje statické metody, které provádějí jednoduché atomické operace na proměnnou. Tyto atomické operace zahrnují přidání, Inkrementace a dekrementace, exchange a podmíněné exchange, na kterém závisí porovnání a číst operace 64bitové celočíselné hodnoty.

Další informace najdete v tématu <xref:System.Threading.Interlocked> reference k rozhraní API.

## <a name="spinwait-structure"></a>Struktura SpinWait

<xref:System.Threading.SpinWait?displayProperty=nameWithType> Struktury poskytuje podporu pro čekání na základě typu číselník. Můžete ho použít, pokud vlákno obsahuje čekání na událost má být signalizován nebo podmínku splnit, ale v případě, že skutečné čekací doba má být menší než doba čekání popisovač čekání pomocí nebo jinak blokování vlákna. S použitím <xref:System.Threading.SpinWait>, můžete zadat krátké doby k aktivaci při čekání a potom yield (třeba podle čekání nebo v režimu spánku) pouze v případě, že nebyla splněna podmínka v určený čas.

Další informace najdete v tématu [objektu SpinWait](spinwait.md) článku a <xref:System.Threading.SpinWait> reference k rozhraní API.

## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Kolekce bezpečné pro vlákna](../collections/thread-safe/index.md)
- [Práce s vlákny funkce a objekty](threading-objects-and-features.md)
