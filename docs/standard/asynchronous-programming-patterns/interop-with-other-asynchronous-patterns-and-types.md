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
ms.openlocfilehash: 981c13c68eaf1eb0c19f95eb1b097935ea02a16d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159751"
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a>Interoperabilita s jinými asynchronními vzory a typy
Rozhraní .NET Framework 1.0 <xref:System.IAsyncResult> zavedlo vzor, jinak známý jako [asynchronní programovací model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md)nebo `Begin/End` vzor.  Rozhraní .NET Framework 2.0 přidalo [asynchronní vzor založený na událostech (EAP).](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  Počínaje rozhraním .NET Framework 4 nahrazuje [asynchronní vzor (TAP) asynchronní vzor (APM)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) a EAP, ale poskytuje možnost snadno vytvářet rutiny migrace z dřívějších vzorů.  
  
 V tomto tématu:  
  
- [Úkoly a APM](#APM) [(od APM do TAP](#ApmToTap) nebo [z TAP do APM)](#TapToApm)  
  
- [Úkoly a eAP](#EAP)  
  
- [Úkoly a popisovače čekání](#WaitHandles) [(od úchytů čekání po klepnutí na klepnutím](#WHToTap) nebo z [klepnutelů na úchyty](#TapToWH))  
  
<a name="APM"></a>
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a>Úkoly a asynchronní programovací model (APM)  
  
<a name="ApmToTap"></a>
### <a name="from-apm-to-tap"></a>Od APM do TAP  
 Vzhledem k tomu, že vzor [asynchronního programovacího modelu (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) je velmi strukturovaný, je poměrně snadné vytvořit obálku, která zpřístupní implementaci APM jako implementaci TAP. Ve skutečnosti rozhraní .NET Framework, počínaje rozhraním .NET Framework 4, <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> zahrnuje pomocné rutiny ve formě přetížení metody k poskytnutí tohoto překladu.  
  
 Zvažte <xref:System.IO.Stream> třídu <xref:System.IO.Stream.BeginRead%2A> <xref:System.IO.Stream.EndRead%2A> a její metody a metody, které <xref:System.IO.Stream.Read%2A> představují protějšek APM synchronní metody:  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 Metodu <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> můžete použít k implementaci obálky TAP pro tuto operaci následujícím způsobem:  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 Tato implementace je podobná následující:  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
<a name="TapToApm"></a>
### <a name="from-tap-to-apm"></a>Z TAP na APM  
 Pokud vaše stávající infrastruktura očekává vzor APM, budete také chtít provést implementaci TAP a použít ji tam, kde se očekává implementace APM.  Vzhledem k tomu, že úkoly lze vytvářet a třída <xref:System.Threading.Tasks.Task> implementuje třídu <xref:System.IAsyncResult>, můžete použít jednoduchou pomocnou funkci. Následující kód používá rozšíření <xref:System.Threading.Tasks.Task%601> třídy, ale můžete použít téměř identické funkce pro neobecné úkoly.  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 Nyní zvažte případ, kdy máte následující implementaci TAP:  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 a chcete zadat tuto implementaci APM:  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 Následující příklad ukazuje jednu migraci do APM:  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
<a name="EAP"></a>
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a>Úkoly a asynchronní vzor založený na událostech (EAP)  
 Obtékání implementace [asynchronního vzoru (EAP) založené na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) je více než obtékání vzoru APM, protože vzor Protokolu EAP má více variant a menší strukturu než vzorek APM.  Chcete-li demonstrovat, následující `DownloadStringAsync` kód obtéká metodu.  `DownloadStringAsync`přijímá identifikátor URI, `DownloadProgressChanged` vyvolá událost při stahování, aby bylo možné hlásit `DownloadStringCompleted` více statistik o průběhu, a vyvolá událost, když je hotová.  Konečným výsledkem je řetězec, který obsahuje obsah stránky na zadaný identifikátor URI.  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
<a name="WaitHandles"></a>
## <a name="tasks-and-wait-handles"></a>Úkoly a popisovače čekání  
  
<a name="WHToTap"></a>
### <a name="from-wait-handles-to-tap"></a>Od úchyty čekání k tap  
 Přestože popisovače čekání neimplementují asynchronní vzor, pokročilí vývojáři mohou použít třídu <xref:System.Threading.WaitHandle> a metodu <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> pro asynchronní oznámení při nastavení popisovače čekání.  Metodu <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> můžete zabalit a povolit alternativu založenou na úlohách k libovolnému synchronnímu čekání na popisovači čekání:  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 Pomocí této metody můžete <xref:System.Threading.WaitHandle> použít existující implementace v asynchronní metody.  Například pokud chcete omezit počet asynchronních operací, které jsou prováděny v určitém okamžiku, můžete využít <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> semafor (objekt).  Můžete omezit na *N* počet operací, které běží souběžně inicializací semaforu počet *N*, čekání na semafor kdykoli chcete provést operaci a uvolnění semaforu, když jste hotovi s operací:  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 Můžete také vytvořit asynchronní semafor, který nespoléhá na popisovače čekání a místo toho pracuje zcela s úkoly. Chcete-li to provést, můžete použít techniky, jako jsou popsány v [náročné task-based asynchronní vzor](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) pro vytváření datových <xref:System.Threading.Tasks.Task>struktur nad .  
  
<a name="TapToWH"></a>
### <a name="from-tap-to-wait-handles"></a>Od klepnutí klepnutím na úchyty čekání  
 Jak již bylo <xref:System.Threading.Tasks.Task> zmíněno, <xref:System.IAsyncResult>třída implementuje <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> a že implementace zpřístupňuje vlastnost, <xref:System.Threading.Tasks.Task> která vrátí popisovač čekání, který bude nastaven po dokončení.  Můžete získat <xref:System.Threading.WaitHandle> pro <xref:System.Threading.Tasks.Task> následující:  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a>Viz také

- [Asynchronní vzor založený na úlohách (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [Implementace asynchronního vzoru založeného na úlohách](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)
- [Použití asynchronního vzoru založeného na úlohách](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
