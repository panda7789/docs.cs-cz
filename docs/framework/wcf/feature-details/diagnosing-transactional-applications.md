---
title: Diagnostikování transakčních aplikací
ms.date: 03/30/2017
ms.assetid: 4a993492-1088-4d10-871b-0c09916af05f
ms.openlocfilehash: 4fa85fea0651d7a31c5a50bbc9c1226421b976b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="diagnosing-transactional-applications"></a>Diagnostikování transakčních aplikací
Toto téma popisuje, jak používat správu Windows Communication Foundation (WCF) a diagnostické funkce k řešení potíží s transakční aplikace.  
  
## <a name="performance-counters"></a>Čítače výkonu  
 WCF poskytuje standardní sadu čítačů výkonu pro vás k měření výkonu transakcí aplikace. Další informace najdete v tématu [čítače výkonu](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md).  
  
 Čítače výkonu jsou omezená na tři různé úrovně: služby, koncový bod a operace, jak je popsáno v následujících tabulkách.  
  
### <a name="service-performance-counters"></a>Čítače výkonu služby  
  
|Čítače výkonu|Popis|  
|-------------------------|-----------------|  
|Počet plynoucích transakcí|Počet transakcí plynoucích do operace v rámci této služby. Tento čítač se zvýší, když je součástí zprávu, která je odeslána do služby transakce.|  
|Počet plynoucích transakcí za sekundu|Počet transakcí plynoucích do operace v rámci této služby v rámci každou sekundu. Tento čítač se zvýší, když je součástí zprávu, která je odeslána do služby transakce.|  
|Počet potvrzených zpracovaných operací|Počet zpracovaných operací provést, jejichž transakce byla dokončena s výstupem potvrzené v rámci této služby. Práci v takových operacích je plně potvrdit. Prostředky jsou aktualizovány v souladu s práci v operaci.|  
|Počet potvrzených zpracovaných operací za sekundu|Počet zpracovaných operací provést, jejichž transakce byla dokončena s výstupem potvrzené v rámci této služby v rámci každou sekundu. Práci v takových operacích je plně potvrdit. Prostředky jsou aktualizovány v souladu s práci v operaci.|  
|Počet přerušených transakčních operací|Počet zpracovaných operací provést, jejichž transakce byla dokončena s výstupem přerušena v rámci této služby. Práci v takových operacích je vrácena zpět. Zdroje jsou vráceny do jejich předchozího stavu.|  
|Počet zrušených zpracovaných operací za sekundu|Počet zpracovaných operací provést, jejichž transakce byla dokončena s výstupem přerušena v rámci této služby v rámci každou sekundu. Práci v takových operacích je vrácena zpět. Zdroje jsou vráceny do jejich předchozího stavu.|  
|Počet nejistých zpracovaných operací|Počet zpracovaných operací provést, jejichž transakce byla dokončena s výstupem nejistých v rámci této služby. Práci s výstupem nejistých se nacházejí v neurčitém stavu. Prostředky jsou uložené čekající na vyřízení výsledek.|  
|Počet nejistých zpracovaných operací za sekundu|Počet zpracovaných operací provést, jejichž transakce byla dokončena s výsledek nejistých v rámci této služby v rámci každou sekundu. Práci s výstupem nejistých se nacházejí v neurčitém stavu. Prostředky jsou uložené čekající na vyřízení výsledek.|  
  
### <a name="endpoint-performance-counters"></a>Čítače výkonu koncového bodu  
  
|Čítače výkonu|Popis|  
|-------------------------|-----------------|  
|Počet plynoucích transakcí|Počet transakcí plynoucích do operací na tento koncový bod. Tento čítač se zvýší, když transakce je součástí zprávu, která je odeslána koncovému bodu.|  
|Počet plynoucích transakcí za sekundu|Počet transakcí plynoucích do operací na tento koncový bod v rámci každou sekundu. Tento čítač se zvýší, když transakce je součástí zprávu, která je odeslána koncovému bodu.|  
  
### <a name="operation-performance-counters"></a>Čítače provozního výkonu  
  
|Čítače výkonu|Popis|  
|-------------------------|-----------------|  
|Počet plynoucích transakcí|Počet transakcí plynoucích do operací na tento koncový bod. Tento čítač se zvýší, když transakce je součástí zprávu, která je odeslána koncovému bodu.|  
|Počet plynoucích transakcí za sekundu|Počet transakcí plynoucích do operací na tento koncový bod v rámci každou sekundu. Tento čítač se zvýší, když transakce je součástí zprávu, která je odeslána koncovému bodu.|  
  
