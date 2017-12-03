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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c752c56fa60cd717f54a7a06d0d3be8b70e7772
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="operation-performance-counters"></a>Čítače provozního výkonu
Čítače provozního výkonu se nacházejí v části `ServiceModelOperation 4.0.0.0` objekt výkonu při zobrazení pomocí sledování výkonu (Perfmon.exe). Každá operace má jednotlivé instance. To znamená Pokud danou zakázku má 10 operace, 10 instancí čítače operace jsou přidruženy k této smlouvy. Instance objektů jsou pojmenované pomocí následujícího vzorce:  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 Tento čítač umožňuje měření využití volání a jak dobře fungují operaci.  
  
> [!CAUTION]
>  Je limit na délka názvu instance čítače výkonu. Když [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] název instance čítače překračuje maximální délku [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] nahrazuje část název instance s hodnotou hash.  
  
## <a name="see-also"></a>Viz také  
 [Čítače výkonu](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
