---
title: Microsoft.Transactions.TransactionBridge.CommitMessageRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4abe01f0-6398-4fba-b2f3-c054b7f7e971
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58adacd909ad5254f9fb1e67b42f122e0ea01ab4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgecommitmessageretry"></a>Microsoft.Transactions.TransactionBridge.CommitMessageRetry
Opakování potvrzení zpráva byla odeslána reagovat účastník.  
  
## <a name="description"></a>Popis  
 Sledovat v případě potřeby místní správce transakcí o doručení zprávy potvrzení k podřízené účastník, protože nepřijala odpověď dané množství času.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Zjistěte, jestli potenciální sítě nebo problémů produktu, které brání doručován včas odpověď.  Pokud řadu tyto zprávy se zobrazují, může to znamenat problémy s infrastrukturou nebo neobvykle dlouhou dobou odezvy. Obě tyto chyby se výrazně zjednodušit propustnost transakce v rámci systému.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
