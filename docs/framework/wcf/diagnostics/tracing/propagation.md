---
title: Šíření
ms.date: 03/30/2017
ms.assetid: f8181e75-d693-48d1-b333-a776ad3b382a
ms.openlocfilehash: 732ae5cb1ce311b78728f8d5de0fd9102bf32499
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578952"
---
# <a name="propagation"></a>Šíření
Toto téma popisuje šíření aktivit v modelu trasování Windows Communication Foundation (WCF).  
  
## <a name="using-propagation-to-correlate-activities-across-endpoints"></a>Korelace aktivit mezi koncovými body pomocí šíření  
 Šíření poskytuje uživateli přímou korelaci chybových trasování pro stejnou jednotku zpracování v koncových bodech aplikace, například požadavek. Chyby emitované v různých koncových bodech pro stejnou jednotku zpracování jsou seskupeny do stejné aktivity, dokonce i napříč doménami aplikace. To se provádí prostřednictvím šíření ID aktivity v záhlavích zpráv. Proto pokud časový limit klienta vyprší kvůli vnitřní chybě serveru, zobrazí se obě chyby ve stejné aktivitě pro přímou korelaci.  
  
 Uděláte to tak, že použijete `ActivityTracing` nastavení, jak je znázorněno v předchozím příkladu. Kromě toho nastavte `propagateActivity` atribut pro `System.ServiceModel` zdroj trasování ve všech koncových bodech.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing" propagateActivity="true" >  
```  
  
 Šíření aktivit je konfigurovatelná možnost, která způsobuje, že WCF přidá hlavičku do odchozích zpráv, což zahrnuje ID aktivity v TLS. Zahrnutím této akce na straně serveru můžeme korelovat aktivity klientů a serverů.  
  
## <a name="propagation-definition"></a>Definice šíření  
 GAId aktivity M se šíří na aktivitu N, pokud platí všechny následující podmínky.  
  
- N se vytvoří kvůli M  
  
- GAId M se říká N.  
  
- GAId se rovná gAId M.  
  
 GAId je šířena prostřednictvím hlavičky zprávy ActivityId, jak je znázorněno v následujícím schématu XML.  
  
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
  
## <a name="propagation-and-activity-boundaries"></a>Hranice šíření a aktivity  
 Pokud je ID aktivity šířeno napříč koncovými body, příjemce zprávy vyšle trasování spuštění a zastavení s tímto (šířeným) ID aktivity. Z každého zdroje trasování proto existuje spuštění a zastavení trasování s tímto gAId. Pokud jsou koncové body ve stejném procesu a používají stejný název zdroje trasování, vytvoří se několik spuštění a zastavení se stejným systémem (stejné gAId, stejný zdroj trasování, stejný proces).  
  
## <a name="synchronization"></a>Synchronizace  
 K synchronizaci událostí mezi koncovými body, které běží na různých počítačích, se do hlavičky ActivityId, která se šíří ve zprávách, přidá ID korelace. Pomocí tohoto ID můžou nástroje synchronizovat události napříč počítači s nesouladem hodin. Konkrétně nástroj pro prohlížeč trasování služby používá toto ID pro zobrazení toků zpráv mezi koncovými body.  
  
## <a name="see-also"></a>Viz také

- [Konfigurace trasování](configuring-tracing.md)
- [Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Scénáře komplexního trasování](end-to-end-tracing-scenarios.md)
- [Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md)
