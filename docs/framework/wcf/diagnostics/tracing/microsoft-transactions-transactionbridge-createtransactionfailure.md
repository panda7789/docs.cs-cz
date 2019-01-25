---
title: Microsoft.Transactions.TransactionBridge.CreateTransactionFailure
ms.date: 03/30/2017
ms.assetid: c3468e23-49a9-4a84-972d-a79a658851b3
ms.openlocfilehash: 947391e0594ffddba8235c519a076d330b73d4d3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632631"
---
# <a name="microsofttransactionstransactionbridgecreatetransactionfailure"></a><span data-ttu-id="5e385-102">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="5e385-102">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span></span>
<span data-ttu-id="5e385-103">Transakci nelze vytvořit.</span><span class="sxs-lookup"><span data-stu-id="5e385-103">A transaction could not be created.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5e385-104">Popis</span><span class="sxs-lookup"><span data-stu-id="5e385-104">Description</span></span>  
 <span data-ttu-id="5e385-105">Trasování se vygeneruje, když není schopen vytvořit transakci MSDTC.</span><span class="sxs-lookup"><span data-stu-id="5e385-105">This trace is generated when MSDTC is unable to create a transaction.</span></span> <span data-ttu-id="5e385-106">To může být z důvodu nedostatku prostředků, místo dostatek protokolu nebo jiné chyby.</span><span class="sxs-lookup"><span data-stu-id="5e385-106">This can be due to low resources, insufficient log space, or other errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="5e385-107">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="5e385-107">Troubleshooting</span></span>  
 <span data-ttu-id="5e385-108">Zkontrolujte stav řetězce v rámci zpráva trasování, má-li zjistit, jestli existuje jakoukoli užitečné.</span><span class="sxs-lookup"><span data-stu-id="5e385-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e385-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5e385-109">See also</span></span>
- [<span data-ttu-id="5e385-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="5e385-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="5e385-111">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="5e385-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="5e385-112">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="5e385-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
