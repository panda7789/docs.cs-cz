---
title: "Diagnostikování chyb pomocí asistentů spravovaného ladění"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EHMDA
helpviewer_keywords:
- run-time error debugging
- managed code, run-time debugging
- resource debugging
- registry, MDAs
- common language runtime, debugging
- MDAs (managed debugging assistants)
- configuration files [.NET Framework], debugging runtime events
- messages, managed debugging assistants
- application configuration files, managed debugging assistants
- debugging [.NET Framework], managed debugging assistants
- environment variables, MDAs
- access violation debugging [.NET Framework]
- diagnostics, managed debugging assistants
- unmanaged code, run-time debugging
- default debug output stream
- memory, debugging
- app.config files, managed debugging assistants
- managed debugging assistants (MDAs)
- debugging [.NET Framework], run-time errors
- trapping events
- runtime, error debugging
- disabling MDAs
- output, managed debugging assistants
- errors [.NET Framework], managed debugging assistants
ms.assetid: 76994ee6-9fa9-4059-b813-26578d24427c
caps.latest.revision: "63"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12a96068412f05d48b8b006385c66f3efbbf9870
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="diagnosing-errors-with-managed-debugging-assistants"></a><span data-ttu-id="698e5-102">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="698e5-102">Diagnosing Errors with Managed Debugging Assistants</span></span>
<span data-ttu-id="698e5-103">Spravované ladění Pomocníci ladění (mda) pomůcek, které spolupracují se modul CLR (CLR) k poskytování informací o stav modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="698e5-103">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span> <span data-ttu-id="698e5-104">Asistentům generovat informační zprávy o událostech runtime, které nelze jinak depeše.</span><span class="sxs-lookup"><span data-stu-id="698e5-104">The assistants generate informational messages about runtime events that you cannot otherwise trap.</span></span> <span data-ttu-id="698e5-105">Mda můžete izolovat aplikace pevný najít chyby, které dojít, když přechod mezi spravovanými a nespravovanými kódu.</span><span class="sxs-lookup"><span data-stu-id="698e5-105">You can use MDAs to isolate hard-to-find application bugs that occur when transitioning between managed and unmanaged code.</span></span> <span data-ttu-id="698e5-106">Můžete povolit nebo zakázat všechny mda přidání klíče registru systému Windows nebo nastavením proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="698e5-106">You can enable or disable all MDAs by adding a key to the Windows registry or by setting an environment variable.</span></span> <span data-ttu-id="698e5-107">Konkrétní mda můžete povolit pomocí nastavení konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="698e5-107">You can enable specific MDAs by using application configuration settings.</span></span> <span data-ttu-id="698e5-108">Můžete nastavit další konfiguraci nastavení pro některé jednotlivé mda v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="698e5-108">You can set additional configuration settings for some individual MDAs in the application's configuration file.</span></span> <span data-ttu-id="698e5-109">Protože tyto konfigurační soubory jsou analyzovat při načtení modulu runtime, je nutné povolit MDA před spuštěním spravované aplikace.</span><span class="sxs-lookup"><span data-stu-id="698e5-109">Because these configuration files are parsed when the runtime is loaded, you must enable the MDA before the managed application starts.</span></span> <span data-ttu-id="698e5-110">Nelze ji povolit pro aplikace, které jste již bylo zahájeno.</span><span class="sxs-lookup"><span data-stu-id="698e5-110">You cannot enable it for applications that have already started.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="698e5-111">Pokud MDA je povoleno, bude aktivní i, pokud není váš kód provádění pod ladicí program.</span><span class="sxs-lookup"><span data-stu-id="698e5-111">When an MDA is enabled, it is active even when your code is not executing under a debugger.</span></span> <span data-ttu-id="698e5-112">Pokud MDA událost se vyvolá, když není k dispozici ladicí program, zpráva o události se zobrazí v dialogovém okně neošetřených výjimek, i když není k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="698e5-112">If an MDA event is raised when a debugger is not present, the event message is presented in an unhandled exception dialog box, although it is not an unhandled exception.</span></span> <span data-ttu-id="698e5-113">Abyste se vyhnuli dialogové okno, odeberte nastavení povolení MDA při není provádění kódu v prostředí ladění.</span><span class="sxs-lookup"><span data-stu-id="698e5-113">To avoid the dialog box, remove the MDA-enabling settings when your code is not executing in a debugging environment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="698e5-114">Pokud váš kód je prováděna v sadě Visual Studio integrované vývojové prostředí (IDE), se můžete vyhnout dialogové okno výjimku, který se zobrazí určité události (mda).</span><span class="sxs-lookup"><span data-stu-id="698e5-114">When your code is executing in the Visual Studio integrated development environment (IDE), you can avoid the exception dialog box that appears for specific MDA events.</span></span> <span data-ttu-id="698e5-115">K tomu, na **ladění** nabídky, klikněte na tlačítko **výjimky**.</span><span class="sxs-lookup"><span data-stu-id="698e5-115">To do that, on the **Debug** menu, click **Exceptions**.</span></span> <span data-ttu-id="698e5-116">(Pokud **ladění** nabídky neobsahuje **výjimky** příkaz, klikněte na tlačítko **přizpůsobit** na **nástroje** nabídky přidat.) V **výjimky** dialogové okno, rozbalte seznam **Pomocníci spravovaného ladění** seznamu a poté zrušte zaškrtnutí **vyvolaná** zaškrtnutí políčka pro jednotlivé (mda).</span><span class="sxs-lookup"><span data-stu-id="698e5-116">(If the **Debug** menu does not contain an **Exceptions** command, click **Customize** on the **Tools** menu to add it.) In the **Exceptions** dialog box, expand the **Managed Debugging Assistants** list, and then clear the **Thrown** check box for the individual MDA.</span></span> <span data-ttu-id="698e5-117">Třeba, aby se zabránilo dialogové okno výjimky pro [contextSwitchDeadlock](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md) vymazat **vyvolaná** zaškrtněte políčko vedle jeho názvu v **spravované ladění Pomocníci** seznamu.</span><span class="sxs-lookup"><span data-stu-id="698e5-117">For example, to avoid the exception dialog box for a [contextSwitchDeadlock](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md) clear the **Thrown** check box next to its name in the **Managed Debugging Assistants** list.</span></span> <span data-ttu-id="698e5-118">Tohoto dialogového okna můžete také povolit zobrazení MDA výjimka dialogových oken.</span><span class="sxs-lookup"><span data-stu-id="698e5-118">You can also use this dialog box to enable the display of MDA exception dialog boxes.</span></span>  
  
 <span data-ttu-id="698e5-119">Následující tabulka uvádí mda dodávaných s rozhraním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="698e5-119">The following table lists the MDAs that ship with the .NET Framework.</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="698e5-120">asynchronousThreadAbort</span><span class="sxs-lookup"><span data-stu-id="698e5-120">asynchronousThreadAbort</span></span>](../../../docs/framework/debug-trace-profile/asynchronousthreadabort-mda.md)|[<span data-ttu-id="698e5-121">bindingFailure</span><span class="sxs-lookup"><span data-stu-id="698e5-121">bindingFailure</span></span>](../../../docs/framework/debug-trace-profile/bindingfailure-mda.md)|  
