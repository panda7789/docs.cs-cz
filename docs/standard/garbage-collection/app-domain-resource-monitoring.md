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
ms.openlocfilehash: 50d601d711579bce2e2651a1efc65d824a50d47a
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44354079"
---
# <a name="application-domain-resource-monitoring"></a>Sledování prostředků domény aplikace
(ARM) sledování prostředků domény aplikace umožňuje hostitelům k monitorování využití procesoru a paměti doménou aplikace. To je užitečné pro hostitele jako je ASP.NET, které používají mnoha aplikačními doménami v dlouho běžící proces. Hostitel může uvolnění domény aplikace aplikace, které nepříznivě ovlivňuje výkon celého procesu, ale pouze pokud může zjistit problematické aplikace. ARM poskytuje informace, které můžete použít pro pomoc při rozhodování.  
  
 Hostitelská služba například může mít mnoho aplikací spuštěných na serveru ASP.NET. Pokud jedna aplikace v procesu začne přijímat příliš mnoho paměti nebo příliš mnoho času procesoru, hostitelské služby slouží k identifikaci domény aplikace, která je příčinou problému ARM.  
  
 ARM je dostatečně jednoduché pro použití v živé aplikace. Přístup k informacím pomocí trasování událostí pro Windows (ETW) nebo přímo prostřednictvím rozhraní API pro spravované nebo nativní.  
  
## <a name="enabling-resource-monitoring"></a>Povolení sledování prostředků  
 ARM je možné povolit čtyři způsoby: zadáním konfiguračního souboru při spuštění common language runtime (CLR), s použitím nespravované hostování rozhraní API, pomocí spravovaného kódu nebo prostřednictvím naslouchání události trasování událostí pro Windows ARM.  
  
 Jakmile ARM je povoleno, začne shromažďování dat ve všech doménách aplikace v procesu. Pokud domény aplikace byl vytvořen před povolením ARM, souhrnná data začne, když je povoleno ARM, není při vytváření domény aplikace. Jakmile je povoleno, ARM nejde zakázat.  
  
-   ARM můžete povolit při spuštění modulu CLR tak, že přidáte [ \<appdomainresourcemonitoring – >](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md) prvku do konfiguračního souboru a nastavení `enabled` atribut `true`. Hodnota `false` (výchozí) znamená, že pouze, ARM není povoleno při spuštění, můžete si ji můžou aktivovat později pomocí jednoho z jiných mechanismů aktivace.  
  
-   Hostitele můžete povolit ARM, můžete si vyžádat [iclrappdomainresourcemonitor –](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) hostování rozhraní. Jakmile se toto rozhraní je byly úspěšně načteny, ARM je povolená.  
  
-   Spravovaný kód můžete povolit ARM nastavením statické (`Shared` v jazyce Visual Basic) <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> vlastnost `true`. Jakmile je vlastnost nastavena, je povoleno ARM.  
  
-   Po spuštění můžete povolit ARM prostřednictvím naslouchání události trasování událostí pro Windows. ARM je povolená a začne vyvolávání událostí pro všechny domény aplikace, když povolíte veřejného poskytovatele `Microsoft-Windows-DotNETRuntime` pomocí `AppDomainResourceManagementKeyword` – klíčové slovo. K chybě korelace dat. s doménami aplikací a vláken, musíte také povolit `Microsoft-Windows-DotNETRuntimeRundown` zprostředkovatele s `ThreadingKeyword` – klíčové slovo.  
  
## <a name="using-arm"></a>Použití ARM  
 ARM poskytuje celkový procesorový čas, který používá aplikační doméně a tři druhy informací o využití paměti.  
  
-   **Celkový čas procesoru pro doménu aplikace v řádu sekund**: Tento výpočet součtem doby vlákna operačního systému pro všechna vlákna, které spotřebovávají doba provádění v doméně aplikace v průběhu svého životního cyklu. Zablokuje nebo spící vláken nepoužívejte času procesoru. Když vlákno volá do nativního kódu, čas, který stráví vlákna v nativním kódu je součástí počet aplikační domény, ve kterém bylo provedeno volání.  
  
    -   Spravované rozhraní API: <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> vlastnost.  
  
    -   Hostování rozhraní API: [iclrappdomainresourcemonitor::getcurrentcputime –](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md) metody.  
  
    -   Události trasování událostí pro Windows: `ThreadCreated`, `ThreadAppDomainEnter`, a `ThreadTerminated` události. Informace o poskytovatelích a klíčová slova, naleznete v tématu "AppDomain zdroje událostí pro sledování" v [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md).  
  
