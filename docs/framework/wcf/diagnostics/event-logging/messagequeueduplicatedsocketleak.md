---
title: MessageQueueDuplicatedSocketLeak
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9721a463-15d1-43dc-8e3a-cae44448de91
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 374a5900839dc1f0151743126de16369fa6bf7ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="messagequeueduplicatedsocketleak"></a><span data-ttu-id="30100-102">MessageQueueDuplicatedSocketLeak</span><span class="sxs-lookup"><span data-stu-id="30100-102">MessageQueueDuplicatedSocketLeak</span></span>
<span data-ttu-id="30100-103">ID: 165</span><span class="sxs-lookup"><span data-stu-id="30100-103">Id: 165</span></span>  
  
 <span data-ttu-id="30100-104">Závažnost: Chyba</span><span class="sxs-lookup"><span data-stu-id="30100-104">Severity: Error</span></span>  
  
 <span data-ttu-id="30100-105">Kategorie: SMSvcHost</span><span class="sxs-lookup"><span data-stu-id="30100-105">Category: SMSvcHost</span></span>  
  
## <a name="description"></a><span data-ttu-id="30100-106">Popis</span><span class="sxs-lookup"><span data-stu-id="30100-106">Description</span></span>  
 <span data-ttu-id="30100-107">Tato událost označuje, že došlo k chybě při odesílání duplicitní soketu.</span><span class="sxs-lookup"><span data-stu-id="30100-107">This event indicates that an error occurred while dispatching a duplicated socket.</span></span> <span data-ttu-id="30100-108">Tento popisovač je nyní úniku v procesu.</span><span class="sxs-lookup"><span data-stu-id="30100-108">This handle is now leaked in the process.</span></span> <span data-ttu-id="30100-109">Události jsou uvedeny zdroje, výjimky, název procesu a ID procesu.</span><span class="sxs-lookup"><span data-stu-id="30100-109">The event lists the Source, Exception, Process Name and Process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30100-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="30100-110">See Also</span></span>  
 [<span data-ttu-id="30100-111">Protokolování událostí</span><span class="sxs-lookup"><span data-stu-id="30100-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="30100-112">Události Obecné referenční informace</span><span class="sxs-lookup"><span data-stu-id="30100-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
