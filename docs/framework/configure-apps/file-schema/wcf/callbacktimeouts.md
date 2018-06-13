---
title: '&lt;callbackTimeouts&gt;'
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: 48da0351d162a2143a26cc5b9eaa05b731358639
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749563"
---
# <a name="ltcallbacktimeoutsgt"></a>&lt;callbackTimeouts&gt;
Určuje hodnotu časového limitu při toku transakcí ze serveru pro položku scénáři zpětného volání duplexní kontrakt.  
  
 \<system.ServiceModel>  
\<chování >  
\<endpointBehaviors >  
\<chování >  
\<callbackTimeOuts >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a>Typ  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`transactionTimeout`|A <xref:System.TimeSpan> hodnotu, která udává interval času v rámci transakce, které musíte dokončit nebo automaticky ukončena. Výchozí hodnota je "00: 00:00".|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chování >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje chování koncového bodu.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
