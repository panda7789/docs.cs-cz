---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 054991687a54ecbf95cc18f58717a4ed3e36f050
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260798"
---
# <a name="persistenceprovider"></a>\<persistenceProvider>
Určuje typ implementace poskytovatele trvalého použít, jakož i časový limit pro operace trvalého uložení.  
  
 \<system.ServiceModel>  
\<chování >  
\<serviceBehaviors>  
\<chování >  
\<persistenceProvider>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|persistenceOperationTimeout|A <xref:System.TimeSpan> hodnota, která určuje časový limit pro operace trvalého uložení. Výchozí hodnota je "00: 00:30".|  
|– typ|Řetězec, který určuje typ továrny poskytovatele trvalosti používat.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje chování element.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek určuje poskytovatele trvalého chování, který se má použít k serializaci stav služby WCF. Mělo by se používat společně s `wsHttpContextBinding` které předává informace o stavu v hlavičkách protokolu HTTP.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
