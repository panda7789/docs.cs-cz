---
title: 4210 - SqlExceptionCaught
ms.date: 03/30/2017
ms.assetid: f0ce8af3-eb4c-48c8-b3d9-dd2f94b5574b
ms.openlocfilehash: 2493014e80e79ac2935c1bcc685147a74e48fb47
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
