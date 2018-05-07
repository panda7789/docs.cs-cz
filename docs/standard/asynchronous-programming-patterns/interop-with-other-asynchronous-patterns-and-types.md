---
title: Interoperabilita s jinými asynchronními vzory a typy
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: f120a5d9-933b-4d1d-acb6-f034a57c3749
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c92725a43e43877488ff9ba93007530c794dd290
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a>Interoperabilita s jinými asynchronními vzory a typy
Rozhraní .NET Framework 1.0 zavedená <xref:System.IAsyncResult> vzoru známé jako [asynchronní programování modelu (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md), nebo `Begin/End` vzor.  Rozhraní .NET Framework 2.0, přidat [na základě událostí asynchronní vzor (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).  Od verze rozhraní .NET Framework 4 [založený na úlohách asynchronní vzor (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) nahrazuje APM a EAP, ale umožňuje snadno vytvářet rutiny migraci ze starších vzory.  
  
 V tomto tématu:  
  
-   [Úlohy a APM](#APM) ([z APM můžete na](#ApmToTap) nebo [z klepněte sem a můžete APM](#TapToApm))  
  
-   [Úlohy a protokolu EAP](#EAP)  
  
-   [Úlohy a obslužné rutiny čekání](#WaitHandles) ([z obslužné rutiny čekání na klepněte na](#WHToTap) nebo [z klepněte sem a můžete obslužné rutiny čekání](#TapToWH))  
  
<a name="APM"></a>   
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a>Úlohy a Model asynchronního programování (APM)  
  
<a name="ApmToTap"></a>   
### <a name="from-apm-to-tap"></a>Z APM můžete na  
 Protože [asynchronní programování modelu (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) vzor je velmi strukturovaných, je poměrně snadné sestavení obálku vystavit jako implementace klepněte na implementaci APM. V faktu, rozhraní .NET Framework, počínaje [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], obsahuje pomocné rutiny ve formě <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> přetížení metody zajistit tento překlad.  
  
 Vezměte v úvahu <xref:System.IO.Stream> třídy a jeho <xref:System.IO.Stream.BeginRead%2A> a <xref:System.IO.Stream.EndRead%2A> metody, které představuje protějšku APM synchronní <xref:System.IO.Stream.Read%2A> metoda:  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 Můžete použít <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> metody k implementaci klepněte na obálku pro tuto operaci následujícím způsobem:  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 Tato implementace je podobný následujícímu:  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
<a name="TapToApm"></a>   
### <a name="from-tap-to-apm"></a>Z klepněte sem a můžete APM  
 Pokud vaše stávající infrastruktury očekává vzoru APM, budete chtít taky trvat klepněte na implementaci a použít ho, kde je očekávána implementace APM.  Vzhledem k tomu, že úkoly lze vytvářet a třída <xref:System.Threading.Tasks.Task> implementuje třídu <xref:System.IAsyncResult>, můžete použít jednoduchou pomocnou funkci. Následující kód používá rozšíření <xref:System.Threading.Tasks.Task%601> třídy, ale můžete použít skoro stejné funkce pro neobecný úlohy.  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 Nyní Představte si případ, kdy máte následující implementaci klepněte na:  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 a chcete poskytovat tato implementace APM:  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 Následující příklad ukazuje jeden migrace APM:  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
<a name="EAP"></a>   
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a>Úlohy a asynchronní vzor (EAP) založených na událostech  
 Zabalení [na základě událostí asynchronní vzor (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) implementace je složitější než zabalení APM vzoru, protože vzoru EAP má menší struktury než vzoru APM a další variace.  K předvedení, se zabalí následující kód `DownloadStringAsync` metoda.  `DownloadStringAsync` přijímá identifikátor URI, vyvolá `DownloadProgressChanged` události při stahování za účelem hlášení více statistiky na průběh a vyvolá `DownloadStringCompleted` událost, pokud se provádí.  Konečný výsledek je řetězec, který obsahuje obsah na stránce na zadaný identifikátor URI.  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
<a name="WaitHandles"></a>   
## <a name="tasks-and-wait-handles"></a>Úlohy a obslužné rutiny čekání  
  
<a name="WHToTap"></a>   
### <a name="from-wait-handles-to-tap"></a>Z obslužné rutiny čekání na klepněte na  
 I když obslužné rutiny čekání nebudete implementovat asynchronní vzor, pokročilé vývojáři mohou použít <xref:System.Threading.WaitHandle> třídy a <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> metody pro asynchronní oznámení, když je nastaven popisovač čekání.  Může obtékat <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> způsob povolení založený na úlohách alternativu, která umožňuje všechny synchronní čekání na popisovač čekání:  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 Pomocí této metody můžete použít existující <xref:System.Threading.WaitHandle> implementace v asynchronních metod.  Například pokud chcete omezit počet asynchronních operací, které jsou prováděny v jakémkoli čase, můžete využít semafor ( <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> objekt).  Můžete omezit na *N* počet operací, které běží souběžně podle inicializace semafor počet *N*, čekání na semaforu vždy, když chcete provést operace a uvolněním semafor, když jste hotovi s operace:  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 Můžete také vytvořit asynchronní semafor, který není závislý na obslužné rutiny čekání a místo toho pracuje úplně úlohy. K tomuto účelu můžete použít techniky, jako jsou popsané v [použití asynchronního vzoru založeného na úloze](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) pro vytvoření datové struktury na <xref:System.Threading.Tasks.Task>.  
  
<a name="TapToWH"></a>   
### <a name="from-tap-to-wait-handles"></a>Z klepněte sem a můžete obslužné rutiny čekání  
 Jak už jsme zmínili, <xref:System.Threading.Tasks.Task> třída implementuje <xref:System.IAsyncResult>, a že implementace zveřejňuje <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> vlastnost, která vrací popisovač čekání, které bude nastaveno při <xref:System.Threading.Tasks.Task> dokončení.  Můžete získat <xref:System.Threading.WaitHandle> pro <xref:System.Threading.Tasks.Task> následujícím způsobem:  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a>Viz také  
 [Asynchronní vzor založený na úlohách (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 [Implementace asynchronního vzoru založeného na úlohách](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)  
 [Použití asynchronního vzoru založeného na úlohách](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
