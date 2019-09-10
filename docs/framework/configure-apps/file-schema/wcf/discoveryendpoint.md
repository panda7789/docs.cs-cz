---
title: <discoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: 32b14f8fb3235040a51455f2099a403c8312c699
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855391"
---
# <a name="discoveryendpoint"></a>\<discoveryEndpoint>

Tento prvek konfigurace definuje standardní koncový bod s pevným kontraktem zjišťování. Po přidání do konfigurace služby určuje, kde naslouchat pro zprávy zjišťování. Po přidání do konfigurace klienta Určuje, kam se mají odesílat dotazy zjišťování.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Oddílu StandardEndpoints >** ](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<discoveryEndpoint >**  
  
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
| discoveryMode    | Řetězec, který určuje režim protokolu zjišťování. Platné hodnoty jsou "ad hoc" a "spravovaná". V spravovaném režimu protokol spoléhá na proxy zjišťování, které funguje jako úložiště zjistitelných služeb. Režim ad hoc vyžaduje, aby protokol používal k vyhledání dostupných služeb mechanismus vícesměrového vysílání UDP. Další informace o této vlastnosti naleznete v tématu <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>. |  
| discoveryVersion | Řetězec, který určuje jednu ze dvou verzí protokolu WS-Discovery. Platné hodnoty jsou WSDiscovery11 a WSDiscoveryApril2005. Tato hodnota je typu <xref:System.ServiceModel.Discovery.DiscoveryVersion>. |  
| maxResponseDelay | Hodnota TimeSpan, která určuje maximální hodnotu pro prodlevu, po kterou bude protokol zjišťování čekat před odesláním určitých zpráv, jako je například shoda sondy nebo vyřešení shody.<br /><br /> Pokud jsou všechny ProbeMatches odesílány ve stejnou dobu, může dojít k zaplavení sítě. Aby k tomu nedošlo, ProbeMatches se odesílají s náhodným zpožděním mezi jednotlivými ProbeMatch. Náhodné zpoždění je v rozsahu 0 až k hodnotě nastavené tímto atributem. Pokud je tento atribut nastaven na hodnotu 0, zprávy ProbeMatches se odesílají v těsné smyčce bez jakéhokoli zpoždění. V opačném případě se zprávy ProbeMatches odesílají s náhodným zpožděním tak, aby celková doba potřebná k odeslání všech ProbeMatches zpráv nepřekročila maxResponseDelay. Tato hodnota je relevantní jenom pro služby, které nepoužívají klienti. |  
| `name`           | Řetězec, který určuje název konfigurace standardního koncového bodu. Název se používá v `endpointConfiguration` atributu koncového bodu služby k propojení standardního koncového bodu s jeho konfigurací. |  
  
### <a name="child-elements"></a>Podřízené prvky

Žádné  
  
### <a name="parent-elements"></a>Nadřazené prvky

| Prvek | Popis |  
| ------- | ----------- |  
| [\<standardEndpoints>](standardendpoints.md) | Kolekce standardních koncových bodů, které jsou předem definovanými koncovými body s jednou nebo více vlastnostmi (adresa, vazba, smlouva) opraveny. |  
  
## <a name="example"></a>Příklad

Následující příklad demonstruje službu, která naslouchá na zprávách zjišťování přes přenos přes síť s vícesměrovým vysíláním. Příklad explicitně určuje verzi WS-Discovery z dubna 2005.  
  
Standardní konfigurace koncového bodu je definována pro každou službu a nelze ji sdílet přes službu. Pokud by měla mít stejný koncový bod zjišťování jiná služba, je nutné do oddílu této služby přidat stejnou konfiguraci.  
  
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

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
