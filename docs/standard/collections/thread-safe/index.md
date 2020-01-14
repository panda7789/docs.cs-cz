---
title: Kolekce se zabezpečenými vlákny
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, overview
ms.assetid: 2e7ca21f-786c-4367-96be-0cf3f3dcc6bd
ms.openlocfilehash: 790543118b18b0422f41c3249512b62aae0cfb03
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75938113"
---
# <a name="thread-safe-collections"></a>Kolekce se zabezpečenými vlákny
.NET Framework 4 zavádí obor názvů <xref:System.Collections.Concurrent?displayProperty=nameWithType>, který obsahuje několik tříd kolekcí, které jsou bezpečné pro přístup z více vláken a jsou škálovatelné. Více vláken může bezpečně a efektivně přidávat nebo odebírat položky z těchto kolekcí, aniž by bylo potřeba provádět další synchronizaci v uživatelském kódu. Při psaní nového kódu, použijte souběžné třídy kolekce vždy, když více vláken bude zapisovat do kolekce současně. Pokud čtete pouze ze sdílené kolekce, pak můžete použít třídy v oboru názvů <xref:System.Collections.Generic?displayProperty=nameWithType>. Doporučujeme, abyste nepoužívali třídy kolekcí 1,0, pokud není nutné cílit na .NET Framework 1,1 nebo starší modul runtime.  
  
