---
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.date: 03/30/2017
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
ms.openlocfilehash: d000447245d973916dfe0df9af5c46b6fa822e32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a>Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
Opakování opětovného přehrání zpráva byla odeslána reagovat coordinator.  
  
## <a name="description"></a>Popis  
 Trasovat potřeby formou opakovaného přehrávání zprávy, která se nadřízený koordinátor znovu odeslat, protože nepřijala odpověď dané množství času místní správce transakcí.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Zjistěte, jestli potenciální sítě nebo problémů produktu, které brání doručován včas odpověď.  Pokud řadu tyto zprávy se zobrazují, může to znamenat problémy s infrastrukturou nebo neobvykle dlouhou dobou odezvy. Obě tyto chyby se výrazně zjednodušit propustnost transakce v rámci systému.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
