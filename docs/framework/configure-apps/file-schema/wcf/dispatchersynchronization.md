---
title: '&lt;dispatcherSynchronization&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c0a6349f50c8810d834d7887daecb6ac9cffb2e9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltdispatchersynchronizationgt"></a>&lt;dispatcherSynchronization&gt;

Určuje chování koncového bodu, umožňující službu pro odeslání odpovědi asynchronně.

\<system.serviceModel > \<chování > \<endpointBehaviors > \<chování >

## <a name="syntax"></a>Syntaxe

```xml
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean" 
                                   maxPendingReceives="Integer" />
```

## <a name="type"></a>Typ

`Type`

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

| Atribut               | Popis       |
| ----------------------- | ----------------- |
| asynchronousSendEnabled | Logická hodnota, která určuje, zda je povoleno chování asynchronní odesílání. |
| `maxPendingReceives`    | Celé číslo, které určuje, že počet souběžných obdrží, které mohou být vystaveny na kanálu.<br /><br /> Tato hodnota musí být nakonfigurovaný jenom po je aplikace správně nakonfigurována omezení chování služby. |

### <a name="child-elements"></a>Podřízené prvky

Žádné

### <a name="parent-elements"></a>Nadřazené prvky

| Prvek | Popis |  
| ------- | ----------- |  
| [\<chování >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje chování koncového bodu. |

## <a name="see-also"></a>Viz také

 <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement><xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
