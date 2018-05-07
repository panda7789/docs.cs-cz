---
title: Sledování prostředků domény aplikace
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- monitoring managed memory use by application domain
- application domains, memory use
- memory use, monitoring
- application domains, resource monitoring
ms.assetid: 318bedf8-7f35-4f00-b34a-2b7b8e3fa315
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45b0f8293b41d42114b189c3ebe917a4f64c4f27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="application-domain-resource-monitoring"></a>Sledování prostředků domény aplikace
(ARM) sledování prostředků domény aplikace umožňuje hostitelům sledování využití procesoru a paměti aplikační doménou. To je užitečné pro hostitele například ASP.NET využívající mnoho aplikační domény v dlouho běžící proces. Hostitel může uvolnění domény aplikace aplikace, která nepříznivě ovlivňuje výkon celý proces, ale pouze pokud se ale může pomoci identifikovat problematické aplikace. ARM poskytuje informace, které je možné, které vám pomohou v rozhodování.  
  
 Hostitelská služba například může mít mnoho aplikací spuštěných na serveru technologie ASP.NET. Pokud jednu aplikaci v procesu začne spotřeba paměti převýší nebo příliš mnoho času procesoru, hostitelské služby slouží k identifikaci doméně aplikace, která je příčinou problému ARM.  
  
 ARM je dostatečně lightweight používat v aplikacích za provozu. Informace můžete přistupovat pomocí trasování událostí pro Windows (ETW) nebo přímo přes spravovaným nebo nativním rozhraní API.  
  
## <a name="enabling-resource-monitoring"></a>Povolení sledování prostředků  
 ARM se dá nastavit čtyři způsoby: zadáním konfiguračního souboru, když se spustí modul CLR (CLR), pomocí nespravované hostující rozhraní API, pomocí spravovaného kódu, nebo naslouchání události ARM ETW.  
  
 Jakmile je povoleno ARM, začne shromažďování dat na všechny domény aplikace v procesu. Pokud domény aplikace byla vytvořena než ARM je povoleno, kumulativní data spustí, když je povoleno ARM, ne v případě, že byla vytvořena domény aplikace. Jakmile je povoleno, nelze zakázat ARM.  
  
-   Můžete povolit ARM při spuštění CLR přidáním [ \<appdomainresourcemonitoring – >](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md) element konfiguračního souboru a nastavení `enabled` atribut `true`. Hodnota `false` (výchozí) pouze znamená, že ARM není povolena při spuštění; ji můžete aktivovat později pomocí jednoho z jiných mechanismů aktivace.  
  
-   Hostitele můžete povolit ARM tím, že požádá [iclrappdomainresourcemonitor –](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) hostování rozhraní. Jakmile se toto rozhraní je byly úspěšně načteny, je povoleno ARM.  
  
-   Spravovaný kód můžete povolit tak statických ARM (`Shared` v jazyce Visual Basic) <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> vlastnost `true`. Jakmile je vlastnost nastavena, je povoleno ARM.  
  
-   Po spuštění můžete povolit ARM naslouchání události trasování událostí. ARM je povolená a začne vyvolávání událostí pro všechny domény aplikace, když povolíte veřejného poskytovatele `Microsoft-Windows-DotNETRuntime` pomocí `AppDomainResourceManagementKeyword` – klíčové slovo. K chybě korelace dat. s doménami aplikací a vláken, musíte zároveň povolit `Microsoft-Windows-DotNETRuntimeRundown` zprostředkovatele s `ThreadingKeyword` – klíčové slovo.  
  
## <a name="using-arm"></a>Pomocí modelu ARM  
 ARM poskytuje celkový procesorového času, který je používán domény aplikace a tři druhy informace o využití paměti.  
  
-   **Celkový čas procesoru pro doménu aplikace v sekundách**: Tato hodnota je vypočtena sčítat vlákno časy uvedeny v operačním systému pro všechna vlákna, které spotřebovávají doba provádění v doméně aplikace během celé jeho životnosti. Blokované nebo spící vláken nepoužívejte času procesoru. Když vlákno volání do nativního kódu, je doba, kterou vlákno stráví v nativním kódu zahrnutí do počtu pro doménu aplikace, kde byla provedena volání.  
  
    -   Spravovaná rozhraní API: <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> vlastnost.  
  
    -   Hostování rozhraní API: [iclrappdomainresourcemonitor::getcurrentcputime –](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md) metoda.  
  
    -   Události trasování událostí pro Windows: `ThreadCreated`, `ThreadAppDomainEnter`, a `ThreadTerminated` události. Informace o klíčových slov a poskytovatelů najdete v tématu "AppDomain prostředků monitorování událostí" v [události ETW CLR](../../../docs/framework/performance/clr-etw-events.md).  
  
