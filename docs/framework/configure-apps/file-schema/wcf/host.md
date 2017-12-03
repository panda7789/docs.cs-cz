---
title: '&lt;hostitele&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d498190e7d7c3a6e879c50324e3b973f0f8e8fa6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="lthostgt"></a>&lt;hostitele&gt;
Určuje nastavení pro hostitele služby.  
  
 \<systém. ServiceModel >  
\<služby >  
\<služby >  
\<hostitele >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<host>  
      <baseAddresses>  
         <baseAddress baseAddress="string" />  
      </baseAddresses>  
      <timeOuts closeTimeout="TimeSpan"  
         openTimeout="TimeSpan" >  
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
|[\<služby >](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|Určuje nastavení pro [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] služby.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [Hostování](../../../../../docs/framework/wcf/feature-details/hosting.md)
