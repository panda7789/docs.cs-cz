---
title: Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
ms.date: 03/30/2017
ms.assetid: ada4baa5-b60d-46b8-ad46-4d69f8d8a9fa
ms.openlocfilehash: 0c53c1617f3aa3c5f16ba16e8ec548e46ce22137
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594332"
---
# <a name="microsofttransactionstransactionbridgepreparemessageretry"></a>Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
Připravená zpráva byla znovu poslána účastníkovi, který nereaguje.  
  
## <a name="description"></a>Popis  
 Sledováno, pokud správce místní transakce potřebuje znovu odeslat přípravu zprávy podřízenému účastníkovi, protože v daném čase nedostal odpověď.  
  
## <a name="troubleshooting"></a>Řešení potíží  
 Prozkoumejte potenciální problémy se sítí nebo produktem, které brání doručení odpovědi včas.  Pokud se zobrazí mnoho z těchto zpráv, může to znamenat problémy s infrastrukturou nebo nezvykle dlouhou dobu odezvy. Oba problémy můžou významně snížit propustnost transakcí v rámci systému.  
  
## <a name="see-also"></a>Viz také

- [Trasování](index.md)
- [Řešení potíží s aplikací pomocí trasování](using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../index.md)
