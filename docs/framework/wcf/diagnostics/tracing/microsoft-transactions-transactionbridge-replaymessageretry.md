---
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.date: 03/30/2017
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
ms.openlocfilehash: 162452d5d12859571d78ef19cf1d838953ee7acd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596204"
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a>Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
Zpráva o opakovaném přehrání byla znovu poslána koordinátorovi, který nereaguje.  
  
## <a name="description"></a>Popis  
 Sledováno, pokud správce místní transakce potřebuje znovu odeslat zprávu o přehrání nadřízenému koordinátora, protože v daném čase nedostala odpověď.  
  
## <a name="troubleshooting"></a>Řešení potíží  
 Prozkoumejte potenciální problémy se sítí nebo produktem, které brání doručení odpovědi včas.  Pokud se zobrazí mnoho z těchto zpráv, může to znamenat problémy s infrastrukturou nebo nezvykle dlouhou dobu odezvy. Oba problémy budou významně snižovat propustnost transakcí v rámci systému.  
  
## <a name="see-also"></a>Viz také

- [Trasování](index.md)
- [Řešení potíží s aplikací pomocí trasování](using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../index.md)
