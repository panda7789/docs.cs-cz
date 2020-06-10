---
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.date: 03/30/2017
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
ms.openlocfilehash: 742e80a3115e8f8caa728e0d8c460ee8b964ddc9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84588714"
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a>Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
Službě protokolu WS-AT se nepodařilo zapsat na transakci pomocí poskytnutého koordinačního kontextu.  
  
## <a name="description"></a>Popis  
 Sledováno, když služba MSDTC nemůže zapsat na transakci pro daný protokol 2PC.  K tomu může dojít, protože transakce již neexistuje, zařazení již není povoleno nebo je již k dispozici příliš mnoho zařazení.  
  
## <a name="troubleshooting"></a>Řešení potíží  
 Zkontrolujte řetězec stavu v rámci zprávy trasování a určete, zda existuje nějaká položka, která je k dispozici.  
  
## <a name="see-also"></a>Viz také

- [Trasování](index.md)
- [Řešení potíží s aplikací pomocí trasování](using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../index.md)
