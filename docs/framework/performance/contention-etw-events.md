---
title: Sporné události ETW – .NET
description: Získejte podrobné informace o událostech ETW pro obsah, které se vyvolají vždy, když jsou kolize kolizí pro System. Threading. monitoruje zámky nebo nativní zámky používané modulem runtime.
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
ms.openlocfilehash: a36b091e0896562fffdb66e895d70049ce0667d7
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309596"
---
# <a name="contention-etw-events"></a><span data-ttu-id="c88dd-103">Sporné události ETW</span><span class="sxs-lookup"><span data-stu-id="c88dd-103">Contention ETW events</span></span>

<span data-ttu-id="c88dd-104">Události kolizí jsou vyvolány vždy, když dojde ke sporům pro <xref:System.Threading.Monitor?displayProperty=nameWithType> zámky nebo nativní zámky používané modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="c88dd-104">Contention events are raised whenever there is contention for <xref:System.Threading.Monitor?displayProperty=nameWithType> locks or native locks used by the runtime.</span></span> <span data-ttu-id="c88dd-105">K sporům dochází, když vlákno čeká na zámek, zatímco jiné vlákno má zámek.</span><span class="sxs-lookup"><span data-stu-id="c88dd-105">Contention occurs when a thread is waiting for a lock while another thread possesses the lock.</span></span>

<span data-ttu-id="c88dd-106">Následující tabulka ukazuje klíčové slovo, pod kterým jsou vyvolány události kolizí, a úroveň událostí.</span><span class="sxs-lookup"><span data-stu-id="c88dd-106">The following table shows the keyword under which contention events are raised, and the level of the events.</span></span> <span data-ttu-id="c88dd-107">Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="c88dd-107">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="c88dd-108">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="c88dd-108">Keyword for raising the event</span></span>|<span data-ttu-id="c88dd-109">Level</span><span class="sxs-lookup"><span data-stu-id="c88dd-109">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c88dd-110">`ContentionKeyword`0x4000</span><span class="sxs-lookup"><span data-stu-id="c88dd-110">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="c88dd-111">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="c88dd-111">Informational (4)</span></span>|

<span data-ttu-id="c88dd-112">Následující tabulka obsahuje informace o události:</span><span class="sxs-lookup"><span data-stu-id="c88dd-112">The following table shows event information:</span></span>

|<span data-ttu-id="c88dd-113">Událost</span><span class="sxs-lookup"><span data-stu-id="c88dd-113">Event</span></span>|<span data-ttu-id="c88dd-114">ID události</span><span class="sxs-lookup"><span data-stu-id="c88dd-114">Event ID</span></span>|<span data-ttu-id="c88dd-115">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="c88dd-115">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|<span data-ttu-id="c88dd-116">81</span><span class="sxs-lookup"><span data-stu-id="c88dd-116">81</span></span>|<span data-ttu-id="c88dd-117">Je zahájeno spor.</span><span class="sxs-lookup"><span data-stu-id="c88dd-117">Contention starts.</span></span> <span data-ttu-id="c88dd-118">Tato událost nezahrnuje dobu, po kterou vlákno čeká na získání zámku. je vyvolána pouze v případě, že vlákno čeká na získání zámku.</span><span class="sxs-lookup"><span data-stu-id="c88dd-118">This event does not include the amount of spinning time before a thread waits to acquire a lock; it is raised only when the thread waits to acquire a lock.</span></span>|
|`ContentionStop`|<span data-ttu-id="c88dd-119">91</span><span class="sxs-lookup"><span data-stu-id="c88dd-119">91</span></span>|<span data-ttu-id="c88dd-120">Spory končí.</span><span class="sxs-lookup"><span data-stu-id="c88dd-120">Contention ends.</span></span>|

<span data-ttu-id="c88dd-121">V následující tabulce jsou uvedena data události:</span><span class="sxs-lookup"><span data-stu-id="c88dd-121">The following table shows event data:</span></span>

|<span data-ttu-id="c88dd-122">Název pole</span><span class="sxs-lookup"><span data-stu-id="c88dd-122">Field name</span></span>|<span data-ttu-id="c88dd-123">Datový typ</span><span class="sxs-lookup"><span data-stu-id="c88dd-123">Data type</span></span>|<span data-ttu-id="c88dd-124">Popis</span><span class="sxs-lookup"><span data-stu-id="c88dd-124">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="c88dd-125">Příznaky</span><span class="sxs-lookup"><span data-stu-id="c88dd-125">Flags</span></span>|<span data-ttu-id="c88dd-126">Win: UInt8</span><span class="sxs-lookup"><span data-stu-id="c88dd-126">win:UInt8</span></span>|<span data-ttu-id="c88dd-127">0 pro správu; 1 pro nativní.</span><span class="sxs-lookup"><span data-stu-id="c88dd-127">0 for managed; 1 for native.</span></span>|
|<span data-ttu-id="c88dd-128">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c88dd-128">ClrInstanceID</span></span>|<span data-ttu-id="c88dd-129">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="c88dd-129">win:UInt16</span></span>|<span data-ttu-id="c88dd-130">Jedinečné ID pro instanci CLR.</span><span class="sxs-lookup"><span data-stu-id="c88dd-130">Unique ID for the instance of CLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="c88dd-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="c88dd-131">See also</span></span>

- [<span data-ttu-id="c88dd-132">Události ETW CLR</span><span class="sxs-lookup"><span data-stu-id="c88dd-132">CLR ETW Events</span></span>](clr-etw-events.md)
