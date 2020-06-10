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
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a><span data-ttu-id="720e6-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="720e6-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span></span>
<span data-ttu-id="720e6-103">Službě protokolu WS-AT se nepodařilo zapsat na transakci pomocí poskytnutého koordinačního kontextu.</span><span class="sxs-lookup"><span data-stu-id="720e6-103">The WS-AT protocol service failed to enlist on a transaction using the provided coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="720e6-104">Popis</span><span class="sxs-lookup"><span data-stu-id="720e6-104">Description</span></span>  
 <span data-ttu-id="720e6-105">Sledováno, když služba MSDTC nemůže zapsat na transakci pro daný protokol 2PC.</span><span class="sxs-lookup"><span data-stu-id="720e6-105">Traced when MSDTC is unable to enlist on a transaction for a given 2pc protocol.</span></span>  <span data-ttu-id="720e6-106">K tomu může dojít, protože transakce již neexistuje, zařazení již není povoleno nebo je již k dispozici příliš mnoho zařazení.</span><span class="sxs-lookup"><span data-stu-id="720e6-106">This can happen because the transaction no longer exists, enlisting is no longer allowed, or too many enlistments are already present.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="720e6-107">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="720e6-107">Troubleshooting</span></span>  
 <span data-ttu-id="720e6-108">Zkontrolujte řetězec stavu v rámci zprávy trasování a určete, zda existuje nějaká položka, která je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="720e6-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="720e6-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="720e6-109">See also</span></span>

- [<span data-ttu-id="720e6-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="720e6-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="720e6-111">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="720e6-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="720e6-112">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="720e6-112">Administration and Diagnostics</span></span>](../index.md)
