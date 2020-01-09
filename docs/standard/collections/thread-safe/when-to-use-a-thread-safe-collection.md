---
title: Kdy použít kolekci s bezpečnými vlákny
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, when to upgrade
ms.assetid: a9babe97-e457-4ff3-b528-a1bc940d5320
ms.openlocfilehash: 5a0abef6de9f932f44fc7e3239b98c3a27846580
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711217"
---
# <a name="when-to-use-a-thread-safe-collection"></a>Kdy použít kolekci s bezpečnými vlákny
.NET Framework 4 zavádí pět nových typů kolekcí, které jsou speciálně navržené tak, aby podporovaly operace přidávání a odebírání s více vlákny. Aby bylo možné dosáhnout bezpečnosti více vláken, tyto nové typy používají různé druhy efektivního uzamykání a synchronizačních mechanismů bez zámků. Synchronizace přidává k operaci režii. Množství režie závisí na druhu používané synchronizace, typu prováděných operací a dalších faktorech, jako je počet vláken, která se pokoušejí souběžně přistupovat ke kolekci.  
  
 V některých scénářích je režijní náklady na synchronizaci zanedbatelná a umožňuje, aby vícevláknový typ byl výrazně rychlejší a lépe škálovatelný, než je ekvivalent bez bezpečného vlákna, pokud je chráněn externím zámkem. V jiných scénářích může režie způsobit, že typ bezpečný pro přístup z více vláken provede a škáluje o stejné nebo ještě pomalejší úrovni než verze typu externě uzamčená bez možnosti bezpečného přístupu z více vláken.  
  
 V následujících částech najdete obecné pokyny k tomu, kdy použít kolekci bezpečnou pro přístup z více vláken a jejich ekvivalent bez bezpečného přístupu k vláknům, který má uživatelem poskytnutý zámek pro operace čtení a zápisu. Vzhledem k tomu, že výkon se může lišit v závislosti na mnoha faktorech, doprovodné materiály nejsou specifické a nemusí nutně platit za všech okolností. Pokud je výkon velmi důležitý, pak nejlepším způsobem určení toho, který typ kolekce použít, je měření výkonu na základě reprezentativních konfigurací počítačů a zatížení. Tento dokument používá následující výrazy:  
  
 *Scénář čistého producenta pro spotřebitele*  
 Jakékoli dané vlákno buď přidává nebo odebírá prvky, ale ne obojí.  
  
 *Smíšený scénář producent – příjemce*  
 Jakékoli dané vlákno je přidávání a odebírání prvků.  
  
 *Zrychlení*  
 Rychlejší výkon algoritmu vzhledem k jinému typu ve stejném scénáři.  
  
 *Škálovatelnost*  
 Zvýšení výkonu, které je úměrné počtu jader v počítači. Algoritmus, který se škáluje, se zrychluje na osm jader, než na dvou jádrech.  
  
## <a name="concurrentqueuet-vs-queuet"></a>ConcurrentQueue (T) vs. Queue (T)  
 V čistých scénářích producent – spotřebitel, kde je doba zpracování každého prvku velmi malá (několik pokynů), pak <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> může nabídnout mírné výhody výkonu v <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>, které mají externí zámek. V tomto scénáři <xref:System.Collections.Concurrent.ConcurrentQueue%601> vychází nejlépe v případě, že jedno vyhrazené vlákno je zařazování do fronty a jedno vyhrazené vlákno rozchází do fronty. Pokud toto pravidlo nevyberete, <xref:System.Collections.Generic.Queue%601> může dokonce fungovat mírně rychleji než <xref:System.Collections.Concurrent.ConcurrentQueue%601> na počítačích, které mají více jader.  
  
 Pokud je doba zpracování okolo 500 na světě (operace s plovoucí desetinnou čárkou) nebo více, pravidlo dvou vláken se nevztahuje na <xref:System.Collections.Concurrent.ConcurrentQueue%601>, což pak má velmi dobrou škálovatelnost. <xref:System.Collections.Generic.Queue%601> se v tomto scénáři dobře nemění.  
  
 Ve smíšených scénářích pro zákazníky, pokud je doba zpracování velmi malá, <xref:System.Collections.Generic.Queue%601>, která má externí zámek, lépe škáluje, než <xref:System.Collections.Concurrent.ConcurrentQueue%601>. Pokud je však čas zpracování okolo 500 nebo více, <xref:System.Collections.Concurrent.ConcurrentQueue%601> lépe škáluje.  
  
