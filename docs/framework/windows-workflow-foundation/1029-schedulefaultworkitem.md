---
title: 1029 - ScheduleFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dfa9553c25f607ec25fd968c2e8c6db061fb49dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="1029---schedulefaultworkitem"></a>1029 - ScheduleFaultWorkItem
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1029|  
|Klíčová slova|WFRuntime|  
|úroveň|Verbose|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že bylo naplánováno FaultWorkItem.  
  
## <a name="message"></a>Zpráva  
 Bylo naplánováno FaultWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.  Výjimka byla rozšířena z aktivity %4, DisplayName: '%5', identifikátor InstanceId: '%6'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|FaultActivity|xs:String|Název typu selhání aktivity.|  
|FaultActivityDisplayName|xs:String|Zobrazovaný název selhání aktivity.|  
|FaultActivityInstanceId|xs:String|Id instance selhání aktivity.|  
|ExceptionActivity|xs:String|Název typu aktivity, která vrátila výjimku.|  
|ExceptionActivityDisplayName|xs:String|Zobrazovaný název aktivity, která vrátila výjimku.|  
|ExceptionActivityInstanceId|xs:String|Id instance aktivity, která vrátila výjimku.|  
|Výjimka|xs:String|Podrobnosti o výjimce pro výjimky|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
