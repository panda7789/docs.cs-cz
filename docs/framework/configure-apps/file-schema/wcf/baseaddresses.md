---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 9b3ed6b39f1743249925d5b6d9a47845c87983bc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850204"
---
# <a name="baseaddresses"></a>\<baseAddresses>
Představuje kolekci `baseAddress` prvků, které jsou základními adresami hostitele služby v prostředí s místním hostováním. Pokud je k dispozici základní adresa, lze koncovým bodům nakonfigurovat adresy relativní vzhledem k základní adrese.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> služeb**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> služby**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> hostitele**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Adres BaseAddresses >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a>type  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<add>](add-of-baseaddresses.md)|Prvek konfigurace, který určuje základní adresy používané hostitelem služby.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<host>](host.md)|Prvek konfigurace, který určuje nastavení pro hostitele služby.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [Hostování](../../../wcf/feature-details/hosting.md)
