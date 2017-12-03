---
title: "401 – StopSignPostEvent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e033d03a-510d-4300-aa65-ef02cb4807f2
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 30e796dec45035e6b68659400ebbae1357137b27
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="401--stopsignpostevent"></a>401 – StopSignPostEvent
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|401|  
|Klíčová slova|Poradce při potížích|  
|úroveň|Informace o|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace nebo analytické|  
  
## <a name="description"></a>Popis  
 Tato událost označuje konec aktivity začátku do konce. Obsahuje název aktivity.  
  
## <a name="message"></a>Zpráva  
 Aktivita hranic.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Rozšířená Data|`xs:string`|Název aktivity.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
