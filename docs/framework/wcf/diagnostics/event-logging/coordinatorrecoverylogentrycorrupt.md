---
title: CoordinatorRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
ms.openlocfilehash: de9d27e74088b1bac9c8a401c5af2b119fc8e90e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797983"
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="9d609-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="9d609-102">CoordinatorRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="9d609-103">Účet 139</span><span class="sxs-lookup"><span data-stu-id="9d609-103">Id: 139</span></span>  
  
 <span data-ttu-id="9d609-104">Závažnost Chyba</span><span class="sxs-lookup"><span data-stu-id="9d609-104">Severity: Error</span></span>  
  
 <span data-ttu-id="9d609-105">Kategorií TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="9d609-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="9d609-106">Popis</span><span class="sxs-lookup"><span data-stu-id="9d609-106">Description</span></span>  
 <span data-ttu-id="9d609-107">Tato událost označuje, že položka protokolu obnovení koordinátora byla poškozena a nelze ji deserializovat.</span><span class="sxs-lookup"><span data-stu-id="9d609-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="9d609-108">Tato chyba může být způsobena ztrátou dat.</span><span class="sxs-lookup"><span data-stu-id="9d609-108">Data loss may result from this error.</span></span> <span data-ttu-id="9d609-109">Událost uvádí ID transakce, data obnovení (kódovaná v kódování Base64), výjimku, název procesu a ID procesu.</span><span class="sxs-lookup"><span data-stu-id="9d609-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d609-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d609-110">See also</span></span>

- [<span data-ttu-id="9d609-111">Protokolování událostí</span><span class="sxs-lookup"><span data-stu-id="9d609-111">Event Logging</span></span>](index.md)
- [<span data-ttu-id="9d609-112">Události – obecné referenční informace</span><span class="sxs-lookup"><span data-stu-id="9d609-112">Events General Reference</span></span>](events-general-reference.md)
