---
title: 4210 - SqlExceptionCaught
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0ce8af3-eb4c-48c8-b3d9-dd2f94b5574b
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fbcb566574e38e3c4688c16bd29a33ff7048bfa4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="4210---sqlexceptioncaught"></a>4210 - SqlExceptionCaught
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|4210|  
|Klíčová slova|WFInstanceStore|  
|úroveň|Upozornění|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že byla zachycena výjimka SQL.  
  
## <a name="message"></a>Zpráva  
 Zachycení zpráva o výjimce SQL číslo %1 %2.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Argument číslo chyby|xs:String|Číslo chyby SQL.|  
|ExceptionMessage|xs:String|Zpráva z výjimky SQL.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
