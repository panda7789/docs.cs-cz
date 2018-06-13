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
ms.openlocfilehash: d7d1f7ba1a0384ed93932733f12aa3306e16b790
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393916"
---
# <a name="clr-etw-events"></a><span data-ttu-id="1985a-102">Události ETW CLR</span><span class="sxs-lookup"><span data-stu-id="1985a-102">CLR ETW Events</span></span>
<span data-ttu-id="1985a-103">Témata v této části popisují trasování událostí pro události systému Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="1985a-103">The topics in this section describe event tracing for Windows (ETW) events.</span></span> <span data-ttu-id="1985a-104">Každá událost má přidružené klíčového slova a úrovně, které jsou popsány v [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="1985a-104">Each event has an associated keyword and level, which are described in the [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md) topic.</span></span> <span data-ttu-id="1985a-105">Modul CLR má dva poskytovatelé pro události:</span><span class="sxs-lookup"><span data-stu-id="1985a-105">The CLR has two providers for the events:</span></span>  
  
-   <span data-ttu-id="1985a-106">Poskytovatel modulu runtime, který vyvolává události v závislosti na tom, které jsou povolené klíčová slova (kategorie událostí).</span><span class="sxs-lookup"><span data-stu-id="1985a-106">The runtime provider, which raises events depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="1985a-107">Poskytovatel modulu runtime CLR GUID je e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span><span class="sxs-lookup"><span data-stu-id="1985a-107">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
-   <span data-ttu-id="1985a-108">Sekvence daneho poskytovatele, který má speciální používá.</span><span class="sxs-lookup"><span data-stu-id="1985a-108">The rundown provider, which has special-purpose uses.</span></span> <span data-ttu-id="1985a-109">Sekvence daneho zprostředkovatel CLR GUID je a669021c-c450-4609-a035-5af59af4df18.</span><span class="sxs-lookup"><span data-stu-id="1985a-109">The CLR rundown provider GUID is a669021c-c450-4609-a035-5af59af4df18.</span></span>  
  
 <span data-ttu-id="1985a-110">Další informace o poskytovateli najdete v tématu [CLR ETW – zprostředkovatelé](../../../docs/framework/performance/clr-etw-providers.md).</span><span class="sxs-lookup"><span data-stu-id="1985a-110">For more information about the providers, see [CLR ETW Providers](../../../docs/framework/performance/clr-etw-providers.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1985a-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1985a-111">In This Section</span></span>  
 [<span data-ttu-id="1985a-112">Události běhových informací</span><span class="sxs-lookup"><span data-stu-id="1985a-112">Runtime Information Events</span></span>](../../../docs/framework/performance/runtime-information-etw-events.md)  
 <span data-ttu-id="1985a-113">Zaznamená informace o modulu runtime, SKU, číslo verze, způsobem, ve kterém byla aktivovaná modul runtime, včetně parametrů příkazového řádku, který byl spuštěn s, identifikátor GUID (pokud existuje) a další relevantní informace.</span><span class="sxs-lookup"><span data-stu-id="1985a-113">Captures information about the runtime, including the SKU, version number, the manner in which the runtime was activated, the command-line parameters it was started with, the GUID (if applicable), and other relevant information.</span></span>  
  
 [<span data-ttu-id="1985a-114">Událost výjimky Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="1985a-114">Exception Thrown_V1 Event</span></span>](../../../docs/framework/performance/exception-thrown-v1-etw-event.md)  
 <span data-ttu-id="1985a-115">Zaznamená informace o výjimkách, které jsou vydány.</span><span class="sxs-lookup"><span data-stu-id="1985a-115">Captures information about exceptions that are thrown.</span></span>  
  
 [<span data-ttu-id="1985a-116">Kolizní události</span><span class="sxs-lookup"><span data-stu-id="1985a-116">Contention Events</span></span>](../../../docs/framework/performance/contention-etw-events.md)  
 <span data-ttu-id="1985a-117">Zaznamená informace o kolizí pro monitorování zámky nebo nativní zámky, které používá modul runtime.</span><span class="sxs-lookup"><span data-stu-id="1985a-117">Captures information about contention for monitor locks or native locks that the runtime uses.</span></span>  
  
 [<span data-ttu-id="1985a-118">Události fondu vláken</span><span class="sxs-lookup"><span data-stu-id="1985a-118">Thread Pool Events</span></span>](../../../docs/framework/performance/thread-pool-etw-events.md)  
 <span data-ttu-id="1985a-119">Zaznamená informace o přístup z více vláken fondy pracovních procesů a fondy vláken vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="1985a-119">Captures information about worker thread pools and I/O thread pools.</span></span>  
  
 [<span data-ttu-id="1985a-120">Události zavaděče</span><span class="sxs-lookup"><span data-stu-id="1985a-120">Loader Events</span></span>](../../../docs/framework/performance/loader-etw-events.md)  
 <span data-ttu-id="1985a-121">Zaznamená informace o načítání a uvolnění domény aplikace, sestavení a moduly.</span><span class="sxs-lookup"><span data-stu-id="1985a-121">Captures information about loading and unloading application domains, assemblies, and modules.</span></span>  
  
 [<span data-ttu-id="1985a-122">Události metod</span><span class="sxs-lookup"><span data-stu-id="1985a-122">Method Events</span></span>](../../../docs/framework/performance/method-etw-events.md)  
 <span data-ttu-id="1985a-123">Zaznamená informace o metodách CLR pro překlad symbol.</span><span class="sxs-lookup"><span data-stu-id="1985a-123">Captures information about CLR methods for symbol resolution.</span></span>  
  
 [<span data-ttu-id="1985a-124">Události kolekce paměti</span><span class="sxs-lookup"><span data-stu-id="1985a-124">Garbage Collection Events</span></span>](../../../docs/framework/performance/garbage-collection-etw-events.md)  
 <span data-ttu-id="1985a-125">Zaznamená informace týkající se uvolňování paměti, která vám pomůžou ladění a Diagnostika.</span><span class="sxs-lookup"><span data-stu-id="1985a-125">Captures information pertaining to garbage collection, to help in diagnostics and debugging.</span></span>  
  
 [<span data-ttu-id="1985a-126">JIT – události trasování (CLR)</span><span class="sxs-lookup"><span data-stu-id="1985a-126">JIT Tracing Events</span></span>](../../../docs/framework/performance/jit-tracing-etw-events.md)  
 <span data-ttu-id="1985a-127">Zaznamená informace o právě za běhu (JIT) vložené a volání tail.</span><span class="sxs-lookup"><span data-stu-id="1985a-127">Captures information about just-in-time (JIT) inlining and tail calls.</span></span>  
  
 [<span data-ttu-id="1985a-128">Události interoperability</span><span class="sxs-lookup"><span data-stu-id="1985a-128">Interop Events</span></span>](../../../docs/framework/performance/interop-etw-events.md)  
 <span data-ttu-id="1985a-129">Zaznamená informace o Microsoft (MSIL intermediate language) se zakázaným inzerováním generování a ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="1985a-129">Captures information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 [<span data-ttu-id="1985a-130">Události ARM</span><span class="sxs-lookup"><span data-stu-id="1985a-130">ARM Events</span></span>](../../../docs/framework/performance/application-domain-resource-monitoring-arm-etw-events.md)  
 <span data-ttu-id="1985a-131">Zachycení podrobné diagnostické informace týkající se stavu služby domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="1985a-131">Captures detailed diagnostic information about the state of an application domain.</span></span>  
  
 [<span data-ttu-id="1985a-132">Události zabezpečení</span><span class="sxs-lookup"><span data-stu-id="1985a-132">Security Events</span></span>](../../../docs/framework/performance/security-etw-events.md)  
 <span data-ttu-id="1985a-133">Zaznamená informace o silným názvem a ověření Authenticode.</span><span class="sxs-lookup"><span data-stu-id="1985a-133">Captures information about strong name and Authenticode verification.</span></span>  
  
 [<span data-ttu-id="1985a-134">Událost zásobníku</span><span class="sxs-lookup"><span data-stu-id="1985a-134">Stack Event</span></span>](../../../docs/framework/performance/stack-etw-event.md)  
 <span data-ttu-id="1985a-135">Zaznamená informace, které se používá s jinými událostmi ke generování trasování zásobníku po je aktivována událost.</span><span class="sxs-lookup"><span data-stu-id="1985a-135">Captures information that is used with other events to generate stack traces after an event is raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1985a-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="1985a-136">See Also</span></span>  
 [<span data-ttu-id="1985a-137">Vylepšení ladění a optimalizace výkonu pomocí trasování událostí pro Windows</span><span class="sxs-lookup"><span data-stu-id="1985a-137">Improve Debugging And Performance Tuning With ETW</span></span>](http://go.microsoft.com/fwlink/?LinkId=179696)  
 [<span data-ttu-id="1985a-138">Blog výkonu Windows</span><span class="sxs-lookup"><span data-stu-id="1985a-138">Windows Performance Blog</span></span>](http://go.microsoft.com/fwlink/?LinkId=179509)  
 [<span data-ttu-id="1985a-139">Řízení přihlašování rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1985a-139">Controlling .NET Framework Logging</span></span>](../../../docs/framework/performance/controlling-logging.md)  
 [<span data-ttu-id="1985a-140">Poskytovatelé Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="1985a-140">CLR ETW Providers</span></span>](../../../docs/framework/performance/clr-etw-providers.md)  
 [<span data-ttu-id="1985a-141">Klíčová slova a úrovně Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="1985a-141">CLR ETW Keywords and Levels</span></span>](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)  
 [<span data-ttu-id="1985a-142">Události Trasování událostí pro Windows v CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="1985a-142">ETW Events in the Common Language Runtime</span></span>](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
