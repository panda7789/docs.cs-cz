---
title: '&lt;BaseAddresses&gt;'
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 8de962cc70e1399dd1e9459473055651f9aca5fb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747483"
---
# <a name="ltbaseaddressesgt"></a>&lt;BaseAddresses&gt;
Představuje kolekci `baseAddress` elementy, které jsou základní adresy pro hostitele služby v prostředí s vlastním hostováním. Pokud základní adresa je k dispozici, může být koncové body nakonfigurované adresy relativně k základní adresu.  
  
 \<system.ServiceModel>  
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
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|Konfigurace element, který určuje základní adresy používané hostitele služby.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<hostitele >](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|Konfigurace element, který určuje nastavení pro hostitele služby.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [Hostování](../../../../../docs/framework/wcf/feature-details/hosting.md)
