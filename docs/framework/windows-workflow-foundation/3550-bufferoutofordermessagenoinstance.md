---
title: 3550 - BufferOutOfOrderMessageNoInstance
ms.date: 03/30/2017
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
ms.openlocfilehash: 1af943e23aa643c6614b946175c0b1854a7ceb62
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="3550---bufferoutofordermessagenoinstance"></a>3550 - BufferOutOfOrderMessageNoInstance
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|3550|  
|Klíčová slova|WFServices|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Označuje, že vyrovnávací pamětí příjmu se nezdařilo. Operaci se pokusí znovu po připravený na zpracování této konkrétní operace v instanci služby.  
  
## <a name="message"></a>Zpráva  
 Operaci '%1' nelze v tuto chvíli provést. Další pokus bude provádět, pokud je připraven ke zpracování této konkrétní operace v instanci služby.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|OperationName|xs:String|Název operace.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
