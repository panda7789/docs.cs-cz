---
title: <synchronousReceive> – element
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: fa14d4606303b2d67cf5ef845d428bb086680204
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938969"
---
# <a name="synchronousreceive-element"></a>\<synchronousReceive – element >
Tento prvek konfigurace slouží k určení chování za běhu pro příjem zpráv v klientské aplikaci nebo službě. Neobsahuje žádné atributy ani podřízené elementy.  
  
 \<system.ServiceModel>  
\<> chování  
\<endpointBehaviors>  
\<> chování  
\<synchronousReceive >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> chování](behavior-of-endpointbehaviors.md)|Určuje chování koncového bodu.|  
  
## <a name="remarks"></a>Poznámky  
 Toto chování použijte, pokud chcete, aby naslouchací proces kanálu použil synchronní příjem, nikoli jako výchozí, asynchronní. Windows Communication Foundation (WCF) vydá nové vlákno pro každý přijatý kanál. Pokud existuje spousta kanálů, existuje možnost, že je možné vymezit vlákna z provozu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
