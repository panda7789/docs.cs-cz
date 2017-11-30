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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0ea98388efe14ac0d18a94ec056a441096a4d7c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a>System.ServiceModel.Channels.ConnectionPoolCloseException
Při ukončování připojení v tomto fondu připojení došlo k výjimce.  
  
## <a name="description"></a>Popis  
 Úroveň trasování chyby označuje, že došlo k chybě při zavírání fondy připojení používá [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]je sdružování připojení funkce. Jedním z možných důvodů pro tento je neúspěšná skončení ve fondu připojení nebo sadu ve fondu připojení v rámci intervalu. Pokud se výjimka, budou zrušeny všechna zbývající uzavřené připojení v tomto fondu; připojení uzavřené v jiných fondech jsou opuštění.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení potíží s vaší aplikace pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a Diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
