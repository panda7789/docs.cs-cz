---
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.date: 03/30/2017
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
ms.openlocfilehash: 93c96d94aaeddeb7e7b04ea80645b8de95b0343e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59143322"
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a><span data-ttu-id="02b17-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="02b17-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span></span>
<span data-ttu-id="02b17-103">Službě protokolu WS-AT se nepodařilo zapsat na transakci pomocí poskytnutého koordinačního kontextu.</span><span class="sxs-lookup"><span data-stu-id="02b17-103">The WS-AT protocol service failed to enlist on a transaction using the provided coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="02b17-104">Popis</span><span class="sxs-lookup"><span data-stu-id="02b17-104">Description</span></span>  
 <span data-ttu-id="02b17-105">Sledovat, když není schopen zařazení v transakci pro danou 2pc protokol MSDTC.</span><span class="sxs-lookup"><span data-stu-id="02b17-105">Traced when MSDTC is unable to enlist on a transaction for a given 2pc protocol.</span></span>  <span data-ttu-id="02b17-106">To může nastat, protože transakce již existuje, uvedení již není povolena nebo moc velký počet zařazení jsou již přítomny.</span><span class="sxs-lookup"><span data-stu-id="02b17-106">This can happen because the transaction no longer exists, enlisting is no longer allowed, or too many enlistments are already present.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="02b17-107">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="02b17-107">Troubleshooting</span></span>  
 <span data-ttu-id="02b17-108">Zkontrolujte stav řetězce v rámci zpráva trasování, má-li zjistit, jestli existuje jakoukoli užitečné.</span><span class="sxs-lookup"><span data-stu-id="02b17-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02b17-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="02b17-109">See also</span></span>

- [<span data-ttu-id="02b17-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="02b17-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="02b17-111">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="02b17-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="02b17-112">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="02b17-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
