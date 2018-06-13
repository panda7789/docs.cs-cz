---
title: Microsoft.Transactions.TransactionBridge.CreateTransactionFailure
ms.date: 03/30/2017
ms.assetid: c3468e23-49a9-4a84-972d-a79a658851b3
ms.openlocfilehash: 67da873444fa067943b202239a0f5675cfa1e388
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474624"
---
# <a name="microsofttransactionstransactionbridgecreatetransactionfailure"></a><span data-ttu-id="845e8-102">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="845e8-102">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span></span>
<span data-ttu-id="845e8-103">Transakce se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="845e8-103">A transaction could not be created.</span></span>  
  
## <a name="description"></a><span data-ttu-id="845e8-104">Popis</span><span class="sxs-lookup"><span data-stu-id="845e8-104">Description</span></span>  
 <span data-ttu-id="845e8-105">Trasování se vygeneruje, když se nepodařilo vytvořit transakce služby MS DTC.</span><span class="sxs-lookup"><span data-stu-id="845e8-105">This trace is generated when MSDTC is unable to create a transaction.</span></span> <span data-ttu-id="845e8-106">To může být z důvodu nízkého stavu prostředků, protokolu dostatek místa nebo jiné chyby.</span><span class="sxs-lookup"><span data-stu-id="845e8-106">This can be due to low resources, insufficient log space, or other errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="845e8-107">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="845e8-107">Troubleshooting</span></span>  
 <span data-ttu-id="845e8-108">Zkontrolujte stav řetězce v rámci zpráva trasování, která k určení, zda existuje libovolnou položku níž lze provést akci.</span><span class="sxs-lookup"><span data-stu-id="845e8-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="845e8-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="845e8-109">See Also</span></span>  
 [<span data-ttu-id="845e8-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="845e8-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="845e8-111">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="845e8-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="845e8-112">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="845e8-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
