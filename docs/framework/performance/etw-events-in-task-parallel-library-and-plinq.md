---
title: Události Trasování událostí pro Windows v knihovně Task Parallel Library a PLINQ
ms.date: 03/30/2017
helpviewer_keywords:
- tasks, ETW events
ms.assetid: 87a9cff5-d86f-4e44-a06e-d12764d0dce2
ms.openlocfilehash: 61429babf7378b9d271ffd60a6228ae4bfe7a5e5
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644250"
---
# <a name="etw-events-in-task-parallel-library-and-plinq"></a>Události Trasování událostí pro Windows v knihovně Task Parallel Library a PLINQ

Paralelní knihovna úloh a PLINQ generují události sledování událostí pro systém Windows (ETW), které můžete použít k profilování a odstraňování potíží s aplikacemi pomocí nástrojů, jako je například nástroj Windows Performance Analyzer. Ve většině scénářů je však nejlepším způsobem, jak profilovat kód paralelní aplikace, použít [vizualizér souběžnosti](/visualstudio/profiling/concurrency-visualizer) v sadě Visual studio.

## <a name="task-parallel-library-etw-events"></a>Události ETW paralelní knihovny úloh

Ve struktuře EVENT_HEADER identifikátor GUID Zprostředkovatel id <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> pro <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> události generované , a je:

`0x2e5dba47, 0xa3d2, 0x4d16, 0x8e, 0xe0, 0x66, 0x71, 0xff, 0xdc, 0xd7, 0xb5`

### <a name="parallel-loop-begin"></a>Paralelní smyčka začíná

EVENT_DESCRIPTOR. Úkol = 1

EVENT_DESCRIPTOR. Id = 1

#### <a name="user-data"></a>Uživatelská data

|**Název**|**Typ**|**Popis**|
|--------------|--------------|---------------------|
|PůvodníIID plánu je na plánu.|<xref:System.Int32?displayProperty=nameWithType>|ID TaskScheduler, který spustil smyčku.|
|Původní ID úloh|<xref:System.Int32?displayProperty=nameWithType>|ID úlohy, která spustila smyčku.|
|Identifikátor ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Jedinečný identifikátor používaný k označení vnoření a párování událostí s sémantikou rozdvojení/spojení.|
|Operationtype|<xref:System.Int32?displayProperty=nameWithType>|Označuje typ smyčky:<br /><br /> 1 = ParallelInvoke<br /><br /> 2 = Parallelfor<br /><br /> 3 = ParallelforEach|
|VčetněOd|<xref:System.Int64?displayProperty=nameWithType>|Počáteční hodnota čítače smyčky|
|ExkluzivněDo|<xref:System.Int64?displayProperty=nameWithType>|Koncová hodnota čítače smyčky|

### <a name="parallel-loop-end"></a>Konec paralelní smyčky
 EVENT_DESCRIPTOR. Úkol = 2

 EVENT_DESCRIPTOR. Id = 2

#### <a name="user-data"></a>Uživatelská data

|**Název**|**Typ**|**Popis**|
|--------------|--------------|---------------------|
|PůvodníIID plánu je na plánu.|<xref:System.Int32?displayProperty=nameWithType>|ID TaskScheduler, který spustil smyčku.|
|Původní ID úloh|<xref:System.Int32?displayProperty=nameWithType>|ID úlohy, která spustila smyčku.|
|Identifikátor ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Jedinečný identifikátor používaný k označení vnoření a párování událostí s sémantikou rozdvojení/spojení.|
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|Celkový počet iterací|

### <a name="parallel-invoke-begin"></a>Paralelní vyvolání begin
 EVENT_DESCRIPTOR. Úkol = 3

 EVENT_DESCRIPTOR. Id = 3

#### <a name="user-data"></a>Uživatelská data

|**Název**|**Typ**|**Popis**|
|--------------|--------------|---------------------|
|PůvodníIID plánu je na plánu.|<xref:System.Int32?displayProperty=nameWithType>|ID TaskScheduler, který spustil smyčku.|
|Původní ID úloh|<xref:System.Int32?displayProperty=nameWithType>|ID úlohy, která spustila smyčku.|
|Identifikátor ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Jedinečný identifikátor používaný k označení vnoření a párování událostí s sémantikou rozdvojení/spojení.|
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|Celkový počet iterací|
|operationType|<xref:System.Int32?displayProperty=nameWithType>|Označuje typ smyčky:<br /><br /> 1 = ParallelInvoke<br /><br /> 2 = Parallelfor<br /><br /> 3 = ParallelforEach|
|Počet akcí|<xref:System.Int32?displayProperty=nameWithType>|Počet akcí, které budou provedeny v paralelní invoke.|

### <a name="parallel-invoke-end"></a>Paralelní konec vyvolání
 EVENT_DESCRIPTOR. Úkol = 4

 EVENT_DESCRIPTOR. Id = 4

#### <a name="user-data"></a>Uživatelská data

|**Název**|**Typ**|**Popis**|
|--------------|--------------|---------------------|
|PůvodníIID plánu je na plánu.|<xref:System.Int32?displayProperty=nameWithType>|ID TaskScheduler, který spustil smyčku.|
|Původní ID úloh|<xref:System.Int32?displayProperty=nameWithType>|ID úlohy, která spustila smyčku.|
|Identifikátor ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Jedinečný identifikátor používaný k označení vnoření a párování událostí s sémantikou rozdvojení/spojení.|

## <a name="plinq-etw-events"></a>Akce PLINQ ETW
 The EVENT_HEADER. Identifikátor identifikátoru ProviderId pro PLINQ je:

`0x159eeeec, 0x4a14, 0x4418, 0xa8, 0xfe, 0xfa, 0xab, 0xcd, 0x98, 0x78, 0x87`

### <a name="parallel-query-begin"></a>Paralelní dotaz začíná
 EVENT_DESCRIPTOR. Úkol = 1

 EVENT_DESCRIPTOR. Id = 1

#### <a name="user-data"></a>Uživatelská data

|**Název**|**Typ**|**Popis**|
|--------------|--------------|---------------------|
|PůvodníIID plánu je na plánu.|<xref:System.Int32?displayProperty=nameWithType>|ID TaskScheduler, který spustil smyčku.|
|Původní ID úloh|<xref:System.Int32?displayProperty=nameWithType>|ID úlohy, která spustila smyčku.|
|Dotazi na id|<xref:System.Int32?displayProperty=nameWithType>|Jedinečný identifikátor dotazu.|

### <a name="parallel-query-end"></a>Konec paralelního dotazu
 EVENT_DESCRIPTOR. Úkol = 2

 EVENT_DESCRIPTOR. Id = 2

#### <a name="user-data"></a>Uživatelská data

|**Název**|**Typ**|**Popis**|
|--------------|--------------|---------------------|
|PůvodníIID plánu je na plánu.|<xref:System.Int32?displayProperty=nameWithType>|ID TaskScheduler, který spustil smyčku.|
|Původní ID úloh|<xref:System.Int32?displayProperty=nameWithType>|ID úlohy, která spustila smyčku.|
|Dotazi na id|<xref:System.Int32?displayProperty=nameWithType>|Jedinečný identifikátor dotazu.|

## <a name="see-also"></a>Viz také

- [Události Trasování událostí pro Windows v rozhraní .NET Framework](etw-events.md)
- [Task Parallel Library (TPL)](../../standard/parallel-programming/task-parallel-library-tpl.md)
- [Paralelní LINQ (PLINQ)](../../standard/parallel-programming/introduction-to-plinq.md)
