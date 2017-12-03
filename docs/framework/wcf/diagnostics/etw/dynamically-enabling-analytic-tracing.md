---
title: "Dynamické povolování analytického sledování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58b63cfc-307a-427d-b69d-9917ff9f44ac
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4984cb7fd89b69f0006c5294c24184bd8d1f1d09
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="dynamically-enabling-analytic-tracing"></a>Dynamické povolování analytického sledování
Pomocí nástrojů, které jsou součástí operačního systému Windows, můžete povolit nebo zakázat trasování dynamicky použitím události trasování událostí pro Windows (ETW). Pro všechny [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] služby, analytické trasování může být povolení i Zakázaní dynamicky bez úpravy souboru Web.config aplikace nebo restartování služby. To umožňuje aplikaci, který vysílá události trasování, které zůstanou nepřerušeného.  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]podobným způsobem můžete nakonfigurovat možnosti sledování. Například můžete změnit úroveň závažnosti z **chyba** k **informace** bez narušení aplikace. To lze provést pomocí následující nástroje:  
  
-   **Logman** – nástroj pro příkazový řádek pro konfiguraci, řízení a dotazování dat trasování. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][Logman vytvoří trasování](http://go.microsoft.com/fwlink/?LinkId=165426) a [aktualizace Logman trasování](http://go.microsoft.com/fwlink/?LinkId=165427).  
  
-   **Prohlížení událostí** – nástroj pro správu grafického rozhraní systému Windows pro zobrazení výsledků trasování. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][Služby WCF a trasování událostí pro Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md) a [Prohlížeč událostí](http://go.microsoft.com/fwlink/?LinkId=165428).  
  
-   **Perfmon** – nástroj správu grafického rozhraní systému Windows, který používá čítače, které se čítačů sledování trasování a důsledky trasování na výkon. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][Ručně vytvořit sadu kolekcí dat](http://go.microsoft.com/fwlink/?LinkId=165429).  
  
### <a name="keywords"></a>Klíčová slova  
 Při použití <xref:System.ServiceModel.Activation.Configuration.ServiceModelActivationSectionGroup.Diagnostics%2A> třídy rozhraní .NET Framework trasovací zprávy jsou obecně filtrovány podle úroveň závažnosti (například chyby, upozornění a informace). Trasování událostí pro Windows podporuje koncept úrovně závažnosti, ale zavádí nové, flexibilní filtru mechanismus pomocí klíčových slov. Klíčová slova jsou libovolné textové hodnoty, které umožní poskytli další kontext, o co znamená, že událost – události trasování.  
  
 Pro [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] analytické trasování, každý trasování událostí má dva typy klíčových slov. Každá událost jako první, má jeden nebo více scénář klíčová slova. Tato klíčová slova označují scénáře, tato událost je určená pro podporu. Existují tři scénáře klíčová slova, každý navržené pro konkrétní účel, jak je znázorněno v následující tabulce. Filtrování pomocí klíčových slov lze změnit dynamicky bez narušení [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služby. To znamená, že můžete dynamicky měnit váš aktuální scénář trasování a množství informací o trasování, které bude shromažďovat. Například můžete změnit `HealthMonitoring` k `Troubleshooting` a zvýšit členitosti trasování událostí.  
  
|– Klíčové slovo|Popis|  
|-------------|-----------------|  
|`HealthMonitoring`|Velmi jednoduché, minimální trasování, která umožňuje sledovat činnost vaší služby.|  
|`EndToEndMonitoring`|Události použitá k podpoře trasování toku zpráv.|  
|`Troubleshooting`|Podrobnější události kolem body rozšiřitelnosti [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].|  
  
 Jakou součást definovat druhé skupině klíčová slova [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] vygenerované události.  
  
|– Klíčové slovo|Popis|  
|-------------|-----------------|  
|`UserEvents`|Události vygenerované pomocí uživatelského kódu a ne [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].|  
|`ServiceModel`|Události vygenerované pomocí [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] modulu runtime.|  
|`ServiceHost`|Události vygenerované pomocí hostitele služby.|  
|`WCFMessageLogging`|[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]zpráva protokolování událostí.|  
  
## <a name="see-also"></a>Viz také  
 [Služby WCF a trasování událostí pro Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)
