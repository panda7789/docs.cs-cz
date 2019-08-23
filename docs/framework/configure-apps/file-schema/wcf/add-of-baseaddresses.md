---
title: <add> z <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: a94c5144d907c26e6f5eef09b1a17b17eb6c9e0f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920221"
---
# <a name="add-of-baseaddresses"></a>\<Přidat > \<> adres BaseAddresses
Představuje prvek konfigurace, který určuje základní adresy používané hostitelem služby.  
  
 \<system.ServiceModel>  
\<> klienta  
\<endpoint>  
\<host>  
\<baseAddresses>  
\<baseAddress – >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a>type  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`baseAddress`|Řetězec, který určuje základní adresu, kterou používá hostitel služby.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<baseAddresses>](baseaddresses.md)|Kolekce `baseAddress` prvků.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [Hostování](../../../wcf/feature-details/hosting.md)
