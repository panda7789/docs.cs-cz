---
title: CoordinatorRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
ms.openlocfilehash: faf4a07badb71588c601cd9390e4d8e3f187e629
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59121625"
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="1e9ab-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="1e9ab-102">CoordinatorRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="1e9ab-103">Id: 139</span><span class="sxs-lookup"><span data-stu-id="1e9ab-103">Id: 139</span></span>  
  
 <span data-ttu-id="1e9ab-104">Závažnost: Chyba</span><span class="sxs-lookup"><span data-stu-id="1e9ab-104">Severity: Error</span></span>  
  
 <span data-ttu-id="1e9ab-105">Kategorie: TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="1e9ab-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="1e9ab-106">Popis</span><span class="sxs-lookup"><span data-stu-id="1e9ab-106">Description</span></span>  
 <span data-ttu-id="1e9ab-107">Tato událost ukazuje na to, že deníkový záznam zotavení koordinátora byl poškozen a nelze deserializovat.</span><span class="sxs-lookup"><span data-stu-id="1e9ab-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="1e9ab-108">Z této chybě může dojít ke ztrátě dat.</span><span class="sxs-lookup"><span data-stu-id="1e9ab-108">Data loss may result from this error.</span></span> <span data-ttu-id="1e9ab-109">ID události seznamy ID transakce, Zotavená data (základ64 kódovaný), výjimky, název procesu a proces.</span><span class="sxs-lookup"><span data-stu-id="1e9ab-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e9ab-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1e9ab-110">See also</span></span>

- [<span data-ttu-id="1e9ab-111">Protokolování událostí</span><span class="sxs-lookup"><span data-stu-id="1e9ab-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)
- [<span data-ttu-id="1e9ab-112">Události – obecné referenční informace</span><span class="sxs-lookup"><span data-stu-id="1e9ab-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
