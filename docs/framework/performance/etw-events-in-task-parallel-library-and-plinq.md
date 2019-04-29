---
title: Události Trasování událostí pro Windows v knihovně Task Parallel Library a PLINQ
ms.date: 03/30/2017
helpviewer_keywords:
- tasks, ETW events
ms.assetid: 87a9cff5-d86f-4e44-a06e-d12764d0dce2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 85ca55e976a010a4875d260b3da30f5bc3cf2ffb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723612"
---
# <a name="etw-events-in-task-parallel-library-and-plinq"></a>Události Trasování událostí pro Windows v knihovně Task Parallel Library a PLINQ

Knihovně Task Parallel Library a PLINQ generovat události trasování pro Windows (ETW) události, které slouží k profilu a řešení potíží s aplikacemi s využitím nástrojů, jako je analyzátor výkonu Windows. Ve většině scénářů si nejlepší způsob, jak profil souběžné použití kódu je však používat [Vizualizátor souběžnosti](/visualstudio/profiling/concurrency-visualizer) v sadě Visual Studio.

## <a name="task-parallel-library-etw-events"></a>Události trasování událostí pro Windows knihovna paralelních úloh

Ve struktuře EVENT_HEADER ProviderId identifikátor GUID pro události generované modulem <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> je:

```
0x2e5dba47, 0xa3d2, 0x4d16, 0x8e, 0xe0, 0x66, 0x71, 0xff, 0xdc, 0xd7, 0xb5
```

### <a name="parallel-loop-begin"></a>Začátek paralelní smyčky

EVENT_DESCRIPTOR.Task = 1

EVENT_DESCRIPTOR.Id = 1

#### <a name="user-data"></a>Uživatelská Data

|**Název**|**Typ**|**Popis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|ID TaskScheduler, který spustil smyčky.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|ID úkolu, který spustil smyčky.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Jedinečný identifikátor, který slouží k označení vnoření a dvojice pro události se sémantikou rozvětvení/spojení.|
|OperationType|<xref:System.Int32?displayProperty=nameWithType>|Určuje typ smyčka:<br /><br /> 1 = ParallelInvoke<br /><br /> 2 = ParallelFor<br /><br /> 3 = ParallelForEach|
|InclusiveFrom|<xref:System.Int64?displayProperty=nameWithType>|Počáteční hodnota čítače smyčky|
|ExclusiveTo|<xref:System.Int64?displayProperty=nameWithType>|Koncové hodnoty čítače cyklů|

### <a name="parallel-loop-end"></a>End paralelní smyčky
 EVENT_DESCRIPTOR.Task = 2

 EVENT_DESCRIPTOR.Id = 2

#### <a name="user-data"></a>Uživatelská Data

|**Název**|**Typ**|**Popis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|ID TaskScheduler, který spustil smyčky.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|ID úkolu, který spustil smyčky.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Jedinečný identifikátor, který slouží k označení vnoření a dvojice pro události se sémantikou rozvětvení/spojení.|
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|Celkový počet iterací|

### <a name="parallel-invoke-begin"></a>Paralelní volání Begin
 EVENT_DESCRIPTOR.Task = 3

 EVENT_DESCRIPTOR.Id = 3

#### <a name="user-data"></a>Uživatelská Data

|**Název**|**Typ**|**Popis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|ID TaskScheduler, který spustil smyčky.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|ID úkolu, který spustil smyčky.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Jedinečný identifikátor, který slouží k označení vnoření a dvojice pro události se sémantikou rozvětvení/spojení.|
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|Celkový počet iterací|
|operationType|<xref:System.Int32?displayProperty=nameWithType>|Určuje typ smyčka:<br /><br /> 1 = ParallelInvoke<br /><br /> 2 = ParallelFor<br /><br /> 3 = ParallelForEach|
|ActionCount|<xref:System.Int32?displayProperty=nameWithType>|Počet akcí, které se spustí paralelní invoke.|

### <a name="parallel-invoke-end"></a>Paralelní volání End
 EVENT_DESCRIPTOR.Task = 4

 EVENT_DESCRIPTOR.Id = 4

#### <a name="user-data"></a>Uživatelská Data

|**Název**|**Typ**|**Popis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|ID TaskScheduler, který spustil smyčky.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|ID úkolu, který spustil smyčky.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Jedinečný identifikátor, který slouží k označení vnoření a dvojice pro události se sémantikou rozvětvení/spojení.|

## <a name="plinq-etw-events"></a>PLINQ trasování událostí pro Windows
 EVENT_HEADER. Identifikátor GUID ProviderId pro PLINQ je:

```
0x159eeeec, 0x4a14, 0x4418, 0xa8, 0xfe, 0xfa, 0xab, 0xcd, 0x98, 0x78, 0x87
```

### <a name="parallel-query-begin"></a>Začátek paralelní dotaz
 EVENT_DESCRIPTOR.Task = 1

 EVENT_DESCRIPTOR.Id = 1

#### <a name="user-data"></a>Uživatelská Data

|**Název**|**Typ**|**Popis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|ID TaskScheduler, který spustil smyčky.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|ID úkolu, který spustil smyčky.|
|QueryID|<xref:System.Int32?displayProperty=nameWithType>|Dotaz jedinečný identifikátor.|

### <a name="parallel-query-end"></a>Konec paralelní dotazu
 EVENT_DESCRIPTOR.Task = 2

 EVENT_DESCRIPTOR.Id = 2

#### <a name="user-data"></a>Uživatelská Data

|**Název**|**Typ**|**Popis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|ID TaskScheduler, který spustil smyčky.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|ID úkolu, který spustil smyčky.|
|QueryID|<xref:System.Int32?displayProperty=nameWithType>|Dotaz jedinečný identifikátor.|

## <a name="see-also"></a>Viz také:

- [Trasování událostí pro Windows – události v rozhraní .NET Framework](../../../docs/framework/performance/etw-events.md)
- [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
