---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: 269500324ad1beaa0b519fa17d251ee942276faa
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269065"
---
# <a name="callbacktimeouts"></a>\<callbackTimeouts>
Určuje maximální dobu proudění transakcí ze serveru do zpětně volaném scénáři kontraktu duplexního zpětného volání.  
  
 \<system.ServiceModel>  
\<chování >  
\<endpointBehaviors>  
\<chování >  
\<callbackTimeOuts>  
  
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
|`transactionTimeout`|A <xref:System.TimeSpan> hodnota, která určuje dobu v rámci transakce, které musíte dokončit nebo bude automaticky ukončena. Výchozí hodnota je "00: 00:00".|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje chování koncového bodu.|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
