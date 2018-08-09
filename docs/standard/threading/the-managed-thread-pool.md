---
title: Spravovaný fond vláken
description: Další informace o fondu vláken .NET, která poskytuje pracovních vláken na pozadí
ms.date: 08/02/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- thread pooling [.NET]
- thread pools [.NET]
- threading [.NET], thread pool
- threading [.NET], pooling
ms.assetid: 2be05b06-a42e-4c9d-a739-96c21d673927
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3894229ff5561e50d42a36f576a89ee7bf01c067
ms.sourcegitcommit: 78bcb629abdbdbde0e295b4e81f350a477864aba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "33592415"
---
# <a name="the-managed-thread-pool"></a>Spravovaný fond vláken

<xref:System.Threading.ThreadPool?displayProperty=nameWithType> Třída poskytuje aplikaci fondu pracovních vláken, která jsou spravována systému, umožňuje soustředit se na aplikace úkoly spíše než vlákna správy. Pokud máte krátký úlohy, které vyžadují zpracování na pozadí, spravovaný fond vláken je snadný způsob, jak využít výhod více vláken. Použití fondu vláken je výrazně jednodušší v rozhraní Framework 4 a novější, protože můžete vytvořit <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> objekty, které provádět asynchronní úlohy ve vlákně fondu vláken.  
  
.NET pomocí vláken fondu vláken pro celou řadu účelů, včetně [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md) činnost, dokončení asynchronních vstupně-výstupních operací, [časovače](timers.md) zpětná volání, zaregistrovaný počkejte operace, asynchronní metody použití delegátů, volá a <xref:System.Net?displayProperty=nameWithType> soketu připojení.  

## <a name="thread-pool-characteristics"></a>Vlastnosti fondu vláken

Vláken fondu vláken se [pozadí](foreground-and-background-threads.md) vlákna. Každé vlákno používá výchozí velikost zásobníku, běží na výchozí prioritu a je v apartmentu s více vlákny. Po dokončení svých úkolů vláken ve fondu vláken se vrátí do fronty čekajících vláken. V tomto okamžiku můžete použít opakovaně. Použití umožňuje aplikacím, aby náklady na vytvoření nové vlákno pro každý úkol.
  
Existuje pouze jedno vlákno sdružení za procesu.  
  
### <a name="exceptions-in-thread-pool-threads"></a>Výjimky v vláken fondu vláken

Proces ukončit neošetřenými výjimkami v vláken fondu vláken. Existují tři výjimkou tohoto pravidla:  
  
- A <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> je vyvolána ve vláknu fondu vláken, protože <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> byla volána.  
- A <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> je vyvolána ve vláknu fondu vláken, protože probíhá uvolnění domény aplikace.  
- Modul common language runtime nebo hostitelský proces ukončí vlákno.  
  
Další informace najdete v tématu [výjimky ve spravovaných vláknech](exceptions-in-managed-threads.md).  
  
### <a name="maximum-number-of-thread-pool-threads"></a>Maximální počet vláken fondu vláken

Počet operací, které můžete ve frontě fondu vláken je omezen pouze dostupnou paměť. Fondu vláken však omezuje počet vláken, která může být současně aktivní v procesu. Pokud jsou všechny vláken fondu vláken zaneprázdněný, další pracovní položky se zařadí do fronty až do vlákna ke spuštění je k dispozici. Od verze rozhraní .NET Framework 4, výchozí velikost fondu vláken pro proces závisí na několika faktorech, jako je například velikost virtuálního adresového prostoru. Proces můžete volat <xref:System.Threading.ThreadPool.GetMaxThreads%2A?displayProperty=nameWithType> metodou ke zjištění počtu vláken.  
  
Maximální počet vláken můžete řídit pomocí <xref:System.Threading.ThreadPool.GetMaxThreads%2A?displayProperty=nameWithType> a <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> metody.  

> [!NOTE]
> Kód, který je hostitelem modulu common language runtime můžete nastavit pomocí velikosti [ `ICorThreadpool::CorSetMaxThreads` ](../../framework/unmanaged-api/hosting/icorthreadpool-corsetmaxthreads-method.md) metody.  
  
### <a name="thread-pool-minimums"></a>Minimálních fondu vláken

Fondu vláken poskytuje nové pracovní vlákna nebo vlákna dokončení vstupně-výstupních operací na vyžádání, dokud nedosáhne zadané minimum pro každou kategorii. Můžete použít <xref:System.Threading.ThreadPool.GetMinThreads%2A?displayProperty=nameWithType> metoda a získat tyto minimální hodnoty.  
  
