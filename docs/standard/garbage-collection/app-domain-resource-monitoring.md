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
ms.openlocfilehash: 12dfdd3ac6d75a3e2a33f93d8847c963ded912e8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286090"
---
# <a name="application-domain-resource-monitoring"></a>Sledování prostředků domény aplikace

Monitorování prostředků domény aplikace (ARM) umožňuje hostitelům monitorovat využití procesoru a paměti podle aplikační domény. To je užitečné pro hostitele, jako je například ASP.NET, které používají mnoho domén aplikací v dlouhotrvajícím procesu. Hostitel může uvolnit aplikační doménu aplikace, která má nepříznivý vliv na výkon celého procesu, ale pouze v případě, že dokáže identifikovat problematickou aplikaci. ARM poskytuje informace, které je možné využít k usnadnění těchto rozhodnutí.

Například hostitelská služba může mít mnoho aplikací, které běží na serveru ASP.NET. Pokud jedna aplikace v procesu začne spotřebovávat příliš mnoho paměti nebo příliš mnoho času procesoru, může hostitelská služba použít ARM k identifikaci domény aplikace, která je příčinou problému.

ARM je dostatečně odlehčený pro použití v živých aplikacích. K informacím získáte přístup pomocí trasování událostí pro Windows (ETW) nebo přímo prostřednictvím spravovaných nebo nativních rozhraní API.

## <a name="enabling-resource-monitoring"></a>Povolení monitorování prostředků

ARM lze povolit čtyřmi způsoby: poskytnutím konfiguračního souboru, když je spuštěn modul CLR (Common Language Runtime), pomocí nespravovaného hostujícího rozhraní API, pomocí spravovaného kódu nebo poslechem událostí technologie ETW ARM.

Jakmile je ARM zapnutý, začne shromažďování dat ve všech doménách aplikace v procesu. Pokud byla doména aplikace vytvořena před tím, než je povolena technologie ARM, kumulativní data se spustí, když je povolena technologie ARM, nikoli při vytvoření domény aplikace. Jakmile je tato možnost povolená, ARM nejde zakázat.

- Můžete povolit ARM při spuštění CLR přidáním [\<appDomainResourceMonitoring>](../../framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md) elementu do konfiguračního souboru a nastavením `enabled` atributu na `true` . Hodnota `false` (výchozí) znamená pouze to, že při spuštění není povolená technologie ARM. později ji můžete aktivovat pomocí některého z dalších aktivačních mechanismů.

- Hostitel může povolit ARM vyžádáním hostitelského rozhraní [ICLRAppDomainResourceMonitor](../../framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) . Po úspěšném získání tohoto rozhraní je ARM zapnutý.

- Spravovaný kód může povolit ARM nastavením statické ( `Shared` v Visual Basic) <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> vlastnosti na `true` . Jakmile je vlastnost nastavena, je povolena podpora ARM.

- Po spuštění můžete na něm povolit ARM tím, že budete naslouchat událostem ETW. ARM je povolen a začíná vykazovat události pro všechny domény aplikace, pokud povolíte veřejného poskytovatele `Microsoft-Windows-DotNETRuntime` pomocí `AppDomainResourceManagementKeyword` klíčového slova. Chcete-li korelovat data s aplikačními doménami a vlákny, musíte také povolit `Microsoft-Windows-DotNETRuntimeRundown` poskytovatele s `ThreadingKeyword` klíčovým slovem.

## <a name="using-arm"></a>Použití ARM

ARM poskytuje celkový čas procesoru používaný doménou aplikace a tři druhy informací o využití paměti.

- **Celkový čas procesoru pro doménu aplikace v sekundách**: Tato hodnota je počítána přidáním časů vláken hlášených operačním systémem pro všechna vlákna, která strávila doba spuštěná v doméně aplikace během své životnosti. Blokovaná nebo spící vlákna nepoužívají čas procesoru. Když vlákno volá do nativního kódu, je čas, který je výsledkem vlákna v nativním kódu, obsažen v počtu pro doménu aplikace, ve které bylo volání provedeno.

  - Spravované rozhraní API: <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> vlastnost.

  - Rozhraní API pro hostování: metoda [ICLRAppDomainResourceMonitor:: getcurrentcputime –](../../framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md) .

  - Události ETW: `ThreadCreated` , `ThreadAppDomainEnter` a `ThreadTerminated` . Informace o zprostředkovatelích a klíčových slovech naleznete v části "události monitorování prostředků AppDomain" v tématu [události technologie CLR ETW](../../framework/performance/clr-etw-events.md).

