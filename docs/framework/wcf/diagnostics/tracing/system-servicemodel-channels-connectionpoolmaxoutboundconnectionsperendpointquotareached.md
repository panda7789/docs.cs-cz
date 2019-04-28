---
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.date: 03/30/2017
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
ms.openlocfilehash: 93c96d94aaeddeb7e7b04ea80645b8de95b0343e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666791"
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a>Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
Službě protokolu WS-AT se nepodařilo zapsat na transakci pomocí poskytnutého koordinačního kontextu.  
  
## <a name="description"></a>Popis  
 Sledovat, když není schopen zařazení v transakci pro danou 2pc protokol MSDTC.  To může nastat, protože transakce již existuje, uvedení již není povolena nebo moc velký počet zařazení jsou již přítomny.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Zkontrolujte stav řetězce v rámci zpráva trasování, má-li zjistit, jestli existuje jakoukoli užitečné.  
  
## <a name="see-also"></a>Viz také:

- [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
