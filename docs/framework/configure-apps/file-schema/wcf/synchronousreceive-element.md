---
title: Element &lt;synchronousReceive&gt;
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: dedbe156dea79c78f05acdb3a044c9080665675a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54598892"
---
# <a name="ltsynchronousreceivegt-element"></a>Element &lt;synchronousReceive&gt;
Tento prvek konfigurace slouží k určení chování za běhu pro příjem zpráv v aplikaci klienta nebo službě. Nemá žádné atributy nebo podřízené prvky.  
  
 \<system.ServiceModel>  
\<chování >  
\<endpointBehaviors>  
\<chování >  
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
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje chování koncového bodu.|  
  
## <a name="remarks"></a>Poznámky  
 Toto chování použijte dáte pokyn, aby modul pro naslouchání kanálu pro použití synchronního přijímat spíše než výchozí, asynchronní. Windows Communication Foundation (WCF) vydá nové vlákno odeslané pro každé přijaté kanálu. Pokud existuje mnoho kanálů, je možné došly vlákna.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
