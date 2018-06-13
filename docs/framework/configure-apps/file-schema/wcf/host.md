---
title: '&lt;hostitele&gt;'
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: ec53568e9d1df9ebb04bc299f491e80674950c63
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34233727"
---
# <a name="lthostgt"></a>&lt;hostitele&gt;
Určuje nastavení pro hostitele služby.  
  
 \<system.ServiceModel>  
\<služby >  
\<služby >  
\<hostitele >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<host>
    <baseAddresses>  
        <add baseAddress="string" />  
    </baseAddresses>  
    <timeOuts closeTimeout="TimeSpan" openTimeout="TimeSpan">  
</host>  
```  
  
## <a name="type"></a>Typ  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<baseAddresses >](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|Kolekce `baseAddress` prvky, které určuje základní adresy používané hostitele služby.|  
|[\<časové limity >](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|Konfigurace element, který určuje dobu dobu povolenou pro hostitele služby otevřete nebo zavřete.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<service>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|Určuje nastavení pro službu Windows Communication Foundation (WCF).|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [Hostování](../../../../../docs/framework/wcf/feature-details/hosting.md)
