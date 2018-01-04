---
title: "Kdy použít kolekci s bezpečnými vlákny"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: thread-safe collections, when to upgrade
ms.assetid: a9babe97-e457-4ff3-b528-a1bc940d5320
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 61444afd5afe52cbcb0f64074ec4479bd6252358
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="when-to-use-a-thread-safe-collection"></a>Kdy použít kolekci s bezpečnými vlákny
[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] Zavádí pět nové typy kolekcí, které jsou speciálně určené pro podporu Vícevláknová přidávat a odebírat operace. K dosažení vláken, použít tyto nové typy různé druhy efektivní zamykání a mechanismy zámku bez synchronizace. Synchronizace přidá režie pro operaci. Množství práce, závisí na typ synchronizace, která se používá, druh operace, které se provádí a dalších faktorů, jako je počet vláken, které se pokoušíte získat přístup ke kolekci současně.  
  
 V některých scénářích synchronizace režie je nepatrné a umožňuje Vícevláknová typ výrazně rychlejší a škálovat mnohem lepší, než ekvivalentní není bezpečná pro přístup z více vláken při ochraně externí zámek. V jiných scénářích může způsobit nároky na typ bezpečného přístupu k provedení a škálování o stejný nebo i pomaleji než verze externě uzamčen, není bezpečná pro přístup z více vláken typu.  
  
 Následující části obsahují obecné pokyny o tom, kdy použít kolekci s bezpečnými vlákny versus ekvivalentem není bezpečná pro přístup z více vláken, který má zadaný uživatelem zámek čtení a zápisu operace. Protože výkon se může lišit v závislosti na mnoha faktorech, není konkrétní pokyny a není nutně platné za všech okolností. Pokud výkon je velmi důležité, je nejlepší způsob, jak určit typů kolekce, které se mají použít k měření výkonu na základě reprezentativní konfiguraci počítače a zatížení. Tento dokument používá následující podmínky:  
  
 *Scénář čistý producent – příjemce*  
 Jakékoli dané vlákno je buď přidáním nebo odebráním elementů, ale ne obojí.  
  
 *Scénář smíšený producent – příjemce*  
 Jakékoli dané vlákno přidání i odebrání elementy.  
  
 *Zrychlení*  
 Rychlejší algoritmické výkonu vzhledem k jinému typu stejný scénář.  
  
 *Škálovatelnost*  
 Zvýšení výkonu, který je přímo úměrná počtu jader v počítači. Algoritmus, který přizpůsobí provede osm jader na rychlejší než u dvě jádra.  
  
## <a name="concurrentqueuet-vs-queuet"></a>ConcurrentQueue(T) vs. Queue(T)  
 V čistě producent – příjemce scénářích, kde je doba zpracování pro každý prvek velmi malé (pár pokynů), pak <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> může nabídnout menší výkony oproti <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> má externí zámek. V tomto scénáři <xref:System.Collections.Concurrent.ConcurrentQueue%601> poskytuje nejlepší výkon, když je služba Řízení front jedním vláknem a jedním vláknem vyřazuje z fronty. Pokud toto pravidlo, pak nevynutíte <xref:System.Collections.Generic.Queue%601> může provádět i mírně rychlejší než <xref:System.Collections.Concurrent.ConcurrentQueue%601> na počítačích, které mají víc jader.  
  
 Pokud doba zpracování je přibližně 500 FLOPS (operací s pohyblivou čárkou) nebo další, pak pravidlo dvou vláken nevztahuje na <xref:System.Collections.Concurrent.ConcurrentQueue%601>, který pak má velmi dobré škálovatelnost. <xref:System.Collections.Generic.Queue%601>nejsou adekvátní i v tomto scénáři.  
  
 Ve smíšených producent – příjemce scénářích, kdy je velmi malý, bude čas zpracování <xref:System.Collections.Generic.Queue%601> má externí zámek škáluje líp, než <xref:System.Collections.Concurrent.ConcurrentQueue%601> nepodporuje. Ale pokud je doba zpracování přibližně 500 FLOPS nebo více, pak se <xref:System.Collections.Concurrent.ConcurrentQueue%601> poskytuje lepší škálovatelnost.  
  
## <a name="concurrentstack-vs-stack"></a>ConcurrentStack vs. Rámec  
 V čistě producent – příjemce scénáře, kdy je čas zpracování velmi malý, pak <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType> a <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType> má externí zámek provede pravděpodobně o totožný s jedním vláknem vyhrazeným operace vložení a jeden vyhrazený vláknem. Ale, jako je počet vláken zvyšuje oba typy zpomalit kvůli rostoucím sporům, a <xref:System.Collections.Generic.Stack%601> by mohl poskytovat lepší, než <xref:System.Collections.Concurrent.ConcurrentStack%601>. Pokud je doba zpracování přibližně 500 FLOPS nebo více, pak oba typy škálování v o stejný kurz.  
  
 Ve smíšených producent – příjemce scénářích, <xref:System.Collections.Concurrent.ConcurrentStack%601> je rychlejší pro malé a velké zatížení.  
  
 Použití <xref:System.Collections.Concurrent.ConcurrentStack%601.PushRange%2A> a <xref:System.Collections.Concurrent.ConcurrentStack%601.TryPopRange%2A> může výrazně zrychlit čas přístupu.  
  
## <a name="concurrentdictionary-vs-dictionary"></a>ConcurrentDictionary vs. Slovník  
 Obecně platí, používat <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> v žádném scénáři, kde jsou přidat a aktualizovat klíče nebo hodnoty z více vláken současně. Ve scénářích, které obsahují časté aktualizace a relativně malý počet čtení <xref:System.Collections.Concurrent.ConcurrentDictionary%602> obecně nabízí mírné výhody. Ve scénářích, které obsahují mnoho čtení a mnoho aktualizací <xref:System.Collections.Concurrent.ConcurrentDictionary%602> obecně je výrazně rychlejší v počítačích, které mají libovolný počet jader.  
  
 Ve scénářích, které obsahují časté aktualizace, můžete zvýšit stupeň souběžnosti v <xref:System.Collections.Concurrent.ConcurrentDictionary%602> a pak měřit zda výkon zvýšil na počítačích, které mají více jader. Pokud změníte úroveň souběžnosti, vyhněte se co nejvíce globální operace.  
  
 Při čtení pouze klíče nebo hodnoty, <xref:System.Collections.Generic.Dictionary%602> je rychlejší, protože pokud slovníku není upravován žádné podprocesy není nutná žádná synchronizace.  
  
## <a name="concurrentbag"></a>ConcurrentBag  
 Ve scénářích čistý producent – příjemce <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> budou pravděpodobně fungovat pomaleji než jiné typy souběžných kolekcí.  
  
 Ve smíšených producent – příjemce scénářích, <xref:System.Collections.Concurrent.ConcurrentBag%601> je obvykle mnohem rychlejší a větší škálovatelnost než žádným jiným typem souběžných kolekce pro malé i velké zatížení.  
  
## <a name="blockingcollection"></a>BlockingCollection  
 Když jsou povinné, sémantika ohraničování a blokování <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> bude pravděpodobně rychlejší než jakákoli vlastní implementace. Podporuje také bohaté zrušení, výčet a výjimek.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [Kolekce se zabezpečenými vlákny](../../../../docs/standard/collections/thread-safe/index.md)  
 [Paralelní programování](../../../../docs/standard/parallel-programming/index.md)
