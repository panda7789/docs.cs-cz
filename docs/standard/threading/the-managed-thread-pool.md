---
title: Spravovaný fond vláken
description: Přečtěte si o fondu vláken .NET, který poskytuje pracovní vlákna na pozadí.
ms.date: 08/02/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- thread pooling [.NET]
- thread pools [.NET]
- threading [.NET], thread pool
- threading [.NET], pooling
ms.assetid: 2be05b06-a42e-4c9d-a739-96c21d673927
ms.openlocfilehash: 2671ce7c9721b15de8a3805da27040e973a62804
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127527"
---
# <a name="the-managed-thread-pool"></a>Spravovaný fond vláken

Třída <xref:System.Threading.ThreadPool?displayProperty=nameWithType> poskytuje aplikaci s fondem pracovních vláken spravovaných systémem, což vám umožňuje soustředit se na úlohy aplikace, nikoli na správu vláken. Pokud máte krátké úlohy, které vyžadují zpracování na pozadí, je spravovaný fond vláken jednoduchý způsob, jak využít více vláken. Použití fondu vláken je výrazně snazší v rozhraní Framework 4 a novějším, protože můžete vytvářet <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> objekty, které provádějí asynchronní úlohy v vláknech fondu vláken.  
  
Rozhraní .NET používá vlákna fondu vláken pro mnoho účelů, včetně operací [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md) , dokončování asynchronního vstupu a výstupu, zpětných volání [časovačů](timers.md) , registrovaných operací čekání, volání asynchronní metody pomocí delegátů a <xref:System.Net?displayProperty=nameWithType>ho soketu. připojení.  

## <a name="thread-pool-characteristics"></a>Charakteristiky fondu vláken

Vlákna fondu vláken jsou vlákna na [pozadí](foreground-and-background-threads.md) . Každé vlákno používá výchozí velikost zásobníku, běží na výchozí prioritě a je v vícevláknovém objektu apartment. Jakmile vlákno ve fondu vláken dokončí svůj úkol, bude vrácen do fronty čekajících vláken. Od této chvíle se dá znovu použít. Toto opakované použití umožňuje aplikacím vyhnout se nákladům na vytvoření nového vlákna pro každý úkol.
  
Každý proces má pouze jeden fond vláken.  
  
### <a name="exceptions-in-thread-pool-threads"></a>Výjimky v vláknech fondu vláken

Neošetřené výjimky v vláknech fondu vláken ukončí proces. Toto pravidlo obsahuje tři výjimky:  
  
- <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> je vyvolána ve vlákně fondu vláken, protože byla volána <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.  
- <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> je vyvolána ve vlákně fondu vláken, protože byla uvolněna doména aplikace.  
- Modul CLR (Common Language Runtime) nebo hostitelský proces ukončí vlákno.  
  
Další informace naleznete v tématu [výjimky ve spravovaných vláknech](exceptions-in-managed-threads.md).  
  
### <a name="maximum-number-of-thread-pool-threads"></a>Maximální počet vláken fondu vláken

Počet operací, které lze zařadit do fronty ve fondu vláken, je omezen pouze dostupnou pamětí. Fond vláken ale omezuje počet vláken, která může být současně aktivní v procesu. Pokud jsou všechny podprocesy fondu vláken zaneprázdněny, jsou další pracovní položky zařazeny do fronty, dokud nebudou vlákna provedena k dispozici. Počínaje .NET Framework 4 je výchozí velikost fondu vláken pro proces závislá na několika faktorech, například na velikosti virtuálního adresního prostoru. Proces může volat metodu <xref:System.Threading.ThreadPool.GetMaxThreads%2A?displayProperty=nameWithType> k určení počtu vláken.  
  
Maximální počet vláken můžete řídit pomocí metod <xref:System.Threading.ThreadPool.GetMaxThreads%2A?displayProperty=nameWithType> a <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType>.  

> [!NOTE]
> Kód, který je hostitelem modulu CLR (Common Language Runtime), může nastavit velikost pomocí metody [`ICorThreadpool::CorSetMaxThreads`](../../framework/unmanaged-api/hosting/icorthreadpool-corsetmaxthreads-method.md) .  
  
### <a name="thread-pool-minimums"></a>Minimum fondu vláken

Fond vláken poskytuje nová pracovní vlákna nebo vstupně-výstupní vlákna na vyžádání, dokud nedosáhne zadaného minima pro každou kategorii. K získání těchto minimálních hodnot můžete použít metodu <xref:System.Threading.ThreadPool.GetMinThreads%2A?displayProperty=nameWithType>.  
  
