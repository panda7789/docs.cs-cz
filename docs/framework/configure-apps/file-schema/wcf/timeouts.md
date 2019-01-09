---
title: '&lt;vypršení časových limitů&gt;'
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: e39deeb251865b87eb7734e4447088ca2f221d1d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148328"
---
# <a name="lttimeoutsgt"></a>&lt;vypršení časových limitů&gt;
Představuje prvek konfigurace, který určuje dobu hostitel služby otevřít nebo zavřít.  
  
 \<system.ServiceModel>  
\<klient >  
\<koncový bod >  
\<Hostitel >  
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
|[\<Hostitel >](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|Konfigurace element, který určuje nastavení pro hostitele služby.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [Hostování](../../../../../docs/framework/wcf/feature-details/hosting.md)
