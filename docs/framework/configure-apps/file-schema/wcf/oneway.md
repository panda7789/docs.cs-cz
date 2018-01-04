---
title: '&lt;Typ oneWay&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1436bc0c1708649378ec6747aed9c23cfc1744dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltonewaygt"></a>&lt;Typ oneWay&gt;
Umožňuje směrování paketů a použití jednosměrné metody pro vlastní vazby.  
  
 \<system.serviceModel >  
\<vazby >  
\<customBinding >  
\<Vazba >  
\<Typ oneWay >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<oneWay packetRoutable="Boolean">  
        <channelPoolSettings  
           idleTimeout"TimeSpan"  
          leaseTimeout"TimeSpan"  
          maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
```xml  
</oneWay>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`packetRoutable`|Logická hodnota, která určuje, zda je povoleno směrování paketů. Výchozí hodnota je `false`.|  
|`MaxAcceptedChannels`|Celé číslo, které určuje maximální počet kanálů, které jsou přípustné.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<channelPoolSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> objekt, který obsahuje vlastnosti fondu kanál pro aktuální kanál.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vazba >](../../../../../docs/framework/misc/binding.md)|Definuje všechny možnosti vazba vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 Povolit směrování paketů, jednosměrné převod vrstvy je nutné, který poskytuje tento element. Uživatel může vytvořit vlastní vazby, který vrstvách tuto vazbu pomocí deklaracemi relace nebo požadavku a odpovědi přenosového Chcete-li paket směrovatelné. Tento element je také užitečné, když chcete vystavit jednosměrné metody více nativní způsobem. Další transformace je možné použít v této vrstvě, jako je například složené duplexní a spolehlivého zasílání zpráv.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>  
 <xref:System.ServiceModel.Configuration.OneWayElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
