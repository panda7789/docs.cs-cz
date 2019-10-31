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
ms.openlocfilehash: 54e300bef1818fd08f27d7920eec68ee1f2c45bb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141378"
---
# <a name="application-domain-resource-monitoring"></a>Sledování prostředků domény aplikace

Monitorování prostředků domény aplikace (ARM) umožňuje hostitelům monitorovat využití procesoru a paměti podle aplikační domény. To je užitečné pro hostitele, jako je například ASP.NET, které používají mnoho domén aplikací v dlouhotrvajícím procesu. Hostitel může uvolnit aplikační doménu aplikace, která má nepříznivý vliv na výkon celého procesu, ale pouze v případě, že dokáže identifikovat problematickou aplikaci. ARM poskytuje informace, které je možné využít k usnadnění těchto rozhodnutí.

Například hostitelská služba může mít mnoho aplikací, které běží na serveru ASP.NET. Pokud jedna aplikace v procesu začne spotřebovávat příliš mnoho paměti nebo příliš mnoho času procesoru, může hostitelská služba použít ARM k identifikaci domény aplikace, která je příčinou problému.

ARM je dostatečně odlehčený pro použití v živých aplikacích. K informacím získáte přístup pomocí trasování událostí pro Windows (ETW) nebo přímo prostřednictvím spravovaných nebo nativních rozhraní API.

## <a name="enabling-resource-monitoring"></a>Povolení monitorování prostředků

ARM lze povolit čtyřmi způsoby: poskytnutím konfiguračního souboru, když je spuštěn modul CLR (Common Language Runtime), pomocí nespravovaného hostujícího rozhraní API, pomocí spravovaného kódu nebo poslechem událostí technologie ETW ARM.

Jakmile je ARM zapnutý, začne shromažďování dat ve všech doménách aplikace v procesu. Pokud byla doména aplikace vytvořena před tím, než je povolena technologie ARM, kumulativní data se spustí, když je povolena technologie ARM, nikoli při vytvoření domény aplikace. Jakmile je tato možnost povolená, ARM nejde zakázat.

- ARM můžete povolit při spuštění CLR přidáním prvku [\<appDomainResourceMonitoring >](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md) do konfiguračního souboru a nastavením atributu `enabled` na `true`. Hodnota `false` (výchozí) znamená pouze to, že ARM není při spuštění povolená. později ji můžete aktivovat pomocí některého z dalších aktivačních mechanismů.

- Hostitel může povolit ARM vyžádáním hostitelského rozhraní [ICLRAppDomainResourceMonitor](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) . Po úspěšném získání tohoto rozhraní je ARM zapnutý.

- Spravovaný kód může povolit ARM nastavením vlastnosti static (`Shared` in Visual Basic) <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> na `true`. Jakmile je vlastnost nastavena, je povolena podpora ARM.

- Po spuštění můžete na něm povolit ARM tím, že budete naslouchat událostem ETW. ARM je povolený a zahajuje Vyvolávání událostí pro všechny domény aplikace, když povolíte `Microsoft-Windows-DotNETRuntime` veřejného poskytovatele pomocí klíčového slova `AppDomainResourceManagementKeyword`. Chcete-li korelovat data s doménami aplikací a vlákny, musíte také povolit poskytovatele `Microsoft-Windows-DotNETRuntimeRundown` s klíčovým slovem `ThreadingKeyword`.

## <a name="using-arm"></a>Použití ARM

ARM poskytuje celkový čas procesoru používaný doménou aplikace a tři druhy informací o využití paměti.

- **Celkový čas procesoru pro doménu aplikace v sekundách**: Tato hodnota je počítána přidáním časů vláken hlášených operačním systémem pro všechna vlákna, která strávila doba spuštěná v doméně aplikace během své životnosti. Blokovaná nebo spící vlákna nepoužívají čas procesoru. Když vlákno volá do nativního kódu, je čas, který je výsledkem vlákna v nativním kódu, obsažen v počtu pro doménu aplikace, ve které bylo volání provedeno.

  - Managed API: <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> – vlastnost.

  - Rozhraní API pro hostování: metoda [ICLRAppDomainResourceMonitor:: getcurrentcputime –](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md) .

  - Události ETW: události `ThreadCreated`, `ThreadAppDomainEnter`a `ThreadTerminated`. Informace o zprostředkovatelích a klíčových slovech naleznete v části "události monitorování prostředků AppDomain" v tématu [události technologie CLR ETW](../../../docs/framework/performance/clr-etw-events.md).