|[<span data-ttu-id="698e5-122">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="698e5-122">callbackOnCollectedDelegate</span></span>](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)|[<span data-ttu-id="698e5-123">contextSwitchDeadlock</span><span class="sxs-lookup"><span data-stu-id="698e5-123">contextSwitchDeadlock</span></span>](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md)|  
|[<span data-ttu-id="698e5-124">dangerousThreadingAPI</span><span class="sxs-lookup"><span data-stu-id="698e5-124">dangerousThreadingAPI</span></span>](../../../docs/framework/debug-trace-profile/dangerousthreadingapi-mda.md)|[<span data-ttu-id="698e5-125">dateTimeInvalidLocalFormat</span><span class="sxs-lookup"><span data-stu-id="698e5-125">dateTimeInvalidLocalFormat</span></span>](../../../docs/framework/debug-trace-profile/datetimeinvalidlocalformat-mda.md)|  
|[<span data-ttu-id="698e5-126">dirtyCastAndCallOnInterface</span><span class="sxs-lookup"><span data-stu-id="698e5-126">dirtyCastAndCallOnInterface</span></span>](../../../docs/framework/debug-trace-profile/dirtycastandcalloninterface-mda.md)|[<span data-ttu-id="698e5-127">disconnectedContext</span><span class="sxs-lookup"><span data-stu-id="698e5-127">disconnectedContext</span></span>](../../../docs/framework/debug-trace-profile/disconnectedcontext-mda.md)|  
|[<span data-ttu-id="698e5-128">dllMainReturnsFalse</span><span class="sxs-lookup"><span data-stu-id="698e5-128">dllMainReturnsFalse</span></span>](../../../docs/framework/debug-trace-profile/dllmainreturnsfalse-mda.md)|[<span data-ttu-id="698e5-129">exceptionSwallowedOnCallFromCom</span><span class="sxs-lookup"><span data-stu-id="698e5-129">exceptionSwallowedOnCallFromCom</span></span>](../../../docs/framework/debug-trace-profile/exceptionswallowedoncallfromcom-mda.md)|  
|[<span data-ttu-id="698e5-130">failedQI</span><span class="sxs-lookup"><span data-stu-id="698e5-130">failedQI</span></span>](../../../docs/framework/debug-trace-profile/failedqi-mda.md)|[<span data-ttu-id="698e5-131">fatalExecutionEngineError</span><span class="sxs-lookup"><span data-stu-id="698e5-131">fatalExecutionEngineError</span></span>](../../../docs/framework/debug-trace-profile/fatalexecutionengineerror-mda.md)|  
|[<span data-ttu-id="698e5-132">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="698e5-132">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)|[<span data-ttu-id="698e5-133">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="698e5-133">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)|  
|[<span data-ttu-id="698e5-134">illegalPrepareConstrainedRegion</span><span class="sxs-lookup"><span data-stu-id="698e5-134">illegalPrepareConstrainedRegion</span></span>](../../../docs/framework/debug-trace-profile/illegalprepareconstrainedregion-mda.md)|[<span data-ttu-id="698e5-135">invalidApartmentStateChange</span><span class="sxs-lookup"><span data-stu-id="698e5-135">invalidApartmentStateChange</span></span>](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md)|  
|[<span data-ttu-id="698e5-136">invalidCERCall</span><span class="sxs-lookup"><span data-stu-id="698e5-136">invalidCERCall</span></span>](../../../docs/framework/debug-trace-profile/invalidcercall-mda.md)|[<span data-ttu-id="698e5-137">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="698e5-137">invalidFunctionPointerInDelegate</span></span>](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)|  
|[<span data-ttu-id="698e5-138">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="698e5-138">invalidGCHandleCookie</span></span>](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)|[<span data-ttu-id="698e5-139">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="698e5-139">invalidIUnknown</span></span>](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)|  
|[<span data-ttu-id="698e5-140">invalidMemberDeclaration</span><span class="sxs-lookup"><span data-stu-id="698e5-140">invalidMemberDeclaration</span></span>](../../../docs/framework/debug-trace-profile/invalidmemberdeclaration-mda.md)|[<span data-ttu-id="698e5-141">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="698e5-141">invalidOverlappedToPinvoke</span></span>](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)|  
|[<span data-ttu-id="698e5-142">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="698e5-142">invalidVariant</span></span>](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)|[<span data-ttu-id="698e5-143">jitCompilationStart</span><span class="sxs-lookup"><span data-stu-id="698e5-143">jitCompilationStart</span></span>](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md)|  
|[<span data-ttu-id="698e5-144">loaderLock</span><span class="sxs-lookup"><span data-stu-id="698e5-144">loaderLock</span></span>](../../../docs/framework/debug-trace-profile/loaderlock-mda.md)|[<span data-ttu-id="698e5-145">loadFromContext</span><span class="sxs-lookup"><span data-stu-id="698e5-145">loadFromContext</span></span>](../../../docs/framework/debug-trace-profile/loadfromcontext-mda.md)|  
|[<span data-ttu-id="698e5-146">marshalCleanupError</span><span class="sxs-lookup"><span data-stu-id="698e5-146">marshalCleanupError</span></span>](../../../docs/framework/debug-trace-profile/marshalcleanuperror-mda.md)|[<span data-ttu-id="698e5-147">marshaling</span><span class="sxs-lookup"><span data-stu-id="698e5-147">marshaling</span></span>](../../../docs/framework/debug-trace-profile/marshaling-mda.md)|  
|[<span data-ttu-id="698e5-148">memberInfoCacheCreation</span><span class="sxs-lookup"><span data-stu-id="698e5-148">memberInfoCacheCreation</span></span>](../../../docs/framework/debug-trace-profile/memberinfocachecreation-mda.md)|[<span data-ttu-id="698e5-149">moduloObjectHashcode</span><span class="sxs-lookup"><span data-stu-id="698e5-149">moduloObjectHashcode</span></span>](../../../docs/framework/debug-trace-profile/moduloobjecthashcode-mda.md)|  
|[<span data-ttu-id="698e5-150">nonComVisibleBaseClass</span><span class="sxs-lookup"><span data-stu-id="698e5-150">nonComVisibleBaseClass</span></span>](../../../docs/framework/debug-trace-profile/noncomvisiblebaseclass-mda.md)|[<span data-ttu-id="698e5-151">notMarshalable</span><span class="sxs-lookup"><span data-stu-id="698e5-151">notMarshalable</span></span>](../../../docs/framework/debug-trace-profile/notmarshalable-mda.md)|  
|[<span data-ttu-id="698e5-152">openGenericCERCall</span><span class="sxs-lookup"><span data-stu-id="698e5-152">openGenericCERCall</span></span>](../../../docs/framework/debug-trace-profile/opengenericcercall-mda.md)|[<span data-ttu-id="698e5-153">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="698e5-153">overlappedFreeError</span></span>](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)|  
|[<span data-ttu-id="698e5-154">pInvokeLog</span><span class="sxs-lookup"><span data-stu-id="698e5-154">pInvokeLog</span></span>](../../../docs/framework/debug-trace-profile/pinvokelog-mda.md)|[<span data-ttu-id="698e5-155">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="698e5-155">pInvokeStackImbalance</span></span>](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)|  
|[<span data-ttu-id="698e5-156">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="698e5-156">raceOnRCWCleanup</span></span>](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)|[<span data-ttu-id="698e5-157">reentrancy</span><span class="sxs-lookup"><span data-stu-id="698e5-157">reentrancy</span></span>](../../../docs/framework/debug-trace-profile/reentrancy-mda.md)|  
|[<span data-ttu-id="698e5-158">releaseHandleFailed</span><span class="sxs-lookup"><span data-stu-id="698e5-158">releaseHandleFailed</span></span>](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md)|[<span data-ttu-id="698e5-159">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="698e5-159">reportAvOnComRelease</span></span>](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)|  
|[<span data-ttu-id="698e5-160">streamWriterBufferedDataLost</span><span class="sxs-lookup"><span data-stu-id="698e5-160">streamWriterBufferedDataLost</span></span>](../../../docs/framework/debug-trace-profile/streamwriterbuffereddatalost-mda.md)|[<span data-ttu-id="698e5-161">virtualCERCall</span><span class="sxs-lookup"><span data-stu-id="698e5-161">virtualCERCall</span></span>](../../../docs/framework/debug-trace-profile/virtualcercall-mda.md)|  
  
 <span data-ttu-id="698e5-162">Ve výchozím nastavení aktivuje rozhraní .NET Framework podmnožinu mda pro všechny spravované ladicí programy.</span><span class="sxs-lookup"><span data-stu-id="698e5-162">By default, the .NET Framework activates a subset of MDAs for all managed debuggers.</span></span> <span data-ttu-id="698e5-163">Můžete zobrazit výchozí nastavení v sadě Visual Studio kliknutím **výjimky** na **ladění** nabídce a rozšíření **Pomocníci spravovaného ladění** seznamu.</span><span class="sxs-lookup"><span data-stu-id="698e5-163">You can view the default set in Visual Studio by clicking **Exceptions** on the **Debug** menu and expanding the **Managed Debugging Assistants** list.</span></span>  
  
