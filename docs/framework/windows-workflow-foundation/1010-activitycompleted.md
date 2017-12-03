---
title: 1010 - ActivityCompleted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d256284e-3fd2-4c33-82f4-abb617575706
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d26aa2c30defd2eb794d013155e05ccd496eebe6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="1010---activitycompleted"></a>1010 - ActivityCompleted
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1010|  
|Klíčová slova|WFRuntime|  
|úroveň|Informace o|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že aktivita dokončila spuštění.  
  
## <a name="message"></a>Zpráva  
 Aktivita "%1", DisplayName: %2, identifikátor InstanceId: '%3' byla dokončena ve stavu "%4".  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Aktivita|xs:String|Název typu aktivity.|  
|displayName|xs:String|Zobrazovaný název aktivity.|  
|identifikátor instanceId|xs:String|Id instance aktivity.|  
|Stav|xs:String|Stav aktivity.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
