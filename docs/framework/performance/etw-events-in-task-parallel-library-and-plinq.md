---
title: Události Trasování událostí pro Windows v knihovně Task Parallel Library a PLINQ
ms.date: 03/30/2017
helpviewer_keywords:
- tasks, ETW events
ms.assetid: 87a9cff5-d86f-4e44-a06e-d12764d0dce2
ms.openlocfilehash: 93fcd3215bdcbb30960f19e23ae15f32bb9ddd84
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716099"
---
# <a name="etw-events-in-task-parallel-library-and-plinq"></a>Události Trasování událostí pro Windows v knihovně Task Parallel Library a PLINQ

Událost paralelní knihovna a PLINQ generují události trasování událostí pro Windows (ETW), které můžete použít k profilování a řešení potíží s aplikacemi pomocí nástrojů, jako je Windows Performance Analyzer. Ve většině scénářů je však nejlepším způsobem profilování paralelního kódu aplikace použití [Vizualizátor souběžnosti](/visualstudio/profiling/concurrency-visualizer) v aplikaci Visual Studio.

## <a name="task-parallel-library-etw-events"></a>Úkoly paralelní knihovny trasování událostí pro Windows

Ve struktuře EVENT_HEADER je identifikátor identifikátoru ProviderId pro události vygenerované <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType><xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType>:

`0x2e5dba47, 0xa3d2, 0x4d16, 0x8e, 0xe0, 0x66, 0x71, 0xff, 0xdc, 0xd7, 0xb5`

### <a name="parallel-loop-begin"></a>Začátek paralelní smyčky

EVENT_DESCRIPTOR. Úkol = 1

EVENT_DESCRIPTOR. ID = 1

#### <a name="user-data"></a>Uživatelská data

|**Jméno**|**Typ**|**Popis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|ID TaskScheduler, které spustilo smyčku.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|ID úkolu, který spustil smyčku|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Jedinečný identifikátor, který slouží k označení vnořování a párů pro události s sémantikou rozvětvení/spojení.|
|OperationType|<xref:System.Int32?displayProperty=nameWithType>|Určuje typ smyčky:<br /><br /> 1 = ParallelInvoke<br /><br /> 2 = ParallelFor<br /><br /> 3 = ParallelForEach|
|InclusiveFrom|<xref:System.Int64?displayProperty=nameWithType>|Počáteční hodnota čítače smyčky|
|ExclusiveTo|<xref:System.Int64?displayProperty=nameWithType>|Koncová hodnota čítače smyčky|

### <a name="parallel-loop-end"></a>Konec paralelní smyčky
 EVENT_DESCRIPTOR. Úloha = 2

 EVENT_DESCRIPTOR. ID = 2

#### <a name="user-data"></a>Uživatelská data

|**Jméno**|**Typ**|**Popis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|ID TaskScheduler, které spustilo smyčku.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|ID úkolu, který spustil smyčku|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Jedinečný identifikátor, který slouží k označení vnořování a párů pro události s sémantikou rozvětvení/spojení.|
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|Celkový počet iterací|

### <a name="parallel-invoke-begin"></a>Zahájení paralelního vyvolání
 EVENT_DESCRIPTOR. Úloha = 3

 EVENT_DESCRIPTOR. ID = 3

#### <a name="user-data"></a>Uživatelská data

|**Jméno**|**Typ**|**Popis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|ID TaskScheduler, které spustilo smyčku.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|ID úkolu, který spustil smyčku|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Jedinečný identifikátor, který slouží k označení vnořování a párů pro události s sémantikou rozvětvení/spojení.|
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|Celkový počet iterací|
|operationType|<xref:System.Int32?displayProperty=nameWithType>|Určuje typ smyčky:<br /><br /> 1 = ParallelInvoke<br /><br /> 2 = ParallelFor<br /><br /> 3 = ParallelForEach|
|ActionCount|<xref:System.Int32?displayProperty=nameWithType>|Počet akcí, které budou provedeny při paralelním volání metody.|

### <a name="parallel-invoke-end"></a>Ukončení paralelního vyvolání
 EVENT_DESCRIPTOR. Úloha = 4

 EVENT_DESCRIPTOR. ID = 4

#### <a name="user-data"></a>Uživatelská data

|**Jméno**|**Typ**|**Popis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|ID TaskScheduler, které spustilo smyčku.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|ID úkolu, který spustil smyčku|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Jedinečný identifikátor, který slouží k označení vnořování a párů pro události s sémantikou rozvětvení/spojení.|

## <a name="plinq-etw-events"></a>Události ETW pro PLINQ
 EVENT_HEADER. Identifikátor GUID pro PLINQ je:

`0x159eeeec, 0x4a14, 0x4418, 0xa8, 0xfe, 0xfa, 0xab, 0xcd, 0x98, 0x78, 0x87`

### <a name="parallel-query-begin"></a>Začátek paralelního dotazu
 EVENT_DESCRIPTOR. Úkol = 1

 EVENT_DESCRIPTOR. ID = 1

#### <a name="user-data"></a>Uživatelská data

|**Jméno**|**Typ**|**Popis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|ID TaskScheduler, které spustilo smyčku.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|ID úkolu, který spustil smyčku|
|QueryID|<xref:System.Int32?displayProperty=nameWithType>|Jedinečný identifikátor dotazu.|

### <a name="parallel-query-end"></a>Ukončení paralelního dotazu
 EVENT_DESCRIPTOR. Úloha = 2

 EVENT_DESCRIPTOR. ID = 2

#### <a name="user-data"></a>Uživatelská data

|**Jméno**|**Typ**|**Popis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|ID TaskScheduler, které spustilo smyčku.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|ID úkolu, který spustil smyčku|
|QueryID|<xref:System.Int32?displayProperty=nameWithType>|Jedinečný identifikátor dotazu.|

## <a name="see-also"></a>Viz také:

- [Trasování událostí pro Windows – události v rozhraní .NET Framework](etw-events.md)
- [Task Parallel Library (TPL)](../../standard/parallel-programming/task-parallel-library-tpl.md)
- [Paralelní LINQ (PLINQ)](../../standard/parallel-programming/parallel-linq-plinq.md)
