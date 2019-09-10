---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: b9c67ac03f0eb73a2a4cdd43ab48fe12871a1cc3
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854974"
---
# <a name="timeouts"></a>\<Časové limity >
Představuje prvek konfigurace, který určuje časový interval, po který může hostitel služby otevřít nebo zavřít.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> služeb**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> služby**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> hostitele**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Časové limity >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`closeTimeout`|<xref:System.TimeSpan> Hodnota, která určuje časový interval, po který může hostitel služby zavřít.|  
|`openTimeout`|<xref:System.TimeSpan> Hodnota, která určuje časový interval, po který může hostitel služby otevřít.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<host>](host.md)|Prvek konfigurace, který určuje nastavení pro hostitele služby.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [Hostování](../../../wcf/feature-details/hosting.md)
