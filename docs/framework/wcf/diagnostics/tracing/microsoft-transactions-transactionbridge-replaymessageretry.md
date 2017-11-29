---
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9e7e87c379c84829934a929ec27bd5dacde3931f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a>Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
Opakování opětovného přehrání zpráva byla odeslána reagovat coordinator.  
  
## <a name="description"></a>Popis  
 Trasovat potřeby formou opakovaného přehrávání zprávy, která se nadřízený koordinátor znovu odeslat, protože nepřijala odpověď dané množství času místní správce transakcí.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Zjistěte, jestli potenciální sítě nebo problémů produktu, které brání doručován včas odpověď.  Pokud řadu tyto zprávy se zobrazují, může to znamenat problémy s infrastrukturou nebo neobvykle dlouhou dobou odezvy. Obě tyto chyby se výrazně zjednodušit propustnost transakce v rámci systému.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení potíží s vaší aplikace pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a Diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
