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
ms.openlocfilehash: f90ba7a245b36b24c190304f34a4481d1abda121
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a>Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
Zařazení v transakci pomocí kontextu zadaný koordinaci služba protokolu WS-AT se nezdařilo.  
  
## <a name="description"></a>Popis  
 Sledovat, když služba MSDTC nelze uvést v transakci pro danou 2pc protokol.  Tomu může dojít, protože transakce již neexistuje, uvedení již není povoleno nebo příliš mnoho zařazení jsou již přítomny.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Zkontrolujte stav řetězce v rámci zpráva trasování, která k určení, zda existuje libovolnou položku níž lze provést akci.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Řešení potíží s vaší aplikace pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Správa a Diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
