---
title: Kolizní události trasování událostí pro Windows – .NET
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 95f56a6c8b51c58ed36d5d0de428bf57b728009c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723937"
---
# <a name="contention-etw-events"></a><span data-ttu-id="8c4d0-102">Kolizní události trasování událostí pro Windows</span><span class="sxs-lookup"><span data-stu-id="8c4d0-102">Contention ETW events</span></span>

<span data-ttu-id="8c4d0-103">Kolizní události jsou vyvolány pokaždé, když je nutné vyřešit <xref:System.Threading.Monitor?displayProperty=nameWithType> uzamčení nebo nativní zámky modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="8c4d0-103">Contention events are raised whenever there is contention for <xref:System.Threading.Monitor?displayProperty=nameWithType> locks or native locks used by the runtime.</span></span> <span data-ttu-id="8c4d0-104">Kolize nastane, pokud vlákno čeká na zámek a jiné vlákno drží zámek.</span><span class="sxs-lookup"><span data-stu-id="8c4d0-104">Contention occurs when a thread is waiting for a lock while another thread possesses the lock.</span></span>

<span data-ttu-id="8c4d0-105">V následující tabulce jsou uvedeny klíčové slovo, pod kterým jsou vyvolány události kolize a úroveň události.</span><span class="sxs-lookup"><span data-stu-id="8c4d0-105">The following table shows the keyword under which contention events are raised, and the level of the events.</span></span> <span data-ttu-id="8c4d0-106">Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="8c4d0-106">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="8c4d0-107">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="8c4d0-107">Keyword for raising the event</span></span>|<span data-ttu-id="8c4d0-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="8c4d0-108">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="8c4d0-109">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="8c4d0-109">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="8c4d0-110">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="8c4d0-110">Informational (4)</span></span>|

<span data-ttu-id="8c4d0-111">V následující tabulce jsou uvedeny informace o události:</span><span class="sxs-lookup"><span data-stu-id="8c4d0-111">The following table shows event information:</span></span>

|<span data-ttu-id="8c4d0-112">Událost</span><span class="sxs-lookup"><span data-stu-id="8c4d0-112">Event</span></span>|<span data-ttu-id="8c4d0-113">ID události</span><span class="sxs-lookup"><span data-stu-id="8c4d0-113">Event ID</span></span>|<span data-ttu-id="8c4d0-114">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="8c4d0-114">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|<span data-ttu-id="8c4d0-115">81</span><span class="sxs-lookup"><span data-stu-id="8c4d0-115">81</span></span>|<span data-ttu-id="8c4d0-116">Kolize spustí.</span><span class="sxs-lookup"><span data-stu-id="8c4d0-116">Contention starts.</span></span> <span data-ttu-id="8c4d0-117">Tato událost nezahrnuje množství zprovozňování dobu, než vlákno čeká na získání zámku; je aktivována pouze v případě, že vlákno čeká na získání zámku.</span><span class="sxs-lookup"><span data-stu-id="8c4d0-117">This event does not include the amount of spinning time before a thread waits to acquire a lock; it is raised only when the thread waits to acquire a lock.</span></span>|
|`ContentionStop`|<span data-ttu-id="8c4d0-118">91</span><span class="sxs-lookup"><span data-stu-id="8c4d0-118">91</span></span>|<span data-ttu-id="8c4d0-119">Kolize skončí.</span><span class="sxs-lookup"><span data-stu-id="8c4d0-119">Contention ends.</span></span>|

<span data-ttu-id="8c4d0-120">V následující tabulce jsou uvedeny data události:</span><span class="sxs-lookup"><span data-stu-id="8c4d0-120">The following table shows event data:</span></span>

|<span data-ttu-id="8c4d0-121">Název pole</span><span class="sxs-lookup"><span data-stu-id="8c4d0-121">Field name</span></span>|<span data-ttu-id="8c4d0-122">Datový typ</span><span class="sxs-lookup"><span data-stu-id="8c4d0-122">Data type</span></span>|<span data-ttu-id="8c4d0-123">Popis</span><span class="sxs-lookup"><span data-stu-id="8c4d0-123">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="8c4d0-124">Příznaky</span><span class="sxs-lookup"><span data-stu-id="8c4d0-124">Flags</span></span>|<span data-ttu-id="8c4d0-125">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="8c4d0-125">win:UInt8</span></span>|<span data-ttu-id="8c4d0-126">0 pro spravované; 1 pro nativní.</span><span class="sxs-lookup"><span data-stu-id="8c4d0-126">0 for managed; 1 for native.</span></span>|
|<span data-ttu-id="8c4d0-127">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="8c4d0-127">ClrInstanceID</span></span>|<span data-ttu-id="8c4d0-128">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="8c4d0-128">win:UInt16</span></span>|<span data-ttu-id="8c4d0-129">Jedinečné ID pro instanci modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="8c4d0-129">Unique ID for the instance of CLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="8c4d0-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c4d0-130">See also</span></span>

- [<span data-ttu-id="8c4d0-131">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="8c4d0-131">CLR ETW Events</span></span>](clr-etw-events.md)