## <a name="enabling-and-disabling-mdas"></a><span data-ttu-id="698e5-164">Povolení a zákaz mda</span><span class="sxs-lookup"><span data-stu-id="698e5-164">Enabling and Disabling MDAs</span></span>  
 <span data-ttu-id="698e5-165">Můžete povolit nebo zakázat mda pomocí klíče registru, proměnné prostředí a nastavení konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="698e5-165">You can enable and disable MDAs by using a registry key, an environment variable, and application configuration settings.</span></span> <span data-ttu-id="698e5-166">Je nutné povolit klíč registru nebo proměnné prostředí pro použití nastavení konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="698e5-166">You must enable either the registry key or the environment variable to use the application configuration settings.</span></span>  
  
 <span data-ttu-id="698e5-167">V sadě Visual Studio 2005 a novějších verzích Pokud proces hostování je povoleno, nelze zakázat mda, které jsou v sadě výchozí nebo povolit mda, které není ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="698e5-167">In Visual Studio 2005 and later versions, when the hosting process is enabled, you cannot disable MDAs that are in the default set or enable MDAs that are not in the default set.</span></span> <span data-ttu-id="698e5-168">Proces hostování je zapnutá ve výchozím nastavení, takže musí být explicitně zakázány.</span><span class="sxs-lookup"><span data-stu-id="698e5-168">The hosting process is enabled by default, so it must be explicitly disabled.</span></span>  
  
 <span data-ttu-id="698e5-169">Pokud chcete zakázat hostitelského procesu v sadě Visual Studio, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="698e5-169">To disable the hosting process in Visual Studio, do the following:</span></span>  
  
