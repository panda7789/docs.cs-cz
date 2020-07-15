---
title: Poskytovatelé CLR ETW
description: 'Přečtěte si podrobnosti o dvou zprostředkovatelích trasování událostí modulu CLR (Common Language Runtime) pro Windows (ETW): poskytovatel runtimne a poskytovatel doběhu.'
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
ms.openlocfilehash: 9f86e8334482880c4f7cb23ec93a3c826c083389
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309648"
---
# <a name="clr-etw-providers"></a><span data-ttu-id="46471-103">Poskytovatelé CLR ETW</span><span class="sxs-lookup"><span data-stu-id="46471-103">CLR ETW Providers</span></span>
<span data-ttu-id="46471-104">Modul CLR (Common Language Runtime) má dva zprostředkovatele: poskytovatele modulu runtime a poskytovatele doběhu.</span><span class="sxs-lookup"><span data-stu-id="46471-104">The common language runtime (CLR) has two providers: the runtime provider and the rundown provider.</span></span>  
  
 <span data-ttu-id="46471-105">Zprostředkovatel modulu runtime vyvolává události v závislosti na tom, která klíčová slova (kategorie událostí) jsou povolena.</span><span class="sxs-lookup"><span data-stu-id="46471-105">The runtime provider raises events, depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="46471-106">Například můžete shromáždit události zavaděče povolením `LoaderKeyword` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="46471-106">For example, you can collect loader events by enabling the `LoaderKeyword` keyword.</span></span>  
  
 <span data-ttu-id="46471-107">Události trasování událostí pro Windows (ETW) jsou protokolovány do souboru s příponou. ETL, která může být později zpracována v souborech hodnot oddělených čárkou (. csv) podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="46471-107">Event Tracing for Windows (ETW) events are logged into a file that has an .etl extension, which can later be post-processed in comma-separated value (.csv) files as needed.</span></span> <span data-ttu-id="46471-108">Informace o tom, jak převést soubor. ETL na soubor. csv, najdete v tématu [řízení .NET Framework protokolování](controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="46471-108">For information about how to convert the .etl file to a .csv file, see [Controlling .NET Framework Logging](controlling-logging.md).</span></span>  
  
## <a name="the-runtime-provider"></a><span data-ttu-id="46471-109">Zprostředkovatel modulu runtime</span><span class="sxs-lookup"><span data-stu-id="46471-109">The Runtime Provider</span></span>  
 <span data-ttu-id="46471-110">Poskytovatel modulu runtime je hlavním zprostředkovatelem modulu CLR ETW.</span><span class="sxs-lookup"><span data-stu-id="46471-110">The runtime provider is the main CLR ETW provider.</span></span>  
  
 <span data-ttu-id="46471-111">Identifikátor GUID zprostředkovatele modulu runtime CLR je e13c0d23-CCBC-4e12-931B-d9cc2eee27e4.</span><span class="sxs-lookup"><span data-stu-id="46471-111">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
 <span data-ttu-id="46471-112">Příklady, jak pomocí běžně dostupných nástrojů protokolovat a zobrazovat události CLR ETW, najdete v tématu [řízení .NET Framework protokolování](controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="46471-112">For examples of how to log and view CLR ETW events by using commonly available tools, see [Controlling .NET Framework Logging](controlling-logging.md).</span></span>  
  
 <span data-ttu-id="46471-113">Kromě používání klíčových slov, jako je například `LoaderKeyword` , možná budete muset povolit klíčová slova pro protokolování událostí, které mohou být vyvolány příliš často.</span><span class="sxs-lookup"><span data-stu-id="46471-113">In addition to using keywords such as `LoaderKeyword`, you may have to enable keywords for logging events that may be raised too frequently.</span></span> <span data-ttu-id="46471-114">`StartEnumerationKeyword` `EndEnumerationKeyword` Klíčová slova a umožňují tyto události a jsou shrnuty v [klíčových slovech a klíčích rozhraní CLR pro trasování a úrovně](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="46471-114">The `StartEnumerationKeyword` and the `EndEnumerationKeyword` keywords enable these events and are summarized in [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>  
  
## <a name="the-rundown-provider"></a><span data-ttu-id="46471-115">Poskytovatel doběhu</span><span class="sxs-lookup"><span data-stu-id="46471-115">The Rundown Provider</span></span>  
 <span data-ttu-id="46471-116">Pro určité účely zvláštního použití musí být poskytovatel doběhu zapnutý.</span><span class="sxs-lookup"><span data-stu-id="46471-116">The rundown provider must be turned on for certain special-purpose uses.</span></span> <span data-ttu-id="46471-117">Nicméně pro většinu uživatelů by měl stačit poskytovatel modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="46471-117">However, for a majority of users, the runtime provider should suffice.</span></span>  
  
 <span data-ttu-id="46471-118">Identifikátor GUID zprostředkovatele doběhu CLR je A669021C-C450-4609-A035-5AF59AF4DF18.</span><span class="sxs-lookup"><span data-stu-id="46471-118">The CLR rundown provider GUID is A669021C-C450-4609-A035-5AF59AF4DF18.</span></span>  
  
 <span data-ttu-id="46471-119">V normálním případě je protokolování ETW povoleno před spuštěním procesu a protokolování je po ukončení procesu vypnuté.</span><span class="sxs-lookup"><span data-stu-id="46471-119">Normally, ETW logging is enabled before a process launches, and the logging is turned off after the process exits.</span></span> <span data-ttu-id="46471-120">Pokud je však protokolování ETW při provádění procesu zapnuté, pro tento proces jsou potřeba další informace.</span><span class="sxs-lookup"><span data-stu-id="46471-120">However, if ETW logging is turned on while the process is executing, additional information is needed about the process.</span></span> <span data-ttu-id="46471-121">Například pro rozlišení symbolů musíte protokolovat události metody pro metody, které již byly načteny před zapnutím protokolování.</span><span class="sxs-lookup"><span data-stu-id="46471-121">For example, for symbol resolution you have to log method events for methods that were already loaded before logging was turned on.</span></span>  
  
 <span data-ttu-id="46471-122">`DCStart`Události a `DCEnd` zachytí stav procesu při spuštění a zastavení shromažďování dat.</span><span class="sxs-lookup"><span data-stu-id="46471-122">The `DCStart` and `DCEnd` events capture the state of the process when data collection was started and stopped.</span></span> <span data-ttu-id="46471-123">(Stav odkazuje na informace na vysoké úrovni, včetně metod, které již byly zkompilovány JIT (just-in-time) a sestavení, která byla načtena.) Tyto dvě události mohou poskytnout informace o tom, co se v procesu již stalo. například které metody byly kompilovány JIT a tak dále.</span><span class="sxs-lookup"><span data-stu-id="46471-123">(State refers to information at a high level, including the methods that were already just-in-time (JIT) compiled and assemblies that were loaded.) These two events can provide information about what has already happened in the process; for example, which methods were JIT- compiled, and so on.</span></span>  
  
 <span data-ttu-id="46471-124">`DC` `DCStart` `DCEnd` `DCInit` V rámci poskytovatele doběhu jsou vyvolány pouze události s,, nebo v jejich názvech.</span><span class="sxs-lookup"><span data-stu-id="46471-124">Only the events with `DC`, `DCStart`, `DCEnd`, or `DCInit` in their names are raised under the rundown provider.</span></span> <span data-ttu-id="46471-125">Kromě toho jsou tyto události vyvolány pouze pod poskytovatelem doběhu.</span><span class="sxs-lookup"><span data-stu-id="46471-125">Additionally, these events are raised only under the rundown provider.</span></span>  
  
 <span data-ttu-id="46471-126">Kromě filtrů klíčového slova události poskytovatel doběhu také podporuje `StartRundownKeyword` `EndRundownKeyword` klíčová slova a pro zajištění cíleného filtrování.</span><span class="sxs-lookup"><span data-stu-id="46471-126">In addition to the event keyword filters, the rundown provider also supports the `StartRundownKeyword` and `EndRundownKeyword` keywords to provide targeted filtering.</span></span>  
  
### <a name="start-rundown"></a><span data-ttu-id="46471-127">Spustit doběhu</span><span class="sxs-lookup"><span data-stu-id="46471-127">Start Rundown</span></span>  
 <span data-ttu-id="46471-128">Pokud je povoleno protokolování pod poskytovatelem doběhu s klíčovým slovem, spustí se spouštěcí doběhu `StartRundownKeyword` .</span><span class="sxs-lookup"><span data-stu-id="46471-128">A start rundown is triggered when logging under the rundown provider is enabled with the `StartRundownKeyword` keyword.</span></span> <span data-ttu-id="46471-129">Tím dojde `DCStart` k vyvolání události a zachycení stavu systému.</span><span class="sxs-lookup"><span data-stu-id="46471-129">This causes the `DCStart` event to be raised, and captures the state of the system.</span></span> <span data-ttu-id="46471-130">Před začátkem výčtu `DCStartInit` je vyvolána událost.</span><span class="sxs-lookup"><span data-stu-id="46471-130">Before the start of the enumeration, the `DCStartInit` event is raised.</span></span> <span data-ttu-id="46471-131">Na konci výčtu `DCStartComplete` je vyvolána událost, aby upozornila kontroleru na normální ukončení sběru dat.</span><span class="sxs-lookup"><span data-stu-id="46471-131">At the end of the enumeration, the `DCStartComplete` event is raised to notify the controller that data collection terminated normally.</span></span>  
  
### <a name="end-rundown"></a><span data-ttu-id="46471-132">Konec doběhu</span><span class="sxs-lookup"><span data-stu-id="46471-132">End Rundown</span></span>  
 <span data-ttu-id="46471-133">Pokud je povoleno protokolování pod poskytovatelem doběhu, je aktivováno end doběhu s `EndRundownKeyword` klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="46471-133">An end rundown is triggered when logging under the rundown provider is enabled with the `EndRundownKeyword` keyword.</span></span> <span data-ttu-id="46471-134">Konec doběhu zastaví profilování u procesu, který pokračuje v provádění.</span><span class="sxs-lookup"><span data-stu-id="46471-134">End rundown stops profiling on a process that continues to execute.</span></span> <span data-ttu-id="46471-135">`DCEnd`Události zachytí stav systému, když je profilování zastaveno.</span><span class="sxs-lookup"><span data-stu-id="46471-135">The `DCEnd` events capture the state of the system when profiling is stopped.</span></span>  
  
 <span data-ttu-id="46471-136">Před začátkem výčtu `DCEndInit` je vyvolána událost.</span><span class="sxs-lookup"><span data-stu-id="46471-136">Before the start of the enumeration, the `DCEndInit` event is raised.</span></span> <span data-ttu-id="46471-137">Na konci výčtu `DCEndComplete` je vyvolána událost, aby byl příjemce upozorněn na normální ukončení sběru dat.</span><span class="sxs-lookup"><span data-stu-id="46471-137">At the end of the enumeration, the `DCEndComplete` event is raised to notify the consumer that data collection terminated normally.</span></span> <span data-ttu-id="46471-138">Spuštění doběhu a end doběhu se primárně používá pro spravované rozlišení symbolů.</span><span class="sxs-lookup"><span data-stu-id="46471-138">Start rundown and end rundown are primarily used for managed symbol resolution.</span></span> <span data-ttu-id="46471-139">Spustit doběhu může poskytnout informace o rozsahu adres pro metody, které již byly kompilovány JIT před spuštěním relace profilování.</span><span class="sxs-lookup"><span data-stu-id="46471-139">Start rundown can provide address range information for methods that were already JIT-compiled before the profiling session was started.</span></span> <span data-ttu-id="46471-140">Koncová doběhu může poskytnout informace o rozsahu adres pro všechny metody, které byly kompilovány JIT, když se profilování vypíná.</span><span class="sxs-lookup"><span data-stu-id="46471-140">End rundown can provide address range information for all methods that have been JIT-compiled when profiling is about to be turned off.</span></span>  
  
 <span data-ttu-id="46471-141">K ukončení doběhu dojde automaticky při zastavení relace profilování.</span><span class="sxs-lookup"><span data-stu-id="46471-141">End rundown does not happen automatically when a profiling session is stopped.</span></span> <span data-ttu-id="46471-142">Místo toho nástroj, který se pokouší provést rozlišení spravovaného symbolu, musí explicitně vyvolat relaci poskytovatele CLR doběhu s `EndRundownKeyword` povoleným klíčovým slovem, těsně před zastavením profilace.</span><span class="sxs-lookup"><span data-stu-id="46471-142">Instead, a tool that is seeking to perform managed symbol resolution has to explicitly invoke a CLR rundown provider session with the `EndRundownKeyword` keyword enabled, just before profiling is stopped.</span></span>  
  
 <span data-ttu-id="46471-143">I když buď spustit doběhu nebo End doběhu může poskytnout informace o rozsahu adres pro spravované řešení, doporučujeme použít `EndRundownKeyword` klíčové slovo (které poskytuje `DCEnd` události) místo `StartRundownKeyword` klíčového slova (které poskytuje `DCStart` události).</span><span class="sxs-lookup"><span data-stu-id="46471-143">Although either start rundown or end rundown can provide method address range information for managed symbol resolution, we recommend that you use the `EndRundownKeyword` keyword (which supplies `DCEnd` events) instead of the `StartRundownKeyword` keyword (which supplies `DCStart` events).</span></span> <span data-ttu-id="46471-144">Použití `StartRundownKeyword` způsobí, že doběhu proběhne během relace profilování, což může narušit scénář profilace.</span><span class="sxs-lookup"><span data-stu-id="46471-144">Using `StartRundownKeyword` causes the rundown to happen during the profiling session, which may disturb the profiled scenario.</span></span>  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a><span data-ttu-id="46471-145">Shromažďování dat ETW pomocí zprostředkovatelů runtime a doběhu</span><span class="sxs-lookup"><span data-stu-id="46471-145">ETW Data Collection Using Runtime and Rundown Providers</span></span>  
 <span data-ttu-id="46471-146">Následující příklad ukazuje, jak použít poskytovatele CLR doběhu způsobem, který umožňuje rozlišení symbolů spravovaných procesů s minimálním dopadem, bez ohledu na to, zda procesy začínají nebo končí uvnitř nebo vně profilace okna.</span><span class="sxs-lookup"><span data-stu-id="46471-146">The following example demonstrates how to use the CLR rundown provider in a way that allows symbol resolution of managed processes with minimal impact, regardless of whether the processes start or end inside or outside the profiled window.</span></span>  
  
1. <span data-ttu-id="46471-147">Zapnout protokolování ETW pomocí zprostředkovatele modulu CLR Runtime:</span><span class="sxs-lookup"><span data-stu-id="46471-147">Turn on ETW logging by using the CLR runtime provider:</span></span>  
  
    ```console
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl
    ```  
  
     <span data-ttu-id="46471-148">Protokol bude uložen do souboru souboru clr1. ETL.</span><span class="sxs-lookup"><span data-stu-id="46471-148">The log will be saved to the clr1.etl file.</span></span>  
  
2. <span data-ttu-id="46471-149">Chcete-li zastavit profilaci, když proces pokračuje v provádění, spusťte poskytovatele doběhu a zaznamenejte `DCEnd` události:</span><span class="sxs-lookup"><span data-stu-id="46471-149">To stop profiling while the process continues to execute, start the rundown provider to capture the `DCEnd` events:</span></span>  
  
    ```console
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl
    ```  
  
     <span data-ttu-id="46471-150">To umožňuje kolekci `DCEnd` událostí spustit relaci doběhu.</span><span class="sxs-lookup"><span data-stu-id="46471-150">This enables the collection of `DCEnd` events to start a rundown session.</span></span> <span data-ttu-id="46471-151">Pro shromáždění všech událostí možná budete muset počkat 30 až 60 sekund.</span><span class="sxs-lookup"><span data-stu-id="46471-151">You may need to wait 30 to 60 seconds for all events to be collected.</span></span> <span data-ttu-id="46471-152">Protokol bude uložen do souboru souboru clr1. ET2.</span><span class="sxs-lookup"><span data-stu-id="46471-152">The log will be saved to the clr1.et2 file.</span></span>  
  
3. <span data-ttu-id="46471-153">Vypnout všechny profily trasování událostí pro Windows:</span><span class="sxs-lookup"><span data-stu-id="46471-153">Turn off all ETW profiling:</span></span>  
  
    ```console
    xperf -stop clrRundown
    xperf -stop clr  
    ```  
  
4. <span data-ttu-id="46471-154">Sloučením profilů vytvořte jeden soubor protokolu:</span><span class="sxs-lookup"><span data-stu-id="46471-154">Merge the profiles to create one log file:</span></span>  
  
    ```console
    xperf -merge clr1.etl clr2.etl merged.etl  
    ```  
  
     <span data-ttu-id="46471-155">Sloučený soubor. ETL bude obsahovat události z relací zprostředkovatelů runtime a doběhu.</span><span class="sxs-lookup"><span data-stu-id="46471-155">The merged.etl file will contain the events from the runtime and the rundown provider sessions.</span></span>  
  
 <span data-ttu-id="46471-156">Nástroj může spustit kroky 2 a 3 (spuštění relace doběhu a následná ukončení profilace) místo okamžitého vypnutí profilování, když uživatel požaduje, aby bylo profilování zastaveno.</span><span class="sxs-lookup"><span data-stu-id="46471-156">A tool can execute steps 2 and 3 (starting a rundown session and then terminating profiling) instead of immediately turning off profiling when a user requests profiling to be stopped.</span></span> <span data-ttu-id="46471-157">Nástroj může také provádět krok 4.</span><span class="sxs-lookup"><span data-stu-id="46471-157">A tool can also execute step 4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46471-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="46471-158">See also</span></span>

- [<span data-ttu-id="46471-159">Události Trasování událostí pro Windows v CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="46471-159">ETW Events in the Common Language Runtime</span></span>](etw-events-in-the-common-language-runtime.md)
