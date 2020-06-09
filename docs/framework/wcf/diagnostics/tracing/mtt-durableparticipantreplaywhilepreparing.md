---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: 31fb8d466c76c7490aa80dfcab089332af4036a2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589129"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a>Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
Služba protokolu WS-AT obdržela zprávu o přehrání od trvalého účastníka, který nereagoval na přípravu. V důsledku toho byla transakce přerušena.  
  
## <a name="description"></a>Popis  
 Sledováno, pokud je přijata zpráva o opětovném přehrání, zatímco se stále připravuje trvalý účastník. Toto je neplatná zpráva pro tento stav a transakce bude přerušena.  
  
## <a name="troubleshooting"></a>Řešení potíží

Přijetí této chyby může znamenat, že trvalý účastník (včetně podřízeného TransactionManagers) se obnovil z chyby. Nejedná se však o výsledek transakce a požádá o jeho stav.  
  
## <a name="see-also"></a>Viz také

- [Trasování](index.md)
- [Řešení potíží s aplikací pomocí trasování](using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../index.md)
