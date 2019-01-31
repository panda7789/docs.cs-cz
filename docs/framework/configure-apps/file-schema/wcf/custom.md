---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 2b268d9d040bbeed2b3563783226f7ca8c18e3b5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254285"
---
# <a name="custom"></a>\<vlastní >
Určuje nastavení pro službu překladače vlastní sdílené.  
  
\<system.serviceModel>  
\<vazby >  
\<netPeerBinding>  
\<Vytvoření vazby >  
\<resolver>  
\<vlastní >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`address`|Identifikátor URI, který určuje adresu partnerského uzlu, který je hostitelem služby překladače vlastní sdílené.|  
|`resolverType`|Řetězec, který určuje typ překladače vlastní sdílené služby.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Určuje identitu pro nakonfigurovaný s tímto elementem překladače vlastní partnerských uzlů. Tento prvek je typu <xref:System.ServiceModel.Configuration.IdentityElement>.|  
|[\<headers>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|Kolekce záhlaví adres, který slouží pro zprávy protokolu SOAP zpracovat rozpoznávání vlastní druhé strany.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<resolver>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|Mechanismus rozpoznávání partnera, který se používá pro partnerské sítě ID k sadě adres partnerských uzlů, jenž jsou součástí sítě.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek definuje základního nastavení pro vlastní sdílené překladač služby, včetně koncového bodu adresy partnerského uzlu hostování služby a nastavení konkrétní vazby. Další informace o vytvoření vlastní mechanismus rozpoznávání najdete v tématu [přidání vlastní mechanismus rozpoznávání pro kanál PeerChannel aplikaci](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [Překladače partnerských uzlů](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
- [Přidání vlastní mechanismus rozpoznávání pro kanál PeerChannel aplikaci](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)
