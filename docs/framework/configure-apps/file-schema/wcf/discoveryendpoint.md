---
title: '&lt;DiscoveryEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: ab00a80904cdcd2844a44c154edb2e424633427b
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145377"
---
# <a name="ltdiscoveryendpointgt"></a>&lt;DiscoveryEndpoint&gt;

Tento prvek konfigurace definuje standardní koncový bod s pevným kontraktem zjišťování. Po přidání do konfigurace služby, se určuje, kde naslouchat zprávám zjišťování. Po přidání do konfigurace klienta Určuje, kam má odesílat dotazy zjišťování.  
  
\<system.serviceModel>  
\<standardEndpoints >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <discoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        name="String" />
    </discoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy

| Atribut        | Popis |  
| ---------------- | ----------- |  
| discoveryMode    | Řetězec, který určuje režim protokolu zjišťování. Platné hodnoty jsou "Ad hoc" a "Spravovaný". Ve spravovaném režimu protokol spoléhá na Proxy zjišťování, která slouží jako úložiště zjistitelné služby. Režimu ad hoc vyžaduje protokol UDP použití vícesměrového vysílání mechanismus pro vyhledání dostupných služeb. Další informace o vlastnosti, naleznete v tématu <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>. |  
| DiscoveryVersion | Řetězec, který určuje jeden ze dvou verzí protokolu WS-Discovery. Platné hodnoty jsou WSDiscovery11 a WSDiscoveryApril2005. Tato hodnota je typu <xref:System.ServiceModel.Discovery.DiscoveryVersion>. |  
| maxResponseDelay | Časový interval hodnotu, která určuje maximální hodnotu zpoždění protokolu zjišťování bude čekat před odesláním některé zprávy, jako je například sběru dat nebo vyřešit shoda.<br /><br /> Pokud se všechny ProbeMatches odesílají ve stejnou dobu, může docházet k síti storm. Chcete-li tomu zabránit, ProbeMatches odesílají pomocí náhodného zpoždění mezi každou ProbeMatch. Náhodné zpoždění je v rozsahu od 0 do hodnoty nastavené v tomto atributu. Pokud tento atribut je nastaven na hodnotu 0, jsou odesílány zprávy ProbeMatches v těsné smyčce bez jakéhokoli zpoždění. V opačném případě případě odesílají zprávy ProbeMatches s některé náhodné zpoždění nepřekročí celkový čas potřebný k odeslání všech zpráv ProbeMatches maxResponseDelay. Tato hodnota platí pouze pro služby, se používají klienti. |  
| `name`           | Řetězec, který určuje název konfigurace standardního koncového bodu. Název se používá v `endpointConfiguration` atribut koncového bodu služby propojit s jeho konfigurace je standardní koncový bod. |  
  
### <a name="child-elements"></a>Podřízené prvky

Žádné  
  
### <a name="parent-elements"></a>Nadřazené prvky

| Prvek | Popis |  
| ------- | ----------- |  
| [\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md) | Kolekce standardních koncových bodů, které jsou předem definované koncové body s jedním nebo více z jejich vlastností (adresu, vazbu, kontrakt) pevné. |  
  
## <a name="example"></a>Příklad

Následující příklad ukazuje služba naslouchá na zprávy zjišťování přes rovnocenný přenos net vícesměrového vysílání. Příklad explicitně určuje WS-Discovery verze 2005. dubna.  
  
Standardní koncový bod konfigurace je definována na službu a se nedají sdílet mezi službu. Pokud jiná služba by měl mít stejný koncový bod zjišťování, stejnou konfiguraci musí být přidán do části této služby.  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService" />
    <endpoint name="peerNetDiscovery"
              binding="peerTcpBinding"
              address="net.p2p://discoveryMesh/multicast"
              kind="discoveryEndpoint"
              endpointConfiguration="peerTcpDiscoveryEndpointConfiguration"
              bindingConfiguration="discoveryPeerTcpBindingConfig" />
  </service>
</services>
<standardEndpoints>
  <discoveryEndpoint>
    <standardEndpoint name="peerTcpDiscoveryEndpointConfiguration"
                      version="WSDiscoveryApril2005" />
  </discoveryEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a>Viz také:

<xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
