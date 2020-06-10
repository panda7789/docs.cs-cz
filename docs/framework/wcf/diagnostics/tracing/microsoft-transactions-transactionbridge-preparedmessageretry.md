---
title: Microsoft.Transactions.TransactionBridge.PreparedMessageRetry
ms.date: 03/30/2017
ms.assetid: 2194292d-bf5f-4aef-9336-cd3c4795cb71
ms.openlocfilehash: 50dd3070525bbc6d36956b25dee587ec7864d3ff
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594306"
---
# <a name="microsofttransactionstransactionbridgepreparedmessageretry"></a>Microsoft.Transactions.TransactionBridge.PreparedMessageRetry
Připravená zpráva byla znovu poslána koordinátorovi, který nereaguje.  
  
## <a name="description"></a>Popis  
 Sledováno, pokud správce místní transakce potřebuje znovu odeslat připravenou zprávu nadřazenému koordinátorovi, protože nedostal odpověď v daném časovém intervalu.  
  
## <a name="troubleshooting"></a>Řešení potíží  
 Prozkoumejte potenciální problémy se sítí nebo produktem, které brání doručení odpovědi včas.  Pokud se zobrazí mnoho z těchto zpráv, může to znamenat problémy s infrastrukturou nebo nezvykle dlouhou dobu odezvy. Oba problémy budou významně snižovat propustnost transakcí v rámci systému.  
  
## <a name="see-also"></a>Viz také

- [Trasování](index.md)
- [Řešení potíží s aplikací pomocí trasování](using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../index.md)
