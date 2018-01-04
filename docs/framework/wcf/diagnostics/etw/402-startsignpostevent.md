---
title: "402 – StartSignpostEvent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e5be126-765d-4ac9-88e7-008e9ef4f0e5
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62587e6aa15ef57d5fee349795dfd60bb52812d1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="402---startsignpostevent"></a>402 – StartSignpostEvent
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|402|  
|Klíčová slova|Poradce při potížích|  
|úroveň|Informace o|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace nebo analytické|  
  
## <a name="description"></a>Popis  
 Tato událost označuje začátek aktivitu začátku do konce. Obsahuje název aktivity.  
  
## <a name="message"></a>Zpráva  
 Aktivita hranic.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Rozšířená Data|`xs:string`|Název aktivity.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
