---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: b764bc21e9c4555b39c3d096212b6e6bcabb62ff
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855210"
---
# <a name="host"></a>\<host>
Určuje nastavení pro hostitele služby.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> služeb**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> služby**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> hostitele**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
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
|[\<baseAddresses>](baseaddresses.md)|Kolekce `baseAddress` prvků, které určují základní adresy používané hostitelem služby.|  
|[\<Časové limity >](timeouts.md)|Prvek konfigurace, který určuje časový interval, po který může hostitel služby otevřít nebo zavřít.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<service>](service.md)|Určuje nastavení pro službu Windows Communication Foundation (WCF).|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [Hostování](../../../wcf/feature-details/hosting.md)
