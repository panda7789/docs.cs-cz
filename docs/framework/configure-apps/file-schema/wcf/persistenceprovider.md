---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 4fc9e1332effc51e183a84cf2d3653357277d2ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934142"
---
# <a name="persistenceprovider"></a>\<persistenceProvider >
Určuje typ používané implementace poskytovatele trvalosti a také časový limit pro operace trvalého uložení.  
  
 \<system.ServiceModel>  
\<> chování  
\<serviceBehaviors>  
\<> chování  
\<persistenceProvider >  
  
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
|persistenceOperationTimeout|<xref:System.TimeSpan> Hodnota, která určuje časový limit, který se používá pro operace trvalosti. Výchozí hodnota je "00:00:30".|  
|– typ|Řetězec, který určuje typ továrny poskytovatele trvalosti, který se má použít.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> chování](behavior-of-endpointbehaviors.md)|Určuje chování element.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek určuje poskytovatele trvalosti, který se použije k serializaci stavu služby WCF. Měl by se používat společně s tím `wsHttpContextBinding` , který předává informace o stavu v hlavičkách protokolu HTTP.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
