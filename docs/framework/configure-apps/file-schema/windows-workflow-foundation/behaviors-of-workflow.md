---
title: <behaviors>pracovního postupu
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 05a15cdf5c043eb5d94b36028324310d2b7a8413
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398880"
---
# <a name="behaviors-of-workflow"></a>\<behaviors>pracovního postupu
Tento prvek obsahuje kolekci **serviceBehaviors** .  Každý prvek v kolekci definuje chování elementů používané služby pracovního postupu. Každý prvek chování je identifikován podle jeho jedinečného atributu **Name** .  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**  
  
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
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|Tento oddíl konfigurace představuje všechny chování definované pro službu konkrétního pracovního postupu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<system.serviceModel>](../wcf/system-servicemodel.md)|Kořenový element všechny elementy konfigurace pracovního postupu.|  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [Konfigurace a rozšíření modulu runtime s chováním](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
