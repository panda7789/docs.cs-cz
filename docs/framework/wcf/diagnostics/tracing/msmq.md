---
title: MSMQ
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9fca29f-fa44-4ec4-bb48-b10800694500
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e72d3e400440b830b689f476753a7c8c40fe2586
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="msmq"></a>MSMQ
V aplikaci služby MSMQ žádná další aktivita se přenáší z tohoto kanálu zařazených do fronty pro služby MSMQ a ze služby MSMQ ve frontě kanálu.  
  
 Kromě toho jsou ID zprávy služby MSMQ a ID zprávy protokolu SOAP (spolu s ID aktivity, pokud existuje) jako součást trasování kanálu ve frontě na operaci odeslání trasovat.  
  
 ID zprávy služby MSMQ a ID zprávy protokolu SOAP (spolu s aktivity, které ID, pokud existuje) budou trasovány jako součást trasování kanálu ve frontě na operace příjmu.  
  
 Požadované přenosy na operace příjmu jsou spuštěný podobně jako ostatní přenosu (přijímat bajtů -> procesu zpráva -> operaci).
