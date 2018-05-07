---
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.date: 03/30/2017
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
ms.openlocfilehash: 9dd2ba5a3e94ff794d4b8a8775944355b105f790
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a>Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
Zařazení v transakci pomocí kontextu zadaný koordinaci služba protokolu WS-AT se nezdařilo.  
  
## <a name="description"></a>Popis  
 Sledovat, když služba MSDTC nelze uvést v transakci pro danou 2pc protokol.  Tomu může dojít, protože transakce již neexistuje, uvedení již není povoleno nebo příliš mnoho zařazení jsou již přítomny.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Zkontrolujte stav řetězce v rámci zpráva trasování, která k určení, zda existuje libovolnou položku níž lze provést akci.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