## <a name="thread-synchronization-in-the-net-framework-10-and-20-collections"></a>Synchronizace vláken v kolekcích .NET Framework 1,0 a 2,0  
 Kolekce představené v .NET Framework 1,0 se nacházejí v oboru názvů <xref:System.Collections?displayProperty=nameWithType>. Tyto kolekce, které zahrnují běžně používané <xref:System.Collections.ArrayList> a <xref:System.Collections.Hashtable>, poskytují určitou bezpečnost vlákna prostřednictvím vlastnosti `Synchronized`, která vrací obálku bezpečnou pro vlákno kolem kolekce. Obálka funguje tak, že při každé operaci přidání nebo odebrání zamkne celou kolekci. Proto musí každé vlákno, které se pokouší o přístup ke kolekci, počkat na jeho vypnutí, aby bylo možné provést jeden zámek. To není škálovatelné a může způsobit výrazné snížení výkonu pro velké kolekce. Návrh také není zcela chráněn před konflikty časování. Další informace najdete v tématu [synchronizace v obecných kolekcích](https://docs.microsoft.com/archive/blogs/bclteam/synchronization-in-generic-collections-brian-grunkemeyer).  
  
 Třídy kolekce představené v .NET Framework 2,0 se nacházejí v oboru názvů <xref:System.Collections.Generic?displayProperty=nameWithType>. Mezi ně patří <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.Dictionary%602>a tak dále. Tyto třídy poskytují lepší bezpečnost typů a výkon v porovnání s třídami .NET Framework 1,0. Třídy kolekce .NET Framework 2,0 však neposkytují žádnou synchronizaci vláken; uživatelský kód musí poskytovat veškerou synchronizaci při přidávání nebo odebírání položek na více vláknech současně.  
  
 V .NET Framework 4 doporučujeme třídy souběžných kolekcí, protože neposkytují pouze bezpečnost typů tříd kolekce .NET Framework 2,0, ale také efektivnější a více kompletních bezpečnostních vláken než kolekce .NET Framework 1,0. sdělit.  
  
## <a name="fine-grained-locking-and-lock-free-mechanisms"></a>Jemně odstupňované uzamykání a mechanismy bez zámků  
 Některé typy souběžných kolekcí používají zjednodušené synchronizační mechanismy, například <xref:System.Threading.SpinLock>, <xref:System.Threading.SpinWait>, <xref:System.Threading.SemaphoreSlim>a <xref:System.Threading.CountdownEvent>, které jsou v .NET Framework 4 novinkou. Tyto typy synchronizace obvykle využívají *zaneprázdněné odstřeďování* pro krátká období, předtím než se vlákno umístí do stavu true Wait. Pokud se očekává, že čekací časy budou velmi krátké, otáčející se mnohem méně výpočetně nákladný než čekání, což zahrnuje nákladný přechod jádra. Pro třídy kolekcí, které používají odstřeďování, tato efektivita znamená, že více vláken může přidávat a odebírat položky s velmi vysokou mírou. Další informace o zablokování vs. blokování naleznete v tématu [struktuře SpinLock](../../../../docs/standard/threading/spinlock.md) a [objektu SpinWait](../../../../docs/standard/threading/spinwait.md).  
  
 Třídy <xref:System.Collections.Concurrent.ConcurrentQueue%601> a <xref:System.Collections.Concurrent.ConcurrentStack%601> nepoužívají zámky vůbec. Místo toho se spoléhají na operace <xref:System.Threading.Interlocked> k zajištění bezpečnosti vláken.  
  
> [!NOTE]
> Vzhledem k tomu, že třídy souběžných kolekcí podporují <xref:System.Collections.ICollection>, poskytují implementace pro vlastnosti <xref:System.Collections.ICollection.IsSynchronized%2A> a <xref:System.Collections.ICollection.SyncRoot%2A>, i když tyto vlastnosti nejsou důležité. `IsSynchronized` vždy vrací `false` a `SyncRoot` je vždy `null` (`Nothing` v Visual Basic).  
  
 V následující tabulce jsou uvedeny typy kolekce v oboru názvů <xref:System.Collections.Concurrent?displayProperty=nameWithType>.  
  
|Type|Popis|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601>|Poskytuje ohraničování a blokování funkcionality pro jakýkoli typ, který implementuje <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>. Další informace naleznete v tématu [BlockingCollection – přehled](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602>|Implementace slovníku párů klíč-hodnota, který je bezpečný pro přístup z více vláken.|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601>|Implementace fronty FIFO (First-in, First-in), která je bezpečná pro přístup z více vláken.|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601>|Implementace zásobníku LIFO (poslední v, první ven), bezpečná pro přístup z více vláken.|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601>|Implementace neuspořádané kolekce prvků v bezpečném vlákně|  
|<xref:System.Collections.Concurrent.IProducerConsumerCollection%601>|Rozhraní, které musí typ implementovat pro použití v `BlockingCollection`.|  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[BlockingCollection – přehled](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)|Popisuje funkce poskytované typem <xref:System.Collections.Concurrent.BlockingCollection%601>.|  
|[Postupy: Přidávání a odebírání položek v ConcurrentDictionary](../../../../docs/standard/collections/thread-safe/how-to-add-and-remove-items.md)|Popisuje, jak přidat nebo odebrat prvky z <xref:System.Collections.Concurrent.ConcurrentDictionary%602>|  
|[Postupy: Přidávání a odebírání jednotlivých položek v BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md)|Popisuje, jak přidat a načíst položky z blokující kolekce bez použití enumerátoru jen pro čtení.|  
|[Postupy: Přidání funkcí ohraničování a blokování do kolekce](../../../../docs/standard/collections/thread-safe/how-to-add-bounding-and-blocking.md)|Popisuje způsob použití libovolné třídy kolekce jako základního mechanismu úložiště pro kolekci <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>.|  
|[Postupy: Použití příkazu ForEach k odebrání položek v BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md)|Popisuje, jak použít `foreach`(`For Each` v Visual Basic) k odebrání všech položek v blokující kolekci.|  
|[Postupy: Použití polí blokujících kolekcí v datovém kanálu](../../../../docs/standard/collections/thread-safe/how-to-use-arrays-of-blockingcollections.md)|Popisuje, jak použít více blokujících kolekcí současně pro implementaci kanálu.|  
|[Postupy: Vytvoření fondu objektů pomocí ConcurrentBag](../../../../docs/standard/collections/thread-safe/how-to-create-an-object-pool.md)|Zobrazuje způsob používání souběžného kontejneru za účelem zlepšení výkonu v situacích, kdy je možné namísto neustálého vytváření nových objektů opětovně používat stávající objekty.|  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>
