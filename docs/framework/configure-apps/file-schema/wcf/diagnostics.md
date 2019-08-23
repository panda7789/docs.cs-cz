---
title: <diagnostics>
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 170cae5b328c86073c1d8e7710bb19e98ab5688c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925879"
---
# <a name="diagnostics"></a>\<> diagnostiky
`diagnostics` Prvek definuje nastavení, které může být použito správcem pro kontrolu a kontrolu v době běhu.  
  
 \<system.ServiceModel>  
\<> diagnostiky  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>
  <diagnostics etwProviderId="String"
               performanceCounters="Off/ServiceOnly/All/Default"
               wmiProviderEnabled="Boolean">
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
    <messageLogging logEntireMessage="Boolean"
                    logMalformedMessages="Boolean"
                    logMessagesAtServiceLevel="Boolean"
                    logMessagesAtTransportLevel="Boolean"
                    maxMessagesToLog="Integer"
                    maxSizeOfMessageToLog="Integer">
      <filters>
        <clear />
      </filters>
    </messageLogging>
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|etwProviderId|Řetězec určující identifikátor poskytovatele trasování událostí, který zapisuje události do relací ETW.|  
|Čítače výkonu|Určuje, zda jsou povoleny čítače výkonu pro sestavení. Platné hodnoty jsou<br /><br /> Zaokrouhl Čítače výkonu jsou zakázané.<br />- ServiceOnly: Jsou povoleny pouze čítače výkonu relevantní pro tuto službu.<br />Všem Čítače výkonu lze zobrazit za běhu.<br />Výchozí Vytvoří se jedna instance čítače výkonu _WCF_Admin. Tato instance slouží k povolení shromažďování dat technologie SQM pro použití v infrastruktuře. Žádná z hodnot čítače této instance není aktualizována, a proto zůstane nula. Toto je výchozí hodnota, pokud není pro WCF k dispozici žádná konfigurace.|  
|wmiProviderEnabled|Logická hodnota určující, zda je povolen zprostředkovatel rozhraní WMI pro sestavení. Zprostředkovatel rozhraní WMI je nutný pro uživatele, aby získal přístup k kontrolním a kontrolním funkcím Windows Communication Foundation (WCF) za běhu. Výchozí hodnota je `false`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<endToEndTracing >](endtoendtracing.md)|Prvek konfigurace, který umožňuje povolit nebo zakázat různé aspekty komplexního trasování během běžící aplikace služby.|  
|[\<messageLogging >](messagelogging.md)|Popisuje nastavení pro protokolování zpráv WCF.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|serviceModel|Kořenový element všech elementů konfigurace služby WCF.|  
  
## <a name="remarks"></a>Poznámky  
 `diagnostics` Oddíl definuje nastavení diagnostiky pro všechny služby, které jsou umístěny v sestavení. Není možné definovat samostatné nastavení diagnostiky na úrovni služby, pokud v sestavení není pouze jedna služba. Atributy jsou nastaveny podle požadavků oddílu.  
  
## <a name="example"></a>Příklad  
  
```xml  
<diagnostics wmiProviderEnabled="false"
             performanceCounters="all">
  <messageLogging logEntireMessage="true"
                  logMalformedMessages="true"
                  logMessagesAtServiceLevel="true"
                  logMessagesAtTransportLevel="true"
                  maxMessagesToLog="42"
                  maxSizeOfMessageToLog="42">
    <filters>
      <clear />
    </filters>
  </messageLogging>
</diagnostics>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
