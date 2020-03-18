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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141378"
---
# <a name="application-domain-resource-monitoring"></a>Sledování prostředků domény aplikace

Monitorování prostředků domény aplikace (ARM) umožňuje hostitelům sledovat využití procesoru a paměti podle domény aplikace. To je užitečné pro hostitele, jako je ASP.NET, které používají mnoho aplikačních domén v dlouhotrvajícím procesu. Hostitel může uvolnit doménu aplikace, která nepříznivě ovlivňuje výkon celého procesu, ale pouze v případě, že může identifikovat problematickou aplikaci. ARM poskytuje informace, které mohou být použity na pomoc při provádění těchto rozhodnutí.

Například hostingová služba může mít mnoho aplikací spuštěna na serveru ASP.NET. Pokud jedna aplikace v procesu začne spotřebovávat příliš mnoho paměti nebo příliš mnoho času procesoru, hostitelská služba může použít ARM k identifikaci domény aplikace, která je příčinou problému.

ARM je dostatečně lehký pro použití v živých aplikacích. K informacím můžete přistupovat pomocí trasování událostí pro Windows (ETW) nebo přímo prostřednictvím spravovaných nebo nativních oken API.

## <a name="enabling-resource-monitoring"></a>Povolení monitorování prostředků

ARM lze povolit čtyřmi způsoby: poskytnutím konfiguračního souboru při spuštění clr (COMMON Language runtime), pomocí nespravovaného hostitelského rozhraní API, pomocí spravovaného kódu nebo nasloucháním událostem ARM ETW.

Jakmile arm je povolena, začne shromažďovat data na všech aplikačních domén v procesu. Pokud byla doména aplikace vytvořena před povolením arm, kumulativní data se spustí, když je povolena ARM, ne když byla vytvořena doména aplikace. Jakmile je povolena, nelze zakázat ARM.

- Arm při spuštění CLR můžete povolit přidáním prvku [ \<appDomainResourceMonitoring](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)>`enabled` do konfiguračního souboru a nastavením atributu na `true`. Hodnota `false` (výchozí) znamená pouze to, že ARM není povolena při spuštění; můžete aktivovat později pomocí jednoho z dalších aktivačních mechanismů.

- Hostitel může povolit ARM vyžádáním hostitelského rozhraní [ICLRAppDomainResourceMonitor.](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) Jakmile je toto rozhraní úspěšně získáno, arm je povolena.

- Spravovaný kód může povolit ARM nastavením statické vlastnosti (v`Shared` jazyce Visual Basic) <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> na `true`. Jakmile je vlastnost nastavena, arm je povolena.

- Můžete povolit ARM po spuštění nasloucháním událostem ETW. ARM je povolena a začne vyvolávat události pro `Microsoft-Windows-DotNETRuntime` všechny domény `AppDomainResourceManagementKeyword` aplikace, když povolíte veřejného zprostředkovatele pomocí klíčového slova. Chcete-li korelovat data s aplikačními doménami a vlákny, musíte také povolit `Microsoft-Windows-DotNETRuntimeRundown` zprostředkovatele s klíčovým slovem. `ThreadingKeyword`

## <a name="using-arm"></a>Použití ARM

ARM poskytuje celkový čas procesoru, který používá doména aplikace a tři druhy informací o využití paměti.

- **Celkový čas procesoru pro doménu aplikace v sekundách**: Vypočítá se tak, že sečte tečasy vlákna hlášené operačním systémem pro všechna vlákna, která strávila čas prováděním v doméně aplikace během své životnosti. Blokované nebo spící podprocesy nepoužívají čas procesoru. Když vlákno volá do nativního kódu, čas, který vlákno stráví v nativním kódu, je zahrnut v počtu pro doménu aplikace, kde bylo volání provedeno.

  - Spravované rozhraní <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> API: vlastnost.

  - Hosting API: [METODA ICLRAppDomainResourceMonitor::GetCurrentCpuTime.](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md)

  - Události `ThreadCreated`ETW: `ThreadAppDomainEnter`, `ThreadTerminated` , a události. Informace o zprostředkovatelích a klíčových slovech naleznete v tématu Události monitorování prostředků domény aplikace v [události CLR ETW](../../../docs/framework/performance/clr-etw-events.md).

