---
title: 39458 - TrackingRecordTruncated
ms.date: 03/30/2017
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
ms.openlocfilehash: 416feb4073b31178b016ae72c9cd85e15c4a68c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514479"
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
