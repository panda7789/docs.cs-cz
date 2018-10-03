---
title: Čítače výkonu WCF
ms.date: 03/30/2017
helpviewer_keywords:
- performance counters [WCF]
ms.assetid: f559b2bd-ed83-4988-97a1-e88f06646609
ms.openlocfilehash: d0ad7ee0bc3ea1d15197e6b8d9888d60b21a2f15
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48032693"
---
# <a name="wcf-performance-counters"></a>Čítače výkonu WCF
Windows Communication Foundation (WCF) obsahuje velké sady čítače výkonu umožňují měřit výkon vaší aplikace.  
  
## <a name="enabling-performance-counters"></a>Povolení čítače výkonu  
 Čítače výkonu služby WCF pomocí konfiguračního souboru app.config služby WCF můžete povolit následujícím způsobem:  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
    </system.serviceModel>  
</configuration>  
```  
  
 `performanceCounters` Atribut můžete nastavit pro povolení konkrétní typ čítače výkonu. Platné hodnoty jsou  
  
-   All: Všechny kategorie čítače (ServiceModelService, ServiceModelEndpoint a ServiceModelOperation) jsou povoleny.  
  
-   ServiceOnly: Jsou povoleny pouze ServiceModelService kategorie čítače. Jedná se o výchozí hodnotu.  
  
-   Vypnuto: Čítače výkonu ServiceModel * jsou zakázány.  
  
 Pokud chcete povolit čítače výkonu pro všechny aplikace, WCF, můžete umístit nastavení konfigurace v souboru Machine.config.  Podrobnosti najdete **zvýšit velikost paměti pro čítače výkonu** níže v části Další informace o konfiguraci na svém počítači dostatek paměti pro čítače výkonu.  
  
 Pokud používáte bodů rozšiřitelnosti WCF, jako je vlastní operace invokers, by měly taky vydávat vlastní čítače výkonu. Je to proto, že pokud se rozhodnete implementovat bod rozšiřitelnosti, WCF může už negeneruje data čítače výkonu ve výchozí cestě. Pokud implementujete není podpora čítače výkonu ruční, nemusíte vidět data čítače výkonu, které očekáváte.  
  
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
 Chcete-li zobrazit data zachycená pomocí čítačů výkonu, můžete použít sledování výkonu (Perfmon.exe), který je součástí Windows. Tento nástroj můžete spustit tak, že přejdete do **Start**a klikněte na tlačítko **spustit** a typ `perfmon.exe` v dialogovém okně.  
  
> [!NOTE]
>  Instance čítače výkonu může uvolnit před poslední zprávy byly zpracovány Dispečer koncového bodu. Výsledkem může být údaje o výkonu není zachycena pro několik zpráv.  
  
## <a name="increasing-memory-size-for-performance-counters"></a>Zvětšení velikosti paměti pro čítače výkonu  
 WCF používá samostatné sdílené paměti pro své kategorie čítače výkonu.  
  
 Ve výchozím nastavení je samostatnou sdílenou paměť nastavit čtvrtletí velikost globálního výkonu čítače paměti. Výchozí globálního výkonu čítače paměti je 524,288 bajtů. Proto se tři kategorie čítače výkonu WCF mají výchozí velikost přibližně 128 kB. V závislosti na vlastnosti modul runtime WCF aplikací na počítači, může být vyčerpání paměti čítače výkonu. Pokud k tomu dojde, WCF zapíše chybu do protokolu událostí aplikace. Obsah chyba uvádí, že čítač výkonu nebyl načten a položka obsahuje výjimku "System.InvalidOperationException: zobrazení souboru vlastních čítačů je nedostatek paměti." Pokud je povoleno trasování na úrovni chyby, je také sledovat toto selhání. Pokud dojde k vyčerpání paměti čítače výkonu, pokračování a spouštění aplikací WCF pomocí čítačů výkonu povolena by mohlo způsobit snížení výkonu. Pokud jste správcem počítače, měli byste nakonfigurovat ji přidělit dostatek paměti pro podporu maximální počet čítačů výkonu, které mohou existovat v každém okamžiku.  
  
 Můžete změnit velikost paměti čítače výkonu WCF kategorií v registru. Uděláte to tak, budete muset přidat novou hodnotu DWORD s názvem `FileMappingSize` do tří následujících umístění a nastavte ji na požadovanou hodnotu v bajtech. Po restartování počítače, aby tyto změny jsou přijata platit.  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance  
  
 Když jsou odstraněny velký počet objektů (například hostitel služby) ale čeká na prováděno uvolnění paměti `PrivateBytes` čítače výkonu se registrují neobvykle velký počet. Chcete-li vyřešit tento problém, můžete buď přidat čítače specifické pro aplikaci nebo použijte `performanceCounters` atribut pro povolení pouze SLA čítače.  
  
## <a name="types-of-performance-counters"></a>Typy čítačů výkonu  
 Čítače výkonu jsou omezená na třech různých úrovních: služba, koncový bod a operace.  
  
 Chcete-li načíst název instance čítače výkonu můžete použít rozhraní WMI. Například  
  
-   Název instance čítače služby můžete získat prostřednictvím rozhraní WMI [služby](../../../../../docs/framework/wcf/diagnostics/wmi/service.md) vlastnost "CounterInstanceName" instance.  
  
-   Název instance čítače koncového bodu můžete získat prostřednictvím rozhraní WMI [koncový bod](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) vlastnost "CounterInstanceName" instance.  
  
-   Název instance čítače operace můžete získat prostřednictvím rozhraní WMI [koncový bod](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) "GetOperationCounterInstanceName" metodu instance.  
  
 Další informace o rozhraní WMI najdete v tématu [pomocí Windows Management Instrumentation k diagnostice](../../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
### <a name="service-performance-counters"></a>Čítače výkonu služby  
 Čítače výkonu služby měření chování služby jako celek a slouží k diagnostice výkonu celou službu. Najdete v části `ServiceModelService 4.0.0.0` objekt výkonu při zobrazení pomocí sledování výkonu. Tyto instance jsou pojmenovány pomocí následujícího vzorce:  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
 Čítače v oboru služby se shromažďuje od čítače v kolekce koncových bodů.  
  
 Čítače výkonu pro vytvoření instance služby se zvýší, když se vytvoří nová třída InstanceContext. Všimněte si, že se vytvoří nová třída InstanceContext, i když obdržíte zprávu bez aktivace (s existující služby), nebo když připojit k instanci služby z jedné relace, ukončit relaci a potom se znova připojit z jiné relace.  
  
### <a name="endpoint-performance-counters"></a>Čítače výkonu koncového bodu  
 Čítače výkonu koncového bodu umožňují podívat se na data, která odráží, jak koncový bod přijímá zprávy. Najdete v části `ServiceModelEndpoint 4.0.0.0` objekt výkonu při prohlížení použití nástroje Sledování výkonu. Tyto instance jsou pojmenovány pomocí následujícího vzorce:  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 Data jsou podobné, co se shromažďují pro jednotlivé operace, ale pouze se agreguje přes koncový bod.  
  
 Čítače v oboru koncový bod se shromažďuje od čítače v kolekci operací.  
  
> [!NOTE]
>  Pokud dva koncové body mají stejné kontraktu jména a adresy, jsou mapovány na stejnou instanci čítače.  
  
### <a name="operation-performance-counters"></a>Čítače provozního výkonu  
 Čítače provozního výkonu se nacházejí v rámci `ServiceModelOperation 4.0.0.0` objekt výkonu při zobrazení pomocí nástroje Sledování výkonu. Každá operace má jednotlivé instance. To znamená že pokud má daný kontrakt 10 operací, jsou 10 instancí čítače operace spojené s touto smlouvou. Instance objektů jsou pojmenovány pomocí následujícího vzorce:  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 Tento čítač umožňuje měřit využití volání a jak dobře fungují operace.  
  
 Když čítače jsou viditelné v několika oborech, dat shromážděných z vyššího oboru se agregují s daty z nižší obory. Například `Calls` na koncový bod představuje součet všech volání operace v rámci koncový bod; `Calls` na službu představuje součet všech volání pro všechny koncové body v rámci služby.  
  
> [!NOTE]
>  Pokud máte na kontrakt operace duplicitní názvy, získáte jenom jedna instance čítačů pro obě operace.  
  
## <a name="programming-the-wcf-performance-counters"></a>Programování čítače výkonu WCF  
 Několik souborů se instalují do složky instalace sady SDK tak, aby čítače výkonu WCF můžete přistupovat prostřednictvím kódu programu. Tyto soubory jsou uvedeny následovně.  
  
-   _ServiceModelEndpointPerfCounters.vrg  
  
-   _ServiceModelOperationPerfCounters.vrg  
  
-   _ServiceModelServicePerfCounters.vrg  
  
-   _SMSvcHostPerfCounters.vrg  
  
-   _TransactionBridgePerfCounters.vrg  
  
 Další informace o tom, jak programově přístup k čítačům najdete v tématu [programovací architektura čítače výkonu](https://go.microsoft.com/fwlink/?LinkId=95179).  
  
## <a name="see-also"></a>Viz také  
 [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
