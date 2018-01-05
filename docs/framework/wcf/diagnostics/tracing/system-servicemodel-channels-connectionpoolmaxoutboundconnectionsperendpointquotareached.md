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
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a><span data-ttu-id="a1c5e-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="a1c5e-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span></span>
<span data-ttu-id="a1c5e-103">Zařazení v transakci pomocí kontextu zadaný koordinaci služba protokolu WS-AT se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="a1c5e-103">The WS-AT protocol service failed to enlist on a transaction using the provided coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a1c5e-104">Popis</span><span class="sxs-lookup"><span data-stu-id="a1c5e-104">Description</span></span>  
 <span data-ttu-id="a1c5e-105">Sledovat, když služba MSDTC nelze uvést v transakci pro danou 2pc protokol.</span><span class="sxs-lookup"><span data-stu-id="a1c5e-105">Traced when MSDTC is unable to enlist on a transaction for a given 2pc protocol.</span></span>  <span data-ttu-id="a1c5e-106">Tomu může dojít, protože transakce již neexistuje, uvedení již není povoleno nebo příliš mnoho zařazení jsou již přítomny.</span><span class="sxs-lookup"><span data-stu-id="a1c5e-106">This can happen because the transaction no longer exists, enlisting is no longer allowed, or too many enlistments are already present.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="a1c5e-107">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="a1c5e-107">Troubleshooting</span></span>  
 <span data-ttu-id="a1c5e-108">Zkontrolujte stav řetězce v rámci zpráva trasování, která k určení, zda existuje libovolnou položku níž lze provést akci.</span><span class="sxs-lookup"><span data-stu-id="a1c5e-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1c5e-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1c5e-109">See Also</span></span>  
 [<span data-ttu-id="a1c5e-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="a1c5e-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="a1c5e-111">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="a1c5e-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="a1c5e-112">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="a1c5e-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
