---
title: 39456 – TrackingRecordDropped
ms.date: 03/30/2017
ms.assetid: da13d5bc-1736-47a4-b3fd-064ca8040326
ms.openlocfilehash: f117c7759bab1759a7d614db275de88f8b37c331
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774423"
---
# <a name="39456---trackingrecorddropped"></a>39456 – TrackingRecordDropped
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|39456|  
|klíčová slova|WFTracking|  
|úroveň|Upozornění|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že záznamem sledování byla vyřazena, protože její velikost přesahuje maximální povolenou poskytovatelem relace trasování událostí pro Windows.  
  
## <a name="message"></a>Zpráva  
 Velikost záznamu sledování %1 překračuje maximum povolené relací ETW pro poskytovatele %2  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Výjimka|xs:string|Podrobnosti o výjimce pro výjimku|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
