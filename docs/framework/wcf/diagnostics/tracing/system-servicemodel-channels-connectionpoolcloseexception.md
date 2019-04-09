---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: 3dd28276cd3a39497c0387f5b9d0adec23d07c37
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182192"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a>System.ServiceModel.Channels.ConnectionPoolCloseException
Při zavírání připojení v tomto fondu připojení došlo k výjimce.  
  
## <a name="description"></a>Popis  
 Úroveň trasování chyba označuje, že došlo k chybě při zavírání sdružení připojení používá sdružování funkce Windows Communication Foundation (WCF) pro připojení. Jeden z možných důvodů je neúspěšné uzavření připojení z fondu nebo sadu připojení ve fondu v rámci CloseTimeout. Při vyvolání této výjimky budou zrušeny všechny zbývající neuzavřený připojení v tomto fondu; Neuzavřený připojení v rámci fondy jsou zastavena.  
  
## <a name="see-also"></a>Viz také:

- [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Řešení potíží s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
