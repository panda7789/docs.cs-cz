---
title: Dynamické povolování analytického sledování
ms.date: 03/30/2017
ms.assetid: 58b63cfc-307a-427d-b69d-9917ff9f44ac
ms.openlocfilehash: bea64ac9a9312d17b7f47e72a46d876552e20a12
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798094"
---
# <a name="dynamically-enabling-analytic-tracing"></a>Dynamické povolování analytického sledování
Pomocí nástrojů, které se dodávají s operačním systémem Windows, můžete povolit nebo zakázat trasování dynamicky pomocí trasování událostí pro Windows (ETW). Pro všechny [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] služby Windows Communication Foundation (WCF) lze analytické trasování povolit a zakázat dynamicky bez změny souboru Web. config aplikace nebo restartování služby. To umožňuje aplikaci, která vysílá události trasování, zůstat nerušená.  
  
 Možnosti trasování WCF lze nakonfigurovat podobným způsobem. Můžete například změnit úroveň závažnosti z chyby na **informace** , aniž by **došlo** k narušení aplikace. Můžete to udělat pomocí následujících nástrojů:  
  
- **Logman** – nástroj příkazového řádku pro konfiguraci, řízení a dotazování dat trasování. Další informace naleznete v tématu [logman create Trace](https://go.microsoft.com/fwlink/?LinkId=165426) a [logman update Trace](https://go.microsoft.com/fwlink/?LinkId=165427).  
  
- **EventViewer** -Windows Graphics Management Tool pro zobrazení výsledků trasování. Další informace najdete v tématu [služby WCF a trasování událostí pro Windows](../../samples/wcf-services-and-event-tracing-for-windows.md) a [Prohlížeč událostí](https://go.microsoft.com/fwlink/?LinkId=165428).  
  
- **Perfmon** – Nástroj pro správu grafiky ve Windows, který využívá čítače ke sledování čítačů trasování a důsledky trasování výkonu. Další informace najdete v tématu [Ruční vytvoření sady kolekcí dat](https://go.microsoft.com/fwlink/?LinkId=165429).  
  
### <a name="keywords"></a>klíčová slova  
 Při použití <xref:System.ServiceModel.Activation.Configuration.ServiceModelActivationSectionGroup.Diagnostics%2A> třídy jsou .NET Framework trasovací zprávy všeobecně filtrovány podle úrovně závažnosti (například chyba, upozornění a informace). ETW podporuje koncept úrovně závažnosti, ale zavádí nový flexibilní mechanizmus filtru s použitím klíčových slov. Klíčová slova jsou libovolné textové hodnoty, které umožňují trasování událostí poskytnout další kontext o tom, co událost znamená.  
  
 Pro analytická trasování WCF mají jednotlivé události trasování dva typy klíčových slov. Za prvé má každá událost jedno nebo více klíčových slov scénáře. Tato klíčová slova označují scénáře, které mají být touto událostí podporovány. Existují tři klíčová slova scénářů, která jsou navržena pro konkrétní účel, jak je znázorněno v následující tabulce. Filtrování pomocí klíčových slov lze dynamicky měnit bez narušení služby WCF. To znamená, že můžete dynamicky měnit aktuální scénář trasování a množství trasovacích informací, které shromažďujete. Můžete například změnit `HealthMonitoring` na `Troubleshooting` a zvýšit členitost události trasování.  
  
|Klíčové slovo|Popis|  
|-------------|-----------------|  
|`HealthMonitoring`|Velmi odlehčené a minimální trasování, které umožňuje monitorovat aktivitu vaší služby.|  
|`EndToEndMonitoring`|Události používané k podpoře trasování toku zpráv|  
|`Troubleshooting`|Podrobnější události kolem bodů rozšiřitelnosti WCF.|  
  
 Druhá skupina klíčových slov definuje, kterou součást .NET Framework vyvolala událost.  
  
|Klíčové slovo|Popis|  
|-------------|-----------------|  
|`UserEvents`|Události emitované kódem uživatele, nikoli .NET Framework.|  
|`ServiceModel`|Události emitované modulem runtime služby WCF.|  
|`ServiceHost`|Události emitované hostitelem služby.|  
|`WCFMessageLogging`|Události protokolování zpráv WCF.|  
  
## <a name="see-also"></a>Viz také:

- [Služby WCF a Trasování událostí pro Windows](../../samples/wcf-services-and-event-tracing-for-windows.md)
