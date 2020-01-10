---
title: Sporné události ETW – .NET
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
ms.openlocfilehash: 98fc2adcaebe4c9646ab9960f796982681a9015a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716138"
---
# <a name="contention-etw-events"></a><span data-ttu-id="a2795-102">Sporné události ETW</span><span class="sxs-lookup"><span data-stu-id="a2795-102">Contention ETW events</span></span>

<span data-ttu-id="a2795-103">Události kolizí jsou vyvolány vždy, když dojde ke sporu pro <xref:System.Threading.Monitor?displayProperty=nameWithType> zámky nebo nativní zámky používané modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="a2795-103">Contention events are raised whenever there is contention for <xref:System.Threading.Monitor?displayProperty=nameWithType> locks or native locks used by the runtime.</span></span> <span data-ttu-id="a2795-104">K sporům dochází, když vlákno čeká na zámek, zatímco jiné vlákno má zámek.</span><span class="sxs-lookup"><span data-stu-id="a2795-104">Contention occurs when a thread is waiting for a lock while another thread possesses the lock.</span></span>

<span data-ttu-id="a2795-105">Následující tabulka ukazuje klíčové slovo, pod kterým jsou vyvolány události kolizí, a úroveň událostí.</span><span class="sxs-lookup"><span data-stu-id="a2795-105">The following table shows the keyword under which contention events are raised, and the level of the events.</span></span> <span data-ttu-id="a2795-106">Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a2795-106">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="a2795-107">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="a2795-107">Keyword for raising the event</span></span>|<span data-ttu-id="a2795-108">Úroveň</span><span class="sxs-lookup"><span data-stu-id="a2795-108">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a2795-109">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="a2795-109">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="a2795-110">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="a2795-110">Informational (4)</span></span>|

<span data-ttu-id="a2795-111">Následující tabulka obsahuje informace o události:</span><span class="sxs-lookup"><span data-stu-id="a2795-111">The following table shows event information:</span></span>

|<span data-ttu-id="a2795-112">Událost</span><span class="sxs-lookup"><span data-stu-id="a2795-112">Event</span></span>|<span data-ttu-id="a2795-113">ID události</span><span class="sxs-lookup"><span data-stu-id="a2795-113">Event ID</span></span>|<span data-ttu-id="a2795-114">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="a2795-114">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|<span data-ttu-id="a2795-115">81</span><span class="sxs-lookup"><span data-stu-id="a2795-115">81</span></span>|<span data-ttu-id="a2795-116">Je zahájeno spor.</span><span class="sxs-lookup"><span data-stu-id="a2795-116">Contention starts.</span></span> <span data-ttu-id="a2795-117">Tato událost nezahrnuje dobu, po kterou vlákno čeká na získání zámku. je vyvolána pouze v případě, že vlákno čeká na získání zámku.</span><span class="sxs-lookup"><span data-stu-id="a2795-117">This event does not include the amount of spinning time before a thread waits to acquire a lock; it is raised only when the thread waits to acquire a lock.</span></span>|
|`ContentionStop`|<span data-ttu-id="a2795-118">91</span><span class="sxs-lookup"><span data-stu-id="a2795-118">91</span></span>|<span data-ttu-id="a2795-119">Spory končí.</span><span class="sxs-lookup"><span data-stu-id="a2795-119">Contention ends.</span></span>|

<span data-ttu-id="a2795-120">V následující tabulce jsou uvedena data události:</span><span class="sxs-lookup"><span data-stu-id="a2795-120">The following table shows event data:</span></span>

|<span data-ttu-id="a2795-121">Název pole</span><span class="sxs-lookup"><span data-stu-id="a2795-121">Field name</span></span>|<span data-ttu-id="a2795-122">Datový typ</span><span class="sxs-lookup"><span data-stu-id="a2795-122">Data type</span></span>|<span data-ttu-id="a2795-123">Popis</span><span class="sxs-lookup"><span data-stu-id="a2795-123">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="a2795-124">Příznaky</span><span class="sxs-lookup"><span data-stu-id="a2795-124">Flags</span></span>|<span data-ttu-id="a2795-125">Win: UInt8</span><span class="sxs-lookup"><span data-stu-id="a2795-125">win:UInt8</span></span>|<span data-ttu-id="a2795-126">0 pro správu; 1 pro nativní.</span><span class="sxs-lookup"><span data-stu-id="a2795-126">0 for managed; 1 for native.</span></span>|
|<span data-ttu-id="a2795-127">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a2795-127">ClrInstanceID</span></span>|<span data-ttu-id="a2795-128">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="a2795-128">win:UInt16</span></span>|<span data-ttu-id="a2795-129">Jedinečné ID pro instanci CLR.</span><span class="sxs-lookup"><span data-stu-id="a2795-129">Unique ID for the instance of CLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="a2795-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a2795-130">See also</span></span>

- [<span data-ttu-id="a2795-131">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="a2795-131">CLR ETW Events</span></span>](clr-etw-events.md)