> [!NOTE]
> Pokud je poptávka nízká, skutečný počet vláken fondu vláken může klesnout pod minimální hodnotu.  
  
Po dosažení minima může fond vláken vytvořit další vlákna nebo počkat na dokončení některých úloh. Počínaje .NET Framework 4 vytvoří fond vláken a zničí pracovní vlákna, aby bylo možné optimalizovat propustnost, která je definována jako počet úloh, které jsou dokončeny na jednotku času. Příliš málo vláken nemusí mít optimální využití dostupných prostředků, zatímco příliš mnoho vláken může zvýšit spory prostředků.  
  
> [!CAUTION]
> Pomocí metody <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> lze zvýšit minimální počet nečinných vláken. Nicméně zbytečně rostoucí tyto hodnoty mohou způsobit problémy s výkonem. Pokud je spuštěno příliš mnoho úloh současně, je možné, že jsou všechny pravděpodobně pomalé. Ve většině případů bude fond vláken lépe fungovat s vlastním algoritmem pro přidělování vláken.  

## <a name="using-the-thread-pool"></a>Použití fondu vláken

Počínaje .NET Framework 4 je nejjednodušší způsob, jak použít fond vláken, použít [úlohu Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md). Ve výchozím nastavení typy TPL jako <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> používají vlákna fondu vláken ke spouštění úloh.

Fond vláken můžete použít také voláním <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> ze spravovaného kódu (nebo [`ICorThreadpool::CorQueueUserWorkItem`](../../framework/unmanaged-api/hosting/icorthreadpool-corqueueuserworkitem-method.md) z nespravovaného kódu) a předáním <xref:System.Threading.WaitCallback?displayProperty=nameWithType> delegáta představujícího metodu, která úlohu provádí.

Dalším způsobem, jak použít fond vláken, je zařadit pracovní položky, které se vztahují k operaci čekání pomocí metody <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> a předat <xref:System.Threading.WaitHandle?displayProperty=nameWithType>, který při signalizaci nebo vypršení časového limitu volá metodu reprezentovanou <xref:System.Threading.WaitOrTimerCallback?displayProperty=nameWithType> delegátem. Vlákna fondu vláken se používají k vyvolání metod zpětného volání.  

Příklady najdete v odkazovaných stránkách rozhraní API.
  
## <a name="skipping-security-checks"></a>Přeskakuje se kontroly zabezpečení.

Fond vláken také poskytuje metody <xref:System.Threading.ThreadPool.UnsafeQueueUserWorkItem%2A?displayProperty=nameWithType> a <xref:System.Threading.ThreadPool.UnsafeRegisterWaitForSingleObject%2A?displayProperty=nameWithType>. Tyto metody použijte pouze v případě, že jste si jisti, že zásobník volajícího je nepodstatný pro žádné kontroly zabezpečení provedené během provádění úlohy ve frontě. <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> a <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> zachytávání zásobníku volajícího, který je sloučen do zásobníku vlákna fondu vláken, když vlákno spustí úlohu. Je-li vyžadováno ověření zabezpečení, je nutné zkontrolovat celý zásobník. I když kontroly poskytují bezpečnost, má také náklady na výkon.  

## <a name="when-not-to-use-thread-pool-threads"></a>Kdy nepoužívat vlákna fondu vláken

Existuje několik scénářů, ve kterých je vhodné vytvořit a spravovat vlastní vlákna namísto použití vláken fondu vláken:  
  
- Vyžadujete vlákno na popředí.  
- Vyžadujete, aby vlákno mělo určitou prioritu.  
- Máte úkoly, které způsobují, že vlákno bude po dlouhou dobu blokováno. Fond vláken má maximální počet vláken, takže velký počet blokovaných vláken fondu vláken může bránit spuštění úloh.  
- Vlákna je nutné umístit do jediného typu apartment. Všechna <xref:System.Threading.ThreadPool> vlákna jsou ve vícevláknovém objektu apartment.  
- Je nutné mít k vláknu přidruženou stabilní identitu nebo vyhradit vlákno pro úlohu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.ThreadPool?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>
- [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md)
- [Postupy: Vrácení hodnoty z úlohy](../parallel-programming/how-to-return-a-value-from-a-task.md)
- [Funkce a objekty dělení na vlákna](threading-objects-and-features.md)
- [Vlákna a dělení na vlákna](threads-and-threading.md)
- [Asynchronní vstupně-výstupní operace se soubory](../io/asynchronous-file-i-o.md)
- [Časovače](timers.md)
