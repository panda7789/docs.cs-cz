---
title: Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
ms.date: 03/30/2017
ms.assetid: ada4baa5-b60d-46b8-ad46-4d69f8d8a9fa
ms.openlocfilehash: affa647b30dbeb9237e4c20ebb441645eda94276
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474321"
---
# <a name="microsofttransactionstransactionbridgepreparemessageretry"></a>Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
Příprava opakování zpráva byla odeslána reagovat účastník.  
  
## <a name="description"></a>Popis  
 Sledovat v případě potřeby místní správce transakcí o doručení zprávy Příprava na podřízené účastník, protože nepřijala odpověď dané množství času.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Zjistěte, jestli potenciální sítě nebo problémů produktu, které brání doručován včas odpověď.  Pokud řadu tyto zprávy se zobrazují, může to znamenat problémy s infrastrukturou nebo neobvykle dlouhou dobou odezvy. Obě problémy může výrazně snížit propustnost transakce v rámci systému.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
