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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5fa64c87bc4cd0c8dc677d8b4c59de45e31d3270
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a><span data-ttu-id="aa123-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="aa123-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span></span>
<span data-ttu-id="aa123-103">Zařazení v transakci pomocí kontextu zadaný koordinaci služba protokolu WS-AT se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="aa123-103">The WS-AT protocol service failed to enlist on a transaction using the provided coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="aa123-104">Popis</span><span class="sxs-lookup"><span data-stu-id="aa123-104">Description</span></span>  
 <span data-ttu-id="aa123-105">Sledovat, když služba MSDTC nelze uvést v transakci pro danou 2pc protokol.</span><span class="sxs-lookup"><span data-stu-id="aa123-105">Traced when MSDTC is unable to enlist on a transaction for a given 2pc protocol.</span></span>  <span data-ttu-id="aa123-106">Tomu může dojít, protože transakce již neexistuje, uvedení již není povoleno nebo příliš mnoho zařazení jsou již přítomny.</span><span class="sxs-lookup"><span data-stu-id="aa123-106">This can happen because the transaction no longer exists, enlisting is no longer allowed, or too many enlistments are already present.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="aa123-107">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="aa123-107">Troubleshooting</span></span>  
 <span data-ttu-id="aa123-108">Zkontrolujte stav řetězce v rámci zpráva trasování, která k určení, zda existuje libovolnou položku níž lze provést akci.</span><span class="sxs-lookup"><span data-stu-id="aa123-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa123-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="aa123-109">See Also</span></span>  
 [<span data-ttu-id="aa123-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="aa123-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="aa123-111">Řešení potíží s vaší aplikace pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="aa123-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="aa123-112">Správa a Diagnostika</span><span class="sxs-lookup"><span data-stu-id="aa123-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
