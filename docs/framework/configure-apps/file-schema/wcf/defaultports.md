---
title: '&lt;defaultPorts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1886f6efdfaa8f4105e6ef16ad72093867e0f3fe
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltdefaultportsgt"></a>&lt;defaultPorts&gt;
Kolekce výchozí porty výpis komunikaci výchozí koncové body, které klientská aplikace naslouchá.  
  
\<systém. ServiceModel >  
\<chování >  
\<serviceBehaviors >  
\<chování >  
\<useRequestHeadersForMetadataAddress >  
\<defaultPorts >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Přidat > z \<defaultPorts >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|Koncový bod výchozí komunikace, která klientská aplikace naslouchá.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<useRequestHeadersForMetadataAddress >](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|Seznam výchozích portů.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