-   **Celkový počet spravovaných přidělení provedené domény aplikace během celé jeho životnosti v bajtech**: Celkový počet přidělených vždy nezahrnují využití paměti aplikační doménou, protože přidělené objekty může mít krátkodobé trvání. Ale pokud aplikace přiděluje a uvolní velký počet objektů, náklady na přidělení může být důležité.  
  
    -   Spravovaná rozhraní API: <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> vlastnost.  
  
    -   Hostování rozhraní API: [iclrappdomainresourcemonitor::getcurrentallocated –](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md) metoda.  
  
    -   Události trasování událostí pro Windows: `AppDomainMemAllocated` událostí, `Allocated` pole.  
  
-   **Spravované paměti v bajtech, který je odkazován objektem domény aplikace a který přežil nejnovější plná blokování kolekce**: Tento počet je přesný až po úplné, blokování kolekce. (Je na rozdíl od souběžných kolekce, které probíhat na pozadí a neblokují aplikace.) Například <xref:System.GC.Collect?displayProperty=nameWithType> přetížení metody způsobí, že plná blokování kolekce.  
  
    -   Spravovaná rozhraní API: <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> vlastnost.  
  
    -   Hostování rozhraní API: [iclrappdomainresourcemonitor::getcurrentsurvived –](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) metody `pAppDomainBytesSurvived` parametr.  
  
    -   Události trasování událostí pro Windows: `AppDomainMemSurvived` událostí, `Survived` pole.  
  
-   **Celkový počet spravované paměti v bajtech, který je odkazován objektem proces a který přežil nejnovější plná blokování kolekce**: survived paměti pro jednotlivé aplikace domény je možné porovnávat s tímto číslem.  
  
    -   Spravovaná rozhraní API: <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType> vlastnost.  
  
    -   Hostování rozhraní API: [iclrappdomainresourcemonitor::getcurrentsurvived –](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) metody `pTotalBytesSurvived` parametr.  
  
    -   Události trasování událostí pro Windows: `AppDomainMemSurvived` událostí, `ProcessSurvived` pole.  
  
### <a name="determining-when-a-full-blocking-collection-occurs"></a>Blokování kolekce dojde k určení, kdy úplné,  
 Pokud chcete zjistit, když se o přesném zadání počty zůstal naživu paměti, potřebujete vědět, když kolekci úplné a blokování právě došlo. Metoda pro to závisí na rozhraní API používáte k prozkoumání statistiky ARM.  
  
#### <a name="managed-api"></a>Spravovaná rozhraní API  
 Pokud používáte vlastnosti <xref:System.AppDomain> třídu, můžete použít <xref:System.GC.RegisterForFullGCNotification%2A?displayProperty=nameWithType> metoda registrace pro oznámení o úplné kolekce. Prahová hodnota, které můžete použít není důležité, protože se čeká na dokončení kolekci spíše než přístup kolekce. Potom můžete zavolat <xref:System.GC.WaitForFullGCComplete%2A?displayProperty=nameWithType> metoda, která blokuje až po dokončení úplné kolekce. Můžete vytvořit vlákno, která volá metodu ve smyčce a nemá žádné potřeby analýzy vždy, když metoda vrátí.  
  
 Alternativně můžete volat <xref:System.GC.CollectionCount%2A?displayProperty=nameWithType> metoda pravidelně chcete zobrazit, pokud má vyšší počet kolekcí 2. generace. V závislosti na frekvence cyklického dotazování nemusí tato technika zadejte jako přesné uvedením výskytu úplné kolekce.  
  
#### <a name="hosting-api"></a>Hostování rozhraní API  
 Pokud používáte nespravovaného rozhraní API hostování, váš hostitel musí projít modulu CLR implementace [ihostgcmanager –](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md) rozhraní. Volání CLR [ihostgcmanager::suspensionending –](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) metoda při obnoví spuštění vláken, které byly pozastaveny během kolekce. Modul CLR předá generování dokončené kolekce jako parametr metody, tak hostitele můžete určit, zda byla kolekce celé nebo jeho část. Vaši implementaci [ihostgcmanager::suspensionending –](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) metoda mohou odesílat dotazy na zůstal naživu paměť k zajištění, že jsou počty načíst také nejsou aktualizovány.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
 [ICLRAppDomainResourceMonitor – rozhraní](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [\<appdomainresourcemonitoring – >](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)  
 [Události Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-events.md)
