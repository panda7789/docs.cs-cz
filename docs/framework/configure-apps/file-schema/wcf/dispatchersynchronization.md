---
title: '&lt;dispatcherSynchronization&gt;'
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 537dee408f1af29a06042de439a2c1e7d7874222
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555385"
---
# <a name="ltdispatchersynchronizationgt"></a>&lt;dispatcherSynchronization&gt;
  
Určuje chování koncového bodu umožňující službě odeslání asynchronních odpovědí.  
  
\<system.serviceModel>  
\<chování >  
\<endpointBehaviors>  
\<chování >  
  
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
| asynchronousSendEnabled | Logická hodnota, která určuje, zda je povoleno chování asynchronního odeslání. |
| `maxPendingReceives`    | Celé číslo, které určuje, že počet souběžných přijímání, která může na kanálu uskutečněna.<br /><br /> Tato hodnota musí být nakonfigurovaný jenom po jste správně nakonfigurovali chování při omezování služby. |

### <a name="child-elements"></a>Podřízené prvky

Žádné

### <a name="parent-elements"></a>Nadřazené prvky

| Prvek | Popis |  
| ------- | ----------- |  
| [\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje chování koncového bodu. |

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
