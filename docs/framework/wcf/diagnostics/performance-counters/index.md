---
title: "Čítače výkonu WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: performance counters [WCF]
ms.assetid: f559b2bd-ed83-4988-97a1-e88f06646609
caps.latest.revision: "37"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f3f9834e99fb7fa98e2f986a1ce5460aa387143f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-performance-counters"></a>Čítače výkonu WCF
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]obsahuje velké sady čítačů výkonu můžete měřit výkon vaší aplikace.  
  
## <a name="enabling-performance-counters"></a>Povolení čítače výkonu  
 Můžete povolit čítače výkonu pro [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] přes z konfiguračního souboru app.config [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služby následujícím způsobem:  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
    </system.serviceModel>  
</configuration>  
```  
  
 `performanceCounters` Atributu můžete nastavit pro povolení určitý typ čítače výkonu. Platné hodnoty jsou  
  
-   All: Všechny kategorie čítače (ServiceModelService, ServiceModelEndpoint a ServiceModelOperation) jsou povoleny.  
  
-   ServiceOnly: Jsou povoleny pouze ServiceModelService kategorie čítače. Jedná se o výchozí hodnotu.  
  
-   Vypnuto: Čítače výkonu ServiceModel * jsou zakázány.  
  
 Pokud chcete povolit čítače výkonu pro všechny [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] aplikace, nastavení konfigurace můžete umístit v souboru Machine.config.  Najdete v tématu **zvýšit velikost paměti pro čítače výkonu** části níže pro další informace o konfiguraci dostatek paměti pro čítače výkonu v počítači.  
  
 Pokud používáte [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] body rozšiřitelnosti například vlastní operaci invokers jste měli také emitování čítače výkonu. Je to proto, pokud byste implementovat bod rozšiřitelnosti, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] může už negeneruje data čítače výkonu standardní ve výchozí cestě. Pokud jste neimplementuje podporu čítače výkonu ruční, nemusíte vidět data čítače výkonu, které očekáváte.  
  
 Můžete také povolit čítače výkonu ve vašem kódu následujícím způsobem  
  
```  
using System.Configuration;  
using System.ServiceModel.Configuration;  
using System.ServiceModel.Diagnostics;  
Configuration config = ConfigurationManager.OpenExeConfiguration(  
    ConfigurationUserLevel.None);  
ServiceModelSectionGroup sg = ServiceModelSectionGroup.GetSectionGroup(config);  
sg.Diagnostic.PerformanceCounters = PerformanceCounterScope.All;  
config.Save();  
```  
  
## <a name="viewing-performance-data"></a>Zobrazení dat výkonu  
 Chcete-li zobrazit data zaznamenaná podle čítače výkonu, můžete použít sledování výkonu (Perfmon.exe), která se dodává s Windows. Tento nástroj můžete spustit přechodem na **spustit**a klikněte na tlačítko **spustit** a typ `perfmon.exe` v dialogovém okně.  
  
> [!NOTE]
>  Instance čítače výkonu se může uvolnit před poslední zprávy byly zpracovány dispečera koncový bod. Výsledkem může být data výkonu není zaznamenaná pro několik zprávy.  
  
## <a name="increasing-memory-size-for-performance-counters"></a>Zvýšit velikost paměti pro čítače výkonu  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]používá samostatné sdílené paměti pro jeho kategorie čítače výkonu.  
  
 Ve výchozím nastavení je samostatnou sdílené paměti hodnotu čtvrtletí velikost globálního výkonu čítače paměti. Výchozí globální výkonu čítač paměť je 524,288 bajtů. Proto tří [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] kategorie čítače výkonu mají výchozí velikost přibližně 128 KB. V závislosti na vlastnosti runtime [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] může dojít k vyčerpání aplikace na počítači, paměti čítače výkonu. V takovém případě [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zapíše chybu do protokolu událostí aplikace. Obsah chyba stavy nebyla načtena čítače výkonu, a položka obsahuje výjimku "System.InvalidOperationException: vlastní čítače souboru zobrazení je nedostatek paměti." Pokud je trasování povoleno na úrovni chyba, toto selhání je také trasovat. Pokud dojde k vyčerpání paměti čítače výkonu, pokračování v používání vaší [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] aplikací pomocí čítače výkonu, které jsou povolené může způsobit snížení výkonu. Pokud jste správce počítače, byste ho měli nakonfigurovat přidělit dostatek paměti pro podporu maximální počet čítače výkonu, které může existovat kdykoli.  
  
 Můžete změnit velikost paměti čítače výkonu pro [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] kategorií v registru. To pokud chcete udělat, je nutné přidat novou hodnotu DWORD s názvem `FileMappingSize` do tří následujících umístění a nastavte ji na požadovanou hodnotu v bajtech. Restartujte svůj počítač tak, aby se projevily změny.  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance  
  
 Když jsou odstraněny velký počet objektů (například ServiceHost), ale čeká na uklizeny, `PrivateBytes` čítače výkonu se registrují neobvykle vysoké číslo. Chcete-li vyřešit tento problém, můžete buď přidejte vlastní čítače specifické pro aplikace nebo použijte `performanceCounters` atribut pro povolení čítače pouze úrovně služby.  
  
## <a name="types-of-performance-counters"></a>Typy čítačů výkonu  
 Čítače výkonu jsou omezená na tři různé úrovně: služby, koncový bod a operace.  
  
 Můžete načíst název instance čítače výkonu služby WMI. Například  
  
-   Název instance čítače služby můžete získat prostřednictvím služby WMI [služby](../../../../../docs/framework/wcf/diagnostics/wmi/service.md) "CounterInstanceName" vlastnost instance.  
  
-   Název instance čítače koncového bodu můžete získat prostřednictvím služby WMI [koncový bod](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) "CounterInstanceName" vlastnost instance.  
  
-   Název instance čítače operace můžete získat prostřednictvím služby WMI [koncový bod](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) metodu instance "GetOperationCounterInstanceName".  
  
 Další informace o rozhraní WMI najdete v tématu [pomocí rozhraní Windows Management Instrumentation pro diagnostiku](../../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
### <a name="service-performance-counters"></a>Čítače výkonu služby  
 Čítače výkonu služby měřit chování služby jako celek a umožňuje diagnostikovat provádění celou služeb. Najdete v části `ServiceModelService 4.0.0.0` objekt výkonu při zobrazení pomocí sledování výkonu. Instance jsou pojmenované pomocí následujícího vzorce:  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
 Čítače v oboru služby se shromažďují z čítače v kolekci koncových bodů.  
  
 Čítače výkonu pro vytvoření instance služby se zvýší, když se vytvoří nový objekt InstanceContext. Všimněte si, že i když obdržíte zprávu bez aktivace (s existující službu), nebo při připojení k instanci z jedné relace, ukončením relace a poté znovu připojit z jiné relace je vytvořen nový objekt InstanceContext.  
  
### <a name="endpoint-performance-counters"></a>Čítače výkonu koncového bodu  
 Čítače výkonu koncového bodu umožňují podívejte se na data, která znázorňuje, jak koncový bod přijímá zprávy. Najdete v části `ServiceModelEndpoint 4.0.0.0` objekt výkonu při zobrazení pomocí sledování výkonu. Instance jsou pojmenované pomocí následujícího vzorce:  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 Data je podobná co se shromažďují pro jednotlivé operace, ale je pouze agregován přes koncový bod.  
  
 Čítače v oboru koncový bod se shromažďují z čítačů v kolekci operací.  
  
> [!NOTE]
>  Pokud dva koncové body mají stejné kontrakt názvy a adresy, jsou namapované na stejnou instanci čítače.  
  
### <a name="operation-performance-counters"></a>Čítače provozního výkonu  
 Čítače provozního výkonu se nacházejí v části `ServiceModelOperation 4.0.0.0` objekt výkonu při zobrazení pomocí sledování výkonu. Každá operace má jednotlivé instance. To znamená Pokud danou zakázku má 10 operace, 10 instancí čítače operace jsou přidruženy k této smlouvy. Instance objektů jsou pojmenované pomocí následujícího vzorce:  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 Tento čítač umožňuje měření využití volání a jak dobře fungují operaci.  
  
 Pokud čítače jsou viditelné na víc oborů, jsou data shromážděná z vyššího oboru agregován s daty z nižší oborů. Například `Calls` na koncový bod představuje součet hodnot všechna volání operace v rámci koncový bod; `Calls` na službu představuje součet hodnot všechna volání všechny koncové body v rámci služby.  
  
> [!NOTE]
>  Pokud máte operaci duplicitní názvy na kontraktu, zobrazí pouze jedna instance čítače pro obě operace.  
  
## <a name="programming-the-wcf-performance-counters"></a>Programování čítače výkonu WCF  
 Několik souborů jsou nainstalovány ve složce instalace sady SDK, takže může získat přístup [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] čítače výkonu prostřednictvím kódu programu. Tyto soubory jsou uvedené následujícím způsobem.  
  
-   _ServiceModelEndpointPerfCounters.vrg  
  
-   _ServiceModelOperationPerfCounters.vrg  
  
-   _ServiceModelServicePerfCounters.vrg  
  
-   _SMSvcHostPerfCounters.vrg  
  
-   _TransactionBridgePerfCounters.vrg  
  
 Další informace o tom, jak počítadla přístup prostřednictvím kódu programu najdete v tématu [architektura programování čítače výkonu](http://go.microsoft.com/fwlink/?LinkId=95179).  
  
## <a name="see-also"></a>Viz také  
 [Správa a Diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
