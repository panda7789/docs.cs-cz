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
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159751"
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a>Interoperabilita s jinými asynchronními vzory a typy
.NET Framework 1,0 představil vzor <xref:System.IAsyncResult>, jinak označované jako [asynchronní programovací model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md)nebo vzor `Begin/End`.  .NET Framework 2,0 přidal [asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).  Počínaje .NET Framework 4, [asynchronní vzor založený na úlohách (klepněte) nahrazuje rozhraní](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) APM i EAP, ale poskytuje možnost snadného sestavení rutin migrace z předchozích vzorů.  
  
 V tomto tématu:  
  
- [Úlohy a APM](#APM) ([od APM po klepnutí](#ApmToTap) nebo [z klepněte na APM](#TapToApm))  
  
- [Úlohy a EAP](#EAP)  
  
- [Úlohy a obslužné rutiny čekání](#WaitHandles) ([z obslužných rutin čekání na klepnutí](#WHToTap) nebo [z klepnutí na obslužné rutiny čekání](#TapToWH))  
  
<a name="APM"></a>
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a>Úlohy a model asynchronního programování (APM)  
  
<a name="ApmToTap"></a>
### <a name="from-apm-to-tap"></a>Od APM po klepnutí  
 Vzhledem k tomu, že je vzor [asynchronního programovacího modelu (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) velmi strukturovaný, je poměrně snadné vytvořit obálku, aby vystavila implementaci APM jako klepnutím na implementaci. Ve skutečnosti .NET Framework, počínaje .NET Framework 4, obsahuje pomocné rutiny ve formě <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> přetížení metod pro poskytnutí tohoto překladu.  
  
 Zvažte třídu <xref:System.IO.Stream> a její metody <xref:System.IO.Stream.BeginRead%2A> a <xref:System.IO.Stream.EndRead%2A>, které reprezentují protějšek APM pro synchronní <xref:System.IO.Stream.Read%2A> metodu:  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 Pomocí metody <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> můžete pro tuto operaci implementovat obálku klepnutím následujícím způsobem:  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 Tato implementace je podobná následující:  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
<a name="TapToApm"></a>
### <a name="from-tap-to-apm"></a>Z klepnutí na APM  
 Pokud vaše stávající infrastruktura očekává vzor APM, budete také chtít provést implementaci klepnutím a použít ji tam, kde se očekává implementace APM.  Vzhledem k tomu, že úkoly lze vytvářet a třída <xref:System.Threading.Tasks.Task> implementuje třídu <xref:System.IAsyncResult>, můžete použít jednoduchou pomocnou funkci. Následující kód používá rozšíření <xref:System.Threading.Tasks.Task%601> třídy, ale můžete použít téměř totožnou funkci pro neobecné úlohy.  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 Nyní vezměte v úvahu případ, kde máte následující implementaci klepnutím:  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 a chcete poskytnout tuto implementaci APM:  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 Následující příklad ukazuje jednu migraci na APM:  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
<a name="EAP"></a>
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a>Úlohy a asynchronní vzor založený na událostech (EAP)  
 Zabalení implementace [asynchronního vzoru založeného na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) je větší než zabalení vzoru APM, protože vzor protokolu EAP má větší variaci a méně než strukturu APM.  K předvedení následujícího kódu zabalí metodu `DownloadStringAsync`.  `DownloadStringAsync` přijímá identifikátor URI, vyvolává během stahování událost `DownloadProgressChanged`, aby bylo možné ohlásit více statistik průběhu, a událost `DownloadStringCompleted` po dokončení vyvolá.  Konečný výsledek je řetězec, který obsahuje obsah stránky se zadaným identifikátorem URI.  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
<a name="WaitHandles"></a>
## <a name="tasks-and-wait-handles"></a>Úlohy a obslužné rutiny čekání  
  
<a name="WHToTap"></a>
### <a name="from-wait-handles-to-tap"></a>Z obslužných rutin čekání na klepnutí  
 Ačkoli obslužné rutiny čekání neimplementují asynchronní vzorek, pokročilí vývojáři mohou použít třídu <xref:System.Threading.WaitHandle> a metodu <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> pro asynchronní oznámení, když je nastaven popisovač čekání.  Metodu <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> lze zabalit, chcete-li povolit alternativu na základě úlohy do synchronního čekání na popisovač čekání:  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 Pomocí této metody můžete použít existující implementace <xref:System.Threading.WaitHandle> v asynchronních metodách.  Například pokud chcete omezit počet asynchronních operací, které jsou spuštěny v určitém čase, můžete použít semafor (objekt <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>).  Můžete omezit na *n* počet operací, které se souběžně spouštějí, inicializací počtu semaforu na *N*, čekáním na semafor kdykoli chcete provést operaci, a uvolněním semaforu, když jste dokončili operaci:  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 Můžete také vytvořit asynchronní semafor, který nespoléhá na obslužné rutiny čekání a místo toho funguje zcela s úkoly. K tomu můžete použít techniky, jako jsou popsány v tématu použití [asynchronního vzoru založeného na úlohách](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) pro vytváření datových struktur nad <xref:System.Threading.Tasks.Task>.  
  
<a name="TapToWH"></a>
### <a name="from-tap-to-wait-handles"></a>Od klepnutí do čekání na zpracování  
 Jak už jsme uvedli, třída <xref:System.Threading.Tasks.Task> implementuje <xref:System.IAsyncResult>a tato implementace zpřístupňuje vlastnost <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A>, která vrací popisovač čekání, který se nastaví po dokončení <xref:System.Threading.Tasks.Task>.  <xref:System.Threading.WaitHandle> pro <xref:System.Threading.Tasks.Task> můžete získat takto:  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a>Viz také

- [Asynchronní vzor založený na úlohách (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [Implementace asynchronního vzoru založeného na úlohách](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)
- [Použití asynchronního vzoru založeného na úlohách](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
