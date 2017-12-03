---
title: 39458 - TrackingRecordTruncated
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1d2bc07cff75fce7ddb50da9f54d161d7f235cab
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="39458---trackingrecordtruncated"></a>39458 - TrackingRecordTruncated
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|39458|  
|Klíčová slova|WFTracking|  
|úroveň|Upozornění|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že záznam sledování byla zkrácena. Byly odebrány proměnné a poznámky nebo uživatelská data.  
  
## <a name="message"></a>Zpráva  
 Zkrácená sledování záznam %1 zapsána do relace trasování událostí pro Windows pomocí zprostředkovatele %2. Odebrali jsme proměnné a poznámky nebo uživatelská data  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|RecordNumber|xs:String|Počet záznamů sledování.|  
|ProviderId|xs:String|Id zprostředkovatele trasování událostí pro Windows.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
