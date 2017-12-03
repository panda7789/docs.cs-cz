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
ms.openlocfilehash: d4e8eee0ebc3702445b41d1f81742d18dfa98d44
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a>System.ServiceModel.Channels.ConnectionPoolCloseException
Při ukončování připojení v tomto fondu připojení došlo k výjimce.  
  
## <a name="description"></a>Popis  
 Úroveň trasování chyby označuje, že došlo k chybě při zavírání fondy připojení používá [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]je sdružování připojení funkce. Jedním z možných důvodů pro tento je neúspěšná skončení ve fondu připojení nebo sadu ve fondu připojení v rámci intervalu. Pokud se výjimka, budou zrušeny všechna zbývající uzavřené připojení v tomto fondu; připojení uzavřené v jiných fondech jsou opuštění.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení potíží s vaší aplikace pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a Diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
