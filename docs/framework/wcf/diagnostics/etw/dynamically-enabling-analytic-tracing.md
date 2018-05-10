---
title: Dynamické povolování analytického sledování
ms.date: 03/30/2017
ms.assetid: 58b63cfc-307a-427d-b69d-9917ff9f44ac
ms.openlocfilehash: 68152741541fdbc048ba290cfb956babaed2e0d7
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="dynamically-enabling-analytic-tracing"></a>Dynamické povolování analytického sledování
Pomocí nástrojů, které jsou součástí operačního systému Windows, můžete povolit nebo zakázat trasování dynamicky použitím události trasování událostí pro Windows (ETW). Pro všechny [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] služby Windows Communication Foundation (WCF), analytické trasování může být povolení i Zakázaní dynamicky bez úpravy souboru Web.config aplikace nebo restartování služby. To umožňuje aplikaci, který vysílá události trasování, které zůstanou nepřerušeného.  
  
 Podobným způsobem můžete nakonfigurovat možnosti trasování WCF. Například můžete změnit úroveň závažnosti z **chyba** k **informace** bez narušení aplikace. To lze provést pomocí následující nástroje:  
  
-   **Logman** – nástroj pro příkazový řádek pro konfiguraci, řízení a dotazování dat trasování. Další informace najdete v tématu [trasování vytvořit Logman](http://go.microsoft.com/fwlink/?LinkId=165426) a [Logman aktualizace trasování](http://go.microsoft.com/fwlink/?LinkId=165427).  
  
-   **Prohlížení událostí** – nástroj pro správu grafického rozhraní systému Windows pro zobrazení výsledků trasování. Další informace najdete v tématu [služby WCF a trasování událostí pro Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md) a [Prohlížeč událostí](http://go.microsoft.com/fwlink/?LinkId=165428).  
  
-   **Perfmon** – nástroj správu grafického rozhraní systému Windows, který používá čítače, které se čítačů sledování trasování a důsledky trasování na výkon. Další informace najdete v tématu [dat kolekce nastavit ručně vytvořit](http://go.microsoft.com/fwlink/?LinkId=165429).  
  
### <a name="keywords"></a>Klíčová slova  
 Při použití <xref:System.ServiceModel.Activation.Configuration.ServiceModelActivationSectionGroup.Diagnostics%2A> třídy rozhraní .NET Framework trasovací zprávy jsou obecně filtrovány podle úroveň závažnosti (například chyby, upozornění a informace). Trasování událostí pro Windows podporuje koncept úrovně závažnosti, ale zavádí nové, flexibilní filtru mechanismus pomocí klíčových slov. Klíčová slova jsou libovolné textové hodnoty, které umožní poskytli další kontext, o co znamená, že událost – události trasování.  
  
 Analytické trasování WCF jednotlivých trasování událostí má dva typy klíčová slova. Každá událost jako první, má jeden nebo více scénář klíčová slova. Tato klíčová slova označují scénáře, tato událost je určená pro podporu. Existují tři scénáře klíčová slova, každý navržené pro konkrétní účel, jak je znázorněno v následující tabulce. Filtrování pomocí klíčových slov lze změnit dynamicky bez narušení služby WCF. To znamená, že můžete dynamicky měnit váš aktuální scénář trasování a množství informací o trasování, které bude shromažďovat. Například můžete změnit `HealthMonitoring` k `Troubleshooting` a zvýšit členitosti trasování událostí.  
  
|– Klíčové slovo|Popis|  
|-------------|-----------------|  
|`HealthMonitoring`|Velmi jednoduché, minimální trasování, která umožňuje sledovat činnost vaší služby.|  
|`EndToEndMonitoring`|Události použitá k podpoře trasování toku zpráv.|  
|`Troubleshooting`|Podrobnější události kolem body rozšiřitelnosti služby WCF.|  
  
 Jakou součást definovat druhé skupině klíčová slova [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] vygenerované události.  
  
|– Klíčové slovo|Popis|  
|-------------|-----------------|  
|`UserEvents`|Události vygenerované pomocí uživatelského kódu a ne [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].|  
|`ServiceModel`|Události vygenerované modulem WCF runtime.|  
|`ServiceHost`|Události vygenerované pomocí hostitele služby.|  
|`WCFMessageLogging`|Události protokolování zpráv WCF.|  
  
## <a name="see-also"></a>Viz také  
 [Služby WCF a Trasování událostí pro Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)
