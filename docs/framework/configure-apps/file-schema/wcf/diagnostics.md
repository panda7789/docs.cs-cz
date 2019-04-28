---
title: <diagnostics>
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 3fc7828d399555f7c459f6dd067ce9a24b8998b6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704051"
---
# <a name="diagnostics"></a>\<Diagnostika >
`diagnostics` Prvek definuje nastavení, které můžete použít správce pro řízení a kontrolu za běhu.  
  
 \<system.ServiceModel>  
\<Diagnostika >  
  
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
|etwProviderId|Řetězec určující identifikátor poskytovatele trasování událostí, která zapisuje události do relací ETW.|  
|performanceCounters|Určuje, zda jsou povoleny čítače výkonu pro sestavení. Platné hodnoty jsou<br /><br /> -Vypnuto: Čítače výkonu jsou zakázány.<br />-ServiceOnly: Je povoleno pouze čítače výkonu relevantní pro tuto službu.<br />-Všechny: Čítače výkonu lze zobrazit v době běhu.<br />– Výchozí hodnota: Je vytvořen _WCF_Admin instance čítače výkonu jediné. Tato instance se používá k povolení shromažďování dat technologie SQM pro používá infrastrukturu. Žádné hodnoty čítače pro tuto instanci se aktualizují a proto bude i nadále na nule. Toto je výchozí hodnota, pokud není k dispozici pro službu WCF žádná konfigurace.|  
|wmiProviderEnabled|Logická hodnota, která určuje, zda je povolen zprostředkovatel rozhraní WMI pro sestavení. Zprostředkovatel rozhraní WMI pro uživatele je potřeba k získání přístupu za běhu k řízení a kontrolu funkce služby Windows Communication Foundation (WCF). Výchozí hodnota je `false`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<endToEndTracing>](../../../../../docs/framework/configure-apps/file-schema/wcf/endtoendtracing.md)|Konfigurace element, který umožňuje povolit nebo zakázat různé aspekty začátku do konce trasování za běhu aplikace služby.|  
|[\<messageLogging>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)|Popisuje nastavení pro protokolování zpráv WCF.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|serviceModel|Kořenový element všechny elementy konfigurace WCF.|  
  
## <a name="remarks"></a>Poznámky  
 `diagnostics` Oddíl definuje nastavení diagnostiky pro všechny služby v sestavení. Není možné definovat nastavení samostatné diagnostiky na úrovni služby, dokud není v sestavení pouze pro jednu službu. Atributy se nastavují podle požadavků části.  
  
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
