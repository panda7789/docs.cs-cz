---
title: "&lt;služby&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46a2e0d810068db6409bc7b0fd1443a41c3d3ec3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicesgt"></a>&lt;služby&gt;
Služby jsou definovány v `services` oddílu konfiguračního souboru. Každá služba má svůj vlastní `service` konfigurační oddíl.  
  
 \<systém. ServiceModel >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>  
        <services>  
        <service>  
        </service>  
        </services>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<služby >](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|Definujte kontrakt služby, chování a koncové body konkrétní služby.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<system.serviceModel >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|Kořenový element všechny konfigurační prvky Windows Communication Foundation (WCF).|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.ServicesSection>
