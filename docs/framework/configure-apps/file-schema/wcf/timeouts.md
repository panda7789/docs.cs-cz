---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: b6ae5faa2dd2ffef9669a0245a75227b0f669cf7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59118063"
---
# <a name="timeouts"></a>\<vypršení časových limitů >
Představuje prvek konfigurace, který určuje dobu hostitel služby otevřít nebo zavřít.  
  
 \<system.ServiceModel>  
\<client>  
\<endpoint>  
\<host>  
\<vypršení časových limitů >  
  
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
|`closeTimeout`|A <xref:System.TimeSpan> hodnota, která určuje časový interval povolený pro hostitel služby zavřít.|  
|`openTimeout`|A <xref:System.TimeSpan> hodnota, která určuje časový interval povolený pro hostitel služby otevřít.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<host>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|Konfigurace element, který určuje nastavení pro hostitele služby.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [Hostování](../../../../../docs/framework/wcf/feature-details/hosting.md)
