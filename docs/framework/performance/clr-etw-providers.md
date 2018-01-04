---
title: "Poskytovatelé CLR ETW"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b76b3a1d4969a5ed81e5fa90afb06050b780804
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="clr-etw-providers"></a><span data-ttu-id="74ce6-102">Poskytovatelé CLR ETW</span><span class="sxs-lookup"><span data-stu-id="74ce6-102">CLR ETW Providers</span></span>
<span data-ttu-id="74ce6-103">Modul CLR (CLR) má dva poskytovatelé: Zprostředkovatel runtime a sekvence daneho zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="74ce6-103">The common language runtime (CLR) has two providers: the runtime provider and the rundown provider.</span></span>  
  
 <span data-ttu-id="74ce6-104">Poskytovatel modulu runtime vyvolá událostí, v závislosti na tom, které jsou povolené klíčová slova (kategorie událostí).</span><span class="sxs-lookup"><span data-stu-id="74ce6-104">The runtime provider raises events, depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="74ce6-105">Například můžete shromažďovat události zavaděče povolení `LoaderKeyword` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="74ce6-105">For example, you can collect loader events by enabling the `LoaderKeyword` keyword.</span></span>  
  
 <span data-ttu-id="74ce6-106">Sledování události systému Windows (ETW) událostí se protokolují do souboru, který má příponu ETL, který lze později po zpracovat v souborech hodnot oddělených čárkami (.csv) podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="74ce6-106">Event tracking for Windows (ETW) events are logged into a file that has an .etl extension, which can later be post-processed in comma-separated value (.csv) files as needed.</span></span> <span data-ttu-id="74ce6-107">Informace o tom, jak převést soubor .etl do souboru CSV naleznete v tématu [řízení protokolování rozhraní .NET Framework](../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="74ce6-107">For information about how to convert the .etl file to a .csv file, see [Controlling .NET Framework Logging](../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
## <a name="the-runtime-provider"></a><span data-ttu-id="74ce6-108">Poskytovatel modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="74ce6-108">The Runtime Provider</span></span>  
 <span data-ttu-id="74ce6-109">Modul runtime se hlavní zprostředkovatel CLR ETW.</span><span class="sxs-lookup"><span data-stu-id="74ce6-109">The runtime provider is the main CLR ETW provider.</span></span>  
  
 <span data-ttu-id="74ce6-110">Poskytovatel modulu runtime CLR GUID je e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span><span class="sxs-lookup"><span data-stu-id="74ce6-110">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
 <span data-ttu-id="74ce6-111">Příklady, jak protokolování a zobrazení CLR ETW – události pomocí běžných nástrojů, najdete v části [řízení protokolování rozhraní .NET Framework](../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="74ce6-111">For examples of how to log and view CLR ETW events by using commonly available tools, see [Controlling .NET Framework Logging](../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
 <span data-ttu-id="74ce6-112">Kromě používání klíčová slova, jako `LoaderKeyword`, možná budete muset povolit klíčová slova pro protokolování událostí, které mohou být vyvolány příliš často.</span><span class="sxs-lookup"><span data-stu-id="74ce6-112">In addition to using keywords such as `LoaderKeyword`, you may have to enable keywords for logging events that may be raised too frequently.</span></span> <span data-ttu-id="74ce6-113">`StartEnumerationKeyword` a `EndEnumerationKeyword` klíčová slova povolit tyto události a jsou shrnuty v [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="74ce6-113">The `StartEnumerationKeyword` and the `EndEnumerationKeyword` keywords enable these events and are summarized in [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).</span></span>  
  
## <a name="the-rundown-provider"></a><span data-ttu-id="74ce6-114">Sekvence daneho zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="74ce6-114">The Rundown Provider</span></span>  
 <span data-ttu-id="74ce6-115">Sekvence daneho zprostředkovatele musí být zapnut pro určité speciální používá.</span><span class="sxs-lookup"><span data-stu-id="74ce6-115">The rundown provider must be turned on for certain special-purpose uses.</span></span> <span data-ttu-id="74ce6-116">Ale pro většinu uživatelů, měla by stačit runtime zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="74ce6-116">However, for a majority of users, the runtime provider should suffice.</span></span>  
  
 <span data-ttu-id="74ce6-117">Sekvence daneho zprostředkovatel CLR GUID je A669021C-C450-4609-A035-5AF59AF4DF18.</span><span class="sxs-lookup"><span data-stu-id="74ce6-117">The CLR rundown provider GUID is A669021C-C450-4609-A035-5AF59AF4DF18.</span></span>  
  
 <span data-ttu-id="74ce6-118">Za normálních okolností je povoleno protokolování trasování událostí pro Windows předtím, než spustí proces a po ukončení procesu, je protokolování vypnuté.</span><span class="sxs-lookup"><span data-stu-id="74ce6-118">Normally, ETW logging is enabled before a process launches, and the logging is turned off after the process exits.</span></span> <span data-ttu-id="74ce6-119">Ale pokud protokolování trasování událostí pro Windows zapnutý, při procesu provádí, je potřeba další informace o procesu.</span><span class="sxs-lookup"><span data-stu-id="74ce6-119">However, if ETW logging is turned on while the process is executing, additional information is needed about the process.</span></span> <span data-ttu-id="74ce6-120">Například pro překlad symbol máte protokolování událostí, metoda pro metody, které již byly načteny před protokolování zapnutý.</span><span class="sxs-lookup"><span data-stu-id="74ce6-120">For example, for symbol resolution you have to log method events for methods that were already loaded before logging was turned on.</span></span>  
  
 <span data-ttu-id="74ce6-121">`DCStart` a `DCEnd` události zaznamenat stav procesu, při shromažďování dat byl spuštění a zastavení.</span><span class="sxs-lookup"><span data-stu-id="74ce6-121">The `DCStart` and `DCEnd` events capture the state of the process when data collection was started and stopped.</span></span> <span data-ttu-id="74ce6-122">(Stav odkazuje na informace na vysoké úrovni, včetně metody, které již byly v běhu (JIT) zkompilovat a sestavení, které byly načteny.) Tyto dvě události může poskytnout informace o co bylo provedeno v procesu. například, které metody byly JIT-kompilovat, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="74ce6-122">(State refers to information at a high level, including the methods that were already just-in-time (JIT) compiled and assemblies that were loaded.) These two events can provide information about what has already happened in the process; for example, which methods were JIT- compiled, and so on.</span></span>  
  
 <span data-ttu-id="74ce6-123">Jenom události s `DC`, `DCStart`, `DCEnd`, nebo `DCInit` jejich názvy jsou vyvolány v rámci sekvence daneho zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="74ce6-123">Only the events with `DC`, `DCStart`, `DCEnd`, or `DCInit` in their names are raised under the rundown provider.</span></span> <span data-ttu-id="74ce6-124">Kromě toho tyto události jsou vyvolány pouze v rámci sekvence daneho zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="74ce6-124">Additionally, these events are raised only under the rundown provider.</span></span>  
  
 <span data-ttu-id="74ce6-125">Kromě události – klíčové slovo filtry, sekvence daneho zprostředkovatel také podporuje `StartRundownKeyword` a `EndRundownKeyword` klíčová slova zajistit cílové filtrování.</span><span class="sxs-lookup"><span data-stu-id="74ce6-125">In addition to the event keyword filters, the rundown provider also supports the `StartRundownKeyword` and `EndRundownKeyword` keywords to provide targeted filtering.</span></span>  
  
### <a name="start-rundown"></a><span data-ttu-id="74ce6-126">Spustit Rundown</span><span class="sxs-lookup"><span data-stu-id="74ce6-126">Start Rundown</span></span>  
 <span data-ttu-id="74ce6-127">Spuštění rundown se aktivuje, když je povoleno protokolování v rámci sekvence daneho zprostředkovatele s `StartRundownKeyword` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="74ce6-127">A start rundown is triggered when logging under the rundown provider is enabled with the `StartRundownKeyword` keyword.</span></span> <span data-ttu-id="74ce6-128">To způsobí, že `DCStart` událost, která má být vyvolána a zachytí stavu systému.</span><span class="sxs-lookup"><span data-stu-id="74ce6-128">This causes the `DCStart` event to be raised, and captures the state of the system.</span></span> <span data-ttu-id="74ce6-129">Před zahájením výčtu `DCStartInit` událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="74ce6-129">Before the start of the enumeration, the `DCStartInit` event is raised.</span></span> <span data-ttu-id="74ce6-130">Na konci výčtu `DCStartComplete` událost se vyvolá, upozornit na řadič, který shromažďování dat ukončeno normálně.</span><span class="sxs-lookup"><span data-stu-id="74ce6-130">At the end of the enumeration, the `DCStartComplete` event is raised to notify the controller that data collection terminated normally.</span></span>  
  
### <a name="end-rundown"></a><span data-ttu-id="74ce6-131">End Rundown</span><span class="sxs-lookup"><span data-stu-id="74ce6-131">End Rundown</span></span>  
 <span data-ttu-id="74ce6-132">Rundown end se aktivuje, když je povoleno protokolování v rámci sekvence daneho zprostředkovatele s `EndRundownKeyword` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="74ce6-132">An end rundown is triggered when logging under the rundown provider is enabled with the `EndRundownKeyword` keyword.</span></span> <span data-ttu-id="74ce6-133">Profilace v procesu, který bude pokračovat v provádění sekvence daneho zastaví end.</span><span class="sxs-lookup"><span data-stu-id="74ce6-133">End rundown stops profiling on a process that continues to execute.</span></span> <span data-ttu-id="74ce6-134">`DCEnd` Události zaznamenání stavu systému při vytváření profilu je zastavena.</span><span class="sxs-lookup"><span data-stu-id="74ce6-134">The `DCEnd` events capture the state of the system when profiling is stopped.</span></span>  
  
 <span data-ttu-id="74ce6-135">Před zahájením výčtu `DCEndInit` událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="74ce6-135">Before the start of the enumeration, the `DCEndInit` event is raised.</span></span> <span data-ttu-id="74ce6-136">Na konci výčtu `DCEndComplete` událost se vyvolá oznámit příjemce, který shromažďování dat ukončeno normálně.</span><span class="sxs-lookup"><span data-stu-id="74ce6-136">At the end of the enumeration, the `DCEndComplete` event is raised to notify the consumer that data collection terminated normally.</span></span> <span data-ttu-id="74ce6-137">Spuštění sekvence daneho a end rundown primárně pro spravované symbol řešení.</span><span class="sxs-lookup"><span data-stu-id="74ce6-137">Start rundown and end rundown are primarily used for managed symbol resolution.</span></span> <span data-ttu-id="74ce6-138">Spuštění rundown může poskytnout informace o rozsah adres pro metody, které již byly kompilována před relace profilování byla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="74ce6-138">Start rundown can provide address range information for methods that were already JIT-compiled before the profiling session was started.</span></span> <span data-ttu-id="74ce6-139">End rundown může poskytnout informace o rozsah adres pro všechny metody, které byly kompilována při profilace je přibližně po zapnutí vypnout.</span><span class="sxs-lookup"><span data-stu-id="74ce6-139">End rundown can provide address range information for all methods that have been JIT-compiled when profiling is about to be turned off.</span></span>  
  
 <span data-ttu-id="74ce6-140">Pokud je zastavená relace profilování end rundown neprobíhá automaticky.</span><span class="sxs-lookup"><span data-stu-id="74ce6-140">End rundown does not happen automatically when a profiling session is stopped.</span></span> <span data-ttu-id="74ce6-141">Místo toho nástroj, který se snaží provést řešení spravované symbol má explicitně vyvolat relaci CLR sekvence daneho zprostředkovatele s `EndRundownKeyword` – klíčové slovo povoleno, těsně před profilace je zastavena.</span><span class="sxs-lookup"><span data-stu-id="74ce6-141">Instead, a tool that is seeking to perform managed symbol resolution has to explicitly invoke a CLR rundown provider session with the `EndRundownKeyword` keyword enabled, just before profiling is stopped.</span></span>  
  
 <span data-ttu-id="74ce6-142">I když rundown počáteční nebo koncové rundown může poskytnout informace o rozsahu adres metoda pro spravované symbol řešení, doporučujeme použít `EndRundownKeyword` – klíčové slovo (které zdroje `DCEnd` události) místo `StartRundownKeyword` – klíčové slovo (který poskytuje `DCStart` událostí).</span><span class="sxs-lookup"><span data-stu-id="74ce6-142">Although either start rundown or end rundown can provide method address range information for managed symbol resolution, we recommend that you use the `EndRundownKeyword` keyword (which supplies `DCEnd` events) instead of the `StartRundownKeyword` keyword (which supplies `DCStart` events).</span></span> <span data-ttu-id="74ce6-143">Pomocí `StartRundownKeyword` způsobí, že rundown provést během relace profilování, které by mohly narušit PROFILOVANÉHO scénář.</span><span class="sxs-lookup"><span data-stu-id="74ce6-143">Using `StartRundownKeyword` causes the rundown to happen during the profiling session, which may disturb the profiled scenario.</span></span>  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a><span data-ttu-id="74ce6-144">Shromažďování dat trasování událostí pro Windows pomocí modulu Runtime a sekvence daneho zprostředkovatelé</span><span class="sxs-lookup"><span data-stu-id="74ce6-144">ETW Data Collection Using Runtime and Rundown Providers</span></span>  
 <span data-ttu-id="74ce6-145">Následující příklad ukazuje, jak použít poskytovatele sekvence daneho CLR způsobem, který umožňuje řešení symbol spravovaných procesů s minimálním dopadem, bez ohledu na to, zda procesy začínat nebo končit uvnitř nebo mimo okno PROFILOVANÉHO.</span><span class="sxs-lookup"><span data-stu-id="74ce6-145">The following example demonstrates how to use the CLR rundown provider in a way that allows symbol resolution of managed processes with minimal impact, regardless of whether the processes start or end inside or outside the profiled window.</span></span>  
  
1.  <span data-ttu-id="74ce6-146">Zapněte protokolování trasování událostí pro Windows pomocí zprostředkovatele runtime CLR:</span><span class="sxs-lookup"><span data-stu-id="74ce6-146">Turn on ETW logging by using the CLR runtime provider:</span></span>  
  
    ```  
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl      
    ```  
  
     <span data-ttu-id="74ce6-147">Protokol se uloží do souboru clr1.etl.</span><span class="sxs-lookup"><span data-stu-id="74ce6-147">The log will be saved to the clr1.etl file.</span></span>  
  
2.  <span data-ttu-id="74ce6-148">Zastavit profilování při proces bude pokračovat v provádění, spusťte sekvence daneho zprostředkovatele, který má zaznamenat `DCEnd` události:</span><span class="sxs-lookup"><span data-stu-id="74ce6-148">To stop profiling while the process continues to execute, start the rundown provider to capture the `DCEnd` events:</span></span>  
  
    ```  
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl      
    ```  
  
     <span data-ttu-id="74ce6-149">To umožňuje kolekce `DCEnd` události pro spuštění sekvence daneho relace.</span><span class="sxs-lookup"><span data-stu-id="74ce6-149">This enables the collection of `DCEnd` events to start a rundown session.</span></span> <span data-ttu-id="74ce6-150">Pravděpodobně muset počkat 30 – 60 sekund pro všechny události, které se mají shromažďovat.</span><span class="sxs-lookup"><span data-stu-id="74ce6-150">You may need to wait 30 to 60 seconds for all events to be collected.</span></span> <span data-ttu-id="74ce6-151">Protokol se uloží do souboru clr1.et2.</span><span class="sxs-lookup"><span data-stu-id="74ce6-151">The log will be saved to the clr1.et2 file.</span></span>  
  
3.  <span data-ttu-id="74ce6-152">Vypněte všechny profilace trasování událostí pro Windows:</span><span class="sxs-lookup"><span data-stu-id="74ce6-152">Turn off all ETW profiling:</span></span>  
  
    ```  
    xperf -stop clrRundown   
    xperf -stop clr  
    ```  
  
4.  <span data-ttu-id="74ce6-153">Sloučení profilů vytvořit jeden soubor protokolu:</span><span class="sxs-lookup"><span data-stu-id="74ce6-153">Merge the profiles to create one log file:</span></span>  
  
    ```  
    xperf -merge -d clr1.etl clr2.etl merged.etl  
    ```  
  
     <span data-ttu-id="74ce6-154">Soubor merged.etl bude obsahovat události z modulu runtime a relace sekvence daneho zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="74ce6-154">The merged.etl file will contain the events from the runtime and the rundown provider sessions.</span></span>  
  
 <span data-ttu-id="74ce6-155">Nástroj můžete spustit kroky 2 a 3 (spuštění sekvence daneho relace a pak ukončení profilace) namísto okamžitě vypnutí profilace, když se uživatel požadavky profilace zastavení.</span><span class="sxs-lookup"><span data-stu-id="74ce6-155">A tool can execute steps 2 and 3 (starting a rundown session and then terminating profiling) instead of immediately turning off profiling when a user requests profiling to be stopped.</span></span> <span data-ttu-id="74ce6-156">Nástroj můžete spustit také krok 4.</span><span class="sxs-lookup"><span data-stu-id="74ce6-156">A tool can also execute step 4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74ce6-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="74ce6-157">See Also</span></span>  
 [<span data-ttu-id="74ce6-158">Události Trasování událostí pro Windows v CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="74ce6-158">ETW Events in the Common Language Runtime</span></span>](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