## <a name="windows-management-instrumentation"></a>Windows Management Instrumentation  
 WCF zpřístupní dat kontroly služby za běhu prostřednictvím poskytovatele WCF Windows Management Instrumentation (WMI). Další informace o přístup k datům WMI najdete v tématu [pomocí rozhraní Windows Management Instrumentation pro diagnostiku](../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
 Počet jen pro čtení vlastnosti WMI znamenat nastavení transakcí na použité pro službu. V následujících tabulkách najdete tato nastavení.  
  
 Na službě `ServiceBehaviorAttribute` má následující vlastnosti.  
  
|Název|Typ|Popis|  
|----------|----------|-----------------|  
|ReleaseServiceInstanceOnTransactionComplete|Boolean|Určuje, jestli je objekt služby recykluje po dokončení aktuální transakci.|  
|TransactionAutoCompleteOnSessionClose|Boolean|Určuje, zda jsou nevyřízené transakce dokončeny zavře aktuální relaci.|  
|TransactionIsolationLevel|Řetězec, který obsahuje platná hodnota <xref:System.Transactions.IsolationLevel> výčtu.|Určuje úroveň izolace transakce, která podporuje tuto službu.|  
|Vlastnost TransactionTimeout|<xref:System.DateTime>|Určuje časový interval, ve kterém musíte dokončit transakci.|  
  
 `ServiceTimeoutsBehavior` Má následující vlastnosti.  
  
|Název|Typ|Popis|  
|----------|----------|-----------------|  
|Vlastnost TransactionTimeout|<xref:System.DateTime>|Určuje časový interval, ve kterém musíte dokončit transakci.|  
  
 U vazby, `TransactionFlowBindingElement` má následující vlastnosti.  
  
|Název|Typ|Popis|  
|----------|----------|-----------------|  
|TransactionProtocol|Řetězec, který obsahuje platná hodnota <xref:System.ServiceModel.TransactionProtocol> typu.|Určuje protokol transakcí pro použití v toku transakce.|  
|TransactionFlow|Boolean|Určuje, zda je povolena příchozí tok transakcí.|  
  
 U určité operace `OperationBehaviorAttribute` má následující vlastnosti:  
  
|Název|Typ|Popis|  
|----------|----------|-----------------|  
|Vlastnost TransactionAutoComplete|Boolean|Určuje, zda chcete automaticky potvrzení aktuální transakce, pokud dojde k žádné neošetřených výjimek.|  
|Vlastností TransactionScopeRequired|Boolean|Určuje, zda operace vyžaduje transakci.|  
  
 U určité operace `TransactionFlowAttribute` má následující vlastnosti.  
  
|Název|Typ|Popis|  
|----------|----------|-----------------|  
|TransactionFlowOption|Řetězec, který obsahuje platná hodnota <xref:System.ServiceModel.TransactionFlowOption> výčtu.|Určuje rozsah toku transakci, která je potřeba.|  
  
## <a name="tracing"></a>Trasování  
 Trasování umožňují monitorovat a analyzovat chyb v transakčních aplikací. Můžete povolit trasování pomocí těchto způsobů:  
  
-   Standardní trasování WCF  
  
     Tento typ trasování je stejný jako trasování všechny aplikace WCF. Další informace najdete v tématu [Konfigurace trasování](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).  
  
-   Trasování WS-AtomicTransaction  
  
     WS-AtomicTransaction trasování je možné zapnout pomocí [WS-AtomicTransaction Configuration Utility (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md). Tyto funkce trasování poskytuje přehled o stavu transakce a účastníky v systému. Také povolit trasování interní Model služby, můžete nastavit `HKLM\SOFTWARE\Microsoft\WSAT\3.0\ServiceModelDiagnosticTracing` klíč registru na platnou hodnotu <xref:System.Diagnostics.SourceLevels> výčtu. Můžete povolit protokolování stejným způsobem jako ostatní aplikace WCF zpráv.  
  
-   `System.Transactions` trasování  
  
     Pokud používáte protokol OleTransactions, nemohou být nalezeny zprávy protokolu. Podpora trasování <xref:System.Transactions> poskytuje infrastrukturu (který používá OleTransactions) umožňuje uživatelům zobrazit události, které do transakce došlo k chybě. Povolení trasování pro <xref:System.Transactions> aplikace, zahrnují následující kód `App.config` konfigurační soubor.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Správa a diagnostika](../../../../docs/framework/wcf/diagnostics/index.md)  
 [Konfigurace trasování](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [Nástroj pro konfiguraci WS-AtomicTransaction (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
