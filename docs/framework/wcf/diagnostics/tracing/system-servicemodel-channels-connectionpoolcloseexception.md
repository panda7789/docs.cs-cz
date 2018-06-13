---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: f3474fc1bb0ed0d11df6289ed6470447d815f5ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33475748"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a>System.ServiceModel.Channels.ConnectionPoolCloseException
Při ukončování připojení v tomto fondu připojení došlo k výjimce.  
  
## <a name="description"></a>Popis  
 Úrovně trasování chyby označuje, že došlo k chybě při zavírání používanou pro připojení Windows Communication Foundation (WCF) je funkce sdružování připojení fondů. Jedním z možných důvodů pro tento je neúspěšná skončení ve fondu připojení nebo sadu ve fondu připojení v rámci intervalu. Pokud se výjimka, budou zrušeny všechna zbývající uzavřené připojení v tomto fondu; připojení uzavřené v jiných fondech jsou opuštění.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
