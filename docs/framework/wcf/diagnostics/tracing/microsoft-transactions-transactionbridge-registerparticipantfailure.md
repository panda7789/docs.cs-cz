---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: 1819a269a6775c8541f38f4aa5d733002e3c1e9f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599673"
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a>Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
Službě protokolu WS-AT se nepodařilo zaregistrovat účastníka pro kontrolní protokol.  
  
## <a name="description"></a>Popis  
 Sledováno, pokud služba MSDTC detekuje neplatnou žádost o registraci. To může být způsobeno několika žádostmi o registraci dokončení a interními chybami.  
  
## <a name="troubleshooting"></a>Řešení potíží  
 Nepokoušejte se registrovat na dokončení více než jednou.  Také zkontrolujte řetězec stavu v rámci zprávy trasování a určete, zda existuje nějaká položka, která je k dispozici.  
  
## <a name="see-also"></a>Viz také

- [Trasování](index.md)
- [Řešení potíží s aplikací pomocí trasování](using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../index.md)
