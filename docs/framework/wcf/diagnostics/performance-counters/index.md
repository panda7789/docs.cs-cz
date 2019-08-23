---
title: Čítače výkonu WCF
ms.date: 03/30/2017
helpviewer_keywords:
- performance counters [WCF]
ms.assetid: f559b2bd-ed83-4988-97a1-e88f06646609
ms.openlocfilehash: 4368bd57718f52816d4efad39932bcc0959b67a2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951303"
---
# <a name="wcf-performance-counters"></a>Čítače výkonu WCF
Windows Communication Foundation (WCF) obsahuje velkou sadu čítačů výkonu, které vám pomůžou posoudit výkon aplikace.  
  
## <a name="enabling-performance-counters"></a>Povolení čítačů výkonu  
 Můžete povolit čítače výkonu pro službu WCF prostřednictvím konfiguračního souboru App. config služby WCF následujícím způsobem:  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
    </system.serviceModel>  
</configuration>  
```  
  
 `performanceCounters` Atribut lze nastavit tak, aby povoloval konkrétní typ čítačů výkonu. Platné hodnoty jsou  
  
- Všem Jsou povoleny všechny čítače kategorií (ServiceModelService, ServiceModelEndpoint a ServiceModelOperation).  
  
- ServiceOnly: Jsou povoleny pouze čítače kategorií ServiceModelService. Jedná se o výchozí hodnotu.  
  
- Zaokrouhl Čítače výkonu ServiceModel * jsou zakázané.  
  
 Pokud chcete povolit čítače výkonu pro všechny aplikace WCF, můžete nastavení konfigurace umístit do souboru Machine. config.  Další informace o konfiguraci dostatečné paměti pro čítače výkonu na počítači najdete v části **zvětšení paměti pro čítače výkonu** .  
  
 Pokud používáte body rozšiřitelnosti WCF, jako je například vlastní operace invokers, měli byste také vygenerovat vlastní čítače výkonu. Důvodem je, že pokud implementujete bod rozšiřitelnosti, WCF již nesmí generovat standardní data čítače výkonu ve výchozí cestě. Pokud neimplementujete ruční podporu čítače výkonu, nemusí se vám zobrazovat očekávaná data čítače výkonu.  
  
 Čítače výkonu můžete v kódu povolit také následujícím způsobem:  
  
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
  
## <a name="viewing-performance-data"></a>Zobrazení údajů o výkonu  
 Chcete-li zobrazit data zachycená čítači výkonu, můžete použít nástroj sledování výkonu (Perfmon. exe), který je součástí systému Windows. Tento nástroj můžete spustit tak, že přejdete na **Start**a kliknete na `perfmon.exe` **Spustit** a do dialogového okna zadejte.  
  
> [!NOTE]
> Instance čítače výkonu mohou být vydány před tím, než byly poslední zprávy zpracovány dispečerem koncového bodu. To může vést k tomu, že se data o výkonu nezaznamenávají pro několik zpráv.  
  
## <a name="increasing-memory-size-for-performance-counters"></a>Zvýšení velikosti paměti pro čítače výkonu  
 WCF používá pro kategorie čítače výkonu samostatnou sdílenou paměť.  
  
 Ve výchozím nastavení je samostatná sdílená paměť nastavená na čtvrtinu velikosti globální paměti čítače výkonu. Výchozí globální paměť čítače výkonu je 524 288 bajtů. Proto tři kategorie čítače výkonu WCF mají výchozí velikost přibližně 128 KB každého. V závislosti na charakteristikách modulu runtime aplikací WCF na počítači může být vyčerpána paměť čítače výkonu. Pokud k tomu dojde, WCF zapíše chybu do protokolu událostí aplikace. Obsah chyby uvádí, že čítač výkonu nebyl načten, a položka obsahuje výjimku "System. InvalidOperationException: Zobrazení souboru vlastních čítačů není dostatek paměti. " Pokud je trasování povoleno na úrovni chyby, tato chyba se také sleduje. Pokud je paměť čítače výkonu vyčerpána, může pokračovat v spouštění aplikací WCF s povolenými čítači výkonu, což může způsobit snížení výkonu. Pokud jste správcem počítače, měli byste ho nakonfigurovat, aby bylo možné přidělit dostatek paměti pro podporu maximálního počtu čítačů výkonu, které mohou existovat kdykoli.  
  
 Můžete změnit množství paměti čítače výkonu pro kategorie WCF v registru. K tomu je potřeba přidat novou hodnotu DWORD s názvem `FileMappingSize` do tří následujících umístění a nastavit ji na požadovanou hodnotu v bajtech. Restartujte počítač, aby byly tyto změny uplatněny.  
  
- HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance  
  
- HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance  
  
- HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance  
  
 V `PrivateBytes` případě, že je velký počet objektů (například ServiceHost) vyřazen z paměti, ale čeká na uvolňování paměti, bude čítač výkonu registrovat neobvykle vysoké číslo. Chcete-li tento problém vyřešit, můžete buď přidat vlastní čítače specifické pro danou aplikaci, nebo pomocí `performanceCounters` atributu povolit pouze čítače na úrovni služby.  
  
## <a name="types-of-performance-counters"></a>Typy čítačů výkonu  
 Čítače výkonu jsou vymezeny na tři různé úrovně: Služba, koncový bod a operace.  
  
 Pomocí rozhraní WMI můžete načíst název instance čítače výkonu. Například  
  
- Název instance čítače služby se dá získat prostřednictvím vlastnosti CounterInstanceName instance [služby](../../../../../docs/framework/wcf/diagnostics/wmi/service.md) WMI.  
  
- Název instance čítače koncového bodu se dá získat pomocí vlastnosti CounterInstanceName instance [koncového bodu](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) služby WMI.  
  
- Název instance čítače operace se dá získat pomocí metody GetOperationCounterInstanceName instance [koncového bodu](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) služby WMI.  
  
 Další informace o rozhraní WMI najdete v tématu [použití rozhraní WMI (Windows Management Instrumentation) pro diagnostiku](../../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
### <a name="service-performance-counters"></a>Čítače výkonu služby  
 Čítače výkonu služby měří chování služby jako celku a dají se použít k diagnostice výkonu celé služby. Lze je najít v `ServiceModelService 4.0.0.0` objektu výkonu při zobrazení pomocí nástroje sledování výkonu. Instance jsou pojmenovány pomocí následujícího vzoru:  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
 Čítač v oboru služby je agregován z čítače v kolekci koncových bodů.  
  
 Čítače výkonu pro vytvoření instance služby se zvýší při vytvoření nové třídy InstanceContext. Všimněte si, že se vytvoří nová třída InstanceContext, i když obdržíte neaktivační zprávu (s existující službou) nebo když se připojíte k instanci z jedné relace, ukončíte relaci a pak se znovu připojíte z jiné relace.  
  
### <a name="endpoint-performance-counters"></a>Čítače výkonu koncového bodu  
 Čítače výkonu koncového bodu umožňují podívat se na data, která odrážejí, jak koncový bod přijímá zprávy. Lze je najít v `ServiceModelEndpoint 4.0.0.0` objektu výkonu při zobrazení pomocí nástroje sledování výkonu. Instance jsou pojmenovány pomocí následujícího vzoru:  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 Data jsou podobná tomu, co se shromažďují pro jednotlivé operace, ale agreguje se jenom v rámci koncového bodu.  
  
 Čítač v rozsahu koncového bodu je agregovaný z čítačů v kolekci operací.  
  
> [!NOTE]
> Pokud dva koncové body mají stejné názvy kontraktů a adres, jsou namapovány na stejnou instanci čítače.  
  
### <a name="operation-performance-counters"></a>Čítače výkonu operací  
 Čítače výkonu operace se při prohlížení s `ServiceModelOperation 4.0.0.0` monitorováním výkonu nacházejí v objektu výkonu. Každá operace má jednotlivou instanci. To znamená, že pokud má daný kontrakt 10 operací, je k této smlouvě přidruženo 10 instancí čítače operací. Instance objektů jsou pojmenovány pomocí následujícího vzoru:  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 Tento čítač vám umožní změřit způsob, jakým se volání používá, a to, jak dobře probíhá operace.  
  
 Když jsou čítače viditelné ve více oborech, data shromážděná z většího rozsahu jsou agregována s daty z nižších rozsahů. Například `Calls` na koncovém bodu představuje součet všech volání operací v rámci koncového bodu. `Calls` ve službě představuje součet všech volání všech koncových bodů v rámci služby.  
  
> [!NOTE]
> Pokud ve smlouvě máte duplicitní názvy operací, získáte pro obě operace jenom jednu instanci čítače.  
  
## <a name="programming-the-wcf-performance-counters"></a>Programování čítačů výkonu WCF  
 V instalační složce sady SDK je nainstalováno několik souborů, aby bylo možné získat přístup k čítačům výkonu WCF programově. Tyto soubory jsou uvedené níže.  
  
- _ServiceModelEndpointPerfCounters.vrg  
  
- _ServiceModelOperationPerfCounters.vrg  
  
- _ServiceModelServicePerfCounters.vrg  
  
- _SMSvcHostPerfCounters.vrg  
  
- _TransactionBridgePerfCounters.vrg  
  
 Další informace o tom, jak programově přistupovat k čítačům, najdete v tématu [Architektura programování čítače výkonu](https://go.microsoft.com/fwlink/?LinkId=95179).  
  
## <a name="see-also"></a>Viz také:

- [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
