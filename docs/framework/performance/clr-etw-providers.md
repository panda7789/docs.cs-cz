---
title: Poskytovatelé CLR ETW
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 639ebe1552fd3950bd77acd7b5730b0d3bdb150f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59302618"
---
# <a name="clr-etw-providers"></a><span data-ttu-id="03a7e-102">Poskytovatelé CLR ETW</span><span class="sxs-lookup"><span data-stu-id="03a7e-102">CLR ETW Providers</span></span>
<span data-ttu-id="03a7e-103">Modul CLR (CLR) má dva zprostředkovatele: zprostředkovatele běhového prostředí a zprostředkovatele doběhu.</span><span class="sxs-lookup"><span data-stu-id="03a7e-103">The common language runtime (CLR) has two providers: the runtime provider and the rundown provider.</span></span>  
  
 <span data-ttu-id="03a7e-104">Zprostředkovatel modulu runtime vyvolává události, v závislosti na tom, které jsou povolené klíčová slova (kategorie události).</span><span class="sxs-lookup"><span data-stu-id="03a7e-104">The runtime provider raises events, depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="03a7e-105">Například můžete shromažďovat události načítání povolením `LoaderKeyword` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="03a7e-105">For example, you can collect loader events by enabling the `LoaderKeyword` keyword.</span></span>  
  
 <span data-ttu-id="03a7e-106">Událost sledování pro Windows (ETW) jsou zaznamenány do souboru s příponou ETL, který lze později zpracovat do souborů hodnot oddělených čárkami (CSV), podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="03a7e-106">Event tracking for Windows (ETW) events are logged into a file that has an .etl extension, which can later be post-processed in comma-separated value (.csv) files as needed.</span></span> <span data-ttu-id="03a7e-107">Informace o převodu souborů ETL do souboru CSV najdete v tématu [řízení protokolování rozhraní .NET Framework](../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="03a7e-107">For information about how to convert the .etl file to a .csv file, see [Controlling .NET Framework Logging](../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
## <a name="the-runtime-provider"></a><span data-ttu-id="03a7e-108">Zprostředkovatel běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="03a7e-108">The Runtime Provider</span></span>  
 <span data-ttu-id="03a7e-109">Zprostředkovatel běhového prostředí je hlavním zprostředkovatelem modulu CLR ETW.</span><span class="sxs-lookup"><span data-stu-id="03a7e-109">The runtime provider is the main CLR ETW provider.</span></span>  
  
 <span data-ttu-id="03a7e-110">Identifikátor GUID zprostředkovatele CLR runtime je e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span><span class="sxs-lookup"><span data-stu-id="03a7e-110">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
 <span data-ttu-id="03a7e-111">Příklady protokolování a zobrazení událostí CLR ETW pomocí běžných nástrojů, naleznete v tématu [řízení protokolování rozhraní .NET Framework](../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="03a7e-111">For examples of how to log and view CLR ETW events by using commonly available tools, see [Controlling .NET Framework Logging](../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
 <span data-ttu-id="03a7e-112">Kromě použití klíčových slov, jako `LoaderKeyword`, možná budete muset povolit klíčová slova pro protokolování událostí, které mohou být vyvolány příliš často.</span><span class="sxs-lookup"><span data-stu-id="03a7e-112">In addition to using keywords such as `LoaderKeyword`, you may have to enable keywords for logging events that may be raised too frequently.</span></span> <span data-ttu-id="03a7e-113">`StartEnumerationKeyword` a `EndEnumerationKeyword` klíčová slova povolují tyto události a jsou shrnuta v [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="03a7e-113">The `StartEnumerationKeyword` and the `EndEnumerationKeyword` keywords enable these events and are summarized in [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).</span></span>  
  
## <a name="the-rundown-provider"></a><span data-ttu-id="03a7e-114">Zprostředkovatel doběhu</span><span class="sxs-lookup"><span data-stu-id="03a7e-114">The Rundown Provider</span></span>  
 <span data-ttu-id="03a7e-115">Zprostředkovatel doběhu musí být zapnuta pro některé zvláštní účely použití.</span><span class="sxs-lookup"><span data-stu-id="03a7e-115">The rundown provider must be turned on for certain special-purpose uses.</span></span> <span data-ttu-id="03a7e-116">Pro většinu uživatelů však měl postačit zprostředkovatel běhového prostředí.</span><span class="sxs-lookup"><span data-stu-id="03a7e-116">However, for a majority of users, the runtime provider should suffice.</span></span>  
  
 <span data-ttu-id="03a7e-117">Identifikátor GUID zprostředkovatele doběhu modulu CLR je A669021C-C450-4609-A035-5AF59AF4DF18.</span><span class="sxs-lookup"><span data-stu-id="03a7e-117">The CLR rundown provider GUID is A669021C-C450-4609-A035-5AF59AF4DF18.</span></span>  
  
 <span data-ttu-id="03a7e-118">Za normálních okolností je protokolování ETW povoleno před spustí proces a po ukončení procesu, je protokolování vypnuté.</span><span class="sxs-lookup"><span data-stu-id="03a7e-118">Normally, ETW logging is enabled before a process launches, and the logging is turned off after the process exits.</span></span> <span data-ttu-id="03a7e-119">Nicméně pokud protokolování trasování událostí pro Windows je zapnuto při provádění procesu, je potřeba další informace o procesu.</span><span class="sxs-lookup"><span data-stu-id="03a7e-119">However, if ETW logging is turned on while the process is executing, additional information is needed about the process.</span></span> <span data-ttu-id="03a7e-120">Například pro rozlišení symbolů máte zaznamenat události metod pro metody, které již byly zavedeny před zapnutím protokolování.</span><span class="sxs-lookup"><span data-stu-id="03a7e-120">For example, for symbol resolution you have to log method events for methods that were already loaded before logging was turned on.</span></span>  
  
 <span data-ttu-id="03a7e-121">`DCStart` a `DCEnd` události zachycují stav procesu při shromažďování dat bylo spuštění a zastavení.</span><span class="sxs-lookup"><span data-stu-id="03a7e-121">The `DCStart` and `DCEnd` events capture the state of the process when data collection was started and stopped.</span></span> <span data-ttu-id="03a7e-122">(Stav odkazuje na informace na vysoké úrovni, včetně metod, které již byly just-in-time (JIT) zkompilována a sestavení, která byla načtena.) Tyto dvě události mohou poskytnout informace o co se stalo již v procesu. například které metody byly zkompilovány JIT, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="03a7e-122">(State refers to information at a high level, including the methods that were already just-in-time (JIT) compiled and assemblies that were loaded.) These two events can provide information about what has already happened in the process; for example, which methods were JIT- compiled, and so on.</span></span>  
  
 <span data-ttu-id="03a7e-123">Pouze události, jejichž `DC`, `DCStart`, `DCEnd`, nebo `DCInit` v názvu jsou vyvolány skrze zprostředkovatele doběhu.</span><span class="sxs-lookup"><span data-stu-id="03a7e-123">Only the events with `DC`, `DCStart`, `DCEnd`, or `DCInit` in their names are raised under the rundown provider.</span></span> <span data-ttu-id="03a7e-124">Kromě toho tyto události jsou vyvolány pouze skrze zprostředkovatele doběhu.</span><span class="sxs-lookup"><span data-stu-id="03a7e-124">Additionally, these events are raised only under the rundown provider.</span></span>  
  
 <span data-ttu-id="03a7e-125">Kromě filtrů klíčových slov událostí zprostředkovatele doběhu také podporuje `StartRundownKeyword` a `EndRundownKeyword` klíčová slova k poskytování cílení filtrování.</span><span class="sxs-lookup"><span data-stu-id="03a7e-125">In addition to the event keyword filters, the rundown provider also supports the `StartRundownKeyword` and `EndRundownKeyword` keywords to provide targeted filtering.</span></span>  
  
### <a name="start-rundown"></a><span data-ttu-id="03a7e-126">Začátek doběhu</span><span class="sxs-lookup"><span data-stu-id="03a7e-126">Start Rundown</span></span>  
 <span data-ttu-id="03a7e-127">Začátek doběhu je vyvolán, pokud je povoleno protokolování zprostředkovatele doběhu pomocí `StartRundownKeyword` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="03a7e-127">A start rundown is triggered when logging under the rundown provider is enabled with the `StartRundownKeyword` keyword.</span></span> <span data-ttu-id="03a7e-128">To způsobí, že `DCStart` událost vyvolána a zachycen stav systému.</span><span class="sxs-lookup"><span data-stu-id="03a7e-128">This causes the `DCStart` event to be raised, and captures the state of the system.</span></span> <span data-ttu-id="03a7e-129">Před zahájením výčtu `DCStartInit` událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="03a7e-129">Before the start of the enumeration, the `DCStartInit` event is raised.</span></span> <span data-ttu-id="03a7e-130">Na konci výčtu `DCStartComplete` událost je vyvolávána s cílem upozornit kontroler, který sběr dat byl korektně ukončen.</span><span class="sxs-lookup"><span data-stu-id="03a7e-130">At the end of the enumeration, the `DCStartComplete` event is raised to notify the controller that data collection terminated normally.</span></span>  
  
### <a name="end-rundown"></a><span data-ttu-id="03a7e-131">Konec doběhu</span><span class="sxs-lookup"><span data-stu-id="03a7e-131">End Rundown</span></span>  
 <span data-ttu-id="03a7e-132">Konec doběhu se aktivuje, když je povoleno protokolování zprostředkovatele doběhu pomocí `EndRundownKeyword` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="03a7e-132">An end rundown is triggered when logging under the rundown provider is enabled with the `EndRundownKeyword` keyword.</span></span> <span data-ttu-id="03a7e-133">Konec doběhu zastaví profilování procesu, který pokračuje v provádění.</span><span class="sxs-lookup"><span data-stu-id="03a7e-133">End rundown stops profiling on a process that continues to execute.</span></span> <span data-ttu-id="03a7e-134">`DCEnd` Události zachycují stav systému, když je profilování zastaveno.</span><span class="sxs-lookup"><span data-stu-id="03a7e-134">The `DCEnd` events capture the state of the system when profiling is stopped.</span></span>  
  
 <span data-ttu-id="03a7e-135">Před zahájením výčtu `DCEndInit` událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="03a7e-135">Before the start of the enumeration, the `DCEndInit` event is raised.</span></span> <span data-ttu-id="03a7e-136">Na konci výčtu `DCEndComplete` událost je vyvolávána s cílem upozornit, že sběr dat byl korektně ukončen.</span><span class="sxs-lookup"><span data-stu-id="03a7e-136">At the end of the enumeration, the `DCEndComplete` event is raised to notify the consumer that data collection terminated normally.</span></span> <span data-ttu-id="03a7e-137">Začátek doběhu a konec doběhu jsou primárně určené pro rozlišení spravovaných symbolů.</span><span class="sxs-lookup"><span data-stu-id="03a7e-137">Start rundown and end rundown are primarily used for managed symbol resolution.</span></span> <span data-ttu-id="03a7e-138">Začátek doběhu může poskytnout informace o metodách, které již byly zkompilovány JIT před spuštěním relace profilování se rozsahu adres.</span><span class="sxs-lookup"><span data-stu-id="03a7e-138">Start rundown can provide address range information for methods that were already JIT-compiled before the profiling session was started.</span></span> <span data-ttu-id="03a7e-139">Konec doběhu může poskytnout informace o rozsahu adres pro všechny metody, které byly zkompilovány JIT profilace se vypne.</span><span class="sxs-lookup"><span data-stu-id="03a7e-139">End rundown can provide address range information for all methods that have been JIT-compiled when profiling is about to be turned off.</span></span>  
  
 <span data-ttu-id="03a7e-140">Konec doběhu neprobíhá automaticky při zastavení relace profilování.</span><span class="sxs-lookup"><span data-stu-id="03a7e-140">End rundown does not happen automatically when a profiling session is stopped.</span></span> <span data-ttu-id="03a7e-141">Místo toho nástroj, který se snaží provést rozlišení spravovaných symbolů musí explicitně vyvolat relaci zprostředkovatele doběhu modulu CLR s `EndRundownKeyword` – klíčové slovo povolena, pouze předtím, než je profilování zastaveno.</span><span class="sxs-lookup"><span data-stu-id="03a7e-141">Instead, a tool that is seeking to perform managed symbol resolution has to explicitly invoke a CLR rundown provider session with the `EndRundownKeyword` keyword enabled, just before profiling is stopped.</span></span>  
  
 <span data-ttu-id="03a7e-142">Přestože začátek doběhu a konec doběhu může poskytnout informace o rozsahu adres metody pro rozlišení spravovaných symbolů, doporučujeme použít `EndRundownKeyword` – klíčové slovo (které poskytuje `DCEnd` události) místo `StartRundownKeyword` – klíčové slovo (který poskytuje `DCStart` události).</span><span class="sxs-lookup"><span data-stu-id="03a7e-142">Although either start rundown or end rundown can provide method address range information for managed symbol resolution, we recommend that you use the `EndRundownKeyword` keyword (which supplies `DCEnd` events) instead of the `StartRundownKeyword` keyword (which supplies `DCStart` events).</span></span> <span data-ttu-id="03a7e-143">Pomocí `StartRundownKeyword` způsobí spuštění doběhu během relace profilování, což může narušit profilovaný scénář.</span><span class="sxs-lookup"><span data-stu-id="03a7e-143">Using `StartRundownKeyword` causes the rundown to happen during the profiling session, which may disturb the profiled scenario.</span></span>  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a><span data-ttu-id="03a7e-144">Shromažďování dat trasování událostí pro Windows pomocí modulu Runtime a zprostředkovatele doběhu</span><span class="sxs-lookup"><span data-stu-id="03a7e-144">ETW Data Collection Using Runtime and Rundown Providers</span></span>  
 <span data-ttu-id="03a7e-145">Následující příklad ukazuje použití zprostředkovatele doběhu modulu CLR způsobem, který umožňuje rozlišení symbolů pro spravované procesy s minimálním dopadem, bez ohledu na to, zda procesy začínají nebo končí uvnitř nebo vně profilovacího okna.</span><span class="sxs-lookup"><span data-stu-id="03a7e-145">The following example demonstrates how to use the CLR rundown provider in a way that allows symbol resolution of managed processes with minimal impact, regardless of whether the processes start or end inside or outside the profiled window.</span></span>  
  
1. <span data-ttu-id="03a7e-146">Zapnutí protokolování událostí ETW pomocí zprostředkovatele modulu CLR runtime:</span><span class="sxs-lookup"><span data-stu-id="03a7e-146">Turn on ETW logging by using the CLR runtime provider:</span></span>  
  
    ```  
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl      
    ```  
  
     <span data-ttu-id="03a7e-147">Protokol bude uložen do souboru clr1.etl.</span><span class="sxs-lookup"><span data-stu-id="03a7e-147">The log will be saved to the clr1.etl file.</span></span>  
  
2. <span data-ttu-id="03a7e-148">K zastavení profilování, zatímco proces pokračuje v provádění, spustit zprostředkovatele doběhu zachycení `DCEnd` události:</span><span class="sxs-lookup"><span data-stu-id="03a7e-148">To stop profiling while the process continues to execute, start the rundown provider to capture the `DCEnd` events:</span></span>  
  
    ```  
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl      
    ```  
  
     <span data-ttu-id="03a7e-149">To umožňuje shromažďování `DCEnd` události spuštění relace doběhu.</span><span class="sxs-lookup"><span data-stu-id="03a7e-149">This enables the collection of `DCEnd` events to start a rundown session.</span></span> <span data-ttu-id="03a7e-150">Budete muset počkat 30 – 60 sekund pro všechny události, které se mají shromažďovat.</span><span class="sxs-lookup"><span data-stu-id="03a7e-150">You may need to wait 30 to 60 seconds for all events to be collected.</span></span> <span data-ttu-id="03a7e-151">Protokol bude uložen do souboru clr1.et2.</span><span class="sxs-lookup"><span data-stu-id="03a7e-151">The log will be saved to the clr1.et2 file.</span></span>  
  
3. <span data-ttu-id="03a7e-152">Vypnutí všech profilování ETW:</span><span class="sxs-lookup"><span data-stu-id="03a7e-152">Turn off all ETW profiling:</span></span>  
  
    ```  
    xperf -stop clrRundown   
    xperf -stop clr  
    ```  
  
4. <span data-ttu-id="03a7e-153">Je třeba sloučit profily pro vytvoření jednoho souboru protokolu:</span><span class="sxs-lookup"><span data-stu-id="03a7e-153">Merge the profiles to create one log file:</span></span>  
  
    ```  
    xperf -merge clr1.etl clr2.etl merged.etl  
    ```  
  
     <span data-ttu-id="03a7e-154">Soubor merged.etl bude obsahovat události z modulu runtime a relace skrze zprostředkovatele doběhu.</span><span class="sxs-lookup"><span data-stu-id="03a7e-154">The merged.etl file will contain the events from the runtime and the rundown provider sessions.</span></span>  
  
 <span data-ttu-id="03a7e-155">Nástroj může spustit kroky 2 a 3 (spuštění relace doběhu a potom ukončení profilování) místo okamžitého vypnutí profilování, když uživatel žádostí, aby bylo profilování zastaveno.</span><span class="sxs-lookup"><span data-stu-id="03a7e-155">A tool can execute steps 2 and 3 (starting a rundown session and then terminating profiling) instead of immediately turning off profiling when a user requests profiling to be stopped.</span></span> <span data-ttu-id="03a7e-156">Nástroj může také spustit krok 4.</span><span class="sxs-lookup"><span data-stu-id="03a7e-156">A tool can also execute step 4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03a7e-157">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03a7e-157">See also</span></span>

- [<span data-ttu-id="03a7e-158">Události Trasování událostí pro Windows v CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="03a7e-158">ETW Events in the Common Language Runtime</span></span>](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
