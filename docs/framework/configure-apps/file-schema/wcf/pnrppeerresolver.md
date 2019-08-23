---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: e7e82117304ac133e5e84c0fc36b987560bcef96
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933799"
---
# <a name="pnrppeerresolver"></a>\<pnrpPeerResolver>
Určuje, že jako překladač se použije překladač PNRP (Peer Name Resolution Protocol). Tento prvek je nepovinný, protože PNRP je výchozí překladač.  
  
 \<system.serviceModel>  
\<> vazeb  
\<customBinding >  
\<> vazby  
\<pnrpResolver>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|Typ překladače|Řetězec, který určuje překladač, který se má použít. Tento atribut je nepovinný. Pokud není nastavená, nebo pokud je nastavená na prázdný řetězec, použije se PNRP.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> vazby](../../../misc/binding.md)|Definuje všechny schopnosti vazby vlastní vazby.|  
  
## <a name="example"></a>Příklad  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [Překladače partnerských uzlů](../../../wcf/feature-details/peer-resolvers.md)
