---
title: Diagnostikování transakčních aplikací
ms.date: 03/30/2017
ms.assetid: 4a993492-1088-4d10-871b-0c09916af05f
ms.openlocfilehash: aca5f95e2085dfadf06da35dfd86af72c0b6092d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101709"
---
# <a name="diagnosing-transactional-applications"></a>Diagnostikování transakčních aplikací
Toto téma popisuje postup řešení potíží s transakční aplikace pomocí správy služby Windows Communication Foundation (WCF) a funkce Diagnostika.  
  
## <a name="performance-counters"></a>Čítače výkonu  
 WCF poskytuje standardní sadu čítačů výkonu pro vás k měření výkonu transakční aplikace. Další informace najdete v tématu [čítače výkonu](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md).  
  
 Čítače výkonu jsou omezená na třech různých úrovních: služba, koncový bod a operace, jak je popsáno v následujících tabulkách.  
  
### <a name="service-performance-counters"></a>Čítače výkonu služby  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|Počet plynoucích transakcí|Počet transakcí, které byly převedeny do operací v této službě. Hodnota tohoto čítače se zvýší pokaždé, když transakce je zpráva odeslaná do služby.|  
|Počet plynoucích transakcí za sekundu|Počet transakcí, které byly převedeny do operací v rámci této služby v rámci každou sekundu. Hodnota tohoto čítače se zvýší pokaždé, když transakce je zpráva odeslaná do služby.|  
|Počet potvrzených zpracovaných operací|Provést, počet operací s podporou transakcí, jejichž transakce byla dokončena s výsledkem v této službě potvrzen. Práce s takovými operacemi jsou zcela potvrzeny. Prostředky jsou aktualizovány v souladu s provedenými během operace.|  
|Počet potvrzených zpracovaných operací za sekundu|Provést, počet operací s podporou transakcí, jejichž transakce byla dokončena s výsledkem v této službě potvrzen v rámci každou sekundu. Práce s takovými operacemi jsou zcela potvrzeny. Prostředky jsou aktualizovány v souladu s provedenými během operace.|  
|Počet přerušených transakčních operací|Provést, počet operací s podporou transakcí, jejichž transakce byla dokončena s výsledkem v této službě přerušen. Práce s takovými operacemi je vrácena zpět. Prostředky jsou vráceny do jejich předchozího stavu.|  
|Počet zrušených zpracovaných operací za sekundu|Provést, počet operací s podporou transakcí, jejichž transakce byla dokončena s výsledkem v této službě přerušen v rámci každou sekundu. Práce s takovými operacemi je vrácena zpět. Prostředky jsou vráceny do jejich předchozího stavu.|  
|Počet nejistých zpracovaných operací|Provést, počet operací s podporou transakcí, jejichž transakce byla dokončena s nejistým v této službě. Činnosti provedené s nejistým výsledkem je v neurčitém stavu. Prostředky jsou podrženy.|  
|Počet nejistých zpracovaných operací za sekundu|Provést, počet operací s podporou transakcí, jejichž transakce byla dokončena s nejistým nejistým výsledkem v této služby v rámci každou sekundu. Činnosti provedené s nejistým výsledkem je v neurčitém stavu. Prostředky jsou podrženy.|  
  
### <a name="endpoint-performance-counters"></a>Čítače výkonu koncového bodu  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|Počet plynoucích transakcí|Počet transakcí, které byly převedeny do operací v tomto koncovém bodu. Hodnota tohoto čítače se zvýší pokaždé, když transakce je zpráva odeslaná do koncového bodu.|  
|Počet plynoucích transakcí za sekundu|Počet transakcí, které byly převedeny do operací v tomto koncovém bodu v rámci každou sekundu. Hodnota tohoto čítače se zvýší pokaždé, když transakce je zpráva odeslaná do koncového bodu.|  
  
### <a name="operation-performance-counters"></a>Čítače provozního výkonu  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|Počet plynoucích transakcí|Počet transakcí, které byly převedeny do operací v tomto koncovém bodu. Hodnota tohoto čítače se zvýší pokaždé, když transakce je zpráva odeslaná do koncového bodu.|  
|Počet plynoucích transakcí za sekundu|Počet transakcí, které byly převedeny do operací v tomto koncovém bodu v rámci každou sekundu. Hodnota tohoto čítače se zvýší pokaždé, když transakce je zpráva odeslaná do koncového bodu.|  
  
