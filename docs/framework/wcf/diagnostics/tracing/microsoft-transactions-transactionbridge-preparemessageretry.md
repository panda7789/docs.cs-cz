---
title: Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
ms.date: 03/30/2017
ms.assetid: ada4baa5-b60d-46b8-ad46-4d69f8d8a9fa
ms.openlocfilehash: f168cb24d87f3159a1ea41003c2ffa7041ce8c09
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710440"
---
# <a name="microsofttransactionstransactionbridgepreparemessageretry"></a>Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
Přípravy opakování zpráva byla odeslána poslána účastníkovi.  
  
## <a name="description"></a>Popis  
 Trasovaná potřeby znovu odeslat zprávu připravit podřízené účastníkovi, protože neobdržela odpověď v daném čase místní správce transakcí.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Prošetření potenciálních sítě nebo problémů s produktem, které brání znemožňuje doručování včas odpověď.  Pokud řadu tyto zprávy se zobrazují, může to znamenat problémy s infrastrukturou nebo neobvykle dlouhou dobou odezvy. Oba problémy může výrazně omezit propustnost transakcí v rámci systému.  
  
## <a name="see-also"></a>Viz také:
- [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
