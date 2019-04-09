---
title: Dynamické povolování analytického sledování
ms.date: 03/30/2017
ms.assetid: 58b63cfc-307a-427d-b69d-9917ff9f44ac
ms.openlocfilehash: 219561b1acd2259daad4c984dcf0b15517166c3f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197474"
---
# <a name="dynamically-enabling-analytic-tracing"></a>Dynamické povolování analytického sledování
Pomocí nástrojů, které se dodávají s operačním systémem Windows, můžete povolit nebo zakázat trasování dynamicky pomocí Event Tracing for Windows (ETW). Pro všechny [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] služby Windows Communication Foundation (WCF), analytické trasování může být povolení i Zakázaní dynamicky bez úpravy souboru Web.config aplikace nebo restartování služby. To umožňuje, aby aplikace, který vysílá události trasování k zajištění nepřerušeného.  
  
 Možnosti trasování WCF můžete nakonfigurovat podobným způsobem. Například můžete změnit úroveň závažnosti ze **chyba** k **informace** bez narušení aplikace. To lze provést pomocí následujících nástrojů:  
  
-   **Logman** – nástroj příkazového řádku pro konfiguraci, řízení a dotazování dat trasování. Další informace najdete v tématu [Logman vytvořit trasování](https://go.microsoft.com/fwlink/?LinkId=165426) a [Logman aktualizace trasování](https://go.microsoft.com/fwlink/?LinkId=165427).  
  
-   **EventViewer** – nástroj pro správu grafického rozhraní Windows pro zobrazení výsledků trasování. Další informace najdete v tématu [služby WCF a události trasování pro Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md) a [Prohlížeč událostí](https://go.microsoft.com/fwlink/?LinkId=165428).  
  
-   **Nástroj Perfmon** – nástroje pro správu grafického rozhraní Windows, který používá čítače pro monitorování čítačů trasování a efekty trasování na výkon. Další informace najdete v tématu [Data Collector nastavit ručně vytvořit](https://go.microsoft.com/fwlink/?LinkId=165429).  
  
### <a name="keywords"></a>klíčová slova  
 Při použití <xref:System.ServiceModel.Activation.Configuration.ServiceModelActivationSectionGroup.Diagnostics%2A> třídy, rozhraní .NET Framework trasovací zprávy jsou obecně Filtroval úroveň závažnosti (například Chyba, upozornění a informace). Trasování událostí pro Windows podporuje koncept úrovně závažnosti, ale zavádí nové, flexibilní filtrační mechanismus, pomocí klíčových slov. Klíčová slova jsou libovolné textové hodnoty, které umožní – události trasování poskytli další kontext o tom, co znamená příslušné události.  
  
 Každá událost trasování pro analytické trasování WCF, má dva typy klíčových slov. Každá událost nejprve má nejmíň jeden scénář klíčová slova. Tato klíčová slova označení scénáře, které tato událost je určena na podporu. Existují tři scénáře klíčová slova, jednotlivé nastavené pro konkrétní účel, jak je znázorněno v následující tabulce. Filtrování pomocí klíčových slov můžete změnit dynamicky bez narušení služeb WCF. To znamená, že můžete dynamicky měnit vaší aktuální situaci trasování a množství informací o trasování, který bude shromažďovat. Například můžete změnit `HealthMonitoring` k `Troubleshooting` a zvýšit členitosti trasování událostí.  
  
|Klíčové slovo|Popis|  
|-------------|-----------------|  
|`HealthMonitoring`|Velmi jednoduchý, minimální trasování, která vám umožní monitorovat aktivity vaší služby.|  
|`EndToEndMonitoring`|Událostech, které podporují trasování toku zpráv.|  
|`Troubleshooting`|Podrobnější akcí po bodů rozšiřitelnosti služby WCF.|  
  
 Jakou součást definovat druhé skupině klíčových slov [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] událost, protože ho.  
  
|Klíčové slovo|Popis|  
|-------------|-----------------|  
|`UserEvents`|Události, protože ho vygeneroval kód uživatele, ne [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].|  
|`ServiceModel`|Události generované modulem WCF runtime.|  
|`ServiceHost`|Události, protože ho vygeneroval hostitele služby.|  
|`WCFMessageLogging`|Události protokolování zpráv WCF.|  
  
## <a name="see-also"></a>Viz také:

- [Služby WCF a Trasování událostí pro Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)
