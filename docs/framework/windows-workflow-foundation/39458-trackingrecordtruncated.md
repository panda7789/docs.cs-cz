---
title: 39458 – TrackingRecordTruncated
ms.date: 03/30/2017
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
ms.openlocfilehash: 416feb4073b31178b016ae72c9cd85e15c4a68c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774410"
---
# <a name="39458---trackingrecordtruncated"></a>39458 – TrackingRecordTruncated
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|39458|  
|klíčová slova|WFTracking|  
|úroveň|Upozornění|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že byl zkrácen záznamem sledování. Byly odebrány proměnné, poznámky a uživatelská data.  
  
## <a name="message"></a>Zpráva  
 Oříznutá záznam sledování %1 byl zapsán do relace ETW s poskytovatelem %2. Byly odebrány proměnné, poznámky a uživatelská data  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Číslo záznamu|xs:string|Počet záznamů sledování.|  
|ProviderId|xs:string|Id poskytovatele trasování událostí pro Windows.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
