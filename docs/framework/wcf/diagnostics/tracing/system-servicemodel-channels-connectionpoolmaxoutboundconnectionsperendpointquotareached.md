---
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.date: 03/30/2017
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
ms.openlocfilehash: 4f51777ae690178b83d353f72e63a6f2958b1592
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674580"
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
