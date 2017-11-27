---
title: Microsoft.Transactions.TransactionBridge.CreateTransactionFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3468e23-49a9-4a84-972d-a79a658851b3
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 19312862a9ae801ae0909c390b0c86ee989f7f94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgecreatetransactionfailure"></a><span data-ttu-id="22969-102">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="22969-102">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span></span>
<span data-ttu-id="22969-103">Transakce se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="22969-103">A transaction could not be created.</span></span>  
  
## <a name="description"></a><span data-ttu-id="22969-104">Popis</span><span class="sxs-lookup"><span data-stu-id="22969-104">Description</span></span>  
 <span data-ttu-id="22969-105">Trasování se vygeneruje, když se nepodařilo vytvořit transakce služby MS DTC.</span><span class="sxs-lookup"><span data-stu-id="22969-105">This trace is generated when MSDTC is unable to create a transaction.</span></span> <span data-ttu-id="22969-106">To může být z důvodu nízkého stavu prostředků, protokolu dostatek místa nebo jiné chyby.</span><span class="sxs-lookup"><span data-stu-id="22969-106">This can be due to low resources, insufficient log space, or other errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="22969-107">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="22969-107">Troubleshooting</span></span>  
 <span data-ttu-id="22969-108">Zkontrolujte stav řetězce v rámci zpráva trasování, která k určení, zda existuje libovolnou položku níž lze provést akci.</span><span class="sxs-lookup"><span data-stu-id="22969-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22969-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="22969-109">See Also</span></span>  
 [<span data-ttu-id="22969-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="22969-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="22969-111">Řešení potíží s vaší aplikace pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="22969-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="22969-112">Správa a Diagnostika</span><span class="sxs-lookup"><span data-stu-id="22969-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
