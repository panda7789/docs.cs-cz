---
title: Spravovaný fond vláken
description: Informace o fondu vláken .NET, který poskytuje pracovní vlákna na pozadí
ms.date: 08/02/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- thread pooling [.NET]
- thread pools [.NET]
- threading [.NET], thread pool
- threading [.NET], pooling
ms.assetid: 2be05b06-a42e-4c9d-a739-96c21d673927
ms.openlocfilehash: 2671ce7c9721b15de8a3805da27040e973a62804
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400629"
---
# <a name="the-managed-thread-pool"></a>Spravovaný fond vláken

Třída <xref:System.Threading.ThreadPool?displayProperty=nameWithType> poskytuje vaší aplikaci fond pracovních podprocesů, které jsou spravovány systémem, což vám umožní soustředit se na úlohy aplikace spíše než na správu vláken. Pokud máte krátké úkoly, které vyžadují zpracování na pozadí, fond spravovaných vláken je snadný způsob, jak využít výhod více vláken. Použití fondu vláken je výrazně jednodušší v rámci 4 <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> novější, protože můžete vytvořit a objekty, které provádějí asynchronní úlohy ve vláknech fondu vláken.  
  
.NET používá vlákna fondu vláken pro mnoho účelů, včetně operací [paralelní knihovny úloh (TPL),](../parallel-programming/task-parallel-library-tpl.md) asynchronní vstupně-v.o dokončení, <xref:System.Net?displayProperty=nameWithType> [časovač](timers.md) zpětné volání, registrované operace čekání, volání asynchronní metody pomocí delegátů a připojení soketu.  

## <a name="thread-pool-characteristics"></a>Charakteristiky fondu vláken

Vlákna fondu vláken jsou vlákna [na pozadí.](foreground-and-background-threads.md) Každé vlákno používá výchozí velikost zásobníku, běží na výchozí prioritu a je v apartment s více vlákny. Jakmile vlákno ve fondu vláken dokončí svůj úkol, vrátí se do fronty čekajících vláken. Od této chvíle může být znovu použit. Toto opakované použití umožňuje aplikacím vyhnout se nákladům na vytvoření nového vlákna pro každý úkol.
  
Na každý proces existuje pouze jeden fond vláken.  
  
### <a name="exceptions-in-thread-pool-threads"></a>Výjimky ve vláknech fondu vláken

Neošetřené výjimky ve vláknech fondu vláken ukončí proces. Existují tři výjimky z tohoto pravidla:  
  
- A <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> je vyvolána ve vlákně fondu vláken, protože <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> byl volán.  
- A <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> je vyvolána ve vlákně fondu vláken, protože doména aplikace je uvolněna.  
- Běžný jazyk runtime nebo hostitelský proces ukončí vlákno.  
  
Další informace naleznete [v tématu Výjimky ve spravovaných vláknech](exceptions-in-managed-threads.md).  
  
### <a name="maximum-number-of-thread-pool-threads"></a>Maximální počet vláken fondu vláken

Počet operací, které mohou být zařazeny do fondu vláken, je omezen pouze dostupnou pamětí. Fond vláken však omezuje počet podprocesů, které mohou být aktivní v procesu současně. Pokud jsou všechna vlákna fondu vláken zaneprázdněna, další pracovní položky jsou zařazeny do fronty, dokud nebudou k dispozici vlákna k jejich spuštění. Počínaje rozhraním .NET Framework 4 závisí výchozí velikost fondu vláken pro proces na několika faktorech, jako je například velikost virtuálního adresového prostoru. Proces může volat <xref:System.Threading.ThreadPool.GetMaxThreads%2A?displayProperty=nameWithType> metodu k určení počtu podprocesů.  
  
Můžete řídit maximální počet podprocesů pomocí <xref:System.Threading.ThreadPool.GetMaxThreads%2A?displayProperty=nameWithType> <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> metody a.  

> [!NOTE]
> Kód, který je hostitelem běžného jazyka [`ICorThreadpool::CorSetMaxThreads`](../../framework/unmanaged-api/hosting/icorthreadpool-corsetmaxthreads-method.md) runtime můžete nastavit velikost pomocí metody.  
  
### <a name="thread-pool-minimums"></a>Minima fondu vláken

Fond vláken poskytuje nová pracovní vlákna nebo vstupně-tova dokončení podprocesů na vyžádání, dokud nedosáhne zadaného minima pro každou kategorii. Metodu <xref:System.Threading.ThreadPool.GetMinThreads%2A?displayProperty=nameWithType> můžete použít k získání těchto minimálních hodnot.  
  
