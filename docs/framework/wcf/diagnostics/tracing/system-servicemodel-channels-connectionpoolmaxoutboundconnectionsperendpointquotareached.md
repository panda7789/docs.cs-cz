---
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 41cb1b301d3abc6a15992f36929416053ffa6069
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
