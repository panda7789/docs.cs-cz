---
title: CoordinatorRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
ms.openlocfilehash: 3f51d1269f5ca89f4f02257c8accef3423aa7eb5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33472680"
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="f5cb6-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="f5cb6-102">CoordinatorRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="f5cb6-103">ID: 139</span><span class="sxs-lookup"><span data-stu-id="f5cb6-103">Id: 139</span></span>  
  
 <span data-ttu-id="f5cb6-104">Závažnost: Chyba</span><span class="sxs-lookup"><span data-stu-id="f5cb6-104">Severity: Error</span></span>  
  
 <span data-ttu-id="f5cb6-105">Kategorie: TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="f5cb6-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="f5cb6-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f5cb6-106">Description</span></span>  
 <span data-ttu-id="f5cb6-107">Tato událost označuje, že položka protokolu obnovení koordinátora byl poškozen a nelze deserializovat.</span><span class="sxs-lookup"><span data-stu-id="f5cb6-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="f5cb6-108">Z této chybě může dojít ke ztrátě dat.</span><span class="sxs-lookup"><span data-stu-id="f5cb6-108">Data loss may result from this error.</span></span> <span data-ttu-id="f5cb6-109">Seznamy událost ID transakce, obnovení dat (kódováním Base64), výjimky, název procesu a proces.</span><span class="sxs-lookup"><span data-stu-id="f5cb6-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5cb6-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5cb6-110">See Also</span></span>  
 [<span data-ttu-id="f5cb6-111">Protokolování událostí</span><span class="sxs-lookup"><span data-stu-id="f5cb6-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="f5cb6-112">Události – obecné referenční informace</span><span class="sxs-lookup"><span data-stu-id="f5cb6-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
