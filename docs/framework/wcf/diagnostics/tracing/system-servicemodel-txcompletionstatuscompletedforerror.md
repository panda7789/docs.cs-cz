---
title: System.ServiceModel.TxCompletionStatusCompletedForError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ade4722-a6d5-471c-b960-1cfea4ea2aa9
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4bce99f11ba5a18e80c24fc51e65b66de97f9e7d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodeltxcompletionstatuscompletedforerror"></a><span data-ttu-id="5b5c0-102">System.ServiceModel.TxCompletionStatusCompletedForError</span><span class="sxs-lookup"><span data-stu-id="5b5c0-102">System.ServiceModel.TxCompletionStatusCompletedForError</span></span>
<span data-ttu-id="5b5c0-103">Zadanou transakci pro zadanou operaci byla dokončena z důvodu nezpracované výjimce provádění.</span><span class="sxs-lookup"><span data-stu-id="5b5c0-103">The specified transaction for the specified operation was completed due to an unhandled execution exception.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5b5c0-104">Popis</span><span class="sxs-lookup"><span data-stu-id="5b5c0-104">Description</span></span>  
 <span data-ttu-id="5b5c0-105">Sledovat, když dojde k chybě při pokusu o dokončení aktuální transakci.</span><span class="sxs-lookup"><span data-stu-id="5b5c0-105">Traced when an error occurs during an attempt to complete the current transaction.</span></span> <span data-ttu-id="5b5c0-106">K tomu dojde před odpověď nebo selhání odesílání volajícímu.</span><span class="sxs-lookup"><span data-stu-id="5b5c0-106">This happens before a reply or fault is sent to the caller.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="5b5c0-107">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="5b5c0-107">Troubleshooting</span></span>  
 <span data-ttu-id="5b5c0-108">Zkontrolujte trasovaná zprávu pro zprávu výjimky a všechny položky, kterého lze provést akci.</span><span class="sxs-lookup"><span data-stu-id="5b5c0-108">Inspect the traced message for the exception message and any actionable items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b5c0-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b5c0-109">See Also</span></span>  
 [<span data-ttu-id="5b5c0-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="5b5c0-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="5b5c0-111">Řešení potíží s vaší aplikace pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="5b5c0-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="5b5c0-112">Správa a Diagnostika</span><span class="sxs-lookup"><span data-stu-id="5b5c0-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
