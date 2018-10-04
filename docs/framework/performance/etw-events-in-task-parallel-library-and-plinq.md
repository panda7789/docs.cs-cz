---
title: Události Trasování událostí pro Windows v knihovně Task Parallel Library a PLINQ
ms.date: 03/30/2017
helpviewer_keywords:
- tasks, ETW events
ms.assetid: 87a9cff5-d86f-4e44-a06e-d12764d0dce2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6b5281b90605f14b75b4537333378903d5f67817
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48778270"
---
# <a name="etw-events-in-task-parallel-library-and-plinq"></a>Události Trasování událostí pro Windows v knihovně Task Parallel Library a PLINQ

Knihovně Task Parallel Library a PLINQ generovat události trasování pro Windows (ETW) události, které slouží k profilu a řešení potíží s aplikacemi s využitím nástrojů, jako je analyzátor výkonu Windows. Ve většině scénářů si nejlepší způsob, jak profil souběžné použití kódu je však používat [Vizualizátor souběžnosti](/visualstudio/profiling/concurrency-visualizer) v sadě Visual Studio.

## <a name="task-parallel-library-etw-events"></a>Události trasování událostí pro Windows knihovna paralelních úloh

Ve struktuře EVENT_HEADER ProviderId identifikátor GUID pro události generované modulem <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> je:

```
0x2e5dba47, 0xa3d2, 0x4d16, 0x8e, 0xe0, 0x66, 0x71, 0xff, 0xdc, 0xd7, 0xb5
```

### <a name="parallel-loop-begin"></a>Začátek paralelní smyčky

EVENT_DESCRIPTOR. Úloha = 1

EVENT_DESCRIPTOR. ID = 1

#### <a name="user-data"></a>Uživatelská Data

|**Jméno**|**Typ**|**Popis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|ID TaskScheduler, který spustil smyčky.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|ID úkolu, který spustil smyčky.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Jedinečný identifikátor, který slouží k označení vnoření a dvojice pro události se sémantikou rozvětvení/spojení.|
|Typ operace|<xref:System.Int32?displayProperty=nameWithType>|Určuje typ smyčka:<br /><br /> 1 = ParallelInvoke<br /><br /> 2 = ParallelFor<br /><br /> 3 = ParallelForEach|
|InclusiveFrom|<xref:System.Int64?displayProperty=nameWithType>|Počáteční hodnota čítače smyčky|
|ExclusiveTo|<xref:System.Int64?displayProperty=nameWithType>|Koncové hodnoty čítače cyklů|

### <a name="parallel-loop-end"></a>End paralelní smyčky
 EVENT_DESCRIPTOR. Úloha = 2

 EVENT_DESCRIPTOR. ID = 2

#### <a name="user-data"></a>Uživatelská Data

|**Jméno**|**Typ**|**Popis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|ID TaskScheduler, který spustil smyčky.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|ID úkolu, který spustil smyčky.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Jedinečný identifikátor, který slouží k označení vnoření a dvojice pro události se sémantikou rozvětvení/spojení.|
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|Celkový počet iterací|

### <a name="parallel-invoke-begin"></a>Paralelní volání Begin
 EVENT_DESCRIPTOR. Úloha = 3

 EVENT_DESCRIPTOR. ID = 3

#### <a name="user-data"></a>Uživatelská Data

|**Jméno**|**Typ**|**Popis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|ID TaskScheduler, který spustil smyčky.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|ID úkolu, který spustil smyčky.|
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Jedinečný identifikátor, který slouží k označení vnoření a dvojice pro události se sémantikou rozvětvení/spojení.|
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|Celkový počet iterací|
|Typ operace|<xref:System.Int32?displayProperty=nameWithType>|Určuje typ smyčka:<br /><br /> 1 = ParallelInvoke<br /><br /> 2 = ParallelFor<br /><br /> 3 = ParallelForEach|
|ActionCount|<xref:System.Int32?displayProperty=nameWithType>|Počet akcí, které se spustí paralelní invoke.|

### <a name="parallel-invoke-end"></a>Paralelní volání End
 EVENT_DESCRIPTOR. Úloha = 4

 EVENT_DESCRIPTOR. ID = 4

#### <a name="user-data"></a>Uživatelská Data

|**Jméno**|**Typ**|**Popis**|
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
 EVENT_DESCRIPTOR. Úloha = 1

 EVENT_DESCRIPTOR. ID = 1

#### <a name="user-data"></a>Uživatelská Data

|**Jméno**|**Typ**|**Popis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|ID TaskScheduler, který spustil smyčky.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|ID úkolu, který spustil smyčky.|
|QueryID|<xref:System.Int32?displayProperty=nameWithType>|Dotaz jedinečný identifikátor.|

### <a name="parallel-query-end"></a>Konec paralelní dotazu
 EVENT_DESCRIPTOR. Úloha = 2

 EVENT_DESCRIPTOR. ID = 2

#### <a name="user-data"></a>Uživatelská Data

|**Jméno**|**Typ**|**Popis**|
|--------------|--------------|---------------------|
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|ID TaskScheduler, který spustil smyčky.|
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|ID úkolu, který spustil smyčky.|
|QueryID|<xref:System.Int32?displayProperty=nameWithType>|Dotaz jedinečný identifikátor.|

## <a name="see-also"></a>Viz také

- [Trasování událostí pro Windows – události v rozhraní .NET Framework](../../../docs/framework/performance/etw-events.md)
- [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
