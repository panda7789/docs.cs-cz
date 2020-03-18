---
title: Kdy použít kolekci s bezpečnými vlákny
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, when to upgrade
ms.assetid: a9babe97-e457-4ff3-b528-a1bc940d5320
ms.openlocfilehash: 5a0abef6de9f932f44fc7e3239b98c3a27846580
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711217"
---
# <a name="when-to-use-a-thread-safe-collection"></a>Kdy použít kolekci s bezpečnými vlákny
Rozhraní .NET Framework 4 zavádí pět nových typů kolekce, které jsou speciálně navrženy pro podporu vícevláknových operací přidání a odebrání. Pro dosažení bezpečnosti závitů používají tyto nové typy různé druhy efektivních mechanismů uzamčení a synchronizace bez zámků. Synchronizace zvyšuje režii operace. Množství režie závisí na druhu synchronizace, která se používá, druh operací, které jsou prováděny a další faktory, jako je například počet podprocesů, které se pokoušejí souběžně přistupovat ke kolekci.  
  
 V některých scénářích je režie synchronizace zanedbatelná a umožňuje vícevláknovému typu provádět výrazně rychleji a škálovat mnohem lépe než jeho ekvivalent bez bezpečnosti vláken, pokud je chráněn externím zámkem. V jiných scénářích může režie způsobit, že typ bezpečný pro přístup z více vláken provede a škáluje přibližně stejně nebo dokonce pomaleji než externě uzamčená verze typu, která není bezpečná pro přístup z více vláken.  
  
 Následující části poskytují obecné pokyny o tom, kdy použít kolekci bezpečnou pro přístup z více vláken oproti jeho ekvivalentu, který není bezpečný pro přístup z více vláken a který má zámek zadaný uživatelem kolem operací čtení a zápisu. Vzhledem k tomu, že výkon se může lišit v závislosti na mnoha faktorech, pokyny nejsou specifické a nemusí být nutně platné za všech okolností. Pokud výkon je velmi důležité, pak nejlepší způsob, jak určit, který typ kolekce použít, je měření výkonu na základě konfigurace reprezentativní počítače a zatížení. Tento dokument používá následující termíny:  
  
 *Čistý scénář výrobce a spotřebitele*  
 Jakékoli dané vlákno je buď přidání nebo odebrání prvků, ale ne obojí.  
  
 *Smíšený scénář mezi producentem a spotřebitelem*  
 Jakékoli dané vlákno je přidání a odebrání prvků.  
  
 *Zrychlení*  
 Rychlejší algoritmický výkon vzhledem k jinému typu ve stejném scénáři.  
  
 *Škálovatelnost*  
 Zvýšení výkonu, který je úměrný počtu jader v počítači. Algoritmus, který škáluje provádí rychleji na osm jader, než to dělá na dvou jádrech.  
  
## <a name="concurrentqueuet-vs-queuet"></a>ConcurrentQueue(T) vs. Queue(T)  
 V čistě výrobce a spotřebitele scénáře, kde doba zpracování pro každý <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> prvek je velmi malý <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> (několik pokynů), pak může nabídnout skromné výhody výkonu oproti který má externí zámek. V tomto <xref:System.Collections.Concurrent.ConcurrentQueue%601> scénáři funguje nejlépe, když jeden vyhrazené vlákno je fronty a jeden vyhrazené vlákno je de-queuing. Pokud toto pravidlo nevynucujete, může <xref:System.Collections.Generic.Queue%601> <xref:System.Collections.Concurrent.ConcurrentQueue%601> být dokonce rychlejší než v počítačích s více jádry.  
  
 Pokud doba zpracování je kolem 500 FLOPS (operace s plovoucí desetinnou <xref:System.Collections.Concurrent.ConcurrentQueue%601>tísní) nebo více, pak pravidlo dvou vláken se nevztahuje na , který pak má velmi dobrou škálovatelnost. <xref:System.Collections.Generic.Queue%601>není škálovat dobře v tomto scénáři.  
  
 Ve smíšených scénářích výrobce a spotřebitele, když <xref:System.Collections.Generic.Queue%601> je doba zpracování velmi <xref:System.Collections.Concurrent.ConcurrentQueue%601> malá, a která má externí zámek váhy lepší než nemá. Nicméně, když doba zpracování je kolem 500 <xref:System.Collections.Concurrent.ConcurrentQueue%601> FLOPS nebo více, pak váhy lepší.  
  
