---
title: Diagnostikování transakčních aplikací
ms.date: 03/30/2017
ms.assetid: 4a993492-1088-4d10-871b-0c09916af05f
ms.openlocfilehash: fb3a83083e876cf697621ba70dcf7dd67636f83a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599214"
---
# <a name="diagnosing-transactional-applications"></a>Diagnostikování transakčních aplikací
Toto téma popisuje, jak používat funkci správy a diagnostiky služby Windows Communication Foundation (WCF) k řešení potíží s transakční aplikací.  
  
## <a name="performance-counters"></a>Čítače výkonu  
 WCF poskytuje standardní sadu čítačů výkonu pro měření výkonu transakční aplikace. Další informace najdete v tématu [čítače výkonu](../diagnostics/performance-counters/index.md).  
  
 Čítače výkonu jsou vymezeny na tři různé úrovně: služba, koncový bod a operace, jak je popsáno v následujících tabulkách.  
  
### <a name="service-performance-counters"></a>Čítače výkonu služby  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|Počet plynoucích transakcí|Počet transakcí, které byly v této službě převedeny do operací. Tento čítač se zvyšuje vždy, když se ve zprávě, která je odeslána do služby, vyskytuje transakce.|  
|Počet plynoucích transakcí za sekundu|Počet transakcí, které byly v rámci této služby do každé sekundy předávány do operací. Tento čítač se zvyšuje vždy, když se ve zprávě, která je odeslána do služby, vyskytuje transakce.|  
|Počet potvrzených zpracovaných operací|Počet provedených zpracovaných operací, jejichž transakce byla dokončena s výsledkem potvrzeným v této službě. Práce prováděná v rámci takových operací je plně potvrzena. Prostředky jsou aktualizovány v souladu s prací provedenou v rámci operace.|  
|Počet potvrzených zpracovaných operací za sekundu|Počet provedených zpracovaných operací, jejichž transakce byla dokončena s výsledkem potvrzeným v této službě v každé druhé. Práce prováděná v rámci takových operací je plně potvrzena. Prostředky jsou aktualizovány v souladu s prací provedenou v rámci operace.|  
|Počet přerušených transakčních operací|Počet provedených zpracovaných operací, jejichž transakce byla dokončena a výsledek byl v této službě přerušen. Práce prováděná v rámci takových operací se vrátí zpět. Prostředky se vrátí do předchozího stavu.|  
|Počet zrušených zpracovaných operací za sekundu|Počet provedených zpracovaných operací, jejichž transakce byla dokončena s výsledkem přerušeným v této službě v rámci každé sekundy. Práce prováděná v rámci takových operací se vrátí zpět. Prostředky se vrátí do předchozího stavu.|  
|Počet nejistých zpracovaných operací|Počet provedených zpracovaných operací, jejichž transakce byla dokončena s nejistým výsledkem v této službě. Práce prováděná s nejistým výsledkem je v neurčitém stavu. Prostředky jsou uchovávány v nedokončeném výsledku.|  
|Počet nejistých zpracovaných operací za sekundu|Počet provedených zpracovaných operací, jejichž transakce byla dokončena s nejistým výsledkem v této službě v rámci každé sekundy. Práce prováděná s nejistým výsledkem je v neurčitém stavu. Prostředky jsou uchovávány v nedokončeném výsledku.|  
  
### <a name="endpoint-performance-counters"></a>Čítače výkonu koncového bodu  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|Počet plynoucích transakcí|Počet transakcí, které byly v tomto koncovém bodu převedeny do operací. Tento čítač se zvyšuje vždy, když se ve zprávě odeslané do koncového bodu vyskytuje transakce.|  
|Počet plynoucích transakcí za sekundu|Počet transakcí, které byly za sekundu v tomto koncovém bodu převedeny do operací. Tento čítač se zvyšuje vždy, když se ve zprávě odeslané do koncového bodu vyskytuje transakce.|  
  
### <a name="operation-performance-counters"></a>Čítače provozního výkonu  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|Počet plynoucích transakcí|Počet transakcí, které byly v tomto koncovém bodu převedeny do operací. Tento čítač se zvyšuje vždy, když se ve zprávě odeslané do koncového bodu vyskytuje transakce.|  
|Počet plynoucích transakcí za sekundu|Počet transakcí, které byly za sekundu v tomto koncovém bodu převedeny do operací. Tento čítač se zvyšuje vždy, když se ve zprávě odeslané do koncového bodu vyskytuje transakce.|  
  
## <a name="windows-management-instrumentation"></a>WMI (Windows Management Instrumentation)  
 WCF zpřístupňuje kontrolní data služby za běhu prostřednictvím poskytovatele WCF rozhraní WMI (Windows Management Instrumentation) (WMI). Další informace o přístupu k datům WMI najdete v tématu věnovaném [použití rozhraní WMI (Windows Management Instrumentation) pro diagnostiku](../diagnostics/wmi/index.md).  
  
 Počet vlastností WMI jen pro čtení indikuje nastavení použité transakce pro službu. Všechna tato nastavení jsou uvedená v následujících tabulkách.  
  
 Ve službě `ServiceBehaviorAttribute` má následující vlastnosti.  
  
