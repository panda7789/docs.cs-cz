---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: 0a312d192546655dc327667c00f4f2bbc0c15fdb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602038"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a>System.ServiceModel.Channels.ConnectionPoolCloseException
Při zavírání připojení v tomto fondu připojení došlo k výjimce.  
  
## <a name="description"></a>Popis  
 Tato funkce trasování úrovně chyby indikuje, že došlo k chybě při zavírání fondů připojení používaných funkcí sdružování připojení služby Windows Communication Foundation (WCF). Jedním z možných důvodů je neúspěšné uzavření sdruženého připojení nebo sada připojení ve fondu v rámci CloseTimeout. Pokud je tato výjimka vyvolána, všechna zbývající neuzavřená připojení v rámci tohoto fondu budou přerušena; neuzavřená připojení v rámci jiných fondů jsou opuštěna.  
  
## <a name="see-also"></a>Viz také

- [Trasování](index.md)
- [Řešení potíží s aplikací pomocí trasování](using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../index.md)
