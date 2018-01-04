---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c7a134a60656c6ee237203b69e1bce40656f13d2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a>System.ServiceModel.Channels.ConnectionPoolCloseException
Při ukončování připojení v tomto fondu připojení došlo k výjimce.  
  
## <a name="description"></a>Popis  
 Úroveň trasování chyby označuje, že došlo k chybě při zavírání fondy připojení používá [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]je sdružování připojení funkce. Jedním z možných důvodů pro tento je neúspěšná skončení ve fondu připojení nebo sadu ve fondu připojení v rámci intervalu. Pokud se výjimka, budou zrušeny všechna zbývající uzavřené připojení v tomto fondu; připojení uzavřené v jiných fondech jsou opuštění.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