- **Celkový počet spravovaných přidělení provedených doménou aplikace během její životnosti v bajtech**: Celková alokace ne vždy odrážejí využití paměti doménou aplikace, protože přidělené objekty mohou mít krátkou životnost. Pokud však aplikace přiděluje a uvolňuje obrovské množství objektů, náklady na přidělení může být významné.

  - Spravované rozhraní <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> API: vlastnost.

  - Hostování ROZHRANÍ API: [ICLRAppDomainResourceMonitor::GetCurrentAlocated](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md) metoda.

  - ETW události: `AppDomainMemAllocated` `Allocated` událost, pole.

- **Spravovanou paměť v bajtů, která je odkazována doménou aplikace a která přežila nejnovější úplnou kolekci blokování**: Toto číslo je přesné pouze po úplné, blokující kolekci. (To je na rozdíl od souběžných kolekcí, které se vyskytují na pozadí a neblokují aplikaci.) Například <xref:System.GC.Collect?displayProperty=nameWithType> přetížení metody způsobí úplné blokování kolekce.

  - Spravované rozhraní <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> API: vlastnost.

  - Hosting API: [ICLRAppDomainResourceMonitor::GetCurrentSurvived](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) metoda, `pAppDomainBytesSurvived` parametr.

  - ETW události: `AppDomainMemSurvived` `Survived` událost, pole.

- **Celková spravovaná paměť v bajtech, na kterou proces odkazuje a která přežila poslední úplnou kolekci blokování**: Přežívanou paměť pro jednotlivé aplikační domény lze porovnat s tímto číslem.

  - Spravované rozhraní <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType> API: vlastnost.

  - Hosting API: [ICLRAppDomainResourceMonitor::GetCurrentSurvived](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) metoda, `pTotalBytesSurvived` parametr.

  - ETW události: `AppDomainMemSurvived` `ProcessSurvived` událost, pole.

### <a name="determining-when-a-full-blocking-collection-occurs"></a>Určení, kdy dojde k úplné, blokování kolekce

Chcete-li zjistit, kdy počty přežívaných paměti jsou přesné, musíte vědět, kdy došlo k úplné, blokování kolekce právě došlo. Metoda pro to závisí na rozhraní API, které používáte ke kontrole arm statistiky.

#### <a name="managed-api"></a>Spravované rozhraní API

Pokud používáte vlastnosti <xref:System.AppDomain> třídy, můžete <xref:System.GC.RegisterForFullGCNotification%2A?displayProperty=nameWithType> použít metodu k registraci pro oznámení úplných kolekcí. Prahová hodnota, kterou používáte není důležité, protože čekáte na dokončení kolekce spíše než přístup kolekce. Potom můžete volat <xref:System.GC.WaitForFullGCComplete%2A?displayProperty=nameWithType> metodu, která blokuje, dokud není dokončena úplná kolekce. Můžete vytvořit vlákno, které volá metodu ve smyčce a provádí všechny nezbytné analýzy vždy, když se vrátí metoda.

Alternativně můžete volat <xref:System.GC.CollectionCount%2A?displayProperty=nameWithType> metodu pravidelně a zjistěte, zda se zvýšil počet kolekcí generace 2. V závislosti na četnostdotazování tato technika nemusí poskytnout jako přesný údaj o výskytu úplné kolekce.

#### <a name="hosting-api"></a>Hostování ROZHRANÍ API

Pokud používáte nespravované hostitelské rozhraní API, váš hostitel musí předat CLR implementaci rozhraní [IHostGCManager.](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md) CLR volá [metodu IHostGCManager::SuspensionEnding,](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) když pokračuje v provádění vláken, které byly pozastaveny, zatímco dojde k kolekci. CLR předá generování dokončené kolekce jako parametr metody, takže hostitel může určit, zda kolekce byla úplná nebo částečná. Implementace metody [IHostGCManager::SuspensionEnding](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) může dotazovat na dochovozit paměti, aby bylo zajištěno, že počty jsou načteny, jakmile jsou aktualizovány.

## <a name="see-also"></a>Viz také

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [ICLRAppDomainResourceMonitor – rozhraní](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [\<appDomainResourceMonitoring>](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [Události ETW CLR](../../../docs/framework/performance/clr-etw-events.md)
