---
title: "&lt;vlastní&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4e4b96e1274ad59ae5e63e7935d7408afd069a8c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltcustomgt"></a>&lt;vlastní&gt;
Určuje nastavení pro vlastní sdílené služby překladač.  
  
\<system.serviceModel >  
\<vazby >  
\<netpeerbinding – >  
\<Vazba >  
\<překladač >  
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
|`address`|Identifikátor URI, který určuje adresa koncového bodu sdílené uzlu, který je hostitelem služby vlastní sdílené překladač.|  
|`resolverType`|Řetězec, který určuje typ služby překladač vlastní sdílené.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<identity >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Určuje identitu pro vlastní sdílené překladače nakonfigurovaný s tímto elementem. Tento element je typu <xref:System.ServiceModel.Configuration.IdentityElement>.|  
|[\<hlavičky >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|Kolekce adres hlavičky SOAP pro zprávy zpracovávaných překladač vlastní sdílené.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<překladač >](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|Překladač partnera, který se používá k překladu sdílené OK ID pro sadu adres partnerských uzlů, která představuje několik uzlů, které jsou součástí OK.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element definuje základního nastavení pro vlastní sdílené překladač služby, včetně adresa koncového bodu partnerského uzlu hostování služby a nastavení konkrétní vazby. Další informace o vytvoření vlastní překladač najdete v tématu [přidání vlastní překladač do aplikace PeerChannel](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>  
 <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>  
 <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>  
 [Překladače partnerských uzlů](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [Přidání vlastní překladač do PeerChannel aplikace](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419)
