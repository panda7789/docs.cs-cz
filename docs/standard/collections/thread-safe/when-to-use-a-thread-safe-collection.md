---
title: Kdy použít kolekci s bezpečnými vlákny
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, when to upgrade
ms.assetid: a9babe97-e457-4ff3-b528-a1bc940d5320
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eefa1b52907525059b3403e7eb20542d3b5a5c73
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47109979"
---
# <a name="when-to-use-a-thread-safe-collection"></a>Kdy použít kolekci s bezpečnými vlákny
[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] Představuje pět nových typů, které jsou navrženy speciálně pro podporu vícevláknové přidávat a odebírat operace. Tyto nové typy zajistit zabezpečení vlákna používají různé druhy efektivní zamykání a mechanismy bez zámku synchronizace. Synchronizace přidá nároky na operaci. Množství práce, kterou závisí na typu synchronizace, který se používá, druh operace, které jsou prováděny a dalších faktorů, třeba počet vláken, které se pokoušíte získat přístup ke kolekci současně.  
  
 V některých scénářích synchronizace režie zanedbatelná a umožňuje vícevláknové typ výrazně rychlejší a škálovat mnohem lepší než ekvivalentní vláknově bezpečné při ochraně externí zámek. V jiných scénářích může způsobit nároky na typ bezpečným pro vlákno k provedení a škálování o stejný nebo i pomaleji než externě uzamčen, vláknově bezpečné verze typu.  
  
 Následující části obsahují obecné pokyny o tom, kdy použít kolekci bezpečné pro vlákna a ekvivalentem vláknově bezpečné, který má zadaný uživatel zámku čtení a zápisu operace. Protože výkon se může lišit v závislosti na mnoha faktorech, není konkrétní pokyny a není nutně za všech okolností. Pokud je výkon velmi důležitý, je nejlepší způsob, jak určit, který typ kolekce použít k měření výkonu na základě reprezentativní konfiguraci počítače a zátěže. Tento dokument se vyskytují následující termíny:  
  
 *Scénář čistě producent – příjemce*  
 Jakékoli dané vlákno je přidání nebo odebrání elementů, ale ne obojí.  
  
 *Scénář smíšené producent – příjemce*  
 Jakékoli dané vlákno přidání i odebrání prvků.  
  
 *Zrychlení*  
 Rychlejší vylepšením výkonu vzhledem k jinému typu ve stejné scénáře.  
  
 *Škálovatelnost*  
 Zvýšení výkonu, který je přímo úměrný počtu jader v počítači. Algoritmus, která se škáluje provádí rychleji v osmi jádry, než na dvě jádra.  
  
## <a name="concurrentqueuet-vs-queuet"></a>ConcurrentQueue(T) vs. Queue(T)  
 V čistě producent – příjemce scénářích, kde je doba zpracování pro každý prvek velmi malý (pár pokynů), pak <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> může nabídnout zvýšení výkonu výhody oproti <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> , který má externí zámek. V tomto scénáři <xref:System.Collections.Concurrent.ConcurrentQueue%601> poskytuje nejlepší výkon, když do fronty jedno vyhrazené vlákno a jedno vyhrazené vlákno se vyřazuje z fronty. Pokud není vynucují toto pravidlo potom <xref:System.Collections.Generic.Queue%601> může dokonce provádět mírně rychlejší než <xref:System.Collections.Concurrent.ConcurrentQueue%601> v počítačích s více jádry.  
  
 Při zpracování trvá přibližně 500 FLOPS (operací s pohyblivou čárkou) nebo víc, potom pravidla dvě vlákna se nedá použít u <xref:System.Collections.Concurrent.ConcurrentQueue%601>, která má velmi dobré škálovatelnost. <xref:System.Collections.Generic.Queue%601> nejsou adekvátní i v tomto scénáři.  
  
 Ve smíšených producent – příjemce scénářích, kdy je velmi malý, čas zpracování <xref:System.Collections.Generic.Queue%601> , který má externí zámku škáluje líp, než <xref:System.Collections.Concurrent.ConcurrentQueue%601> nepodporuje. Ale pokud je doba zpracování přibližně 500 FLOPS nebo informace, pak bude <xref:System.Collections.Concurrent.ConcurrentQueue%601> poskytuje lepší škálovatelnost.  
  
## <a name="concurrentstack-vs-stack"></a>ConcurrentStack vs. Rámec  
 V čistě producent – příjemce scénáře, kdy doba zpracování je velmi malý, pak <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType> a <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType> , který má externí zámku provede pravděpodobně o stejným způsobem pracovat s jedním vláknem vyhrazeným a jedno vyhrazené vlákno operace. Nicméně jako počtem vláken, oba typy zpomalit z důvodu zvýšeného počtu kolizí a <xref:System.Collections.Generic.Stack%601> můžou provádět lepší než <xref:System.Collections.Concurrent.ConcurrentStack%601>. Pokud je doba zpracování přibližně 500 FLOPS nebo další, pak oba typy škálování o stejná sazba.  
  
 V kombinovaném producent – příjemce scénáře, <xref:System.Collections.Concurrent.ConcurrentStack%601> je rychlejší pro malé a velké úlohy.  
  
 Použití <xref:System.Collections.Concurrent.ConcurrentStack%601.PushRange%2A> a <xref:System.Collections.Concurrent.ConcurrentStack%601.TryPopRange%2A> může výrazně zrychlit čas přístupu.  
  
## <a name="concurrentdictionary-vs-dictionary"></a>ConcurrentDictionary vs. Slovník  
 Obecně platí, <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> ve všech scénářích, kde jsou přidávání a aktualizaci klíče nebo hodnoty z více vláken současně. Ve scénářích, které obsahují časté aktualizace a relativně malý počet čtení <xref:System.Collections.Concurrent.ConcurrentDictionary%602> obecně nabízí mírné výhody. Ve scénářích, které obsahují mnoho čtení a mnoho aktualizací <xref:System.Collections.Concurrent.ConcurrentDictionary%602> obecně je výrazně rychlejší na počítačích, které mít libovolný počet jader.  
  
 Ve scénářích, které obsahují časté aktualizace, můžete zvýšit stupeň souběžnosti v <xref:System.Collections.Concurrent.ConcurrentDictionary%602> a pak změřit, zda výkon zvýší na počítače, které mají víc jader. Pokud změníte úroveň souběžnosti, vyhněte se globální operace co největší míře.  
  
 Při čtení pouze klíče nebo hodnoty, <xref:System.Collections.Generic.Dictionary%602> je rychlejší, protože není nutná žádná synchronizace, pokud slovník není právě upravuje žádného vlákna.  
  
## <a name="concurrentbag"></a>Objekt ConcurrentBag použil  
 V případech čistě producent – příjemce <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> bude pravděpodobně pracovat pomaleji než u jiných typů souběžných kolekcích.  
  
 V kombinovaném producent – příjemce scénáře, <xref:System.Collections.Concurrent.ConcurrentBag%601> je obvykle mnohem rychlejší a větší škálovatelnost než jakýkoli jiný typ souběžných kolekcích pro malé i velké úlohy.  
  
## <a name="blockingcollection"></a>BlockingCollection  
 Když jsou povinné, sémantika ohraničování a blokování <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> bude pravděpodobně rychlejší než všechny vlastní implementaci. Podporuje také bohaté zrušení, výčet a zpracování výjimek.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
- [Kolekce se zabezpečenými vlákny](../../../../docs/standard/collections/thread-safe/index.md)  
- [Paralelní programování](../../../../docs/standard/parallel-programming/index.md)
