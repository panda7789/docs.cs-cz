---
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 660497012dd057e4ecf95524833e2573fe03a8b0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59224548"
---
# <a name="headers"></a>\<headers>
Koncový bod vyřešíte tak, že jednu nebo víc hlaviček SOAP kromě svůj základní identifikátor URI. Jedna sada scénáře, kde je to užitečné je sada SOAP zprostředkující scénáře, kdy vyžaduje, aby koncový bod klientům tohoto koncového bodu zahrnout záhlaví SOAP určenou pro zprostředkovatele. Tento prvek konfigurace je možné definovat tyto hlavičky vlastní adresu. Položky v kolekci hlaviček koncového bodu jsou uživatelem definované elementy XML. Každý prvek musí být ve správném formátu XML.  
  
 \<system.ServiceModel>  
\<client>  
\<endpoint>  
  
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
 Uživatelem definované elementy XML.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|Konfiguruje různé typy koncových bodů.|  
  
## <a name="remarks"></a>Poznámky  
 Volitelná záhlaví poskytují podrobnější informace o adresování k identifikaci a k interakci s koncovým bodem. Záhlaví může například signalizovat zpracování příchozí zprávy, kde koncový bod má odeslat zpráva s odpovědí nebo které instanci služby pro použití ke zpracování příchozí zprávy z konkrétního uživatele, když jsou k dispozici více instancí.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [Koncové body: Adresy, vazby a kontrakty](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
