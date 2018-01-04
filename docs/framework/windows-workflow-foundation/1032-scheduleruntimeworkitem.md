---
title: 1032 - ScheduleRuntimeWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54688101-becf-42f3-80ca-f53a7b527620
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 81cc73a5ab58e90f1a0ee5bdaf9a491d20206fb3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="1032---scheduleruntimeworkitem"></a>1032 - ScheduleRuntimeWorkItem
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1032|  
|Klíčová slova|WFRuntime|  
|úroveň|Verbose|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že bylo naplánováno RuntimeWorkItem.  
  
## <a name="message"></a>Zpráva  
 Modul runtime pracovní položky bylo naplánováno aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Aktivita|xs:String|Název typu aktivity.|  
|displayName|xs:String|Zobrazovaný název aktivity.|  
|identifikátor instanceId|xs:String|Id instance aktivity.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
