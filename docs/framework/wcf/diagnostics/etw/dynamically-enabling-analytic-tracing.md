---
title: Dynamické povolování analytického sledování
ms.date: 03/30/2017
ms.assetid: 58b63cfc-307a-427d-b69d-9917ff9f44ac
ms.openlocfilehash: 22d122f802e82c2aa04d72a996cb872e06fcaeaa
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674960"
---
# <a name="dynamically-enabling-analytic-tracing"></a>Dynamické povolování analytického sledování
Pomocí nástrojů, které jsou dodávány s operačním systémem Windows, můžete povolit nebo zakázat trasování dynamicky pomocí trasování událostí pro Windows (ETW). Pro [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] všechny služby Windows Communication Foundation (WCF) lze dynamicky povolit a zakázat analytické trasování bez změny souboru Web.config aplikace nebo restartování služby. To umožňuje aplikaci, která vyzařuje trasovací události zůstat nerušený.  
  
 Možnosti trasování WCF lze nakonfigurovat podobným způsobem. Můžete například změnit úroveň závažnosti z **Chyba** na **informace** bez narušení aplikace. To lze provést pomocí následujících nástrojů:  
  
- **Logman** – nástroj příkazového řádku pro konfiguraci, řízení a dotazování na data trasování. Další informace naleznete v tématu [Logman Create Trace](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc788036(v=ws.10)) and [Logman Update Trace](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc788128(v=ws.10)).  
  
- **EventViewer** - Windows grafický nástroj pro správu pro zobrazení výsledků trasování. Další informace naleznete v [tématu WCF Services and Event Tracing for Windows](../../samples/wcf-services-and-event-tracing-for-windows.md) and [Event Viewer](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc766042(v=ws.11)).  
  
- **Perfmon** – Windows grafický nástroj pro správu, který používá čítače pro sledování trasování čítače a vliv trasování na výkon. Další informace naleznete [v tématu Ruční vytvoření sady kolekcí dat](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc766404(v=ws.11)).  
  
### <a name="keywords"></a>Klíčová slova  
 Při použití <xref:System.ServiceModel.Activation.Configuration.ServiceModelActivationSectionGroup.Diagnostics%2A> třídy jsou trasovací zprávy rozhraní .NET Framework obecně filtrovány podle úrovně závažnosti (například Chyba, Upozornění a Informace). ETW podporuje koncept úrovně závažnosti, ale zavádí nový, flexibilní filtrační mechanismus pomocí klíčových slov. Klíčová slova jsou libovolné textové hodnoty, které umožňují trasování událostí poskytnout další kontext o tom, co tato událost znamená.  
  
 Pro wcf analytické trasování každá událost trasování má dva typy klíčových slov. Za prvé, každá událost má jedno nebo více klíčových slov scénáře. Tato klíčová slova označují scénáře, které tato událost má podporovat. Existují tři klíčová slova scénáře, z nichž každé je navrženo pro konkrétní účel, jak je znázorněno v následující tabulce. Filtrování pomocí klíčových slov lze dynamicky změnit bez narušení služby WCF. To znamená, že můžete dynamicky měnit aktuální scénář trasování a množství informací o trasování, které shromažďujete. Můžete například změnit `HealthMonitoring` `Troubleshooting` a zvýšit rozlišovací schopnost události trasování.  
  
|Klíčové slovo|Popis|  
|-------------|-----------------|  
|`HealthMonitoring`|Velmi lehké, minimální trasování, které vám umožní sledovat aktivitu vaší služby.|  
|`EndToEndMonitoring`|Události používané k podpoře trasování toku zpráv.|  
|`Troubleshooting`|Podrobnější události kolem bodů rozšiřitelnosti WCF.|  
  
 Druhá skupina klíčových slov definuje, která součást rozhraní .NET Framework událost vyzařovala.  
  
|Klíčové slovo|Popis|  
|-------------|-----------------|  
|`UserEvents`|Události vyzařované uživatelským kódem a nikoli rozhraním .NET Framework.|  
|`ServiceModel`|Události vyzařované za běhu WCF.|  
|`ServiceHost`|Události vyzařované hostitelem služby.|  
|`WCFMessageLogging`|Události protokolování zpráv WCF.|  
  
## <a name="see-also"></a>Viz také

- [Služby WCF a Trasování událostí pro Windows](../../samples/wcf-services-and-event-tracing-for-windows.md)
