---
title: '&lt;baseAddresses&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 69a049e1daacce901685050ab9fbe99a9c4d3428
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltbaseaddressesgt"></a>&lt;baseAddresses&gt;
Představuje kolekci `baseAddress` elementy, které jsou základní adresy pro hostitele služby v prostředí s vlastním hostováním. Pokud základní adresa je k dispozici, může být koncové body nakonfigurované adresy relativně k základní adresu.  
  
 \<systém. ServiceModel >  
\<klient >  
\<koncový bod >  
\<hostitele >  
\<baseAddresses >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<baseAddresses>  
   <add baseAddress="string" />  
</baseAddresses>  
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
|[\<Přidat >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|Konfigurace element, který určuje základní adresy používané hostitele služby.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<hostitele >](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|Konfigurace element, který určuje nastavení pro hostitele služby.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [Hostování](../../../../../docs/framework/wcf/feature-details/hosting.md)
