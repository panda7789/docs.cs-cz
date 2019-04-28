---
title: <messageLogging>
ms.date: 03/30/2017
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
ms.openlocfilehash: 70fb2df1d37af23d9ec19932806989ce3329bf3c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768911"
---
# <a name="messagelogging"></a>\<messageLogging>
Tento prvek definuje nastavení možností protokolování zpráv Windows Communication Foundation (WCF).  
  
 \<system.ServiceModel>  
\<diagnostic>  
\<messageLogging>  
  
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
|`logEntireMessage`|Logická hodnota určující, zda je zaznamenána celá zpráva (hlavička a tělo zprávy). Výchozí hodnota je `false`, což znamená, že pouze záhlaví zprávy je zaznamenána. Toto nastavení ovlivňuje všechny úrovně protokolování zpráv (služba, přenos a chybně formátovaný).|  
|`logMalformedMessages`|Logická hodnota určující, zda jsou špatně vytvořené zprávy zaznamenány. Špatně vytvořené zprávy se nepočítají do `maxMessagesToLog`. Výchozí hodnota je `false`.|  
|`logMessagesAtServiceLevel`|Logická hodnota určující, zda jsou zprávy trasovány na úrovni služby (před transformací související šifrování a transport). Výchozí hodnota je `false`.|  
|`logMessagesAtTransportLevel`|Logická hodnota určující, zda jsou zprávy trasovány na úrovni přenosu. Jsou použity nějaké filtry zadané v konfiguračním souboru, a jsou trasovány pouze zprávy, které odpovídají filtrům. Výchozí hodnota je `false`.|  
|`maxMessagesToLog`|Kladné celé číslo, které určuje maximální počet zaznamenavaných zpráv. Výchozí hodnota je 1000.|  
|`maxSizeOfMessageToLog`|Kladné celé číslo, které určuje maximální velikost v bajtech zaznamenávané zprávy. Zprávy větší než limit se nebudou protokolovat. Toto nastavení ovlivňuje všechny úrovně trasování. Výchozí hodnota je 262144(0x4000).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|filtry|`filters` Element obsahuje kolekci filtrů XPath. Pokud je povoleno protokolování zpráv přenosu (`logMessagesAtTransportLevel` je `true`), budou zaznamenány pouze zprávy odpovídající filtry.<br /><br /> Filtry se použijí pouze na transportní vrstvě. Protokolování úrovně a poškozené zprávy služby nejsou ovlivněny filtry.<br /><br /> Atribut pouze pro tento element `filter`, je třída XpathFilter.<br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|diagnostika|Definuje nastavení kontroly runtime WCF a ovládací prvek pro správce.|  
  
## <a name="remarks"></a>Poznámky  
 Zprávy jsou zaznamenány na třech různých úrovních v zásobníku: služba, přenos a je poškozený. Každá úroveň lze aktivovat samostatně.  
  
 Filtry jazyka XPath lze přidat můžete protokolovat konkrétní zprávy na úrovni přenosu a služby. Pokud jsou definovány žádné filtry, protokolují se všechny zprávy. Filtry se použijí jenom u záhlaví zprávy. Text se ignoruje. WCF ignoruje text zprávy pro zvýšení výkonu. Pokud chcete filtrovat na základě obsahu těla, můžete vytvořit vlastní naslouchací proces s filtrem, která tak učiní.  
  
 Je potřeba vytvořit naslouchací proces trasování aktivujte trasování zprávy. Naslouchací proces sám může být jakékoli naslouchací proces, který funguje s <xref:System.Diagnostics> architektura trasování. Následující příklad ukazuje, jak vytvořit takový naslouchací proces.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- [Konfigurace protokolování zpráv](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