## <a name="concurrentstack-vs-stack"></a>Souběžný zásobník vs. zásobník  
 V čistě výrobce-spotřebitelské scénáře, kdy je <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType> doba <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType> zpracování velmi malá, pak a že má externí zámek bude pravděpodobně provádět přibližně stejné s jedním vyhrazeným tlačí cípem a jeden vyhrazený odprýskávání vlákno. Však jako počet podprocesů zvyšuje, oba typy zpomalit <xref:System.Collections.Generic.Stack%601> z důvodu <xref:System.Collections.Concurrent.ConcurrentStack%601>zvýšené kolize a může fungovat lépe než . Pokud je doba zpracování kolem 500 FLOPS nebo více, pak oba typy měřítko na přibližně stejnou rychlostí.  
  
 Ve smíšených scénářích <xref:System.Collections.Concurrent.ConcurrentStack%601> výrobce a spotřebitele je rychlejší pro malé i velké úlohy.  
  
 Použití <xref:System.Collections.Concurrent.ConcurrentStack%601.PushRange%2A> a <xref:System.Collections.Concurrent.ConcurrentStack%601.TryPopRange%2A> může výrazně urychlit přístupové časy.  
  
## <a name="concurrentdictionary-vs-dictionary"></a>ConcurrentDictionary vs. Slovník  
 Obecně použijte <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> v každém scénáři, kde přidáváte a aktualizujete klíče nebo hodnoty současně z více vláken. Ve scénářích, které zahrnují časté <xref:System.Collections.Concurrent.ConcurrentDictionary%602> aktualizace a relativně málo čtení, obecně nabízí skromné výhody. Ve scénářích, které zahrnují mnoho <xref:System.Collections.Concurrent.ConcurrentDictionary%602> čtení a mnoho aktualizací, obecně je výrazně rychlejší v počítačích, které mají libovolný počet jader.  
  
 Ve scénářích, které zahrnují časté aktualizace, můžete <xref:System.Collections.Concurrent.ConcurrentDictionary%602> zvýšit stupeň souběžnosti v a pak měřit, zda zvýšení výkonu v počítačích, které mají více jader. Pokud změníte úroveň souběžnosti, vyhněte se globální operace co nejvíce.  
  
 Pokud čtete pouze klíč nebo <xref:System.Collections.Generic.Dictionary%602> hodnoty, je rychlejší, protože není vyžadována žádná synchronizace, pokud slovník není měněn žádnými vlákny.  
  
## <a name="concurrentbag"></a>Concurrentbag  
 V čistě výrobce a <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> spotřebitele scénáře bude pravděpodobně provádět pomaleji než ostatní typy souběžných kolekcí.  
  
 Ve smíšených scénáře <xref:System.Collections.Concurrent.ConcurrentBag%601> výrobce a spotřebitele je obecně mnohem rychlejší a škálovatelné než jakýkoli jiný typ souběžné kolekce pro velké i malé úlohy.  
  
## <a name="blockingcollection"></a>BlockingCollection  
 Při ohraničování a blokování <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> sémantiku jsou požadovány, bude pravděpodobně provádět rychleji než jakékoli vlastní implementace. Podporuje také bohaté zrušení, výčtu a zpracování výjimek.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Kolekce se zabezpečenými vlákny](../../../../docs/standard/collections/thread-safe/index.md)
- [Paralelní programování](../../../../docs/standard/parallel-programming/index.md)
