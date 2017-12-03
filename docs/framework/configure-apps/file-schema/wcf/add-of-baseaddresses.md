---
title: "&lt;add&gt; – &lt;baseAddresses&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cf417653652c2a0f28fe5c6491a7da9949678140
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltbaseaddressesgt"></a>&lt;add&gt; – &lt;baseAddresses&gt;
Představuje konfiguraci element, který určuje základní adresy používané hostitele služby.  
  
 \<systém. ServiceModel >  
\<klient >  
\<koncový bod >  
\<hostitele >  
\<baseAddresses >  
\<baseAddress >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<add baseAddress="string" />  
```  
  
## <a name="type"></a>Typ  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`baseAddress`|Řetězec, který určuje základní adresu použitou touto hostitele služby.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<baseAddresses >](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|Kolekce `baseAddress` elementy.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [Hostování](../../../../../docs/framework/wcf/feature-details/hosting.md)
