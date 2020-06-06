---
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 76b3cbf6b867a983c203141bcd901b2b7b4038d5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855182"
---
# \<headers>
Kromě základního identifikátoru URI může koncový bod adresovat jedna nebo více hlaviček SOAP. Jedna sada scénářů, kde je to užitečné, je sada zprostředkujících scénářů SOAP, kdy koncový bod vyžaduje, aby klienti tohoto koncového bodu zahrnuli hlavičky SOAP cílené na zprostředkovatele. Tento prvek konfigurace lze použít k definování vlastních hlaviček adres. Položky v kolekci hlaviček koncového bodu jsou uživatelsky definované prvky XML. Každý element musí být ve správném formátu XML.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<headers>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
 Uživatelsky definované prvky XML.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<endpoint>](endpoint-of-client.md)|Konfiguruje různé typy koncových bodů.|  
  
## <a name="remarks"></a>Poznámky  
 Volitelná záhlaví poskytují podrobnější informace adresování pro identifikaci nebo interakci s koncovým bodem. Například hlavičky mohou označovat, jak zpracovat příchozí zprávu, kde koncový bod by měl poslat zprávu odpovědi, nebo kterou instanci služby použít ke zpracování příchozí zprávy od určitého uživatele, pokud je k dispozici více instancí.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [Koncové body: adresy, vazby a kontrakty](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
