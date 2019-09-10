---
title: <add> z <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: d75142209ad8706d0cad5ce188d9d991a5e881bc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850593"
---
# <a name="add-of-baseaddresses"></a>\<Přidat > \<> adres BaseAddresses
Představuje prvek konfigurace, který určuje základní adresy používané hostitelem služby.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> služeb**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> služby**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> hostitele**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Adres BaseAddresses >** ](baseaddresses.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Přidat >**  
  
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
