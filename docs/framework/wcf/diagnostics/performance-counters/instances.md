---
title: Instance
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ed0c4a6f13ddcafdb3a9a773be9cd3f017474ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
