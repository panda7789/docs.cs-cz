---
title: Události ETW CLR
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 951941af2568e72fe093860801bd2595b3037e41
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428162"
---
# <a name="clr-etw-events"></a><span data-ttu-id="2c3c2-102">Události ETW CLR</span><span class="sxs-lookup"><span data-stu-id="2c3c2-102">CLR ETW Events</span></span>
<span data-ttu-id="2c3c2-103">The topics in this section describe event tracing for Windows (ETW) events.</span><span class="sxs-lookup"><span data-stu-id="2c3c2-103">The topics in this section describe event tracing for Windows (ETW) events.</span></span> <span data-ttu-id="2c3c2-104">Each event has an associated keyword and level, which are described in the [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md) topic.</span><span class="sxs-lookup"><span data-stu-id="2c3c2-104">Each event has an associated keyword and level, which are described in the [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md) topic.</span></span> <span data-ttu-id="2c3c2-105">The CLR has two providers for the events:</span><span class="sxs-lookup"><span data-stu-id="2c3c2-105">The CLR has two providers for the events:</span></span>  
  
- <span data-ttu-id="2c3c2-106">The runtime provider, which raises events depending on which keywords (categories of events) are enabled.</span><span class="sxs-lookup"><span data-stu-id="2c3c2-106">The runtime provider, which raises events depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="2c3c2-107">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span><span class="sxs-lookup"><span data-stu-id="2c3c2-107">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
- <span data-ttu-id="2c3c2-108">The rundown provider, which has special-purpose uses.</span><span class="sxs-lookup"><span data-stu-id="2c3c2-108">The rundown provider, which has special-purpose uses.</span></span> <span data-ttu-id="2c3c2-109">The CLR rundown provider GUID is a669021c-c450-4609-a035-5af59af4df18.</span><span class="sxs-lookup"><span data-stu-id="2c3c2-109">The CLR rundown provider GUID is a669021c-c450-4609-a035-5af59af4df18.</span></span>  
  
 <span data-ttu-id="2c3c2-110">For more information about the providers, see [CLR ETW Providers](clr-etw-providers.md).</span><span class="sxs-lookup"><span data-stu-id="2c3c2-110">For more information about the providers, see [CLR ETW Providers](clr-etw-providers.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2c3c2-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2c3c2-111">In This Section</span></span>  
 [<span data-ttu-id="2c3c2-112">Události běhových informací</span><span class="sxs-lookup"><span data-stu-id="2c3c2-112">Runtime Information Events</span></span>](runtime-information-etw-events.md)  
 <span data-ttu-id="2c3c2-113">Captures information about the runtime, including the SKU, version number, the manner in which the runtime was activated, the command-line parameters it was started with, the GUID (if applicable), and other relevant information.</span><span class="sxs-lookup"><span data-stu-id="2c3c2-113">Captures information about the runtime, including the SKU, version number, the manner in which the runtime was activated, the command-line parameters it was started with, the GUID (if applicable), and other relevant information.</span></span>  
  
 [<span data-ttu-id="2c3c2-114">Událost výjimky Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="2c3c2-114">Exception Thrown_V1 Event</span></span>](exception-thrown-v1-etw-event.md)  
 <span data-ttu-id="2c3c2-115">Captures information about exceptions that are thrown.</span><span class="sxs-lookup"><span data-stu-id="2c3c2-115">Captures information about exceptions that are thrown.</span></span>  
  
 [<span data-ttu-id="2c3c2-116">Kolizní události</span><span class="sxs-lookup"><span data-stu-id="2c3c2-116">Contention Events</span></span>](contention-etw-events.md)  
 <span data-ttu-id="2c3c2-117">Captures information about contention for monitor locks or native locks that the runtime uses.</span><span class="sxs-lookup"><span data-stu-id="2c3c2-117">Captures information about contention for monitor locks or native locks that the runtime uses.</span></span>  
  
 [<span data-ttu-id="2c3c2-118">Události fondu vláken</span><span class="sxs-lookup"><span data-stu-id="2c3c2-118">Thread Pool Events</span></span>](thread-pool-etw-events.md)  
 <span data-ttu-id="2c3c2-119">Captures information about worker thread pools and I/O thread pools.</span><span class="sxs-lookup"><span data-stu-id="2c3c2-119">Captures information about worker thread pools and I/O thread pools.</span></span>  
  
 [<span data-ttu-id="2c3c2-120">Události zavaděče</span><span class="sxs-lookup"><span data-stu-id="2c3c2-120">Loader Events</span></span>](loader-etw-events.md)  
 <span data-ttu-id="2c3c2-121">Captures information about loading and unloading application domains, assemblies, and modules.</span><span class="sxs-lookup"><span data-stu-id="2c3c2-121">Captures information about loading and unloading application domains, assemblies, and modules.</span></span>  
  
 [<span data-ttu-id="2c3c2-122">Události metod</span><span class="sxs-lookup"><span data-stu-id="2c3c2-122">Method Events</span></span>](method-etw-events.md)  
 <span data-ttu-id="2c3c2-123">Captures information about CLR methods for symbol resolution.</span><span class="sxs-lookup"><span data-stu-id="2c3c2-123">Captures information about CLR methods for symbol resolution.</span></span>  
  
 [<span data-ttu-id="2c3c2-124">Události kolekce paměti</span><span class="sxs-lookup"><span data-stu-id="2c3c2-124">Garbage Collection Events</span></span>](garbage-collection-etw-events.md)  
 <span data-ttu-id="2c3c2-125">Captures information pertaining to garbage collection, to help in diagnostics and debugging.</span><span class="sxs-lookup"><span data-stu-id="2c3c2-125">Captures information pertaining to garbage collection, to help in diagnostics and debugging.</span></span>  
  
 [<span data-ttu-id="2c3c2-126">JIT – události trasování (CLR)</span><span class="sxs-lookup"><span data-stu-id="2c3c2-126">JIT Tracing Events</span></span>](jit-tracing-etw-events.md)  
 <span data-ttu-id="2c3c2-127">Captures information about just-in-time (JIT) inlining and tail calls.</span><span class="sxs-lookup"><span data-stu-id="2c3c2-127">Captures information about just-in-time (JIT) inlining and tail calls.</span></span>  
  
 [<span data-ttu-id="2c3c2-128">Události interoperability</span><span class="sxs-lookup"><span data-stu-id="2c3c2-128">Interop Events</span></span>](interop-etw-events.md)  
 <span data-ttu-id="2c3c2-129">Captures information about Microsoft intermediate language (MSIL) stub generation and caching.</span><span class="sxs-lookup"><span data-stu-id="2c3c2-129">Captures information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 [<span data-ttu-id="2c3c2-130">Události ARM</span><span class="sxs-lookup"><span data-stu-id="2c3c2-130">ARM Events</span></span>](application-domain-resource-monitoring-arm-etw-events.md)  
 <span data-ttu-id="2c3c2-131">Captures detailed diagnostic information about the state of an application domain.</span><span class="sxs-lookup"><span data-stu-id="2c3c2-131">Captures detailed diagnostic information about the state of an application domain.</span></span>  
  
 [<span data-ttu-id="2c3c2-132">Události zabezpečení</span><span class="sxs-lookup"><span data-stu-id="2c3c2-132">Security Events</span></span>](security-etw-events.md)  
 <span data-ttu-id="2c3c2-133">Captures information about strong name and Authenticode verification.</span><span class="sxs-lookup"><span data-stu-id="2c3c2-133">Captures information about strong name and Authenticode verification.</span></span>  
  
 [<span data-ttu-id="2c3c2-134">Událost zásobníku</span><span class="sxs-lookup"><span data-stu-id="2c3c2-134">Stack Event</span></span>](stack-etw-event.md)  
 <span data-ttu-id="2c3c2-135">Captures information that is used with other events to generate stack traces after an event is raised.</span><span class="sxs-lookup"><span data-stu-id="2c3c2-135">Captures information that is used with other events to generate stack traces after an event is raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c3c2-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2c3c2-136">See also</span></span>

- [<span data-ttu-id="2c3c2-137">Improve Debugging And Performance Tuning With ETW</span><span class="sxs-lookup"><span data-stu-id="2c3c2-137">Improve Debugging And Performance Tuning With ETW</span></span>](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw)
- [<span data-ttu-id="2c3c2-138">Windows Performance Blog</span><span class="sxs-lookup"><span data-stu-id="2c3c2-138">Windows Performance Blog</span></span>](https://blogs.msdn.microsoft.com/pigscanfly/tag/xperf/)
- [<span data-ttu-id="2c3c2-139">Řízení přihlašování rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2c3c2-139">Controlling .NET Framework Logging</span></span>](controlling-logging.md)
- [<span data-ttu-id="2c3c2-140">Poskytovatelé Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="2c3c2-140">CLR ETW Providers</span></span>](clr-etw-providers.md)
- [<span data-ttu-id="2c3c2-141">Klíčová slova a úrovně Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="2c3c2-141">CLR ETW Keywords and Levels</span></span>](clr-etw-keywords-and-levels.md)
- [<span data-ttu-id="2c3c2-142">Události Trasování událostí pro Windows v CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="2c3c2-142">ETW Events in the Common Language Runtime</span></span>](etw-events-in-the-common-language-runtime.md)
