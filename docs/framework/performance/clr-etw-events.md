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
ms.openlocfilehash: 6798a83973f94f07a2a215d5208aa55f0f9ae929
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046746"
---
# <a name="clr-etw-events"></a><span data-ttu-id="3b574-102">Události ETW CLR</span><span class="sxs-lookup"><span data-stu-id="3b574-102">CLR ETW Events</span></span>
<span data-ttu-id="3b574-103">Témata v této části popisují události trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="3b574-103">The topics in this section describe event tracing for Windows (ETW) events.</span></span> <span data-ttu-id="3b574-104">Každá událost má přidružené klíčové slovo a úroveň, které jsou popsány v tématu [klíčová slova ETW a úrovně CLR](clr-etw-keywords-and-levels.md) .</span><span class="sxs-lookup"><span data-stu-id="3b574-104">Each event has an associated keyword and level, which are described in the [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md) topic.</span></span> <span data-ttu-id="3b574-105">CLR má dva poskytovatele pro události:</span><span class="sxs-lookup"><span data-stu-id="3b574-105">The CLR has two providers for the events:</span></span>  
  
- <span data-ttu-id="3b574-106">Zprostředkovatel modulu runtime, který vyvolává události v závislosti na tom, která klíčová slova (kategorie událostí) jsou povolena.</span><span class="sxs-lookup"><span data-stu-id="3b574-106">The runtime provider, which raises events depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="3b574-107">Identifikátor GUID zprostředkovatele modulu runtime CLR je e13c0d23-CCBC-4e12-931B-d9cc2eee27e4.</span><span class="sxs-lookup"><span data-stu-id="3b574-107">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
- <span data-ttu-id="3b574-108">Poskytovatel doběhu, který má použití pro zvláštní účely.</span><span class="sxs-lookup"><span data-stu-id="3b574-108">The rundown provider, which has special-purpose uses.</span></span> <span data-ttu-id="3b574-109">Identifikátor GUID zprostředkovatele doběhu CLR je A669021C-C450-4609-A035-5AF59AF4DF18.</span><span class="sxs-lookup"><span data-stu-id="3b574-109">The CLR rundown provider GUID is a669021c-c450-4609-a035-5af59af4df18.</span></span>  
  
 <span data-ttu-id="3b574-110">Další informace o poskytovatelích najdete v tématu [Zprostředkovatelé CLR ETW](clr-etw-providers.md).</span><span class="sxs-lookup"><span data-stu-id="3b574-110">For more information about the providers, see [CLR ETW Providers](clr-etw-providers.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3b574-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="3b574-111">In This Section</span></span>  
 [<span data-ttu-id="3b574-112">Události běhových informací</span><span class="sxs-lookup"><span data-stu-id="3b574-112">Runtime Information Events</span></span>](runtime-information-etw-events.md)  
 <span data-ttu-id="3b574-113">Zachycuje informace o modulu runtime, včetně SKU, čísla verze, způsobu, jakým byl aktivován modul runtime, parametry příkazového řádku, se kterými bylo spuštěno, identifikátor GUID (je-li k dispozici) a další relevantní informace.</span><span class="sxs-lookup"><span data-stu-id="3b574-113">Captures information about the runtime, including the SKU, version number, the manner in which the runtime was activated, the command-line parameters it was started with, the GUID (if applicable), and other relevant information.</span></span>  
  
 [<span data-ttu-id="3b574-114">Událost výjimky Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="3b574-114">Exception Thrown_V1 Event</span></span>](exception-thrown-v1-etw-event.md)  
 <span data-ttu-id="3b574-115">Zachycuje informace o vyvolaných výjimkách.</span><span class="sxs-lookup"><span data-stu-id="3b574-115">Captures information about exceptions that are thrown.</span></span>  
  
 [<span data-ttu-id="3b574-116">Kolizní události</span><span class="sxs-lookup"><span data-stu-id="3b574-116">Contention Events</span></span>](contention-etw-events.md)  
 <span data-ttu-id="3b574-117">Zachycuje informace o sporu pro zámky monitoru nebo nativní zámky, které používá modul runtime.</span><span class="sxs-lookup"><span data-stu-id="3b574-117">Captures information about contention for monitor locks or native locks that the runtime uses.</span></span>  
  
 [<span data-ttu-id="3b574-118">Události fondu vláken</span><span class="sxs-lookup"><span data-stu-id="3b574-118">Thread Pool Events</span></span>](thread-pool-etw-events.md)  
 <span data-ttu-id="3b574-119">Zachycuje informace o fondech pracovních vláken a fondech vláken v/v.</span><span class="sxs-lookup"><span data-stu-id="3b574-119">Captures information about worker thread pools and I/O thread pools.</span></span>  
  
 [<span data-ttu-id="3b574-120">Události zavaděče</span><span class="sxs-lookup"><span data-stu-id="3b574-120">Loader Events</span></span>](loader-etw-events.md)  
 <span data-ttu-id="3b574-121">Zachycuje informace o načítání a uvolňování aplikačních domén, sestavení a modulů.</span><span class="sxs-lookup"><span data-stu-id="3b574-121">Captures information about loading and unloading application domains, assemblies, and modules.</span></span>  
  
 [<span data-ttu-id="3b574-122">Události metod</span><span class="sxs-lookup"><span data-stu-id="3b574-122">Method Events</span></span>](method-etw-events.md)  
 <span data-ttu-id="3b574-123">Zachycuje informace o metodách CLR pro rozlišení symbolů.</span><span class="sxs-lookup"><span data-stu-id="3b574-123">Captures information about CLR methods for symbol resolution.</span></span>  
  
 [<span data-ttu-id="3b574-124">Události kolekce paměti</span><span class="sxs-lookup"><span data-stu-id="3b574-124">Garbage Collection Events</span></span>](garbage-collection-etw-events.md)  
 <span data-ttu-id="3b574-125">Zachycuje informace týkající se uvolňování paměti, které vám pomůžou diagnostikovat a ladit.</span><span class="sxs-lookup"><span data-stu-id="3b574-125">Captures information pertaining to garbage collection, to help in diagnostics and debugging.</span></span>  
  
 [<span data-ttu-id="3b574-126">JIT – události trasování (CLR)</span><span class="sxs-lookup"><span data-stu-id="3b574-126">JIT Tracing Events</span></span>](jit-tracing-etw-events.md)  
 <span data-ttu-id="3b574-127">Zachycuje informace o vkládání za běhu a volání funkce tail.</span><span class="sxs-lookup"><span data-stu-id="3b574-127">Captures information about just-in-time (JIT) inlining and tail calls.</span></span>  
  
 [<span data-ttu-id="3b574-128">Události interoperability</span><span class="sxs-lookup"><span data-stu-id="3b574-128">Interop Events</span></span>](interop-etw-events.md)  
 <span data-ttu-id="3b574-129">Zachycuje informace o generování a ukládání zástupných procedur v jazyce MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="3b574-129">Captures information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 [<span data-ttu-id="3b574-130">Události ARM</span><span class="sxs-lookup"><span data-stu-id="3b574-130">ARM Events</span></span>](application-domain-resource-monitoring-arm-etw-events.md)  
 <span data-ttu-id="3b574-131">Zachycuje podrobné diagnostické informace o stavu domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="3b574-131">Captures detailed diagnostic information about the state of an application domain.</span></span>  
  
 [<span data-ttu-id="3b574-132">Události zabezpečení</span><span class="sxs-lookup"><span data-stu-id="3b574-132">Security Events</span></span>](security-etw-events.md)  
 <span data-ttu-id="3b574-133">Zachycuje informace o silném názvu a ověřování Authenticode.</span><span class="sxs-lookup"><span data-stu-id="3b574-133">Captures information about strong name and Authenticode verification.</span></span>  
  
 [<span data-ttu-id="3b574-134">Událost zásobníku</span><span class="sxs-lookup"><span data-stu-id="3b574-134">Stack Event</span></span>](stack-etw-event.md)  
 <span data-ttu-id="3b574-135">Zachycuje informace, které se používají s jinými událostmi k vygenerování trasování zásobníku po vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="3b574-135">Captures information that is used with other events to generate stack traces after an event is raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b574-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3b574-136">See also</span></span>

- [<span data-ttu-id="3b574-137">Vylepšení ladění a optimalizace výkonu pomocí ETW</span><span class="sxs-lookup"><span data-stu-id="3b574-137">Improve Debugging And Performance Tuning With ETW</span></span>](https://go.microsoft.com/fwlink/?LinkId=179696)
- [<span data-ttu-id="3b574-138">Blog o výkonu Windows</span><span class="sxs-lookup"><span data-stu-id="3b574-138">Windows Performance Blog</span></span>](https://go.microsoft.com/fwlink/?LinkId=179509)
- [<span data-ttu-id="3b574-139">Řízení přihlašování rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3b574-139">Controlling .NET Framework Logging</span></span>](controlling-logging.md)
- [<span data-ttu-id="3b574-140">Poskytovatelé Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="3b574-140">CLR ETW Providers</span></span>](clr-etw-providers.md)
- [<span data-ttu-id="3b574-141">Klíčová slova a úrovně Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="3b574-141">CLR ETW Keywords and Levels</span></span>](clr-etw-keywords-and-levels.md)
- [<span data-ttu-id="3b574-142">Události Trasování událostí pro Windows v CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="3b574-142">ETW Events in the Common Language Runtime</span></span>](etw-events-in-the-common-language-runtime.md)
