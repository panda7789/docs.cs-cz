---
title: Šíření
ms.date: 03/30/2017
ms.assetid: f8181e75-d693-48d1-b333-a776ad3b382a
ms.openlocfilehash: ab8b6c003f9e483dccd7b9c7b2687a409f27fdc3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64600022"
---
# <a name="propagation"></a>Šíření
Toto téma popisuje šíření aktivity v modelu trasování Windows Communication Foundation (WCF).  
  
## <a name="using-propagation-to-correlate-activities-across-endpoints"></a>Pomocí šíření korelovat aktivity napříč koncovými body  
 Šíření poskytuje že uživatele s přímou spojitost s míněním chyby trasování pro stejné jednotky zpracování mezi aplikačními koncovými body, například požadavek. Generované v různých koncových bodů pro stejnou jednotkou zpracování chyby jsou seskupené do stejné aktivity i napříč doménami aplikace. To se provádí prostřednictvím šíření ID aktivity v záhlaví zpráv. Proto pokud klienta vyprší časový limit kvůli vnitřní chybě na serveru, i v se zobrazí chyby do stejné aktivity pro přímou spojitost s míněním.  
  
 Chcete-li to provést, použijte `ActivityTracing` nastavení, jak je uvedeno v předchozím příkladu. Navíc nastavte `propagateActivity` atribut pro `System.ServiceModel` zdroj trasování na všechny koncové body.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing" propagateActivity="true" >  
```  
  
 Šíření aktivity je konfigurovat funkce, která způsobí, že WCF přidat hlavičku odchozí zprávy, která zahrnuje ID aktivity v protokolu TLS. Zahrnutím to na následujících trasování na straně serveru, jsme mohli porovnat činnosti klienta a serveru.  
  
## <a name="propagation-definition"></a>Šíření definice  
 Aktivita M gAId je postoupena do aktivity N, pokud všechny následující podmínky použití.  
  
- N je vytvořen z důvodu M  
  
- Znáte gAId M. N  
  
- N. gAId rovná gAId společnosti M.  
  
 GAId je předávat ActivityId záhlaví zprávy, jak je znázorněno v následujícím schématu XML.  
  
```xml  
<xsd:element name="ActivityId" type="integer" minOccurs="0">  
  <xsd:attribute name="CorrelationId" type="integer" minOccurs="0"/>  
</xsd:element>  
```  
  
 Následuje příklad záhlaví zprávy.  
  
```xml  
<MessageLogTraceRecord>  
  <s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope"
                      xmlns:a="http://www.w3.org/2005/08/addressing">  
    <s:Header>  
      <a:Action s:mustUnderstand="1">http://Microsoft.ServiceModel.Samples/ICalculator/Subtract  
      </a:Action>  
      <a:MessageID>urn:uuid:f0091eae-d339-4c7e-9408-ece34602f1ce  
      </a:MessageID>  
      <ActivityId CorrelationId="f94c6af1-7d5d-4295-b693-4670a8a0ce34"
               xmlns="http://schemas.microsoft.com/2004/09/ServiceModel/Diagnostics">  
        17f59a29-b435-4a15-bf7b-642ffc40eac8  
      </ActivityId>  
      <a:ReplyTo>  
          <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>  
      </a:ReplyTo>  
      <a:To s:mustUnderstand="1">net.tcp://localhost/servicemodelsamples/service</a:To>  
   </s:Header>  
   <s:Body>  
     <Subtract xmlns="http://Microsoft.ServiceModel.Samples">  
       <n1>145</n1>  
       <n2>76.54</n2>  
     </Subtract>  
   </s:Body>  
  </s:Envelope>  
</MessageLogTraceRecord>  
```  
  
## <a name="propagation-and-activity-boundaries"></a>Šíření a hranice aktivity  
 Když aktivita ID rozšířena napříč koncovými body, příjemce zprávy vysílá spuštění a zastavení trasování pomocí tohoto ID aktivity (rozšíří). Proto je spuštění a zastavení trasování pomocí tohoto gAId z každého zdroje trasování. Pokud koncové body jsou v rámci stejného procesu a použijte stejný název zdroje trasování, jsou vytvořeny více spouštění a zastavování se stejným rozložením (stejné gAId, stejný zdroj trasování, stejný proces).  
  
## <a name="synchronization"></a>Synchronizace  
 Aby synchronizovaly události ve více koncových bodů, které běží na různých počítačích, je ID korelace přidat do záhlaví ID aktivity, který se šíří do zpráv. Toto ID můžete použít nástroje pro synchronizaci události v počítačích se hodiny nesrovnalosti. Konkrétně nástroj prohlížeče trasování služeb používá toto ID pro zobrazení zprávy toky mezi koncovými body.  
  
## <a name="see-also"></a>Viz také:

- [Konfigurace trasování](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Scénáře komplexního trasování](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