|Name|Typ|Popis|  
|----------|----------|-----------------|  
|ReleaseServiceInstanceOnTransactionComplete|Logická hodnota|Určuje, zda je objekt služby recyklován po dokončení aktuální transakce.|  
|TransactionAutoCompleteOnSessionClose|Logická hodnota|Určuje, zda jsou nevyřízené transakce dokončeny po zavření aktuální relace.|  
|TransactionIsolationLevel|Řetězec, který obsahuje platnou hodnotu <xref:System.Transactions.IsolationLevel> výčtu.|Určuje úroveň izolace transakce, kterou tato služba podporuje.|  
|Vlastnost TransactionTimeout|<xref:System.DateTime>|Určuje dobu, během které musí být transakce dokončena.|  
  
 `ServiceTimeoutsBehavior`Má následující vlastnost.  
  
|Name|Typ|Popis|  
|----------|----------|-----------------|  
|Vlastnost TransactionTimeout|<xref:System.DateTime>|Určuje dobu, během které musí být transakce dokončena.|  
  
 U vazby `TransactionFlowBindingElement` má následující vlastnosti.  
  
|Name|Typ|Popis|  
|----------|----------|-----------------|  
|TransactionProtocol|Řetězec, který obsahuje platnou hodnotu <xref:System.ServiceModel.TransactionProtocol> typu.|Určuje transakční protokol, který se má použít při toku transakce.|  
|TransactionFlow|Logická hodnota|Určuje, zda je povolen tok příchozích transakcí.|  
  
 U operace `OperationBehaviorAttribute` má následující vlastnosti:  
  
|Name|Typ|Popis|  
|----------|----------|-----------------|  
|Nastaven|Logická hodnota|Určuje, zda se má automaticky potvrdit aktuální transakce, pokud nedošlo k žádné neošetřené výjimce.|  
|Vlastností TransactionScopeRequired nastavenou|Logická hodnota|Určuje, zda operace vyžaduje transakci.|  
  
 U operace `TransactionFlowAttribute` má následující vlastnosti.  
  
|Name|Typ|Popis|  
|----------|----------|-----------------|  
|TransactionFlowOption|Řetězec, který obsahuje platnou hodnotu <xref:System.ServiceModel.TransactionFlowOption> výčtu.|Určuje rozsah, ve kterém je tok transakcí požadován.|  
  
## <a name="tracing"></a>Trasování  
 Trasování vám umožní monitorovat a analyzovat chyby ve vašich transakčních aplikacích. Trasování můžete povolit pomocí následujících způsobů:  
  
- Standardní trasování WCF  
  
     Tento typ trasování je stejný jako trasování jakékoli aplikace WCF. Další informace najdete v tématu [Konfigurace trasování](../diagnostics/tracing/configuring-tracing.md).  
  
- Trasování WS-AtomicTransaction  
  
     Trasování WS-AtomicTransaction lze povolit pomocí [konfiguračního nástroje WS-AtomicTransaction (WsatConfig. exe)](../ws-atomictransaction-configuration-utility-wsatconfig-exe.md). Toto trasování poskytuje přehled o stavu transakcí a účastníků v rámci systému. K povolení trasování interního modelu služby můžete také nastavit `HKLM\SOFTWARE\Microsoft\WSAT\3.0\ServiceModelDiagnosticTracing` klíč registru na platnou hodnotu <xref:System.Diagnostics.SourceLevels> výčtu. Protokolování zpráv můžete povolit stejným způsobem jako ostatní aplikace WCF.  
  
- `System.Transactions`probíhá  
  
     Při použití protokolu OleTransactions nelze trasovat zprávy protokolu. Trasování podporují <xref:System.Transactions> infrastrukturu (která používá OleTransactions) umožňuje uživatelům zobrazit události, ke kterým došlo pro transakce. Chcete-li povolit trasování pro <xref:System.Transactions> aplikaci, zahrňte do `App.config` konfiguračního souboru následující kód.  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
         <sources>  
            <source name="System.Transactions" switchValue="Verbose, ActivityTracing">  
               <listeners>  
                  <add name="Text"  
                     type="System.Diagnostics.XmlWriterTraceListener"  
                     initializeData="SysTx.log"  
                     traceOutputOptions="Callstack" />  
               </listeners>  
            </source>  
         </sources>  
         <trace autoflush="true" indentsize="4">  
         </trace>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
     To také umožňuje trasování WCF, protože WCF používá i <xref:System.Transactions> infrastrukturu.  
  
## <a name="see-also"></a>Viz také

- [Správa a diagnostika](../diagnostics/index.md)
- [Konfigurace trasování](../diagnostics/tracing/configuring-tracing.md)
- [Nástroj pro konfiguraci WS-AtomicTransaction (wsatConfig.exe)](../ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
