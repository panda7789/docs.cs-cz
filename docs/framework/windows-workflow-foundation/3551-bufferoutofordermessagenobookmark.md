---
title: 3551 - BufferOutOfOrderMessageNoBookmark
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9a380def22c270a3fafe118a426609a93862c447
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="3551---bufferoutofordermessagenobookmark"></a>3551 - BufferOutOfOrderMessageNoBookmark
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|3551|  
|Klíčová slova|WFServices|  
|úroveň|Informace o|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace nebo analytické|  
  
## <a name="description"></a>Popis  
 Označuje, že záložku obnovení se nezdařilo. Ve vyrovnávací paměti přijímat operace se pokusí znovu po připravený na zpracování této konkrétní operace v instanci služby.  
  
## <a name="message"></a>Zpráva  
 Operace: %2' na instanci služby '%1' nelze v tuto chvíli provést. Další pokus bude provádět, pokud je připraven ke zpracování této konkrétní operace v instanci služby.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|OperationName|xs:String|Název operace.|  
|ServiceInstanceId|xs:String|Id instance služby.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
