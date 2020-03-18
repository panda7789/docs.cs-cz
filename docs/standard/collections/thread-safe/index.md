---
title: Kolekce se zabezpečenými vlákny
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, overview
ms.assetid: 2e7ca21f-786c-4367-96be-0cf3f3dcc6bd
ms.openlocfilehash: 790543118b18b0422f41c3249512b62aae0cfb03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75938113"
---
# <a name="thread-safe-collections"></a>Kolekce se zabezpečenými vlákny
Rozhraní .NET Framework 4 <xref:System.Collections.Concurrent?displayProperty=nameWithType> zavádí obor názvů, který obsahuje několik tříd kolekce, které jsou bezpečné pro přístup z více vláken a škálovatelné. Více vláken můžete bezpečně a efektivně přidávat nebo odebírat položky z těchto kolekcí, bez nutnosti další synchronizace v uživatelském kódu. Při psaní nového kódu použijte třídy souběžné kolekce vždy, když více vláken bude zapisovat do kolekce současně. Pokud čtete pouze ze sdílené kolekce, můžete použít <xref:System.Collections.Generic?displayProperty=nameWithType> třídy v oboru názvů. Doporučujeme nepoužívat třídy kolekce 1.0, pokud není nutné cílit na rozhraní .NET Framework 1.1 nebo starší za běhu.  
  
