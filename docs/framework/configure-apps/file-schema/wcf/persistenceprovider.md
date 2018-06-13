---
title: '&lt;persistenceProvider&gt;'
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 3c7fd74a84184ddbf8cc8db90141174ed84e5774
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746654"
---
# <a name="ltpersistenceprovidergt"></a>&lt;persistenceProvider&gt;
Určuje typ implementace trvalost zprostředkovatele použít, jakož i časový limit používat pro operace trvalost.  
  
 \<system.ServiceModel>  
\<chování >  
\<serviceBehaviors >  
\<chování >  
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
|persistenceOperationTimeout|A <xref:System.TimeSpan> hodnotu, která určuje časový limit používaných pro operace trvalost. Výchozí hodnota je "00: 00:30".|  
|– typ|Řetězec, který určuje typ objektu pro vytváření zprostředkovatele trvalost používat.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chování >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje chování element.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element určuje trvalost zprostředkovatele, který se má použít k serializaci stav služby WCF. By být používána společně s `wsHttpContextBinding` který předává informace o stavu v hlavičkách protokolu HTTP.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.PersistenceProviderElement>  
 <xref:System.ServiceModel.Persistence.PersistenceProvider>
