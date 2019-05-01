---
title: Microsoft.Transactions.TransactionBridge.CreateTransactionFailure
ms.date: 03/30/2017
ms.assetid: c3468e23-49a9-4a84-972d-a79a658851b3
ms.openlocfilehash: 968444947714315bae902d3d038129c5b8a04cf2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61997942"
---
# <a name="microsofttransactionstransactionbridgecreatetransactionfailure"></a><span data-ttu-id="a0908-102">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="a0908-102">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span></span>
<span data-ttu-id="a0908-103">Transakci nelze vytvořit.</span><span class="sxs-lookup"><span data-stu-id="a0908-103">A transaction could not be created.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a0908-104">Popis</span><span class="sxs-lookup"><span data-stu-id="a0908-104">Description</span></span>  
 <span data-ttu-id="a0908-105">Trasování se vygeneruje, když není schopen vytvořit transakci MSDTC.</span><span class="sxs-lookup"><span data-stu-id="a0908-105">This trace is generated when MSDTC is unable to create a transaction.</span></span> <span data-ttu-id="a0908-106">To může být z důvodu nedostatku prostředků, místo dostatek protokolu nebo jiné chyby.</span><span class="sxs-lookup"><span data-stu-id="a0908-106">This can be due to low resources, insufficient log space, or other errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="a0908-107">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="a0908-107">Troubleshooting</span></span>  
 <span data-ttu-id="a0908-108">Zkontrolujte stav řetězce v rámci zpráva trasování, má-li zjistit, jestli existuje jakoukoli užitečné.</span><span class="sxs-lookup"><span data-stu-id="a0908-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0908-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0908-109">See also</span></span>

- [<span data-ttu-id="a0908-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="a0908-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="a0908-111">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="a0908-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="a0908-112">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="a0908-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
