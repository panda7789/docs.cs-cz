---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: b94c017f6ed3a76a6bc5ed2cb970877ad18ef9ea
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610419"
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