- **Celkový počet spravovaných přidělení provedených aplikační doménou během své životnosti (v bajtech**): celkový počet přidělení neodráží vždycky využití paměti doménou aplikace, protože přidělené objekty můžou být krátkodobé. Pokud však aplikace přiděluje a uvolňuje velký počet objektů, mohou být náklady na přidělení významné.

  - Managed API: <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> – vlastnost.

  - Rozhraní API pro hostování: metoda [ICLRAppDomainResourceMonitor:: GetCurrentAllocated –](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md) .

  - Události ETW: událost `AppDomainMemAllocated` `Allocated` poli.

- **Spravovaná paměť (v bajtech), na kterou se odkazuje doména aplikace a která předržela nejnovější, blokující kolekce**: Toto číslo je přesné až po úplné, blokující kolekci. (To je na rozdíl od souběžných kolekcí, ke kterým dochází na pozadí a neblokuje aplikaci.) Například přetížení metody <xref:System.GC.Collect?displayProperty=nameWithType> způsobuje úplnou, blokující kolekci.

  - Managed API: <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> – vlastnost.

  - Rozhraní API pro hostování: metoda [ICLRAppDomainResourceMonitor:: GetCurrentSurvived –](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) , `pAppDomainBytesSurvived` parametr.

  - Události ETW: událost `AppDomainMemSurvived` `Survived` poli.

- **Celková spravovaná paměť (v bajtech), na kterou se odkazuje proces a která předržela nejnovější zablokované shromažďování**: zachovaná paměť pro jednotlivé aplikační domény se dají porovnat s tímto číslem.

  - Managed API: <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType> – vlastnost.

  - Rozhraní API pro hostování: metoda [ICLRAppDomainResourceMonitor:: GetCurrentSurvived –](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) , `pTotalBytesSurvived` parametr.

  - Události ETW: událost `AppDomainMemSurvived` `ProcessSurvived` poli.

### <a name="determining-when-a-full-blocking-collection-occurs"></a>Určení, kdy dojde k úplnému blokujícímu sběru

Chcete-li zjistit, kdy počty zachované paměti jsou přesné, je třeba znát, kdy došlo k úplnému blokujícímu sběru dat. Tato metoda závisí na rozhraní API, které používáte k prohlédnutí statistik ARM.

#### <a name="managed-api"></a>Spravované rozhraní API

Použijete-li vlastnosti třídy <xref:System.AppDomain>, můžete použít metodu <xref:System.GC.RegisterForFullGCNotification%2A?displayProperty=nameWithType> k registraci oznámení o úplných kolekcích. Prahová hodnota, kterou používáte, není důležitá, protože čekáte na dokončení kolekce, nikoli na přístup kolekce. Pak můžete zavolat metodu <xref:System.GC.WaitForFullGCComplete%2A?displayProperty=nameWithType>, která blokuje až do dokončení celé kolekce. Můžete vytvořit vlákno, které volá metodu ve smyčce a provede veškerou nezbytnou analýzu pokaždé, když se metoda vrátí.

Alternativně můžete metodu <xref:System.GC.CollectionCount%2A?displayProperty=nameWithType> volat pravidelně, abyste viděli, jestli se zvýšil počet kolekcí 2. generace. V závislosti na frekvenci cyklického dotazování by tato technika neposkytovala přesné označení výskytu plné kolekce.

#### <a name="hosting-api"></a>Rozhraní API pro hostování

Pokud používáte rozhraní API nespravovaného hostování, musí hostitel předat CLR implementaci rozhraní [IHostGCManager](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md) . Modul CLR volá metodu [IHostGCManager:: SuspensionEnding –](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) , když pokračuje v provádění podprocesů, které byly pozastaveny při výskytu kolekce. Modul CLR předá generování dokončené kolekce jako parametru metody, takže hostitel může určit, zda byla kolekce zcela nebo částečně. Vaše implementace metody [IHostGCManager:: SuspensionEnding –](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) se může dotazovat na zachovánou paměť, aby se zajistilo, že se počty načítají hned po jejich aktualizaci.

## <a name="see-also"></a>Viz také:

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [ICLRAppDomainResourceMonitor – rozhraní](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [\<appDomainResourceMonitoring >](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [Události Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-events.md)