## <a name="thread-synchronization-in-the-net-framework-10-and-20-collections"></a>Synchronizace vláken v kolekcích .NET Framework 1.0 a 2.0  
 Kolekce zavedené v rozhraní .NET Framework 1.0 <xref:System.Collections?displayProperty=nameWithType> se nacházejí v oboru názvů. Tyto kolekce, které zahrnují běžně <xref:System.Collections.ArrayList> <xref:System.Collections.Hashtable>používané a , poskytují `Synchronized` některé bezpečnost i pro podprocesy prostřednictvím vlastnosti, která vrátí obálku bezpečné pro přístup z více vláken kolem kolekce. Obálka funguje uzamčením celé kolekce při každé operaci přidání nebo odebrání. Proto každé vlákno, které se pokouší o přístup ke kolekci musí čekat na jeho zase trvat jeden zámek. To není škálovatelné a může způsobit významné snížení výkonu pro velké kolekce. Návrh také není zcela chráněn před závodními podmínkami. Další informace naleznete [v tématu Synchronizace v obecných kolekcích](https://docs.microsoft.com/archive/blogs/bclteam/synchronization-in-generic-collections-brian-grunkemeyer).  
  
 Třídy kolekce zavedené v rozhraní .NET Framework 2.0 se nacházejí v oboru <xref:System.Collections.Generic?displayProperty=nameWithType> názvů. Patří <xref:System.Collections.Generic.List%601>mezi <xref:System.Collections.Generic.Dictionary%602>ně , , a tak dále. Tyto třídy poskytují lepší bezpečnost typů a výkon ve srovnání s .NET Framework 1.0 třídy. Třídy kolekce rozhraní .NET Framework 2.0 však neposkytují žádnou synchronizaci vláken. uživatelský kód musí poskytovat všechny synchronizace při přidávání nebo odebírání položek ve více vláknech současně.  
  
 Doporučujeme souběžné kolekce třídy v rozhraní .NET Framework 4, protože poskytují nejen bezpečnost typů .NET Framework 2.0 kolekce tříd, ale také efektivnější a úplnější bezpečnost podprocesu než kolekce .NET Framework 1.0 Poskytnout.  
  
## <a name="fine-grained-locking-and-lock-free-mechanisms"></a>Jemně odstupňované uzamykací a bezblokovací mechanismy  
 Některé typy souběžných kolekcí používají zjednodušené <xref:System.Threading.SpinLock> <xref:System.Threading.SpinWait>synchronizační mechanismy, například , , <xref:System.Threading.SemaphoreSlim>a <xref:System.Threading.CountdownEvent>, které jsou nové v rozhraní .NET Framework 4. Tyto typy synchronizace obvykle používají *zaneprázdněné předení* na krátkou dobu před jejich uvede vlákno do skutečného stavu Wait. Když se očekává, že čekací doby budou velmi krátké, předení je mnohem méně výpočtově drahé než čekání, což zahrnuje nákladný přechod jádra. Pro třídy kolekce, které používají spinning, tato účinnost znamená, že více vláken můžete přidat a odebrat položky ve velmi vysoké míře. Další informace o spinning vs. blocking naleznete v tématu [SpinLock](../../../../docs/standard/threading/spinlock.md) a [SpinWait](../../../../docs/standard/threading/spinwait.md).  
  
 <xref:System.Collections.Concurrent.ConcurrentQueue%601> Třídy <xref:System.Collections.Concurrent.ConcurrentStack%601> a nepoužívají zámky vůbec. Místo toho spoléhají <xref:System.Threading.Interlocked> na operace k dosažení bezpečnosti závitů.  
  
> [!NOTE]
> Vzhledem k tomu, <xref:System.Collections.ICollection>že podporují třídy <xref:System.Collections.ICollection.IsSynchronized%2A> souběžných kolekcí , poskytují implementace vlastností a, <xref:System.Collections.ICollection.SyncRoot%2A> i když tyto vlastnosti jsou irelevantní. `IsSynchronized`vždy `false` vrátí `SyncRoot` a `null` `Nothing` je vždy (v jazyce Visual Basic).  
  
 V následující tabulce jsou uvedeny typy kolekcí v oboru <xref:System.Collections.Concurrent?displayProperty=nameWithType> názvů.  
  
|Typ|Popis|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601>|Poskytuje ohraničovací a blokovací <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>funkce pro všechny typy, které implementuje . Další informace naleznete v tématu [BlockingCollection Overview](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602>|Implementace slovníku párů klíč-hodnota bezpečná pro přístup z více vláken.|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601>|Implementace fronty FIFO (first-in, first-out) bezpečná pro přístup z více vláken.|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601>|Implementace zásobníku LIFO (last-in, first-out) bezpečná pro přístup z více vláken.|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601>|Implementace neuspořádané kolekce prvků bezpečná pro přístup z více vláken.|  
|<xref:System.Collections.Concurrent.IProducerConsumerCollection%601>|Rozhraní, které musí typ implementovat `BlockingCollection`pro použití v .|  
  
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[BlockingCollection – přehled](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)|Popisuje funkce poskytované typem. <xref:System.Collections.Concurrent.BlockingCollection%601>|  
|[Postupy: Přidávání a odebírání položek v ConcurrentDictionary](../../../../docs/standard/collections/thread-safe/how-to-add-and-remove-items.md)|Popisuje, jak přidat a odebrat prvky z<xref:System.Collections.Concurrent.ConcurrentDictionary%602>|  
|[Postupy: Přidávání a odebírání jednotlivých položek v BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md)|Popisuje, jak přidat a načíst položky z kolekce blokování bez použití čítače výčtu jen pro čtení.|  
|[Postupy: Přidání funkcí ohraničování a blokování do kolekce](../../../../docs/standard/collections/thread-safe/how-to-add-bounding-and-blocking.md)|Popisuje, jak použít libovolnou třídu kolekce <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> jako základní mechanismus úložiště pro kolekci.|  
|[Postupy: Použití příkazu ForEach k odebrání položek v kolekci BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md)|Popisuje použití `foreach`aplikace ,`For Each` ( v jazyce Visual Basic) k odebrání všech položek v blokovací kolekci.|  
|[Postupy: Použití polí blokujících kolekcí v datovém kanálu](../../../../docs/standard/collections/thread-safe/how-to-use-arrays-of-blockingcollections.md)|Popisuje, jak používat více blokování kolekce současně k implementaci kanálu.|  
|[Postupy: Vytvoření fondu objektů pomocí ConcurrentBag](../../../../docs/standard/collections/thread-safe/how-to-create-an-object-pool.md)|Zobrazuje způsob používání souběžného kontejneru za účelem zlepšení výkonu v situacích, kdy je možné namísto neustálého vytváření nových objektů opětovně používat stávající objekty.|  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>
