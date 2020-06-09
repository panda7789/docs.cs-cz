---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: c398fc52d5924c033500b95924f9287b43cc9e9d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576600"
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a>System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
Zadaná transakce byla přerušena, protože nebyla dokončena při zavření relace a TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute byla nastavena na hodnotu false.  
  
## <a name="description"></a>Popis  
 Sledováno, pokud byla aktuální aktivní relace zavřena a transakce nebyla dokončena a TransactionAutoCompleteOnSessionClose je nastavena na hodnotu `false` .  
  
## <a name="troubleshooting"></a>Řešení potíží  
 Toto trasování indikuje potenciální chybu aplikace, která by se měla prozkoumat.  
  
## <a name="see-also"></a>Viz také

- [Trasování](index.md)
- [Řešení potíží s aplikací pomocí trasování](using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../index.md)
