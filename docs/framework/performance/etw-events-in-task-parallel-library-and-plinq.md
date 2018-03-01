---
title: "Události Trasování událostí pro Windows v knihovně Task Parallel Library a PLINQ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tasks, ETW events
ms.assetid: 87a9cff5-d86f-4e44-a06e-d12764d0dce2
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a84fdb104296cf15b5f0d2d04f4ddd7ea1419643
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="etw-events-in-task-parallel-library-and-plinq"></a>Události Trasování událostí pro Windows v knihovně Task Parallel Library a PLINQ
Knihovně Task Parallel Library a PLINQ generovat události trasování pro Windows (ETW) události, které můžete použít k profilu a řešení potíží s aplikací pomocí nástroje, jako je analyzátor výkonu systému Windows. Ve většině scénářů, nejlepší způsob, jak kód paralelní aplikace profilu je však používat [vizualizér souběžnosti](/visualstudio/profiling/concurrency-visualizer) v [!INCLUDE[vsUltShort](../../../includes/vsultshort-md.md)].  
  
## <a name="task-parallel-library-etw-events"></a>Události trasování událostí pro úlohy Parallel Library  
 Ve struktuře EVENT_HEADER ProviderId GUID pro události vygenerované <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> je:  
  
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
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|ID úlohy, který spustil smyčky.|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Jedinečný identifikátor, který slouží k určení vnoření a páry pro události se sémantiku rozvětvení/spojení.|  
|Typ operace|<xref:System.Int32?displayProperty=nameWithType>|Určuje typ smyčka:<br /><br /> 1 = ParallelInvoke<br /><br /> 2 = ParallelFor<br /><br /> 3 = ParallelForEach|  
|InclusiveFrom|<xref:System.Int64?displayProperty=nameWithType>|Výchozí hodnota čítače smyčky|  
|ExclusiveTo|<xref:System.Int64?displayProperty=nameWithType>|Koncová hodnota čítače smyčky|  
  
### <a name="parallel-loop-end"></a>Paralelní smyčky End  
 EVENT_DESCRIPTOR. Úloha = 2  
  
 EVENT_DESCRIPTOR. ID = 2  
  
#### <a name="user-data"></a>Uživatelská Data  
  
|**Jméno**|**Typ**|**Popis**|  
|--------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|ID TaskScheduler, který spustil smyčky.|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|ID úlohy, který spustil smyčky.|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Jedinečný identifikátor, který slouží k určení vnoření a páry pro události se sémantiku rozvětvení/spojení.|  
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|Celkový počet iterací|  
  
### <a name="parallel-invoke-begin"></a>Paralelní vyvolání začátek  
 EVENT_DESCRIPTOR. Úloha = 3  
  
 EVENT_DESCRIPTOR. ID = 3  
  
#### <a name="user-data"></a>Uživatelská Data  
  
|**Jméno**|**Typ**|**Popis**|  
|--------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|ID TaskScheduler, který spustil smyčky.|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|ID úlohy, který spustil smyčky.|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Jedinečný identifikátor, který slouží k určení vnoření a páry pro události se sémantiku rozvětvení/spojení.|  
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|Celkový počet iterací|  
|Typ operace|<xref:System.Int32?displayProperty=nameWithType>|Určuje typ smyčka:<br /><br /> 1 = ParallelInvoke<br /><br /> 2 = ParallelFor<br /><br /> 3 = ParallelForEach|  
|ActionCount|<xref:System.Int32?displayProperty=nameWithType>|Počet akcí, které budou spuštěny v paralelní invoke.|  
  
### <a name="parallel-invoke-end"></a>Paralelní vyvolání End  
 EVENT_DESCRIPTOR. Úloha = 4  
  
 EVENT_DESCRIPTOR. ID = 4  
  
#### <a name="user-data"></a>Uživatelská Data  
  
|**Jméno**|**Typ**|**Popis**|  
|--------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|ID TaskScheduler, který spustil smyčky.|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|ID úlohy, který spustil smyčky.|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|Jedinečný identifikátor, který slouží k určení vnoření a páry pro události se sémantiku rozvětvení/spojení.|  
  
## <a name="plinq-etw-events"></a>Události trasování událostí pro Windows PLINQ  
 EVENT_HEADER. GUID ProviderId pro PLINQ je:  
  
```  
0x159eeeec, 0x4a14, 0x4418, 0xa8, 0xfe, 0xfa, 0xab, 0xcd, 0x98, 0x78, 0x87  
```  
  
### <a name="parallel-query-begin"></a>Začátek paralelního dotazu  
 EVENT_DESCRIPTOR. Úloha = 1  
  
 EVENT_DESCRIPTOR. ID = 1  
  
#### <a name="user-data"></a>Uživatelská Data  
  
|**Jméno**|**Typ**|**Popis**|  
|--------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|ID TaskScheduler, který spustil smyčky.|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|ID úlohy, který spustil smyčky.|  
|QueryID|<xref:System.Int32?displayProperty=nameWithType>|Dotaz jedinečný identifikátor.|  
  
### <a name="parallel-query-end"></a>End paralelního dotazu  
 EVENT_DESCRIPTOR. Úloha = 2  
  
 EVENT_DESCRIPTOR. ID = 2  
  
#### <a name="user-data"></a>Uživatelská Data  
  
|**Jméno**|**Typ**|**Popis**|  
|--------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|ID TaskScheduler, který spustil smyčky.|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|ID úlohy, který spustil smyčky.|  
|QueryID|<xref:System.Int32?displayProperty=nameWithType>|Dotaz jedinečný identifikátor.|  
  
## <a name="see-also"></a>Viz také  
 [Trasování událostí pro Windows – události v rozhraní .NET Framework](../../../docs/framework/performance/etw-events.md)  
 [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
