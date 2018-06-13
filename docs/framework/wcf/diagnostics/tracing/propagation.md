---
title: Šíření
ms.date: 03/30/2017
ms.assetid: f8181e75-d693-48d1-b333-a776ad3b382a
ms.openlocfilehash: f4e92c6dec163d191c507dd80bb0d9dc129c6e96
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803234"
---
# <a name="propagation"></a>Šíření
Toto téma popisuje rozšíření aktivity v modelu trasování Windows Communication Foundation (WCF).  
  
## <a name="using-propagation-to-correlate-activities-across-endpoints"></a>Pomocí šíření pro vazbu mezi aktivitami v koncových bodů  
 Šíření poskytuje možnosti pro že uživatele s přímou souvislost chyby trasování pro stejnou jednotku zpracování napříč koncovými body aplikace, například požadavek. Vygenerované v různých koncové body pro stejnou jednotku zpracování chyby jsou seskupené do stejné aktivity, i mezi doménami aplikací. To se provádí prostřednictvím šíření ID aktivity v záhlaví zprávy. Pokud klient časového limitu z důvodu vnitřní chyby v serveru, i chyby vypadat do stejné aktivity pro přímé korelace.  
  
 Chcete-li to provést, použijte `ActivityTracing` nastavení, jak je předvedeno v předchozím příkladu. Kromě toho nastavit `propagateActivity` atribut pro `System.ServiceModel` zdroj trasování na všechny koncové body.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing" propagateActivity="true" >  
```  
  
 Rozšíření aktivity je konfigurovat funkci, která způsobí, že WCF přidat hlavičku do odchozí zprávy, která zahrnuje ID aktivity na TLS. To uvedete na následné trasování na straně serveru, jsme mohou korelovat aktivity klienta a serveru.  
  
## <a name="propagation-definition"></a>Definice šíření  
 Pokud všechny následující podmínky použití aktivity M gAId rozšířena do aktivity N.  
  
-   N je vytvořit z důvodu M  
  
-   Na M gAId je znám N  
  
-   Na N gAId se rovná gAId na M.  
  
 GAId šíří prostřednictvím záhlaví zprávy ID, jak je znázorněno v následujícím schématu XML.  
  
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
          <a:Address>http://www.w3.org/2005/08/addressing/anonymous  
          </a:Address>  
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
 Při šíření ID aktivity napříč koncovými body, příjemce zprávu vysílá spuštění a zastavení trasování s ID tohoto (šířený) aktivity. Je proto zahájení a ukončení trasování s této gAId z každého zdroje trasování. Když koncových bodů jsou v rámci jednoho procesu a používají stejný název zdroj trasování, vytvoří se víc zahájení a ukončení se stejným umístěné (stejné gAId, stejný zdroj trasování, stejný postup).  
  
## <a name="synchronization"></a>Synchronizace  
 Pokud chcete synchronizovat události napříč koncovými body, které běží na různé počítače, CorrelationId vkládá záhlaví aktivity, který se rozšíří do zpráv. Toto ID můžete použít nástroje pro synchronizaci události mezi počítači se službou hodiny nesoulad mezi databází. Konkrétně nástroj prohlížeče trasování služeb používá toto ID pro zobrazující zprávu toků mezi koncovými body.  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace trasování](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [Scénáře komplexního trasování](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