> [!NOTE]
> Při nízké poptávce skutečný počet vláken fondu vláken může klesnou pod minimální hodnoty.  
  
Po dosažení minimální fondu vláken můžete vytvořit další vlákna nebo počkejte na dokončení některých úkolů. Od verze rozhraní .NET Framework 4, fondu vláken vytvoří a odstraní pracovní vlákna k optimalizaci propustnosti, který je definován jako řadu úloh, které dokončí za časovou jednotku. Moc malý počet vláken nemusí optimální využívání dostupných prostředků, zkontrolujte, že příliš mnoho vláken může zlepšit kolize prostředků.  
  
> [!CAUTION]
> Můžete použít <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> způsob zvýšení minimální počet nečinných vláken. Zbytečně zvýšení tyto hodnoty však může způsobit problémy s výkonem. Pokud ve stejnou dobu spuštění příliš mnoho úloh, všechny z nich může zobrazit pomalé. Ve většině případů fondu vláken se líp fungovat se vlastní algoritmus pro přidělování vlákna.  

## <a name="using-the-thread-pool"></a>Použití fondu vláken

Od verze rozhraní .NET Framework 4, nejjednodušší způsob použití fondu vláken je použít [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md). Ve výchozím nastavení, jako jsou typy TPL <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> spouštění úloh pomocí vláken fondu vláken.

Můžete použít také fondu vláken voláním <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> ze spravovaného kódu (nebo [ `ICorThreadpool::CorQueueUserWorkItem` ](../../framework/unmanaged-api/hosting/icorthreadpool-corqueueuserworkitem-method.md) z nespravovaného kódu) a předávání <xref:System.Threading.WaitCallback?displayProperty=nameWithType> delegovat představující metodu, která provede úkol.

Jiný způsob použití fondu vláken je zařadit do fronty pracovních položek, které se vztahují k operace čekání pomocí <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> metoda a předávání <xref:System.Threading.WaitHandle?displayProperty=nameWithType> , při signalizován nebo vypršel časový limit, volá metodu reprezentovanou <xref:System.Threading.WaitOrTimerCallback?displayProperty=nameWithType> delegovat. Vláken fondu vláken se používají k vyvolání metody zpětného volání.  

Příklady zkontrolujte na odkazovaných stránkách rozhraní API.
  
## <a name="skipping-security-checks"></a>Přeskočení kontroly zabezpečení

Také poskytuje fondu vláken <xref:System.Threading.ThreadPool.UnsafeQueueUserWorkItem%2A?displayProperty=nameWithType> a <xref:System.Threading.ThreadPool.UnsafeRegisterWaitForSingleObject%2A?displayProperty=nameWithType> metody. Tyto metody používáte pouze v případě, že jste si jisti, že je zásobníku volajícího, jež se žádné bezpečnostní kontroly během provádění úlohy ve frontě. <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> a <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> i zachytit zásobníku volajícího, který je sloučen do zásobníku vláknu fondu vláken, když vlákno začne spustit úlohu. Pokud kontrola zabezpečení se požaduje, musí být kontrolované celý zásobník. I když je kontrola poskytuje zabezpečení, má také nákladů na výkon.  

## <a name="when-not-to-use-thread-pool-threads"></a>Kdy nepoužívat vláken fondu vláken

Existuje několik scénářů, ve kterých je vhodná k vytváření a správě vlastních vláken namísto používání vláken fondu vláken:  
  
- Vyžadujete, aby vlákno na popředí.  
- Vyžadujete, aby vlákno s konkrétní prioritou.  
- Máte úkoly, které způsobí vlákna a blokovat dlouhou dobu. Fondu vláken má maximální počet vláken, takže Velký počet blokovaných vláken fondu vláken může zabránit úloh spouští.  
- Je potřeba uvést vlákna do jednovláknový apartment. Všechny <xref:System.Threading.ThreadPool> jsou vlákna v apartmentu s více vlákny.  
- Musíte mít stabilní identity přidružené vlákno nebo vlákno vyhradit pro úlohu.  
  
## <a name="see-also"></a>Viz také:

 <xref:System.Threading.ThreadPool?displayProperty=nameWithType>  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>  
 <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>  
 [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md)  
 [Postupy: Vrácení hodnoty z úlohy](../parallel-programming/how-to-return-a-value-from-a-task.md)  
 [Funkce a objekty dělení na vlákna](threading-objects-and-features.md)  
 [Vlákna a dělení na vlákna](threads-and-threading.md)  
 [Asynchronní vstupně-výstupní operace se soubory](../io/asynchronous-file-i-o.md)  
 [Časovače](timers.md)  