1.  <span data-ttu-id="698e5-170">V **Průzkumníku**, vyberte projektu.</span><span class="sxs-lookup"><span data-stu-id="698e5-170">In **Solution Explorer**, select a project.</span></span>  
  
2.  <span data-ttu-id="698e5-171">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="698e5-171">On the **Project** menu, click **Properties**.</span></span>  
  
     <span data-ttu-id="698e5-172">**Návrhář projektu** se zobrazí v okně.</span><span class="sxs-lookup"><span data-stu-id="698e5-172">The **Project Designer** window appears.</span></span>  
  
3.  <span data-ttu-id="698e5-173">Klikněte **ladění** kartě.</span><span class="sxs-lookup"><span data-stu-id="698e5-173">Click the **Debug** tab.</span></span>  
  
4.  <span data-ttu-id="698e5-174">V **povolit ladicí programy** část, zrušte **povolit sady Visual Studio proces hostování** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="698e5-174">In the **Enable Debuggers** section, clear the **Enable the Visual Studio hosting process** check box.</span></span>  
  
 <span data-ttu-id="698e5-175">Zákaz hostitelského procesu však může ovlivnit výkon.</span><span class="sxs-lookup"><span data-stu-id="698e5-175">However, disabling the hosting process can affect performance.</span></span> <span data-ttu-id="698e5-176">Potřeba zakázat mda tak, že zabrání zobrazení dialogového okna (mda) vždy, když obdrží oznámení MDA Visual Studio se můžete vyhnout.</span><span class="sxs-lookup"><span data-stu-id="698e5-176">You can avoid the need to disable MDAs by preventing Visual Studio from displaying the MDA dialog box whenever an MDA notification is received.</span></span> <span data-ttu-id="698e5-177">To lze provést, klikněte na tlačítko **výjimky** na **ladění** nabídky, rozbalte **Pomocníci spravovaného ladění** seznamu a potom vyberte nebo zrušte **vyvolaná**zaškrtnutí políčka pro jednotlivé (mda).</span><span class="sxs-lookup"><span data-stu-id="698e5-177">To do that, click **Exceptions** on the **Debug** menu, expand the **Managed Debugging Assistants** list, and then select or clear the **Thrown** check box for the individual MDA.</span></span>  
  
