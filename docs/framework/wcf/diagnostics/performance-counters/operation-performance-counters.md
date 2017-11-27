---
title: "Čítače provozního výkonu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 83460e1c4db17938466051269dbeba3f19e0b40a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="operation-performance-counters"></a><span data-ttu-id="4f1e0-102">Čítače provozního výkonu</span><span class="sxs-lookup"><span data-stu-id="4f1e0-102">Operation Performance Counters</span></span>
<span data-ttu-id="4f1e0-103">Čítače provozního výkonu se nacházejí v části `ServiceModelOperation 4.0.0.0` objekt výkonu při zobrazení pomocí sledování výkonu (Perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="4f1e0-103">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="4f1e0-104">Každá operace má jednotlivé instance.</span><span class="sxs-lookup"><span data-stu-id="4f1e0-104">Each operation has an individual instance.</span></span> <span data-ttu-id="4f1e0-105">To znamená Pokud danou zakázku má 10 operace, 10 instancí čítače operace jsou přidruženy k této smlouvy.</span><span class="sxs-lookup"><span data-stu-id="4f1e0-105">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="4f1e0-106">Instance objektů jsou pojmenované pomocí následujícího vzorce:</span><span class="sxs-lookup"><span data-stu-id="4f1e0-106">The object instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 <span data-ttu-id="4f1e0-107">Tento čítač umožňuje měření využití volání a jak dobře fungují operaci.</span><span class="sxs-lookup"><span data-stu-id="4f1e0-107">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="4f1e0-108">Je limit na délka názvu instance čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="4f1e0-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="4f1e0-109">Když [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] název instance čítače překračuje maximální délku [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] nahrazuje část název instance s hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="4f1e0-109">When a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] counter instance name exceeds the maximum length, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f1e0-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="4f1e0-110">See Also</span></span>  
 [<span data-ttu-id="4f1e0-111">Čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="4f1e0-111">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
