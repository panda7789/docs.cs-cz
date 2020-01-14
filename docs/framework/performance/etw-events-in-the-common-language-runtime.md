---
title: Události Trasování událostí pro Windows v CLR (Common Language Runtime)
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: 5bb9b6a2-7b57-4aea-8809-32b28bc73e88
ms.openlocfilehash: 49d1141540fb00ab7ef462da5af84f02e6d9fc4d
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937860"
---
# <a name="etw-events-in-the-common-language-runtime"></a><span data-ttu-id="2e49c-102">Události Trasování událostí pro Windows v CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="2e49c-102">ETW Events in the Common Language Runtime</span></span>
<span data-ttu-id="2e49c-103">Modul CLR (Common Language Runtime) poskytuje užitečné funkce trasování událostí pro Windows (ETW) prostřednictvím velkého množství událostí ladění a profilování.</span><span class="sxs-lookup"><span data-stu-id="2e49c-103">The common language runtime (CLR) provides useful event tracing for Windows (ETW) diagnostic information through a large variety of debugging and profiling events.</span></span> <span data-ttu-id="2e49c-104">Události modulu CLR ETW využívají systém trasování ETW systému Windows k rozšíření stávající podpory profilace a ladění poskytované modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="2e49c-104">CLR ETW events leverage the Windows ETW tracing system to augment the existing profiling and debugging support provided by the common language runtime.</span></span>  
  
 <span data-ttu-id="2e49c-105">Další informace o ETW jsou k dispozici v článku [vylepšení ladění a optimalizace výkonu pomocí trasování událostí pro Windows](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw) .</span><span class="sxs-lookup"><span data-stu-id="2e49c-105">More information about ETW is available in the [Improve Debugging and Performance Tuning with ETW](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw) article.</span></span> <span data-ttu-id="2e49c-106">Informace o Xperf najdete v položce [Sada Windows Performance Toolkit – Xperf](https://docs.microsoft.com/archive/blogs/ntdebugging/windows-performance-toolkit-xperf) na blogu NTDebugging.</span><span class="sxs-lookup"><span data-stu-id="2e49c-106">Information about Xperf can be found in the entry [Windows Performance Toolkit - Xperf](https://docs.microsoft.com/archive/blogs/ntdebugging/windows-performance-toolkit-xperf) in the NTDebugging blog.</span></span>  
  
 <span data-ttu-id="2e49c-107">Pro všechny události popsané v tématech událostí se vyžaduje .NET Framework 4 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="2e49c-107">The .NET Framework 4 or later is required for all the events described in the event topics.</span></span> <span data-ttu-id="2e49c-108">Minimální podporovaný klient je operační systém Windows Vista a minimální podporovaný Server je Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="2e49c-108">The Windows Vista operating system is the minimum supported client, and Windows Server 2008 is the minimum supported server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2e49c-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2e49c-109">In This Section</span></span>  
 [<span data-ttu-id="2e49c-110">Řízení přihlašování rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2e49c-110">Controlling .NET Framework Logging</span></span>](controlling-logging.md)  
 <span data-ttu-id="2e49c-111">Popisuje nástroje a příkazy pro zachytávání a zobrazení událostí ETW.</span><span class="sxs-lookup"><span data-stu-id="2e49c-111">Describes the tools and commands for capturing and viewing ETW events.</span></span>  
  
 [<span data-ttu-id="2e49c-112">Poskytovatelé Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="2e49c-112">CLR ETW Providers</span></span>](clr-etw-providers.md)  
 <span data-ttu-id="2e49c-113">Poskytuje informace o modulu runtime a poskytovatelích doběhu a o tom, jak je můžete použít pro shromažďování dat ETW.</span><span class="sxs-lookup"><span data-stu-id="2e49c-113">Provides information about the runtime and rundown providers, and how you can use them for ETW data collection.</span></span>  
  
 [<span data-ttu-id="2e49c-114">Klíčová slova a úrovně Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="2e49c-114">CLR ETW Keywords and Levels</span></span>](clr-etw-keywords-and-levels.md)  
 <span data-ttu-id="2e49c-115">Popisuje klíčová slova pro poskytovatele běhového prostředí a doběhu, která umožňují filtrování událostí podle kategorie.</span><span class="sxs-lookup"><span data-stu-id="2e49c-115">Describes the keywords for the Runtime and Rundown providers that enable the filtering of events by category.</span></span>  
  
 [<span data-ttu-id="2e49c-116">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="2e49c-116">CLR ETW Events</span></span>](clr-etw-events.md)  
 <span data-ttu-id="2e49c-117">Poskytuje podrobné informace o událostech technologie CLR ETW, jejich klíčových slovech, úrovních a datech událostí.</span><span class="sxs-lookup"><span data-stu-id="2e49c-117">Provides detailed information about CLR ETW events, their keywords, levels, and event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e49c-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e49c-118">See also</span></span>

- [<span data-ttu-id="2e49c-119">Trasování událostí pro Windows – události v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2e49c-119">ETW Events in the .NET Framework</span></span>](etw-events.md)
