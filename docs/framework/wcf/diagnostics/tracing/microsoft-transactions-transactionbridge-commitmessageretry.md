---
title: Microsoft.Transactions.TransactionBridge.CommitMessageRetry
ms.date: 03/30/2017
ms.assetid: 4abe01f0-6398-4fba-b2f3-c054b7f7e971
ms.openlocfilehash: f37bc252e12aef94d77c0745d36b5c8232a169eb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599734"
---
# <a name="microsofttransactionstransactionbridgecommitmessageretry"></a>Microsoft.Transactions.TransactionBridge.CommitMessageRetry
Zpráva potvrzení byla znovu poslána účastníkovi, který nereagoval.  
  
## <a name="description"></a>Popis  
 Sledováno, pokud správce místní transakce potřebuje znovu odeslat zprávu potvrzení podřízenému účastníkovi, protože v daném čase nedostal odpověď.  
  
## <a name="troubleshooting"></a>Řešení potíží  
 Prozkoumejte potenciální problémy se sítí nebo produktem, které brání doručení odpovědi včas.  Pokud se zobrazí mnoho z těchto zpráv, může to znamenat problémy s infrastrukturou nebo nezvykle dlouhou dobu odezvy. Oba problémy budou významně snižovat propustnost transakcí v rámci systému.  
  
## <a name="see-also"></a>Viz také

- [Trasování](index.md)
- [Řešení potíží s aplikací pomocí trasování](using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../index.md)
