---
title: Instance
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: 668cfb3026b9ab7259665f5e53873a512b1e2238
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916393"
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