## <a name="windows-management-instrumentation"></a>Windows Management Instrumentation  
 WCF zpřístupňuje dat kontroly služby za běhu pomocí zprostředkovatele WCF Windows Management Instrumentation (WMI). Další informace o přístup k datům služby WMI najdete v tématu [pomocí Windows Management Instrumentation k diagnostice](../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
 Počet WMI vlastnosti jen pro čtení označení transakce použitá nastavení pro službu. Následující tabulky uvádí všechny z těchto nastavení.  
  
 V rámci služby `ServiceBehaviorAttribute` má následující vlastnosti.  
  
|Name|Typ|Popis|  
|----------|----------|-----------------|  
|ReleaseServiceInstanceOnTransactionComplete|Boolean|Určuje, zda je objekt služby vrácen, pokud je aktuální transakce dokončena.|  
|TransactionAutoCompleteOnSessionClose|Boolean|Určuje, zda jsou nevyřízené transakce dokončeny zavře aktuální relaci.|  
|Úroveň TransactionIsolationLevel|Řetězec, který obsahuje platnou hodnotou <xref:System.Transactions.IsolationLevel> výčtu.|Určuje úroveň izolace transakce, který podporuje tuto službu.|  
|Vlastnost TransactionTimeout|<xref:System.DateTime>|Určuje interval, ve kterém musí být transakce dokončena.|  
  
 `ServiceTimeoutsBehavior` Má následující vlastnost.  
  
|Name|Typ|Popis|  
|----------|----------|-----------------|  
|Vlastnost TransactionTimeout|<xref:System.DateTime>|Určuje interval, ve kterém musí být transakce dokončena.|  
  
 U vazby, `TransactionFlowBindingElement` má následující vlastnosti.  
  
|Name|Typ|Popis|  
|----------|----------|-----------------|  
|transactionProtocol|Řetězec, který obsahuje platnou hodnotou <xref:System.ServiceModel.TransactionProtocol> typu.|Určuje protokol transakce pro použití v toku transakce.|  
|TransactionFlow|Boolean|Určuje, zda je povolen tok příchozích transakcí.|  
  
 U určité operace `OperationBehaviorAttribute` má následující vlastnosti:  
  
|Name|Typ|Popis|  
|----------|----------|-----------------|  
|TransactionAutoComplete|Boolean|Určuje, jestli aktuální transakce potvrzena automaticky, pokud se nevyskytnou žádné nezpracované výjimky.|  
|Vlastností TransactionScopeRequired|Boolean|Určuje, zda operace vyžaduje transakci.|  
  
 U určité operace `TransactionFlowAttribute` má následující vlastnosti.  
  
|Name|Typ|Popis|  
|----------|----------|-----------------|  
|TransactionFlowOption|Řetězec, který obsahuje platnou hodnotou <xref:System.ServiceModel.TransactionFlowOption> výčtu.|Určuje rozsah na transakci, která tok je povinný.|  
  
## <a name="tracing"></a>Trasování  
 Trasování umožňují monitorovat a analyzovat chyby v transakční aplikace. Můžete povolit trasování pomocí následujícími způsoby:  
  
-   Standardní trasování WCF  
  
     Tento typ trasování je stejný jako trasování všech aplikací WCF. Další informace najdete v tématu [Konfigurace trasování](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).  
  
-   WS-AtomicTransaction trasování  
  
     Trasování WS-AtomicTransaction se dá nastavit pomocí [WS-AtomicTransaction Configuration Utility (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md). Tyto funkce trasování poskytuje přehled o stavu transakce a účastníků v rámci systému. Umožňuje také interní trasování Model služby, můžete nastavit `HKLM\SOFTWARE\Microsoft\WSAT\3.0\ServiceModelDiagnosticTracing` klíč registru, který platnou hodnotou <xref:System.Diagnostics.SourceLevels> výčtu. Můžete povolit protokolování stejným způsobem jako ostatní aplikace WCF.  
  
-   `System.Transactions` trasování  
  
     Při použití protokolu OleTransactions, nelze protokol zprávy trasovány. Podpora trasování <xref:System.Transactions> poskytuje infrastrukturu (využívající OleTransactions) umožňuje uživatelům zobrazit události, ke kterým došlo na transakce. Povolení trasování pro <xref:System.Transactions> aplikace, zahrnují následující kód `App.config` konfigurační soubor.  
  
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
  
     To také umožňuje trasování WCF, protože také využívá WCF <xref:System.Transactions> infrastruktury.  
  
## <a name="see-also"></a>Viz také:

- [Správa a diagnostika](../../../../docs/framework/wcf/diagnostics/index.md)
- [Konfigurace trasování](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [Nástroj pro konfiguraci WS-AtomicTransaction (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