- **Celkový počet spravovaných přidělení provedených aplikační doménou během své životnosti (v bajtech**): celkový počet přidělení neodráží vždycky využití paměti doménou aplikace, protože přidělené objekty můžou být krátkodobé. Pokud však aplikace přiděluje a uvolňuje velký počet objektů, mohou být náklady na přidělení významné.

  - Spravované rozhraní API: <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> vlastnost.

  - Rozhraní API pro hostování: metoda [ICLRAppDomainResourceMonitor:: GetCurrentAllocated –](../../framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md) .

  - Události ETW: `AppDomainMemAllocated` Event, `Allocated` Field.

- **Spravovaná paměť (v bajtech), na kterou se odkazuje doména aplikace a která předržela nejnovější, blokující kolekce**: Toto číslo je přesné až po úplné, blokující kolekci. (To je na rozdíl od souběžných kolekcí, ke kterým dochází na pozadí a neblokuje aplikaci.) Například <xref:System.GC.Collect?displayProperty=nameWithType> přetížení metody způsobuje úplnou, blokující kolekci.

  - Spravované rozhraní API: <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> vlastnost.

  - Rozhraní API pro hostování: metoda [ICLRAppDomainResourceMonitor:: GetCurrentSurvived –](../../framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) , `pAppDomainBytesSurvived` parametr.

  - Události ETW: `AppDomainMemSurvived` Event, `Survived` Field.

- **Celková spravovaná paměť (v bajtech), na kterou se odkazuje proces a která předržela nejnovější zablokované shromažďování**: zachovaná paměť pro jednotlivé aplikační domény se dají porovnat s tímto číslem.

  - Spravované rozhraní API: <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType> vlastnost.

  - Rozhraní API pro hostování: metoda [ICLRAppDomainResourceMonitor:: GetCurrentSurvived –](../../framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) , `pTotalBytesSurvived` parametr.

  - Události ETW: `AppDomainMemSurvived` Event, `ProcessSurvived` Field.

### <a name="determining-when-a-full-blocking-collection-occurs"></a>Určení, kdy dojde k úplnému blokujícímu sběru

Chcete-li zjistit, kdy počty zachované paměti jsou přesné, je třeba znát, kdy došlo k úplnému blokujícímu sběru dat. Tato metoda závisí na rozhraní API, které používáte k prohlédnutí statistik ARM.

#### <a name="managed-api"></a>Spravované rozhraní API

Použijete-li vlastnosti <xref:System.AppDomain> třídy, můžete použít <xref:System.GC.RegisterForFullGCNotification%2A?displayProperty=nameWithType> metodu k registraci k oznámení úplných kolekcí. Prahová hodnota, kterou používáte, není důležitá, protože čekáte na dokončení kolekce, nikoli na přístup kolekce. Pak můžete zavolat <xref:System.GC.WaitForFullGCComplete%2A?displayProperty=nameWithType> metodu, která blokuje až do dokončení celé kolekce. Můžete vytvořit vlákno, které volá metodu ve smyčce a provede veškerou nezbytnou analýzu pokaždé, když se metoda vrátí.

Alternativně můžete <xref:System.GC.CollectionCount%2A?displayProperty=nameWithType> metodu zavolat pravidelně a zjistit, jestli se počet kolekcí generace 2 zvýšil. V závislosti na frekvenci cyklického dotazování by tato technika neposkytovala přesné označení výskytu plné kolekce.

#### <a name="hosting-api"></a>Rozhraní API pro hostování

Pokud používáte rozhraní API nespravovaného hostování, musí hostitel předat CLR implementaci rozhraní [IHostGCManager](../../framework/unmanaged-api/hosting/ihostgcmanager-interface.md) . Modul CLR volá metodu [IHostGCManager:: SuspensionEnding –](../../framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) , když pokračuje v provádění podprocesů, které byly pozastaveny při výskytu kolekce. Modul CLR předá generování dokončené kolekce jako parametru metody, takže hostitel může určit, zda byla kolekce zcela nebo částečně. Vaše implementace metody [IHostGCManager:: SuspensionEnding –](../../framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) se může dotazovat na zachovánou paměť, aby se zajistilo, že se počty načítají hned po jejich aktualizaci.

## <a name="see-also"></a>Viz také

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [ICLRAppDomainResourceMonitor – rozhraní](../../framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [\<appDomainResourceMonitoring>](../../framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [Události ETW CLR](../../framework/performance/clr-etw-events.md)
