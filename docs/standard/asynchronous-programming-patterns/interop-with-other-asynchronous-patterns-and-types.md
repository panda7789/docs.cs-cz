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
ms.openlocfilehash: 4f6cb2d387e3b979ed0d4407e17287fb93fa0a20
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62031210"
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a>Interoperabilita s jinými asynchronními vzory a typy
Rozhraní .NET Framework 1.0 zavedené <xref:System.IAsyncResult> vzor, jinak známé jako [asynchronního programovacího modelu (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md), nebo `Begin/End` vzor.  Přidání rozhraní .NET Framework 2.0 [události asynchronní vzor založený (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).  Od verze rozhraní .NET Framework 4 [úkolově orientovanou asynchronní vzor (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) nahrazuje funkce APM a protokolu EAP, ale umožňuje snadno vytvářet migraci rutin z předchozích vzory.  
  
 V tomto tématu:  
  
- [Úlohy a APM](#APM) ([z APM klepnutím](#ApmToTap) nebo [z klepnutím APM](#TapToApm))  
  
- [Úlohy a protokolu EAP](#EAP)  
  
- [Úkoly a obslužné rutiny čekání](#WaitHandles) ([z obslužné rutiny čekání klepnutím](#WHToTap) nebo [z klepněte sem a můžete obslužné rutiny čekání](#TapToWH))  
  
<a name="APM"></a>   
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a>Úlohy a Model asynchronního programování (APM)  
  
<a name="ApmToTap"></a>   
### <a name="from-apm-to-tap"></a>Z APM klepnutím  
 Vzhledem k tomu, [asynchronního programovacího modelu (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) vzor je velmi strukturovaných, je poměrně snadné sestavení obálky vystavit jako implementace TAP implementaci APM. Ve skutečnosti, rozhraní .NET Framework počínaje [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], obsahuje pomocné rutiny v podobě <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> přetížení metody k poskytování tohoto převodu.  
  
 Vezměte v úvahu <xref:System.IO.Stream> třídy a jeho <xref:System.IO.Stream.BeginRead%2A> a <xref:System.IO.Stream.EndRead%2A> metody, které představují protějšek APM synchronní <xref:System.IO.Stream.Read%2A> metody:  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 Můžete použít <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> metody k implementaci klepněte na obálku pro tuto operaci následujícím způsobem:  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 Tato implementace se podobá této:  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
<a name="TapToApm"></a>   
### <a name="from-tap-to-apm"></a>Z klepnutím APM  
 Pokud vaší stávající infrastruktury očekává, že vzor APM, je také vhodné přijmout implementace TAP a jeho použití, kde je očekávána implementace APM.  Vzhledem k tomu, že úkoly lze vytvářet a třída <xref:System.Threading.Tasks.Task> implementuje třídu <xref:System.IAsyncResult>, můžete použít jednoduchou pomocnou funkci. Následující kód používá rozšíření <xref:System.Threading.Tasks.Task%601> třídy, ale můžete použít téměř identické funkce pro obecné úlohy.  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 Nyní Představte si případ, kdy máte následující implementace TAP:  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 a chcete poskytnout implementaci této funkce APM:  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 Následující příklad ukazuje jednu migraci do APM:  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
<a name="EAP"></a>   
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a>Úlohy a asynchronní vzor (EAP) založených na událostech  
 Zabalení [události asynchronní vzor založený (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) implementace je složitější než pro zabalení APM vzor, protože vzoru EAP má méně struktury než vzor APM a více variant.  Abychom si předvedli, zabalí následující kód `DownloadStringAsync` metody.  `DownloadStringAsync` přijímá identifikátor URI, vyvolá `DownloadProgressChanged` událostí při stahování za účelem hlášení o průběhu a vyvolá více statistiky `DownloadStringCompleted` událost, když se to dělá.  Konečný výsledek je řetězec, který obsahuje obsah stránky se zadaným identifikátorem URI.  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
<a name="WaitHandles"></a>   
## <a name="tasks-and-wait-handles"></a>Úlohy a obslužné rutiny čekání  
  
<a name="WHToTap"></a>   
### <a name="from-wait-handles-to-tap"></a>Z obslužné rutiny čekání klepnutím  
 I když obslužné rutiny čekání nemusíte implementovat asynchronní vzor, pokročilé mohou vývojáři <xref:System.Threading.WaitHandle> třídy a <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> metody pro asynchronní oznámení, když je nastaven popisovač čekání.  Můžete zabalit <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> metoda umožňuje založené na úlohách alternativu jakékoli synchronní čekání na popisovač čekání:  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 Pomocí této metody můžete použít existující <xref:System.Threading.WaitHandle> implementace v asynchronních metodách.  Například pokud chcete omezit počet asynchronních operací, které jsou spuštěny v určitém čase, můžete využít semafor ( <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> objekt).  Můžete omezit na *N* počet operací, které běží souběžně podle počtu semaforu pro inicializaci *N*, čeká na semaforu kdykoli chcete provádět operace a uvolněním Semaphore – až budete hotovi s operací:  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 Můžete také vytvořit asynchronní semafor, který nevyžaduje obslužné rutiny čekání a místo toho pracuje úplně s úkoly. K tomuto účelu můžete použít techniky, jako jsou ty popsané v [využívání Task-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) pro vytváření datových struktur nad <xref:System.Threading.Tasks.Task>.  
  
<a name="TapToWH"></a>   
### <a name="from-tap-to-wait-handles"></a>Z klepněte sem a můžete obslužné rutiny čekání  
 Jak už jsme zmínili, <xref:System.Threading.Tasks.Task> implementuje třída <xref:System.IAsyncResult>, a zpřístupňuje tuto implementaci <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> vlastnosti, která vrací popisovač čekání, který bude nastavit, když <xref:System.Threading.Tasks.Task> dokončí.  Můžete získat <xref:System.Threading.WaitHandle> pro <xref:System.Threading.Tasks.Task> následujícím způsobem:  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a>Viz také:

- [Asynchronní vzor založený na úlohách (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [Implementace asynchronního vzoru založeného na úlohách](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)
- [Použití asynchronního vzoru založeného na úlohách](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
