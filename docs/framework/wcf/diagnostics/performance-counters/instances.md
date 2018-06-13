---
title: Instance
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: a95acf8e775e0802dc0ed781c562fa6373995a70
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473039"
---
# <a name="instances"></a>Instance
Název čítače: instance.  
  
## <a name="description"></a>Popis  
 Počet kontexty instance, které nyní obsahuje službu.  
  
 Ve většině případů, počet kontexty instance je stejný jako počet instancí. Následující scénáře jsou však výjimkou tohoto pravidla.  
  
-   Volání metody služby <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> metoda explicitně.  
  
-   A <xref:System.ServiceModel.ReleaseInstanceMode> se použije pro <xref:System.ServiceModel.OperationBehaviorAttribute> instance.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
