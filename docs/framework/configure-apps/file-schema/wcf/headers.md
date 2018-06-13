---
title: '&lt;Záhlaví&gt;'
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 7683b07093719cda6b210a4174d47e5785d4644d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747148"
---
# <a name="ltheadersgt"></a>&lt;Záhlaví&gt;
Koncový bod lze řešit nejméně jedno záhlaví SOAP kromě jeho základní identifikátor URI. Jednu sadu scénáře, kde to je užitečné je sada SOAP zprostředkující scénáře, kde koncového bodu vyžaduje klientům tohoto koncového bodu patří zaměřený na prostředníci hlavičky SOAP. Tento element konfigurace slouží k definování takových hlavičky vlastní adresu. Položky v kolekci hlaviček koncový bod se vlastní elementy XML. Každý prvek musí být ve správném formátu XML.  
  
 \<system.ServiceModel>  
\<klient >  
\<koncový bod >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<headers>  
    <Region xmlns="Uri">"String"</Region>  
        <Member xmlns="Uri">"String"</Member>  
</headers>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|Oblast||  
|Člen||  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|Konfiguruje různé typy koncových bodů.|  
  
## <a name="remarks"></a>Poznámky  
 Volitelné záhlaví obsahují podrobnější informace o přidělování k vaší identifikaci nebo interakci s koncovým bodem. Například záhlaví můžete určit, jak zpracovávat příchozí zprávy, kde má koncový bod odeslat zprávu odpovědi nebo které instanci služby pro použití ke zpracování příchozí zprávy z určitého uživatele, když jsou k dispozici více instancí.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Headers%2A>  
 <xref:System.ServiceModel.Channels.AddressHeaderCollection>  
 [Koncové body: adresy, vazby a kontrakty](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
