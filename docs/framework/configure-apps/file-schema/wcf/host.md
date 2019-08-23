---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 21d53df12c2b2d703b771e2b9cb5ee87dafc410e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918710"
---
# <a name="host"></a>\<host>
Určuje nastavení pro hostitele služby.  
  
 \<system.ServiceModel>  
\<> služeb  
\<> služby  
\<host>  
  
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
