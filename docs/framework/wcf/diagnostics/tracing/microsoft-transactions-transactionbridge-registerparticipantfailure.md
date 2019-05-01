---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: e56a9ed1d837af27d481282e0e106d537ec41ee3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61997747"
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a>Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
Službě protokolu WS-AT se nepodařilo zaregistrovat účastníka pro kontrolní protokol.  
  
## <a name="description"></a>Popis  
 Trasovaná Pokud MSDTC zjistí Neplatná žádost o registraci. Může to být způsobeno několika dokončení žádosti o registraci a vnitřní chyby.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Nepokoušejte se zaregistrovat se na dokončení více než jednou.  Také kontrolovat stav řetězce v rámci zpráva trasování, má-li zjistit, jestli existuje jakoukoli užitečné.  
  
## <a name="see-also"></a>Viz také:

- [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
