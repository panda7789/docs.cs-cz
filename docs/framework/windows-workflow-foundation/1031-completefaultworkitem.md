---
title: 1031 - CompleteFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a87ecb0a50437d83dd3c80d213553c8ac2143968
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="1031---completefaultworkitem"></a>1031 - CompleteFaultWorkItem
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1031|  
|Klíčová slova|WFRuntime|  
|úroveň|Verbose|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že je dokončená FaultWorkItem.  
  
## <a name="message"></a>Zpráva  
 FaultWorkItem dokončení aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'. Výjimka byla rozšířena z aktivity %4, DisplayName: '%5', identifikátor InstanceId: '%6'.  
  
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
