---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 842f989ab1f2f0b9e8fe08e8fd729f983e846ffc
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261565"
---
# <a name="userequestheadersformetadataaddress"></a>\<useRequestHeadersForMetadataAddress>
Umožňuje načítání informací o adrese metadat ze záhlaví zpráv požadavku.  
  
\<system.ServiceModel>  
\<chování >  
\<serviceBehaviors>  
\<chování >  
\<useRequestHeadersForMetadataAddress>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
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
|[\<defaultPorts>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|Kolekce výchozích portů obsahující seznam výchozích komunikačních koncových bodů, které naslouchá klientská aplikace.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje chování element.|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
