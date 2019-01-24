---
title: ParticipantRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: ab34785f-f953-4428-93ca-3c50d3f50a4a
ms.openlocfilehash: 6856ac8b70ec30b795585b4ab2d2e76d1b61796c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684499"
---
# <a name="participantrecoverylogentrycorrupt"></a><span data-ttu-id="d99b2-102">ParticipantRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="d99b2-102">ParticipantRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="d99b2-103">Id: 138</span><span class="sxs-lookup"><span data-stu-id="d99b2-103">Id: 138</span></span>  
  
 <span data-ttu-id="d99b2-104">Závažnost: Chyba</span><span class="sxs-lookup"><span data-stu-id="d99b2-104">Severity: Error</span></span>  
  
 <span data-ttu-id="d99b2-105">Kategorie: TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="d99b2-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="d99b2-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d99b2-106">Description</span></span>  
 <span data-ttu-id="d99b2-107">Tato událost ukazuje na to, že deníkový záznam zotavení účastníka byl poškozen a nelze deserializovat.</span><span class="sxs-lookup"><span data-stu-id="d99b2-107">This event indicates that a participant recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="d99b2-108">Z této chybě může dojít ke ztrátě dat.</span><span class="sxs-lookup"><span data-stu-id="d99b2-108">Data loss may result from this error.</span></span> <span data-ttu-id="d99b2-109">ID události seznamy ID transakce, Zotavená data (základ64 kódovaný), výjimky, název procesu a proces.</span><span class="sxs-lookup"><span data-stu-id="d99b2-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d99b2-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d99b2-110">See also</span></span>
- [<span data-ttu-id="d99b2-111">Protokolování událostí</span><span class="sxs-lookup"><span data-stu-id="d99b2-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)
- [<span data-ttu-id="d99b2-112">Události – obecné referenční informace</span><span class="sxs-lookup"><span data-stu-id="d99b2-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
