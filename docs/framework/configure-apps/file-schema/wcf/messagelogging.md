---
title: <messageLogging>
ms.date: 03/30/2017
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
ms.openlocfilehash: 9291c38af28c18d20e23e34e8316b4a9fe523123
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855118"
---
# \<messageLogging>
Tento prvek definuje nastavení možností protokolování zpráv Windows Communication Foundation (WCF).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageLogging>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>
  <diagnostics>
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
|`logEntireMessage`|Logická hodnota, která určuje, zda má být zaznamenána celá zpráva (hlavička a tělo zprávy). Výchozí hodnota je `false` , což znamená, že je protokolována pouze Hlavička zprávy. Toto nastavení má vliv na všechny úrovně protokolování zpráv (služba, přenos a nesprávně vytvořená).|  
|`logMalformedMessages`|Logická hodnota, která určuje, zda jsou špatně vytvořené zprávy zaznamenány. Poškozené zprávy se nepočítají směrem k `maxMessagesToLog` . Výchozí formát je `false`.|  
|`logMessagesAtServiceLevel`|Logická hodnota, která určuje, zda jsou zprávy trasovány na úrovni služby (před transformací související s šifrováním a přenosem). Výchozí formát je `false`.|  
|`logMessagesAtTransportLevel`|Logická hodnota, která určuje, zda jsou zprávy trasovány na úrovni přenosu. Všechny filtry zadané v konfiguračním souboru jsou aplikovány a budou trasovány pouze zprávy, které odpovídají filtrům. Výchozí formát je `false`.|  
|`maxMessagesToLog`|Celé kladné číslo určující maximální počet zpráv, které mají být protokolovány. Výchozí hodnota je 1 000.|  
|`maxSizeOfMessageToLog`|Celé kladné číslo určující maximální velikost zprávy, která se má protokolovat (v bajtech). Zprávy větší, než je limit, nebudou protokolovány. Toto nastavení má vliv na všechny úrovně trasování. Výchozí hodnota je 262144 (0x4000).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|filtry|`filters`Element obsahuje kolekci filtrů XPath. Pokud je povoleno protokolování přenosové zprávy ( `logMessagesAtTransportLevel` je `true` ), budou protokolovány pouze zprávy, které odpovídají filtrům.<br /><br /> Filtry se aplikují jenom na transportní vrstvě. Filtry neovlivní úroveň služeb a nesprávně přihlašování zpráv.<br /><br /> Jediný atribut pro tento prvek, `filter` je Třída XPathFilter.<br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|Diagnostika|Definuje nastavení WCF pro kontrolu a kontrolu za běhu pro správce.|  
  
## <a name="remarks"></a>Poznámky  
 Zprávy jsou protokolovány na třech různých úrovních zásobníku: služba, Transport a poškozená. Jednotlivé úrovně lze aktivovat samostatně.  
  
 Filtry XPath lze přidat do protokolu pro zprávy specifické pro přenos a úrovně služeb. Pokud nejsou definovány žádné filtry, budou protokolovány všechny zprávy. Filtry se aplikují pouze na záhlaví zprávy. Tělo je ignorováno. WCF ignoruje tělo zprávy za účelem zvýšení výkonu. Pokud chcete filtrovat podle obsahu těla, můžete vytvořit vlastní naslouchací proces s filtrem, který to dělá.  
  
 Chcete-li aktivovat trasování zpráv, je nutné vytvořit naslouchací proces trasování. Naslouchací proces může být libovolný naslouchací proces, který pracuje s <xref:System.Diagnostics> architekturou trasování. Následující příklad ukazuje, jak vytvořit takový naslouchací proces.  
  
```xml  
<system.diagnostics>
  <sources>
    <source name="System.ServiceModel"
            switchValue="Verbose">
      <listeners>
        <clear />
        <add type="System.Diagnostics.DefaultTraceListener"
             name="Default"
             traceOutputOptions="None" />
        <add name="ServiceModel Listener"
             traceOutputOptions="None" />
      </listeners>
    </source>
    <source name="System.ServiceModel.MessageLogging">
      <listeners>
        <clear />
        <add type="System.Diagnostics.DefaultTraceListener"
             name="Default"
             traceOutputOptions="None" />
        <add name="MessageLogging Listener"
             traceOutputOptions="None" />
      </listeners>
    </source>
  </sources>
  <sharedListeners>
    <add initializeData="C:\ItProTools\TraceLog.xml"
         type="System.Diagnostics.XmlWriterTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         name="ServiceModel Listener"
         traceOutputOptions="LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack" />
    <add initializeData="C:\ItProTools\MessageLog.log"
         type="System.Diagnostics.XmlWriterTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         name="MessageLogging Listener"
         traceOutputOptions="LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack" />
  </sharedListeners>
</system.diagnostics>
```  
  
## <a name="example"></a>Příklad  
  
```xml  
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
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- [Konfigurace protokolování zpráv](../../../wcf/diagnostics/configuring-message-logging.md)