### <a name="enabling-and-disabling-mdas-by-using-a-registry-key"></a><span data-ttu-id="698e5-178">Povolení a zákaz mda pomocí klíče registru</span><span class="sxs-lookup"><span data-stu-id="698e5-178">Enabling and Disabling MDAs by Using a Registry Key</span></span>  
 <span data-ttu-id="698e5-179">Můžete povolit mda přidáním HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. Podklíč NETFramework\MDA (typ REG_SZ, hodnota 1) v registru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="698e5-179">You can enable MDAs by adding the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\MDA subkey (type REG_SZ, value 1) in the Windows registry.</span></span> <span data-ttu-id="698e5-180">Do textového souboru s názvem MDAEnable.reg zkopírujte následující příklad. Otevřete Editor registru systému Windows (RegEdit.exe) a z **soubor** nabídce zvolte **Import**.</span><span class="sxs-lookup"><span data-stu-id="698e5-180">Copy the following example into a text file named MDAEnable.reg. Open the Windows Registry Editor (RegEdit.exe) and from the **File** menu choose **Import**.</span></span> <span data-ttu-id="698e5-181">Vyberte soubor MDAEnable.reg povolit mda na tomto počítači.</span><span class="sxs-lookup"><span data-stu-id="698e5-181">Select the MDAEnable.reg  file to enable MDAs on that computer.</span></span> <span data-ttu-id="698e5-182">Nastavení podklíč řetězec hodnotu 1 (ne hodnotu DWORD 1) umožňuje při čtení z nastavení MDA *ApplicationName.suffix*. mda.config souboru.</span><span class="sxs-lookup"><span data-stu-id="698e5-182">Setting the subkey to string value of 1 (not DWORD value of 1) enables the reading of MDA settings from the *ApplicationName.suffix*.mda.config file.</span></span> <span data-ttu-id="698e5-183">(Například Poznámkový blok v souboru konfigurace (mda) by se jmenovala notepad.exe.mda.config)</span><span class="sxs-lookup"><span data-stu-id="698e5-183">(For example the MDA configuration file for Notepad would be named notepad.exe.mda.config)</span></span>  
  
