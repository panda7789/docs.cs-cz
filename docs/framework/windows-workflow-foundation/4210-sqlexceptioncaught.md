---
title: 4210 – SqlExceptionCaught
ms.date: 03/30/2017
ms.assetid: f0ce8af3-eb4c-48c8-b3d9-dd2f94b5574b
ms.openlocfilehash: 2493014e80e79ac2935c1bcc685147a74e48fb47
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774254"
---
# <a name="4210---sqlexceptioncaught"></a>4210 – SqlExceptionCaught
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|4210|  
|klíčová slova|WFInstanceStore|  
|úroveň|Upozornění|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že byla zachycena výjimka SQL.  
  
## <a name="message"></a>Zpráva  
 Byla zachycena výjimka SQL číslem %1 a zprávou %2.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|ErrorNumber|xs:string|Číslo chyby SQL.|  
|ExceptionMessage|xs:string|Zpráva z výjimky SQL.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
