---
title: <add> z <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: d66be51fa2626283063c250905efdb7d47babfb0
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279939"
---
# <a name="add-of-baseaddresses"></a>\<Přidat > z \<baseAddresses >
Představuje konfigurační element určující základní adresy použité hostitelem služby.  
  
 \<system.ServiceModel>  
\<client>  
\<endpoint>  
\<host>  
\<baseAddresses>  
\<Vlastnost baseAddress >  
  
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
|`baseAddress`|Řetězec, který určuje základní adresu použitou hostitelem služby.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<baseAddresses>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|Kolekce `baseAddress` elementy.|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [Hostování](../../../../../docs/framework/wcf/feature-details/hosting.md)
