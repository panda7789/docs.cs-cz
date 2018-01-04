---
title: "&lt;chování&gt; pracovního postupu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83c1bf4beb244b72d2fe3d82d749ff6ae6723baf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltbehaviorsgt-of-workflow"></a>&lt;chování&gt; pracovního postupu
Tento prvek obsahuje **serviceBehaviors** kolekce.  Každý prvek v kolekci definuje chování elementů používané služby pracovního postupu. Každý prvek chování je určený podle jeho jedinečné **název** atribut.  
  
 \<systém. ServiceModel >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|Tento oddíl konfigurace představuje všechny chování definované pro službu konkrétního pracovního postupu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<system.serviceModel >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|Kořenový element všechny elementy konfigurace pracovního postupu.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.BehaviorsSection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>  
 [Konfigurace a rozšíření modulu runtime pomocí chování](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