```  
Windows Registry Editor Version 5.00  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]  
"MDA"="1"  
```  
  
 <span data-ttu-id="698e5-184">Pokud počítači běží 32bitová aplikace na 64bitový operační systém, by měl klíč MDA nastavit takto:</span><span class="sxs-lookup"><span data-stu-id="698e5-184">If the computer is running a 32-bit application on a 64-bit operating system, then the MDA key should be set like the following:</span></span>  
  
```  
      Windows Registry Editor Version 5.00   
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]  
"MDA"="1"  
```  
  
 <span data-ttu-id="698e5-185">V tématu [povolení a zákaz mda pomocí nastavení konfigurace specifické pro aplikaci](#appConfig) Další informace.</span><span class="sxs-lookup"><span data-stu-id="698e5-185">See [Enabling and Disabling MDAs by Using Application-Specific Configuration Settings](#appConfig) for more information.</span></span> <span data-ttu-id="698e5-186">Nastavení registru mohou být přepsány COMPLUS_MDA proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="698e5-186">The registry setting can be overridden by the COMPLUS_MDA environment variable.</span></span> <span data-ttu-id="698e5-187">V tématu [povolení a zákaz mda pomocí proměnné prostředí](#envVariable) Další informace.</span><span class="sxs-lookup"><span data-stu-id="698e5-187">See [Enabling and Disabling MDAs by Using an Environment Variable](#envVariable) for more information.</span></span>  
  
 <span data-ttu-id="698e5-188">Mda zakázat, nastavte podklíč (mda) na hodnotu 0 (nula) pomocí Editoru registru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="698e5-188">To disable MDAs, set the MDA subkey to 0 (zero) using the Windows Registry Editor.</span></span>  
  
 <span data-ttu-id="698e5-189">Ve výchozím nastavení jsou povolené některé mda při spuštění aplikace, který je připojen k ladicí program, i bez přidání klíče registru.</span><span class="sxs-lookup"><span data-stu-id="698e5-189">By default, some MDAs are enabled when you run an application that is attached to a debugger, even without adding the registry key.</span></span> <span data-ttu-id="698e5-190">Příkladem takových pomocníci jsou [pInvokeStackImbalance](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) a [invalidApartmentStateChange](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md).</span><span class="sxs-lookup"><span data-stu-id="698e5-190">Examples of such assistants are [pInvokeStackImbalance](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) and [invalidApartmentStateChange](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md).</span></span> <span data-ttu-id="698e5-191">Tyto Pomocníci můžete vypnout spuštěním souboru MDADisable.reg, jak je popsáno výše v této části.</span><span class="sxs-lookup"><span data-stu-id="698e5-191">You can disable these assistants by running the MDADisable.reg file as described earlier in this section.</span></span>  
  
<a name="envVariable"></a>   
### <a name="enabling-and-disabling-mdas-by-using-an-environment-variable"></a><span data-ttu-id="698e5-192">Povolení a zákaz mda pomocí proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="698e5-192">Enabling and Disabling MDAs by Using an Environment Variable</span></span>  
 <span data-ttu-id="698e5-193">MDA aktivace může také řízena proměnnou prostředí COMPLUS_MDA, která přepisuje klíč registru.</span><span class="sxs-lookup"><span data-stu-id="698e5-193">MDA activation can also controlled by the environment variable COMPLUS_MDA, which overrides the registry key.</span></span> <span data-ttu-id="698e5-194">Řetězec COMPLUS_MDA je velká a malá písmena, oddělený středníkem seznam názvů (mda) nebo jiné speciální řídicí řetězce.</span><span class="sxs-lookup"><span data-stu-id="698e5-194">The COMPLUS_MDA string is a case-insensitive, semicolon-delimited list of MDA names or other special control strings.</span></span> <span data-ttu-id="698e5-195">Spuštění v rámci spravované nebo nespravované ladicí program umožňuje sadu mda ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="698e5-195">Starting under a managed or unmanaged debugger enables a set of MDAs by default.</span></span> <span data-ttu-id="698e5-196">K tomu je potřeba implicitně předřazení seznam oddělený středníkem mda povolené ve výchozím nastavení v části ladicí programy na hodnotu v prostředí proměnná nebo klíč registru.</span><span class="sxs-lookup"><span data-stu-id="698e5-196">This is done by implicitly prepending the semicolon-delimited list of MDAs enabled by default under debuggers to the value of the environment variable or registry key.</span></span> <span data-ttu-id="698e5-197">Speciální řídicí řetězce jsou následující:</span><span class="sxs-lookup"><span data-stu-id="698e5-197">The special control strings are the following:</span></span>  
  
-   <span data-ttu-id="698e5-198">`0`-Deaktivuje všechny mda.</span><span class="sxs-lookup"><span data-stu-id="698e5-198">`0` - Deactivates all MDAs.</span></span>  
  
-   <span data-ttu-id="698e5-199">`1`-Načte nastavení MDA z *ApplicationName*. mda.config.</span><span class="sxs-lookup"><span data-stu-id="698e5-199">`1` - Reads MDA settings from *ApplicationName*.mda.config.</span></span>  
  
-   <span data-ttu-id="698e5-200">`managedDebugger`– Explicitně aktivuje všechny mda, které jsou aktivované implicitně při spuštění spravované spustitelný soubor v části ladicí program.</span><span class="sxs-lookup"><span data-stu-id="698e5-200">`managedDebugger` - Explicitly activates all MDAs that are implicitly activated when a managed executable is started under a debugger.</span></span>  
  
-   <span data-ttu-id="698e5-201">`unmanagedDebugger`– Explicitně aktivuje všechny mda, které jsou aktivované implicitně při spuštění spustitelného souboru nespravované pod ladicí program.</span><span class="sxs-lookup"><span data-stu-id="698e5-201">`unmanagedDebugger` - Explicitly activates all MDAs that are implicitly activated when an unmanaged executable is started under a debugger.</span></span>  
  
 <span data-ttu-id="698e5-202">Pokud jsou konfliktní nastavení, nejnovější nastavení přepsat předchozí nastavení:</span><span class="sxs-lookup"><span data-stu-id="698e5-202">If there are conflicting settings, the most recent settings override previous settings:</span></span>  
  
-   <span data-ttu-id="698e5-203">`COMPLUS_MDA=0`Zakáže všechny mda, včetně těch, které implicitně povoleno pod ladicí program.</span><span class="sxs-lookup"><span data-stu-id="698e5-203">`COMPLUS_MDA=0` disables all MDAs, including those implicitly enabled under a debugger.</span></span>  
  
-   <span data-ttu-id="698e5-204">`COMPLUS_MDA=gcUnmanagedToManaged`umožňuje `gcUnmanagedToManaged` kromě všech mda, které jsou implicitně povoleny v rámci ladicí program.</span><span class="sxs-lookup"><span data-stu-id="698e5-204">`COMPLUS_MDA=gcUnmanagedToManaged` enables `gcUnmanagedToManaged` in addition to any MDAs that are implicitly enabled under a debugger.</span></span>  
  
-   <span data-ttu-id="698e5-205">`COMPLUS_MDA=0;gcUnmanagedToManaged`umožňuje `gcUnmanagedToManaged` ale zakáže mda, které by jinak implicitně povolit v části ladicí program.</span><span class="sxs-lookup"><span data-stu-id="698e5-205">`COMPLUS_MDA=0;gcUnmanagedToManaged` enables `gcUnmanagedToManaged` but disables MDAs that would otherwise be implicitly enabled under a debugger.</span></span>  
  
<a name="appConfig"></a>   
### <a name="enabling-and-disabling-mdas-by-using-application-specific-configuration-settings"></a><span data-ttu-id="698e5-206">Povolení a zákaz mda pomocí nastavení konfigurace specifické pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="698e5-206">Enabling and Disabling MDAs by Using Application-Specific Configuration Settings</span></span>  
 <span data-ttu-id="698e5-207">Můžete povolit, zakázat a nakonfigurovat některé Pomocníci jednotlivě v konfiguračním souboru (mda) pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="698e5-207">You can enable, disable, and configure some assistants individually in the MDA configuration file for the application.</span></span> <span data-ttu-id="698e5-208">Pokud chcete povolit použití konfiguračního souboru aplikace pro konfiguraci mda, musí být nastavena na klíč registru (mda) nebo proměnná prostředí COMPLUS_MDA.</span><span class="sxs-lookup"><span data-stu-id="698e5-208">To enable the use of an application configuration file for configuring MDAs, either the MDA registry key or the COMPLUS_MDA environment variable must be set.</span></span> <span data-ttu-id="698e5-209">Konfigurační soubor aplikace se obvykle nachází ve stejném adresáři jako spustitelný soubor (.exe) soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="698e5-209">The application configuration file is typically located in the same directory as the application's executable (.exe) file.</span></span> <span data-ttu-id="698e5-210">Název souboru má tvar *ApplicationName*. mda.config, například notepad.exe.mda.config. Pomocníci, které jsou povoleny v konfiguračním souboru aplikace může mít atributy nebo elementy určená speciálně pro řízení chování tohoto pomocníka.</span><span class="sxs-lookup"><span data-stu-id="698e5-210">The file name takes the form *ApplicationName*.mda.config; for example, notepad.exe.mda.config. Assistants that are enabled in the application configuration file may have attributes or elements specifically designed to control that assistant's behavior.</span></span> <span data-ttu-id="698e5-211">Následující příklad ukazuje, jak povolit a nakonfigurovat [zařazování](../../../docs/framework/debug-trace-profile/marshaling-mda.md).</span><span class="sxs-lookup"><span data-stu-id="698e5-211">The following example shows how to enable and configure the [marshaling](../../../docs/framework/debug-trace-profile/marshaling-mda.md).</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshaling>  
      <methodFilter>  
        <match name="*"/>  
      </methodFilter>  
      <fieldFilter>  
        <match name="*"/>  
      </fieldFilter>  
    </marshaling>  
  </assistants>  
</mdaConfig>  
```  
  
 <span data-ttu-id="698e5-212">`Marshaling` MDA vysílá informace o spravovaný typ, který je právě zařazen do nespravovaný typ pro každý Přechod spravované na nespravované v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="698e5-212">The `Marshaling` MDA emits information about the managed type that is being marshaled to an unmanaged type for each managed-to-unmanaged transition in the application.</span></span> <span data-ttu-id="698e5-213">`Marshaling` (Mda) můžete také filtrovat názvy metody a struktura pole zadaná v `<methodFilter>` a `<fieldFilter>` podřízených elementů v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="698e5-213">The `Marshaling` MDA can also filter the names of the method and structure fields supplied in the `<methodFilter>` and `<fieldFilter>` child elements, respectively.</span></span>  
  
 <span data-ttu-id="698e5-214">Následující příklad ukazuje, jak povolit více mda pomocí obnoveno výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="698e5-214">The following example shows how to enable multiple MDAs by using their default settings.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion />  
    <invalidCERCall />  
    <openGenericCERCall />  
    <virtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="698e5-215">Pokud zadáte více než jeden pomocníka v konfiguračním souboru, můžete musí seznam v abecedním pořadí.</span><span class="sxs-lookup"><span data-stu-id="698e5-215">When you specify more than one assistant in a configuration file, you must list them in alphabetical order.</span></span> <span data-ttu-id="698e5-216">Například, pokud chcete povolit i `virtualCERCall` a `invalidCERCall` mda, je nutné přidat `<invalidCERCall />` položka před `<virtualCERCall />` položku.</span><span class="sxs-lookup"><span data-stu-id="698e5-216">For example, if you want to enable both the `virtualCERCall` and the `invalidCERCall` MDAs, you must add the `<invalidCERCall />` entry before the `<virtualCERCall />` entry.</span></span> <span data-ttu-id="698e5-217">Pokud položky nejsou v abecedním pořadí, se zobrazí zpráva o výjimce souboru nezpracované neplatná konfigurace.</span><span class="sxs-lookup"><span data-stu-id="698e5-217">If the entries are not in alphabetical order, an unhandled invalid configuration file exception message is displayed.</span></span>  
  
### <a name="mda-output"></a><span data-ttu-id="698e5-218">Výstup (mda)</span><span class="sxs-lookup"><span data-stu-id="698e5-218">MDA Output</span></span>  
 <span data-ttu-id="698e5-219">MDA výstup se podobá následující příklad, který se zobrazuje výstup z `pInvokeStackImbalance` (mda).</span><span class="sxs-lookup"><span data-stu-id="698e5-219">MDA output is similar to the following example, which shows the output from the `pInvokeStackImbalance` MDA.</span></span>  
  
 `A call to PInvoke function 'MDATest!MDATest.Program::StdCall' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.`  
  
## <a name="see-also"></a><span data-ttu-id="698e5-220">Viz také</span><span class="sxs-lookup"><span data-stu-id="698e5-220">See Also</span></span>  
 [<span data-ttu-id="698e5-221">Ladění, trasování a profilace</span><span class="sxs-lookup"><span data-stu-id="698e5-221">Debugging, Tracing, and Profiling</span></span>](../../../docs/framework/debug-trace-profile/index.md)
