---
title: Microsoft.Transactions.TransactionBridge.CommitMessageRetry
ms.date: 03/30/2017
ms.assetid: 4abe01f0-6398-4fba-b2f3-c054b7f7e971
ms.openlocfilehash: 3c398aa13a8cd2b87068216d3c07fb29e1a27c3f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168100"
---
# <a name="microsofttransactionstransactionbridgecommitmessageretry"></a>Microsoft.Transactions.TransactionBridge.CommitMessageRetry
Opakování zpráva potvrzení byla odeslána poslána účastníkovi.  
  
## <a name="description"></a>Popis  
 Trasovaná potřeby znovu odeslat zprávu potvrzení do podřízeného člena, protože neobdržela odpověď v daném čase místní správce transakcí.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Prošetření potenciálních sítě nebo problémů s produktem, které brání znemožňuje doručování včas odpověď.  Pokud řadu tyto zprávy se zobrazují, může to znamenat problémy s infrastrukturou nebo neobvykle dlouhou dobou odezvy. Oba problémy výrazně zkrátí propustnost transakcí v rámci systému.  
  
## <a name="see-also"></a>Viz také:

- [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Řešení potíží s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