-   **Celkový počet spravovaných přidělení provedených doménou aplikace během celé jeho životnosti, v bajtech**: Celkový počet přidělení nemusí pokaždé odpovídat využití paměti doménou aplikace, protože přidělené objekty může mít krátkodobé a jednorázové. Ale pokud aplikace přiděluje a uvolňuje velký počet objektů, náklady na přidělení může být významné.  
  
    -   Spravované rozhraní API: <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> vlastnost.  
  
    -   Hostování rozhraní API: [iclrappdomainresourcemonitor::getcurrentallocated –](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md) metody.  
  
    -   Události trasování událostí pro Windows: `AppDomainMemAllocated` události, `Allocated` pole.  
  
-   **Spravované paměti v bajtech, na který odkazuje domény aplikace a který zůstat naživu při poslední úplné blokující kolekce**: Toto číslo je přesné až po plně, blokující kolekce. (Jde na rozdíl od souběžných kolekcí, které probíhá na pozadí a neblokují aplikace.) Například <xref:System.GC.Collect?displayProperty=nameWithType> přetížení metody způsobí, že úplné blokující kolekce.  
  
    -   Spravované rozhraní API: <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> vlastnost.  
  
    -   Hostování rozhraní API: [iclrappdomainresourcemonitor::getcurrentsurvived –](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) metody `pAppDomainBytesSurvived` parametru.  
  
    -   Události trasování událostí pro Windows: `AppDomainMemSurvived` události, `Survived` pole.  
  
-   **Celkový počet spravované paměti v bajtech, na který odkazuje procesu a který zůstat naživu při poslední úplné blokující kolekce**: zachované paměť pro jednotlivé aplikační domény je možné porovnat s tímto číslem.  
  
    -   Spravované rozhraní API: <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType> vlastnost.  
  
    -   Hostování rozhraní API: [iclrappdomainresourcemonitor::getcurrentsurvived –](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) metody `pTotalBytesSurvived` parametru.  
  
    -   Události trasování událostí pro Windows: `AppDomainMemSurvived` události, `ProcessSurvived` pole.  
  
### <a name="determining-when-a-full-blocking-collection-occurs"></a>Blokující kolekce dojde k určení, kdy plně,  
 K určení, kdy jsou přesné počty zachované paměti, je potřeba vědět, kdy má právě došlo k úplné, blokující kolekce. Metoda to závisí na rozhraní API, použijte ke kontrole statistik ARM.  
  
#### <a name="managed-api"></a>Spravované rozhraní API  
 Pokud používáte vlastnosti <xref:System.AppDomain> třídy, můžete použít <xref:System.GC.RegisterForFullGCNotification%2A?displayProperty=nameWithType> metoda registrace pro oznámení o celé kolekce. Prahová hodnota, které používáte není důležitá, protože se během čekání na dokončení kolekce spíše než přístup kolekce. Potom můžete zavolat <xref:System.GC.WaitForFullGCComplete%2A?displayProperty=nameWithType> metodu, která blokuje, dokud se nedokončí celé kolekce. Můžete vytvořit vlákno, které volá metodu ve smyčce a provede všechny potřeby analýzy pokaždé, když se metoda vrátí.  
  
 Alternativně můžete volat <xref:System.GC.CollectionCount%2A?displayProperty=nameWithType> metoda pravidelně, chcete-li zobrazit, pokud se zvýšil počet kolekce generace 2. V závislosti na frekvenci dotazování tuto techniku pravděpodobně naznačují, jako přesné výskytu celé kolekce.  
  
#### <a name="hosting-api"></a>Hostování rozhraní API  
 Pokud používáte nespravované hostujícího rozhraní API, váš hostitel musí projít CLR implementace [ihostgcmanager –](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md) rozhraní. Volání CLR [ihostgcmanager::suspensionending –](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) metody pokračuje v provádění vlákna, která byla pozastavena, když dojde k kolekce. CLR generování dokončené kolekce předá jako parametr metody, tak hostitele můžete určit, zda byla kolekce celé nebo jeho část. Implementace [ihostgcmanager::suspensionending –](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) metoda vyhledávat zachované paměti, chcete-li zajistit, aby počty jsou načteny, jako jsou aktualizovány.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
- [ICLRAppDomainResourceMonitor – rozhraní](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
- [\<appdomainresourcemonitoring – >](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)  
- [Události Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-events.md)
