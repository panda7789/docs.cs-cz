---
title: Kolekce se zabezpečenými vlákny
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, overview
ms.assetid: 2e7ca21f-786c-4367-96be-0cf3f3dcc6bd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7fad67c1a3c53cd83dec6bfa161333b5e20ab4c4
ms.sourcegitcommit: deb9225a55485a5a6e6c7914deb30ccfceb69d3f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2019
ms.locfileid: "54058318"
---
# <a name="thread-safe-collections"></a>Kolekce se zabezpečenými vlákny
[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] Zavádí <xref:System.Collections.Concurrent?displayProperty=nameWithType> obor názvů, který zahrnuje několik tříd kolekcí, které jsou bezpečná a škálovatelná. Více vláken můžete bezpečně a efektivně přidat nebo odebrat položky z těchto kolekcí, bez nutnosti další synchronizace v uživatelském kódu. Pokud píšete nový kód, použijte třídy souběžných kolekcích pokaždé, když se více vláken současně zapíše do kolekce. Pokud jsou pouze čtení ze sdílené kolekce, pak můžete použít třídy v <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů. Doporučujeme, abyste provedli třídy kolekcí verze 1.0, pokud je potřeba cílit na .NET Framework 1.1 nebo starší modul runtime.  
  
## <a name="thread-synchronization-in-the-net-framework-10-and-20-collections"></a>Synchronizace vláken v rozhraní .NET Framework 1.0 a 2.0 kolekce  
 Jsou součástí kolekce zavedené v rozhraní .NET Framework 1.0 <xref:System.Collections?displayProperty=nameWithType> oboru názvů. Tato kolekce, které zahrnují běžně používaných <xref:System.Collections.ArrayList> a <xref:System.Collections.Hashtable>, poskytují některé vlákno bezpečnosti prostřednictvím `Synchronized` vlastnost, která vrátí obálku kolekce bezpečné pro vlákna. Obálka funguje tak, že na každou operaci přidání nebo odebrání zamykání celou kolekci. Proto musíte počkat každý podproces, který se pokouší o přístup ke kolekci přijde vzít jeden zámek. To není škálovatelné a může způsobit významné snížení výkonu u rozsáhlých kolekcí. Návrh navíc není zcela chráněna před časování. Další informace najdete v tématu [synchronizace u obecných kolekcí](https://blogs.msdn.microsoft.com/bclteam/2005/03/15/synchronization-in-generic-collections-brian-grunkemeyer/).  
  
 Třídy kolekcí zavedené v rozhraní .NET Framework 2.0 jsou součástí <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů. Patří mezi ně <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.Dictionary%602>, a tak dále. Tyto třídy poskytují vylepšené typové bezpečnosti a výkonu ve srovnání s tříd rozhraní .NET Framework 1.0. Kolekce tříd rozhraní .NET Framework 2.0 však neposkytují žádné vlákno synchronizace; kód uživatele musí poskytovat všechny synchronizace, při položky jsou přidány nebo odebrány z více vláken současně.  
  
 Souběžné kolekce tříd v doporučujeme [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] protože poskytují nejenom bezpečnost typů kolekce tříd rozhraní .NET Framework 2.0, ale také mnohem efektivnější a kompletní zabezpečení vlákna, než [!INCLUDE[net_v10_short](../../../../includes/net-v10-short-md.md)] kolekce poskytují.  
  
## <a name="fine-grained-locking-and-lock-free-mechanisms"></a>Detailní zamykání a mechanismy bez zámku  
 U některých typů souběžných kolekcích použít mechanismus lehké synchronizace, jako <xref:System.Threading.SpinLock>, <xref:System.Threading.SpinWait>, <xref:System.Threading.SemaphoreSlim>, a <xref:System.Threading.CountdownEvent>, které jsou novinkou [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]. Tyto typy synchronizace obvykle používají *zaneprázdnění* krátkou dobu před jejich vlákna do stavu čekání. hodnotu true. Pokud se očekává velmi krátké doby čekání, je mnohem méně výpočetně náročné než čekání, který zahrnuje nákladný přechod jádra zaneprázdnění. Této efektivity pro třídy kolekcí, které používají zaneprázdnění, znamená, že můžete přidávat a odebírat položky na velmi vysoké míře více vláken. Další informace o rozdílech mezi blokování zaneprázdněním najdete v tématu [SpinLock](../../../../docs/standard/threading/spinlock.md) a [objektu SpinWait](../../../../docs/standard/threading/spinwait.md).  
  
 <xref:System.Collections.Concurrent.ConcurrentQueue%601> a <xref:System.Collections.Concurrent.ConcurrentStack%601> třídy nepoužívejte zámky vůbec. Místo toho spoléhají na <xref:System.Threading.Interlocked> operace zajistit bezpečnost vláken.  
  
> [!NOTE]
>  Protože podporuje souběžné kolekce tříd <xref:System.Collections.ICollection>, poskytují implementace pro <xref:System.Collections.ICollection.IsSynchronized%2A> a <xref:System.Collections.ICollection.SyncRoot%2A> vlastnosti, i když tyto vlastnosti nejsou relevantní. `IsSynchronized` vždy vrátí `false` a `SyncRoot` je vždy `null` (`Nothing` v jazyce Visual Basic).  
  
 V následující tabulce jsou uvedeny typy kolekcí v <xref:System.Collections.Concurrent?displayProperty=nameWithType> oboru názvů.  
  
|Typ|Popis|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601>|Poskytuje funkcí ohraničování a blokování pro libovolný typ, který implementuje <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>. Další informace najdete v tématu [BlockingCollection – přehled](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602>|Bezpečná pro vlákno provádění slovník párů klíč hodnota.|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601>|Bezpečná pro vlákno provádění fronty FIFO (first in, první ven).|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601>|Bezpečná pro vlákno provádění zásobníku LIFO (poslední dovnitř, první ven).|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601>|Bezpečná pro vlákno provádění Neseřazený kolekci elementů.|  
|<xref:System.Collections.Concurrent.IProducerConsumerCollection%601>|Typ musí implementovat pro použití v rozhraní `BlockingCollection`.|  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[BlockingCollection – přehled](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)|Popisuje funkce poskytované službou <xref:System.Collections.Concurrent.BlockingCollection%601> typu.|  
|[Postupy: Přidání a odebrání položek v ConcurrentDictionary](../../../../docs/standard/collections/thread-safe/how-to-add-and-remove-items.md)|Popisuje, jak přidat a odebrat elementy ze <xref:System.Collections.Concurrent.ConcurrentDictionary%602>|  
|[Postupy: Přidat a jednotlivě převzít položek v BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md)|Popisuje, jak přidat a načítat položky z blokující kolekce bez použití čítač jen pro čtení.|  
|[Postupy: Přidání funkcí ohraničování a blokování do kolekce](../../../../docs/standard/collections/thread-safe/how-to-add-bounding-and-blocking.md)|Popisuje, jak použít libovolnou třídu kolekce jako základní mechanizmus úložiště pro <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> kolekce.|  
|[Postupy: Použití příkazu ForEach k odebrání položek v BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md)|Popisuje způsob použití `foreach`, (`For Each` v jazyce Visual Basic) odebrat všechny položky v kolekci blokování.|  
|[Postupy: Použití polí blokujících kolekcí v kanálu](../../../../docs/standard/collections/thread-safe/how-to-use-arrays-of-blockingcollections.md)|Popisuje způsob implementace kanálu pomocí více blokující kolekce ve stejnou dobu.|  
|[Postupy: Vytvoření fondu objektů pomocí ConcurrentBag](../../../../docs/standard/collections/thread-safe/how-to-create-an-object-pool.md)|Zobrazuje způsob používání souběžného kontejneru za účelem zlepšení výkonu v situacích, kdy je možné namísto neustálého vytváření nových objektů opětovně používat stávající objekty.|  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>