> [!NOTE]
> Pokud je poptávka nízká, skutečný počet vláken fondu vláken může klesnout pod minimální hodnoty.  
  
Po dosažení minima fondu vláken můžete vytvořit další vlákna nebo počkat, až některé úkoly dokončit. Počínaje rozhraním .NET Framework 4 vytvoří fond vláken a zničí pracovní vlákna za účelem optimalizace propustnost, která je definována jako počet úkolů, které se dokončí za jednotku času. Příliš málo podprocesů nemusí optimálně využívat dostupné prostředky, zatímco příliš mnoho podprocesů může zvýšit konflikty prostředků.  
  
> [!CAUTION]
> Metodu <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> můžete použít ke zvýšení minimálního počtu nečinných podprocesů. Zbytečně zvýšení těchto hodnot však může způsobit problémy s výkonem. Pokud příliš mnoho úkolů spustit ve stejnou dobu, všechny z nich se může zdát být pomalé. Ve většině případů bude fond vláken fungovat lépe s vlastním algoritmem pro přidělování vláken.  

## <a name="using-the-thread-pool"></a>Použití fondu vláken

Počínaje rozhraním .NET Framework 4 je nejjednodušším způsobem použití fondu vláken použití [paralelní knihovny úloh (TPL).](../parallel-programming/task-parallel-library-tpl.md) Ve výchozím nastavení typy <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> TPL jako a používají vlákna fondu vláken ke spuštění úloh.

Fond vláken můžete také použít <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> voláním ze [`ICorThreadpool::CorQueueUserWorkItem`](../../framework/unmanaged-api/hosting/icorthreadpool-corqueueuserworkitem-method.md) spravovaného kódu (nebo <xref:System.Threading.WaitCallback?displayProperty=nameWithType> z nespravovaného kódu) a předáním delegáta představujícího metodu, která provádí úlohu.

Dalším způsobem, jak použít fond vláken je fronty pracovních položek, <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> které souvisejí <xref:System.Threading.WaitHandle?displayProperty=nameWithType> s operace čekání pomocí metody a předání, které <xref:System.Threading.WaitOrTimerCallback?displayProperty=nameWithType> při signalizaci nebo při vynechání časového režimu volá metodu reprezentovanou delegátem. Vlákna fondu vláken se používají k vyvolání metod zpětného volání.  

Příklady najdete na odkazovaných stránkách rozhraní API.
  
## <a name="skipping-security-checks"></a>Přeskočení bezpečnostních kontrol

Fond vláken také <xref:System.Threading.ThreadPool.UnsafeQueueUserWorkItem%2A?displayProperty=nameWithType> poskytuje <xref:System.Threading.ThreadPool.UnsafeRegisterWaitForSingleObject%2A?displayProperty=nameWithType> a metody. Tyto metody použijte pouze v případě, že jste si jisti, že zásobník volajícího je irelevantní pro všechny kontroly zabezpečení provedené během provádění úlohy ve frontě. <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType>a <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> oba zachytit zásobníku volajícího, který je sloučen do zásobníku podprocesu fondu vláken, když vlákno začne provádět úlohu. Pokud je vyžadována kontrola zabezpečení, musí být zkontrolován celý zásobník. I když kontrola poskytuje bezpečnost, má také náklady na výkon.  

## <a name="when-not-to-use-thread-pool-threads"></a>Pokud nelze použít vlákna fondu vláken

Existuje několik scénářů, ve kterých je vhodné vytvořit a spravovat vlastní vlákna namísto použití vláken fondu vláken:  
  
- Vyžadujete vlákno v popředí.  
- Chcete-li mít určitou prioritu, potřebujete vlákno.  
- Máte úkoly, které způsobují vlákno blokovat po dlouhou dobu. Fond vláken má maximální počet vláken, takže velký počet blokovaných vláken fondu vláken může zabránit spuštění úloh.  
- Musíte umístit nitě do bytu s jedním závitem. Všechny <xref:System.Threading.ThreadPool> nitě jsou v bytě s více závity.  
- Musíte mít stabilní identitu přidruženou k vláknu nebo vyhradit vlákno úkolu.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Threading.ThreadPool?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>
- [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md)
- [Postupy: Vrácení hodnoty z úlohy](../parallel-programming/how-to-return-a-value-from-a-task.md)
- [Objekty a prvky zřetězení](threading-objects-and-features.md)
- [Vlákna a dělení na vlákna](threads-and-threading.md)
- [Asynchronní I/O soubory](../io/asynchronous-file-i-o.md)
- [Časovače](timers.md)
