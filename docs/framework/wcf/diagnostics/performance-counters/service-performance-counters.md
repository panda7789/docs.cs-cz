---
title: "Čítače výkonu služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8145ff12f5a9befdef3cbf5edf69e5162c4d7014
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="service-performance-counters"></a>Čítače výkonu služby
Čítače výkonu služby měřit chování služby jako celek a umožňuje diagnostikovat provádění celou služeb. Najdete v části `ServiceModelService 4.0.0.0` objekt výkonu při zobrazení pomocí sledování výkonu (Perfmon.exe). Instance jsou pojmenované pomocí následujícího vzorce:  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
>  Je limit na délka názvu instance čítače výkonu. Když [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] název instance čítače překračuje maximální délku [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] nahrazuje část název instance s hodnotou hash.  
  
## <a name="see-also"></a>Viz také  
 [Čítače výkonu](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
