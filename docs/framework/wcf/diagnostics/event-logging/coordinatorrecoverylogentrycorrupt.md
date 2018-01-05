---
title: CoordinatorRecoveryLogEntryCorrupt
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae2b8a8bb536d914edd6c7154136867caee553b1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="bf61e-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="bf61e-102">CoordinatorRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="bf61e-103">ID: 139</span><span class="sxs-lookup"><span data-stu-id="bf61e-103">Id: 139</span></span>  
  
 <span data-ttu-id="bf61e-104">Závažnost: Chyba</span><span class="sxs-lookup"><span data-stu-id="bf61e-104">Severity: Error</span></span>  
  
 <span data-ttu-id="bf61e-105">Kategorie: TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="bf61e-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="bf61e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="bf61e-106">Description</span></span>  
 <span data-ttu-id="bf61e-107">Tato událost označuje, že položka protokolu obnovení koordinátora byl poškozen a nelze deserializovat.</span><span class="sxs-lookup"><span data-stu-id="bf61e-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="bf61e-108">Z této chybě může dojít ke ztrátě dat.</span><span class="sxs-lookup"><span data-stu-id="bf61e-108">Data loss may result from this error.</span></span> <span data-ttu-id="bf61e-109">Seznamy událost ID transakce, obnovení dat (kódováním Base64), výjimky, název procesu a proces.</span><span class="sxs-lookup"><span data-stu-id="bf61e-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf61e-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="bf61e-110">See Also</span></span>  
 [<span data-ttu-id="bf61e-111">Protokolování událostí</span><span class="sxs-lookup"><span data-stu-id="bf61e-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="bf61e-112">Události – obecné referenční informace</span><span class="sxs-lookup"><span data-stu-id="bf61e-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
