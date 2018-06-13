---
title: '&lt;messageLogging&gt;'
ms.date: 03/30/2017
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
ms.openlocfilehash: e137070b71cf8a481eef3ea16260c135e29b4932
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750684"
---
# <a name="ltmessagelogginggt"></a>&lt;messageLogging&gt;
Tento element definuje nastavení pro protokolování zpráv možnosti Windows Communication Foundation (WCF).  
  
 \<system.ServiceModel>  
\<diagnostické >  
\<messageLogging >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>  
   <diagnostics>  
       <messageLogging logEntireMessage="Boolean"  
          logMalformedMessages="Boolean"  
          logMessagesAtServiceLevel="Boolean"  
          logMessagesAtTransportLevel="Boolean"  
                    maxMessagesToLog="Integer"  
          maxSizeOfMessageToLog="Integer" >  
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
|`logEntireMessage`|Logická hodnota, která určuje, zda je zaznamenána celé zprávy (záhlaví zprávy a text). Výchozí hodnota je `false`, což znamená, že pouze záhlaví zprávy přihlášen. Toto nastavení ovlivňuje všechny úrovně protokolování zpráv (service, přenos a chybná).|  
|`logMalformedMessages`|Logická hodnota, která určuje, zda mají být protokolovány poškozených zpráv. Poškozených zpráv nepočítá `maxMessagesToLog`. Výchozí hodnota je `false`.|  
|`logMessagesAtServiceLevel`|Logická hodnota, která určuje, zda jsou zprávy nalezeny na úrovni služby (před šifrování a přenosu související transformací). Výchozí hodnota je `false`.|  
|`logMessagesAtTransportLevel`|Logická hodnota, která určuje, zda jsou zprávy nalezeny na úrovni přenosu. Jsou použity žádné filtry zadané v konfiguračním souboru, a budou trasovány pouze zprávy, které splňují podmínky filtrů. Výchozí hodnota je `false`.|  
|`maxMessagesToLog`|Kladné celé číslo, které určuje maximální počet zpráv do protokolu. Výchozí hodnota je 1 000.|  
|`maxSizeOfMessageToLog`|Kladné celé číslo, které určuje maximální velikost v bajtech zprávy do protokolu. Zprávy, které jsou větší než limit se nebudou protokolovat. Toto nastavení ovlivňuje všechny úrovně trasování. Výchozí hodnota je 262144(0x4000).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|filtry|`filters` Element obsahuje kolekci filtrů XPath. Když je povoleno protokolování přenosu zpráv (`logMessagesAtTransportLevel` je `true`), bude do protokolu pouze zprávy odpovídající filtry.<br /><br /> Filtry se použijí jenom v přenosové vrstvě. Protokolování úrovně a poškozených zpráv služby nemá vliv filtry.<br /><br /> Atribut pouze pro tento element `filter`, je třída XpathFilter.<br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|diagnostika|Definuje nastavení WCF pro modul runtime kontroly a řízení pro správce.|  
  
## <a name="remarks"></a>Poznámky  
 Zprávy se zaznamenávají na třech různých úrovních v zásobníku: service, přenos a je poškozený. Každá úroveň je možné aktivovat samostatně.  
  
 Filtry jazyka XPath lze přidat k protokolování konkrétní zpráv na úrovni přenosu a služby. Pokud jsou definovány žádné filtry, jsou protokolovány všechny zprávy. Filtry se použijí jenom u záhlaví zprávy. Text se ignoruje. WCF ignoruje tělo zprávy ke zlepšení výkonu. Pokud chcete filtrovat podle obsah textu, můžete vytvořit vlastní naslouchací proces s filtr, který nemá tak.  
  
 Budete muset vytvořit naslouchací proces trasování aktivujte trasování zpráv. Naslouchací proces samotné může být jakékoli naslouchací proces, který funguje s <xref:System.Diagnostics> architektura trasování. Následující příklad ukazuje, jak vytvořit naslouchací proces.  
  
```xml  
<system.diagnostics>  
    <sources>  
          <source name="System.ServiceModel" switchValue="Verbose">  
              <listeners>  
                    <clear />  
                    <add type="System.Diagnostics.DefaultTraceListener" name="Default"  
                        traceOutputOptions="None" />  
                    <add name="ServiceModel Listener" traceOutputOptions="None" />  
               </listeners>  
        </source>  
            <source name="System.ServiceModel.MessageLogging">  
                <listeners>  
                    <clear />  
                    <add type="System.Diagnostics.DefaultTraceListener" name="Default"  
                        traceOutputOptions="None" />  
                    <add name="MessageLogging Listener" traceOutputOptions="None"/>  
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
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement>  
 [Konfigurace protokolování zpráv](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
