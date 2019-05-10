---
title: Instance
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: e0be9c93b5efe17235dbccd426cdd73fbb739361
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651839"
---
# <a name="instances"></a>Instance
Název čítače: instance.  
  
## <a name="description"></a>Popis  
 Počet kontextů instance, které službu nyní obsahuje.  
  
 Ve většině případů, počet kontextů instance je stejný jako počet instancí. Následující scénáře jsou však výjimka tohoto pravidla.  
  
- Volá metody služby <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> metoda explicitně.  
  
- A <xref:System.ServiceModel.ReleaseInstanceMode> platí pro <xref:System.ServiceModel.OperationBehaviorAttribute> instance.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.OperationBehaviorAttribute>
