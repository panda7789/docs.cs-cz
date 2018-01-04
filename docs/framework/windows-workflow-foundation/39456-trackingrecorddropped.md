---
title: 39456 - TrackingRecordDropped
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: da13d5bc-1736-47a4-b3fd-064ca8040326
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 592d7c0a3725dcb50f7911a198c9dc9b7199a0a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="39456---trackingrecorddropped"></a>39456 - TrackingRecordDropped
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|39456|  
|Klíčová slova|WFTracking|  
|úroveň|Upozornění|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že záznam sledování byla vyřazena, protože jeho velikost překračuje maximální povolenou zprostředkovatele relací trasování událostí pro Windows.  
  
## <a name="message"></a>Zpráva  
 Velikost sledování záznam %1 překračuje maximální povolenou relace trasování událostí pro Windows pro zprostředkovatele: %2  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Výjimka|xs:String|Podrobnosti o výjimce pro výjimky|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
