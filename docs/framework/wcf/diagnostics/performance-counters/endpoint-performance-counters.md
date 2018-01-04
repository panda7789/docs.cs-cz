---
title: "Čítače výkonu koncového bodu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc5fa1b3600489cb2d5f31c263019ae5006edf65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="endpoint-performance-counters"></a>Čítače výkonu koncového bodu
Čítače výkonu koncového bodu zachytit data, která zjistí, jak koncový bod přijímá zprávy. Najdete v části `ServiceModelEndpoint 4.0.0.0` objekt výkonu při zobrazení pomocí sledování výkonu. Instance jsou pojmenované pomocí tohoto vzoru:  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 Data je podobná shromážděné pro jednotlivé operace, ale je pouze agregován přes koncový bod.  
  
> [!CAUTION]
>  Je limit na délka názvu instance čítače výkonu. Když [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] název instance čítače překračuje maximální délku [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] nahrazuje část název instance s hodnotou hash.  
  
## <a name="see-also"></a>Viz také  
 [Čítače výkonu](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