## <a name="concurrentstack-vs-stack"></a>Objektu ConcurrentStack vs. Stack  
 V čistých scénářích producent – spotřebitel, pokud je čas zpracování velmi malý, pak <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType> a <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType>, které mají externí zámek, pravděpodobně budou fungovat přibližně stejně jako jedno vyhrazené vlákno vložení a jedno vyhrazené vyjímáné vlákno. Vzhledem k tomu, že počet vláken se zvyšuje, oba typy zpomalují kvůli zvýšenému kolizí a <xref:System.Collections.Generic.Stack%601> můžou zlepšit <xref:System.Collections.Concurrent.ConcurrentStack%601>. Když je čas zpracování okolo 500 nebo více, pak oba typy škálují přibližně stejnou sazbu.  
  
 Ve smíšených scénářích pro spotřebitele zákazníků je <xref:System.Collections.Concurrent.ConcurrentStack%601> rychlejší pro malé i velké úlohy.  
  
 Použití <xref:System.Collections.Concurrent.ConcurrentStack%601.PushRange%2A> a <xref:System.Collections.Concurrent.ConcurrentStack%601.TryPopRange%2A> může značně zrychlit dobu přístupu.  
  
## <a name="concurrentdictionary-vs-dictionary"></a>ConcurrentDictionary vs. Dictionary  
 Obecně platí, že použijte <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> v jakémkoli scénáři, kdy přidáváte a aktualizujete klíče nebo hodnoty souběžně z více vláken. Ve scénářích, které zahrnují časté aktualizace a poměrně málo čtení, <xref:System.Collections.Concurrent.ConcurrentDictionary%602> obecně nabízí mírné výhody. Ve scénářích, které zahrnují mnoho čtení a mnoho aktualizací, je <xref:System.Collections.Concurrent.ConcurrentDictionary%602> všeobecně výrazně rychlejší na počítačích, které mají libovolný počet jader.  
  
 Ve scénářích, které zahrnují časté aktualizace, můžete zvýšit stupeň souběžnosti v <xref:System.Collections.Concurrent.ConcurrentDictionary%602> a pak změřit, abyste viděli, zda se výkon zvyšuje na počítačích s více jádry. Pokud změníte úroveň souběžnosti, vyhněte se globálním operacím co nejvíce.  
  
 Pokud čtete jenom klíč nebo hodnoty, <xref:System.Collections.Generic.Dictionary%602> je rychlejší, protože není nutná žádná synchronizace, pokud slovník neupravuje žádná vlákna.  
  
## <a name="concurrentbag"></a>ConcurrentBag  
 V čistých scénářích producent-příjemce se <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> pravděpodobně pomaleji než ostatní typy souběžných kolekcí.  
  
 Ve smíšených scénářích pro spotřebitele zákazníků je <xref:System.Collections.Concurrent.ConcurrentBag%601> všeobecně mnohem rychlejší a škálovatelnější než jakýkoli jiný typ souběžného shromažďování pro velké i malé úlohy.  
  
## <a name="blockingcollection"></a>BlockingCollection  
 Pokud jsou požadovány sémantika ohraničování a blokování, <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> pravděpodobně bude pracovat rychleji než jakákoli vlastní implementace. Podporuje také bohatou manipulaci s zrušením, výčtem a zpracováním výjimek.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Kolekce se zabezpečenými vlákny](../../../../docs/standard/collections/thread-safe/index.md)
- [Paralelní programování](../../../../docs/standard/parallel-programming/index.md)
