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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: de51c6d0a3070f8bba8a2c77f9c028e7cfbc944d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="service-performance-counters"></a><span data-ttu-id="05ca1-102">Čítače výkonu služby</span><span class="sxs-lookup"><span data-stu-id="05ca1-102">Service Performance Counters</span></span>
<span data-ttu-id="05ca1-103">Čítače výkonu služby měřit chování služby jako celek a umožňuje diagnostikovat provádění celou služeb.</span><span class="sxs-lookup"><span data-stu-id="05ca1-103">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="05ca1-104">Najdete v části `ServiceModelService 4.0.0.0` objekt výkonu při zobrazení pomocí sledování výkonu (Perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="05ca1-104">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="05ca1-105">Instance jsou pojmenované pomocí následujícího vzorce:</span><span class="sxs-lookup"><span data-stu-id="05ca1-105">The instances are named using the following pattern:</span></span>  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
>  <span data-ttu-id="05ca1-106">Je limit na délka názvu instance čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="05ca1-106">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="05ca1-107">Když [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] název instance čítače překračuje maximální délku [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] nahrazuje část název instance s hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="05ca1-107">When a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] counter instance name exceeds the maximum length, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05ca1-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="05ca1-108">See Also</span></span>  
 [<span data-ttu-id="05ca1-109">Čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="05ca1-109">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
