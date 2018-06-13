---
title: '&lt;Řešitel&gt;'
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: f29c34f53a8bdaee4b30c72bb5d764ae3935fe7a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749020"
---
# <a name="ltresolvergt"></a>&lt;Řešitel&gt;
Určuje sdílené překladače, který se používá k překladu sdílené OK ID sítě pro sadu adres partnerských uzlů, která představuje několik uzlů, které jsou součástí OK.  
  
 \<system.ServiceModel>  
\<vazby >  
\<netpeerbinding – >  
\<Vazba >  
\<překladač >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"  
   referralPolicy="DoNotShare/Service/Share">  
</resolver>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`mode`|Řetězec, který určuje, zda instance překladače sdílené přidruženého k této službě je buď PNRP konkrétní, vlastní překladač, nebo automaticky určeno. Tento atribut je typu <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.|  
|`referralPolicy`|Řetězec, který určuje způsobu, jakým odkazy jsou sdílena mezi partnerské uzly. Tento atribut je typu <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<hlavičky >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|Určuje nastavení pro vlastní sdílené služby překladač.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vazba >](../../../../../docs/framework/misc/binding.md)|Definuje všechny možnosti vazby [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).|  
  
## <a name="remarks"></a>Poznámky  
 Překladač název sdílené je služba zjišťování používá sdílené kanály najít sdílené uzly, které jsou součástí sdílené mřížku. Slouží také "register" uzlu s sdílené mřížky mechanismus, pomocí kterého uzlu sdílené stane známé a dostupné z mřížky sdílené. Další informace o překladače partnerských uzlů najdete v tématu [překladače partnerských uzlů](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.PeerResolver>  
 <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement>  
 [Překladače partnerských uzlů](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [Přidání vlastní překladač do PeerChannel aplikace](http://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)
