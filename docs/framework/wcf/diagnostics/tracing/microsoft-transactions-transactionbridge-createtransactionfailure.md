---
title: Microsoft.Transactions.TransactionBridge.CreateTransactionFailure
ms.date: 03/30/2017
ms.assetid: c3468e23-49a9-4a84-972d-a79a658851b3
ms.openlocfilehash: 968444947714315bae902d3d038129c5b8a04cf2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082513"
---
# <a name="microsofttransactionstransactionbridgecreatetransactionfailure"></a><span data-ttu-id="4e26f-102">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="4e26f-102">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span></span>
<span data-ttu-id="4e26f-103">Transakci nelze vytvořit.</span><span class="sxs-lookup"><span data-stu-id="4e26f-103">A transaction could not be created.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4e26f-104">Popis</span><span class="sxs-lookup"><span data-stu-id="4e26f-104">Description</span></span>  
 <span data-ttu-id="4e26f-105">Trasování se vygeneruje, když není schopen vytvořit transakci MSDTC.</span><span class="sxs-lookup"><span data-stu-id="4e26f-105">This trace is generated when MSDTC is unable to create a transaction.</span></span> <span data-ttu-id="4e26f-106">To může být z důvodu nedostatku prostředků, místo dostatek protokolu nebo jiné chyby.</span><span class="sxs-lookup"><span data-stu-id="4e26f-106">This can be due to low resources, insufficient log space, or other errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="4e26f-107">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="4e26f-107">Troubleshooting</span></span>  
 <span data-ttu-id="4e26f-108">Zkontrolujte stav řetězce v rámci zpráva trasování, má-li zjistit, jestli existuje jakoukoli užitečné.</span><span class="sxs-lookup"><span data-stu-id="4e26f-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e26f-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4e26f-109">See also</span></span>

- [<span data-ttu-id="4e26f-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="4e26f-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="4e26f-111">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="4e26f-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="4e26f-112">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="4e26f-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
