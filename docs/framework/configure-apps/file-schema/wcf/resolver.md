---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: 0dc667f392595d895bd4f2773ab69777d7369446
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738737"
---
# \<resolver>
Určuje rovnocenný překladač, který se používá k překladu ID partnerské sítě na sadu adres partnerských uzlů, které představují několik uzlů, které se účastní sítě.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<resolver>**  
  
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
|`mode`|Řetězec určující, zda je instance překladače partnerského vztahu přidružená k této službě buď specifická pro protokol PNRP, vlastního Překladači nebo automaticky určena. Tento atribut je typu <xref:System.ServiceModel.PeerResolvers.PeerResolverMode> .|  
|`referralPolicy`|Řetězec, který určuje způsob, jakým jsou odkazy sdíleny mezi partnery. Tento atribut je typu <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy> .|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<headers>](headers.md)|Určuje nastavení pro službu Custom peer resolver Service.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|Definuje všechny schopnosti vazby pro [\<netPeerTcpBinding>](netpeertcpbinding.md) .|  
  
## <a name="remarks"></a>Poznámky  
 Překladač názvů partnerů je služba zjišťování, kterou používají rovnocenné kanály k nalezení partnerských uzlů, které se účastní sdílené sítě. Používá se také k registraci uzlu se sdílenou sítí, mechanizmus, který je partnerský uzel známý a dostupný z partnerské sítě. Další informace o překladačích peer-to najdete v tématu věnovaném [překladačům](../../../wcf/feature-details/peer-resolvers.md)peer.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [Překladače partnerských uzlů](../../../wcf/feature-details/peer-resolvers.md)
- [Přidání vlastního překladače do aplikace PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))
