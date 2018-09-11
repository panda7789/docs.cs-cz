---
title: Diagnostikování chyb pomocí asistentů spravovaného ladění
ms.date: 08/14/2018
f1_keywords:
- EHMDA
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b745fa6a78ab2a7ab0b3a94c9921883d3c56c1b7
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44269186"
---
# <a name="diagnose-errors-with-managed-debugging-assistants"></a><span data-ttu-id="429ca-102">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="429ca-102">Diagnose Errors with Managed Debugging Assistants</span></span>

<span data-ttu-id="429ca-103">Spravované Asistenti ladění (mda) jsou pomůcky pro ladění, které fungují ve spojení s modul CLR (CLR), která poskytují informace o stavu modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="429ca-103">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span> <span data-ttu-id="429ca-104">Asistentů generovat informační zprávy o událostech modulu runtime, které nelze zachytit jinak.</span><span class="sxs-lookup"><span data-stu-id="429ca-104">The assistants generate informational messages about runtime events that you cannot otherwise trap.</span></span> <span data-ttu-id="429ca-105">Mda můžete použít k izolování aplikace obtížné najít chyby, ke kterým dochází při přechodu mezi spravovaným a nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="429ca-105">You can use MDAs to isolate hard-to-find application bugs that occur when transitioning between managed and unmanaged code.</span></span>

<span data-ttu-id="429ca-106">Je možné [povolit nebo zakázat](#enable-and-disable-mdas) všechny mda přidání klíče registru Windows nebo nastavením proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="429ca-106">You can [enable or disable](#enable-and-disable-mdas) all MDAs by adding a key to the Windows registry or by setting an environment variable.</span></span> <span data-ttu-id="429ca-107">Konkrétní mda můžete povolit pomocí nastavení konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="429ca-107">You can enable specific MDAs by using application configuration settings.</span></span> <span data-ttu-id="429ca-108">Další nastavení konfigurace pro některé jednotlivých mda můžete nastavit v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="429ca-108">You can set additional configuration settings for some individual MDAs in the application's configuration file.</span></span> <span data-ttu-id="429ca-109">Protože tyto konfigurační soubory jsou analyzovány při načtení modulu runtime, je nutné povolit MDA před spuštěním spravované aplikace.</span><span class="sxs-lookup"><span data-stu-id="429ca-109">Because these configuration files are parsed when the runtime is loaded, you must enable the MDA before the managed application starts.</span></span> <span data-ttu-id="429ca-110">Nelze ji povolit pro aplikace, které jste už začali.</span><span class="sxs-lookup"><span data-stu-id="429ca-110">You cannot enable it for applications that have already started.</span></span>

<span data-ttu-id="429ca-111">V následující tabulce jsou uvedeny mda, které se dodávají s rozhraním .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="429ca-111">The following table lists the MDAs that ship with the .NET Framework:</span></span>

|||
|-|-|
|[<span data-ttu-id="429ca-112">asynchronousThreadAbort</span><span class="sxs-lookup"><span data-stu-id="429ca-112">asynchronousThreadAbort</span></span>](../../../docs/framework/debug-trace-profile/asynchronousthreadabort-mda.md)|[<span data-ttu-id="429ca-113">bindingFailure</span><span class="sxs-lookup"><span data-stu-id="429ca-113">bindingFailure</span></span>](../../../docs/framework/debug-trace-profile/bindingfailure-mda.md)|
|[<span data-ttu-id="429ca-114">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="429ca-114">callbackOnCollectedDelegate</span></span>](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)|[<span data-ttu-id="429ca-115">contextSwitchDeadlock</span><span class="sxs-lookup"><span data-stu-id="429ca-115">contextSwitchDeadlock</span></span>](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md)|
|[<span data-ttu-id="429ca-116">dangerousThreadingAPI</span><span class="sxs-lookup"><span data-stu-id="429ca-116">dangerousThreadingAPI</span></span>](../../../docs/framework/debug-trace-profile/dangerousthreadingapi-mda.md)|[<span data-ttu-id="429ca-117">dateTimeInvalidLocalFormat</span><span class="sxs-lookup"><span data-stu-id="429ca-117">dateTimeInvalidLocalFormat</span></span>](../../../docs/framework/debug-trace-profile/datetimeinvalidlocalformat-mda.md)|
|[<span data-ttu-id="429ca-118">dirtyCastAndCallOnInterface</span><span class="sxs-lookup"><span data-stu-id="429ca-118">dirtyCastAndCallOnInterface</span></span>](../../../docs/framework/debug-trace-profile/dirtycastandcalloninterface-mda.md)|[<span data-ttu-id="429ca-119">disconnectedContext</span><span class="sxs-lookup"><span data-stu-id="429ca-119">disconnectedContext</span></span>](../../../docs/framework/debug-trace-profile/disconnectedcontext-mda.md)|
|[<span data-ttu-id="429ca-120">dllMainReturnsFalse</span><span class="sxs-lookup"><span data-stu-id="429ca-120">dllMainReturnsFalse</span></span>](../../../docs/framework/debug-trace-profile/dllmainreturnsfalse-mda.md)|[<span data-ttu-id="429ca-121">exceptionSwallowedOnCallFromCom</span><span class="sxs-lookup"><span data-stu-id="429ca-121">exceptionSwallowedOnCallFromCom</span></span>](../../../docs/framework/debug-trace-profile/exceptionswallowedoncallfromcom-mda.md)|
|[<span data-ttu-id="429ca-122">failedQI</span><span class="sxs-lookup"><span data-stu-id="429ca-122">failedQI</span></span>](../../../docs/framework/debug-trace-profile/failedqi-mda.md)|[<span data-ttu-id="429ca-123">fatalExecutionEngineError</span><span class="sxs-lookup"><span data-stu-id="429ca-123">fatalExecutionEngineError</span></span>](../../../docs/framework/debug-trace-profile/fatalexecutionengineerror-mda.md)|
|[<span data-ttu-id="429ca-124">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="429ca-124">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)|[<span data-ttu-id="429ca-125">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="429ca-125">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)|
|[<span data-ttu-id="429ca-126">illegalPrepareConstrainedRegion</span><span class="sxs-lookup"><span data-stu-id="429ca-126">illegalPrepareConstrainedRegion</span></span>](../../../docs/framework/debug-trace-profile/illegalprepareconstrainedregion-mda.md)|[<span data-ttu-id="429ca-127">invalidApartmentStateChange</span><span class="sxs-lookup"><span data-stu-id="429ca-127">invalidApartmentStateChange</span></span>](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md)|
|[<span data-ttu-id="429ca-128">invalidCERCall</span><span class="sxs-lookup"><span data-stu-id="429ca-128">invalidCERCall</span></span>](../../../docs/framework/debug-trace-profile/invalidcercall-mda.md)|[<span data-ttu-id="429ca-129">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="429ca-129">invalidFunctionPointerInDelegate</span></span>](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)|
|[<span data-ttu-id="429ca-130">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="429ca-130">invalidGCHandleCookie</span></span>](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)|[<span data-ttu-id="429ca-131">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="429ca-131">invalidIUnknown</span></span>](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)|
|[<span data-ttu-id="429ca-132">invalidMemberDeclaration</span><span class="sxs-lookup"><span data-stu-id="429ca-132">invalidMemberDeclaration</span></span>](../../../docs/framework/debug-trace-profile/invalidmemberdeclaration-mda.md)|[<span data-ttu-id="429ca-133">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="429ca-133">invalidOverlappedToPinvoke</span></span>](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)|
|[<span data-ttu-id="429ca-134">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="429ca-134">invalidVariant</span></span>](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)|[<span data-ttu-id="429ca-135">jitCompilationStart</span><span class="sxs-lookup"><span data-stu-id="429ca-135">jitCompilationStart</span></span>](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md)|
|[<span data-ttu-id="429ca-136">loaderLock</span><span class="sxs-lookup"><span data-stu-id="429ca-136">loaderLock</span></span>](../../../docs/framework/debug-trace-profile/loaderlock-mda.md)|[<span data-ttu-id="429ca-137">loadFromContext</span><span class="sxs-lookup"><span data-stu-id="429ca-137">loadFromContext</span></span>](../../../docs/framework/debug-trace-profile/loadfromcontext-mda.md)|
|[<span data-ttu-id="429ca-138">marshalCleanupError</span><span class="sxs-lookup"><span data-stu-id="429ca-138">marshalCleanupError</span></span>](../../../docs/framework/debug-trace-profile/marshalcleanuperror-mda.md)|[<span data-ttu-id="429ca-139">marshaling</span><span class="sxs-lookup"><span data-stu-id="429ca-139">marshaling</span></span>](../../../docs/framework/debug-trace-profile/marshaling-mda.md)|
|[<span data-ttu-id="429ca-140">memberInfoCacheCreation</span><span class="sxs-lookup"><span data-stu-id="429ca-140">memberInfoCacheCreation</span></span>](../../../docs/framework/debug-trace-profile/memberinfocachecreation-mda.md)|[<span data-ttu-id="429ca-141">moduloObjectHashcode</span><span class="sxs-lookup"><span data-stu-id="429ca-141">moduloObjectHashcode</span></span>](../../../docs/framework/debug-trace-profile/moduloobjecthashcode-mda.md)|
|[<span data-ttu-id="429ca-142">nonComVisibleBaseClass</span><span class="sxs-lookup"><span data-stu-id="429ca-142">nonComVisibleBaseClass</span></span>](../../../docs/framework/debug-trace-profile/noncomvisiblebaseclass-mda.md)|[<span data-ttu-id="429ca-143">notMarshalable</span><span class="sxs-lookup"><span data-stu-id="429ca-143">notMarshalable</span></span>](../../../docs/framework/debug-trace-profile/notmarshalable-mda.md)|
|[<span data-ttu-id="429ca-144">openGenericCERCall</span><span class="sxs-lookup"><span data-stu-id="429ca-144">openGenericCERCall</span></span>](../../../docs/framework/debug-trace-profile/opengenericcercall-mda.md)|[<span data-ttu-id="429ca-145">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="429ca-145">overlappedFreeError</span></span>](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)|
|[<span data-ttu-id="429ca-146">pInvokeLog</span><span class="sxs-lookup"><span data-stu-id="429ca-146">pInvokeLog</span></span>](../../../docs/framework/debug-trace-profile/pinvokelog-mda.md)|[<span data-ttu-id="429ca-147">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="429ca-147">pInvokeStackImbalance</span></span>](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)|
|[<span data-ttu-id="429ca-148">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="429ca-148">raceOnRCWCleanup</span></span>](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)|[<span data-ttu-id="429ca-149">reentrancy</span><span class="sxs-lookup"><span data-stu-id="429ca-149">reentrancy</span></span>](../../../docs/framework/debug-trace-profile/reentrancy-mda.md)|
|[<span data-ttu-id="429ca-150">releaseHandleFailed</span><span class="sxs-lookup"><span data-stu-id="429ca-150">releaseHandleFailed</span></span>](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md)|[<span data-ttu-id="429ca-151">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="429ca-151">reportAvOnComRelease</span></span>](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)|
|[<span data-ttu-id="429ca-152">streamWriterBufferedDataLost</span><span class="sxs-lookup"><span data-stu-id="429ca-152">streamWriterBufferedDataLost</span></span>](../../../docs/framework/debug-trace-profile/streamwriterbuffereddatalost-mda.md)|[<span data-ttu-id="429ca-153">virtualCERCall</span><span class="sxs-lookup"><span data-stu-id="429ca-153">virtualCERCall</span></span>](../../../docs/framework/debug-trace-profile/virtualcercall-mda.md)|

<span data-ttu-id="429ca-154">Ve výchozím nastavení aktivuje rozhraní .NET Framework podmnožinu mda pro všechny spravované ladicí programy.</span><span class="sxs-lookup"><span data-stu-id="429ca-154">By default, the .NET Framework activates a subset of MDAs for all managed debuggers.</span></span> <span data-ttu-id="429ca-155">Můžete zobrazit výchozí nastavení v sadě Visual Studio výběrem **Windows** > **nastavení výjimek** na **ladění** nabídky a pak rozšiřuje **Asistentů spravovaného ladění** seznamu.</span><span class="sxs-lookup"><span data-stu-id="429ca-155">You can view the default set in Visual Studio by choosing **Windows** > **Exception Settings** on the **Debug** menu, and then expanding the **Managed Debugging Assistants** list.</span></span>

![Okno pro nastavení výjimek v sadě Visual Studio](media/diagnosing-errors-with-managed-debugging-assistants/exception-settings-mdas.png)

## <a name="enable-and-disable-mdas"></a><span data-ttu-id="429ca-157">Povolení a zakázání mda</span><span class="sxs-lookup"><span data-stu-id="429ca-157">Enable and Disable MDAs</span></span>

<span data-ttu-id="429ca-158">Můžete povolit nebo zakázat mda pomocí klíče registru, proměnné prostředí a nastavení konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="429ca-158">You can enable and disable MDAs by using a registry key, an environment variable, and application configuration settings.</span></span> <span data-ttu-id="429ca-159">Povolte klíč registru nebo proměnné prostředí použít nastavení konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="429ca-159">You must enable either the registry key or the environment variable to use the application configuration settings.</span></span>

> [!TIP]
> <span data-ttu-id="429ca-160">Místo zákaz mda, můžete sady Visual Studio zabránit v zobrazování dialogových oken MDA při každém přijetí oznámení o MDA.</span><span class="sxs-lookup"><span data-stu-id="429ca-160">Instead of disabling MDAs, you can prevent Visual Studio from displaying the MDA dialog box whenever an MDA notification is received.</span></span> <span data-ttu-id="429ca-161">Chcete-li to mohli udělat, zvolte **Windows** > **nastavení výjimek** na **ladění** nabídky, rozbalte **spravované ladění Asistenti**seznamu a pak zaškrtněte nebo zrušte **přerušení při vyvolání** zaškrtávací políčko pro jednotlivé MDA.</span><span class="sxs-lookup"><span data-stu-id="429ca-161">To do that, choose **Windows** > **Exception Settings** on the **Debug** menu, expand the **Managed Debugging Assistants** list, and then select or clear the **Break When Thrown** check box for the individual MDA.</span></span>

### <a name="registry-key"></a><span data-ttu-id="429ca-162">Klíč registru</span><span class="sxs-lookup"><span data-stu-id="429ca-162">Registry Key</span></span>

<span data-ttu-id="429ca-163">Chcete-li povolit mda, přidejte **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\MDA** podklíč (typ REG_SZ, hodnota 1) v registru Windows.</span><span class="sxs-lookup"><span data-stu-id="429ca-163">To enable MDAs, add the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\MDA** subkey (type REG_SZ, value 1) in the Windows registry.</span></span> <span data-ttu-id="429ca-164">Následující příklad zkopírujte do textového souboru s názvem *MDAEnable.reg*. Otevřete Editor registru (RegEdit.exe), Windows a **souboru** nabídku zvolte **Import**.</span><span class="sxs-lookup"><span data-stu-id="429ca-164">Copy the following example into a text file named *MDAEnable.reg*. Open the Windows Registry Editor (RegEdit.exe), and from the **File** menu choose **Import**.</span></span> <span data-ttu-id="429ca-165">Vyberte *MDAEnable.reg* souboru mda na tomto počítači.</span><span class="sxs-lookup"><span data-stu-id="429ca-165">Select the *MDAEnable.reg* file to enable MDAs on that computer.</span></span> <span data-ttu-id="429ca-166">Nastavení podklíče na hodnotu řetězce **1** (nikoli hodnotu DWORD s názvem **1**) povolí čtení nastavení MDA ze *ApplicationName.suffix*. mda.config souboru.</span><span class="sxs-lookup"><span data-stu-id="429ca-166">Setting the subkey to string value of **1** (not DWORD value of **1**) enables the reading of MDA settings from the *ApplicationName.suffix*.mda.config file.</span></span> <span data-ttu-id="429ca-167">Například konfigurační soubor MDA pro poznámkový blok by se pojmenoval notepad.exe.mda.config.</span><span class="sxs-lookup"><span data-stu-id="429ca-167">For example, the MDA configuration file for Notepad would be named notepad.exe.mda.config.</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="429ca-168">Pokud počítači běží 32bitová aplikace na 64bitový operační systém, by měl vypadat asi takto nastaven klíč MDA:</span><span class="sxs-lookup"><span data-stu-id="429ca-168">If the computer is running a 32-bit application on a 64-bit operating system, then the MDA key should be set like the following:</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="429ca-169">Zobrazit [nastavení konfigurace specifické pro aplikaci](#application-specific-configuration-settings) Další informace.</span><span class="sxs-lookup"><span data-stu-id="429ca-169">See [Application-Specific Configuration Settings](#application-specific-configuration-settings) for more information.</span></span> <span data-ttu-id="429ca-170">Nastavení registru mohou být přepsány COMPLUS_MDA proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="429ca-170">The registry setting can be overridden by the COMPLUS_MDA environment variable.</span></span> <span data-ttu-id="429ca-171">Zobrazit [proměnné prostředí](#environment-variable) Další informace.</span><span class="sxs-lookup"><span data-stu-id="429ca-171">See [Environment Variable](#environment-variable) for more information.</span></span>

<span data-ttu-id="429ca-172">Mda zakázat, nastavte na podklíč MDA **0** (nula) pomocí Editoru registru Windows.</span><span class="sxs-lookup"><span data-stu-id="429ca-172">To disable MDAs, set the MDA subkey to **0** (zero) using the Windows Registry Editor.</span></span>

<span data-ttu-id="429ca-173">Ve výchozím nastavení jsou některé mda povoleny při spuštění aplikace, která je připojena k ladicímu programu, i bez přidání klíče registru.</span><span class="sxs-lookup"><span data-stu-id="429ca-173">By default, some MDAs are enabled when you run an application that is attached to a debugger, even without adding the registry key.</span></span> <span data-ttu-id="429ca-174">Můžete zakázat tyto Asistenti spuštěním *MDADisable.reg* souboru, jak je popsáno výše v této části.</span><span class="sxs-lookup"><span data-stu-id="429ca-174">You can disable these assistants by running the *MDADisable.reg* file as described earlier in this section.</span></span>

### <a name="environment-variable"></a><span data-ttu-id="429ca-175">Proměnná prostředí</span><span class="sxs-lookup"><span data-stu-id="429ca-175">Environment Variable</span></span>

<span data-ttu-id="429ca-176">Aktivace MDA lze také ovládat proměnnou prostředí COMPLUS_MDA, která přepisuje klíč registru.</span><span class="sxs-lookup"><span data-stu-id="429ca-176">MDA activation can also controlled by the environment variable COMPLUS_MDA, which overrides the registry key.</span></span> <span data-ttu-id="429ca-177">Řetězec COMPLUS_MDA je velká a malá písmena, oddělené středníky seznam názvů MDA nebo jiné speciální řídicí řetězce.</span><span class="sxs-lookup"><span data-stu-id="429ca-177">The COMPLUS_MDA string is a case-insensitive, semicolon-delimited list of MDA names or other special control strings.</span></span> <span data-ttu-id="429ca-178">Spouštění v ladicím programu spravované nebo nespravované povoluje sadu mda ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="429ca-178">Starting under a managed or unmanaged debugger enables a set of MDAs by default.</span></span> <span data-ttu-id="429ca-179">To se provádí implicitně předponou v podobě seznam oddělený středníkem mda povolená ve výchozím nastavení v části ladicích programů na hodnotu proměnné nebo registru klíč prostředí.</span><span class="sxs-lookup"><span data-stu-id="429ca-179">This is done by implicitly prepending the semicolon-delimited list of MDAs enabled by default under debuggers to the value of the environment variable or registry key.</span></span> <span data-ttu-id="429ca-180">Speciální řídicí řetězce jsou následující:</span><span class="sxs-lookup"><span data-stu-id="429ca-180">The special control strings are the following:</span></span>

- <span data-ttu-id="429ca-181">`0` -Deaktivuje všechny mda.</span><span class="sxs-lookup"><span data-stu-id="429ca-181">`0` - Deactivates all MDAs.</span></span>

- <span data-ttu-id="429ca-182">`1` -Načte nastavení MDA ze *ApplicationName*. mda.config.</span><span class="sxs-lookup"><span data-stu-id="429ca-182">`1` - Reads MDA settings from *ApplicationName*.mda.config.</span></span>

- <span data-ttu-id="429ca-183">`managedDebugger` -Explicitně aktivuje všechny mda, které jsou aktivovány implicitně při spuštění spravovaného spustitelný soubor v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="429ca-183">`managedDebugger` - Explicitly activates all MDAs that are implicitly activated when a managed executable is started under a debugger.</span></span>

- <span data-ttu-id="429ca-184">`unmanagedDebugger` -Explicitně aktivuje všechny mda, které jsou aktivované implicitně, když se spustí spustitelný soubor nespravované v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="429ca-184">`unmanagedDebugger` - Explicitly activates all MDAs that are implicitly activated when an unmanaged executable is started under a debugger.</span></span>

<span data-ttu-id="429ca-185">Pokud konfliktní nastavení se nejnovější nastavení přepíše předchozí nastavení:</span><span class="sxs-lookup"><span data-stu-id="429ca-185">If there are conflicting settings, the most recent settings override previous settings:</span></span>

- <span data-ttu-id="429ca-186">`COMPLUS_MDA=0` Zakáže všechny mda, včetně těch, které implicitně povoleno v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="429ca-186">`COMPLUS_MDA=0` disables all MDAs, including those implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="429ca-187">`COMPLUS_MDA=gcUnmanagedToManaged` umožňuje `gcUnmanagedToManaged` kromě jakékoli mda, u kterých jde implicitně v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="429ca-187">`COMPLUS_MDA=gcUnmanagedToManaged` enables `gcUnmanagedToManaged` in addition to any MDAs that are implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="429ca-188">`COMPLUS_MDA=0;gcUnmanagedToManaged` umožňuje `gcUnmanagedToManaged` ale zakáže mda, které by jinak implicitně povoleno v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="429ca-188">`COMPLUS_MDA=0;gcUnmanagedToManaged` enables `gcUnmanagedToManaged` but disables MDAs that would otherwise be implicitly enabled under a debugger.</span></span>

### <a name="application-specific-configuration-settings"></a><span data-ttu-id="429ca-189">Nastavení konfigurace specifické pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="429ca-189">Application-Specific Configuration Settings</span></span>

<span data-ttu-id="429ca-190">Můžete povolit, zakázat a nakonfigurovat některé Asistenti jednotlivě v konfiguračním souboru MDA pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="429ca-190">You can enable, disable, and configure some assistants individually in the MDA configuration file for the application.</span></span> <span data-ttu-id="429ca-191">Pokud chcete povolit použití konfiguračního souboru aplikace pro konfiguraci mda, musí být nastavena MDA klíč registru nebo COMPLUS_MDA proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="429ca-191">To enable the use of an application configuration file for configuring MDAs, either the MDA registry key or the COMPLUS_MDA environment variable must be set.</span></span> <span data-ttu-id="429ca-192">Konfigurační soubor aplikace je obvykle umístěn ve stejném adresáři jako spustitelný soubor (.exe) soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="429ca-192">The application configuration file is typically located in the same directory as the application's executable (.exe) file.</span></span> <span data-ttu-id="429ca-193">Název souboru má podobu *ApplicationName*. mda.config, například notepad.exe.mda.config. Pomocníci, které jsou povoleny v konfiguračním souboru aplikace může mít atributy nebo elementy speciálně pro řízení chování této Pomocníka s nastavením.</span><span class="sxs-lookup"><span data-stu-id="429ca-193">The file name takes the form *ApplicationName*.mda.config; for example, notepad.exe.mda.config. Assistants that are enabled in the application configuration file may have attributes or elements specifically designed to control that assistant's behavior.</span></span>

<span data-ttu-id="429ca-194">Následující příklad ukazuje, jak povolit a konfigurovat [zařazování](../../../docs/framework/debug-trace-profile/marshaling-mda.md):</span><span class="sxs-lookup"><span data-stu-id="429ca-194">The following example shows how to enable and configure the [marshaling](../../../docs/framework/debug-trace-profile/marshaling-mda.md):</span></span>

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

<span data-ttu-id="429ca-195">`Marshaling` MDA generuje informace o spravovaný typ, který je právě zařazení na nespravovaný typ pro každý Přechod spravované na nespravované aplikace.</span><span class="sxs-lookup"><span data-stu-id="429ca-195">The `Marshaling` MDA emits information about the managed type that is being marshaled to an unmanaged type for each managed-to-unmanaged transition in the application.</span></span> <span data-ttu-id="429ca-196">`Marshaling` MDA můžete také filtrovat názvy metody a pole struktury zadat v **methodFilter** a **fieldFilter** podřízené prvky v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="429ca-196">The `Marshaling` MDA can also filter the names of the method and structure fields supplied in the **methodFilter** and **fieldFilter** child elements, respectively.</span></span>

<span data-ttu-id="429ca-197">Následující příklad ukazuje, jak povolit více mda pomocí jejich výchozí nastavení:</span><span class="sxs-lookup"><span data-stu-id="429ca-197">The following example shows how to enable multiple MDAs by using their default settings:</span></span>

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
> <span data-ttu-id="429ca-198">Pokud zadáte více než jeden Pomocníka s nastavením v konfiguračním souboru, uveďte je v abecedním pořadí.</span><span class="sxs-lookup"><span data-stu-id="429ca-198">When you specify more than one assistant in a configuration file, you must list them in alphabetical order.</span></span> <span data-ttu-id="429ca-199">Například, pokud chcete povolit obě `virtualCERCall` a `invalidCERCall` mda, je nutné přidat `<invalidCERCall />` položka před `<virtualCERCall />` položka.</span><span class="sxs-lookup"><span data-stu-id="429ca-199">For example, if you want to enable both the `virtualCERCall` and the `invalidCERCall` MDAs, you must add the `<invalidCERCall />` entry before the `<virtualCERCall />` entry.</span></span> <span data-ttu-id="429ca-200">Pokud záznamy nejsou v abecedním pořadí, zobrazí se zprávou výjimky neošetřené neplatnou konfigurací souboru.</span><span class="sxs-lookup"><span data-stu-id="429ca-200">If the entries are not in alphabetical order, an unhandled invalid configuration file exception message is displayed.</span></span>

## <a name="mda-exceptions"></a><span data-ttu-id="429ca-201">Výjimky MDA</span><span class="sxs-lookup"><span data-stu-id="429ca-201">MDA exceptions</span></span>

<span data-ttu-id="429ca-202">Pokud je povolena MDA, je aktivní i když váš kód neprobíhá v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="429ca-202">When an MDA is enabled, it's active even when your code is not executing under a debugger.</span></span> <span data-ttu-id="429ca-203">Pokud MDA událost se vyvolá, když ladicí program není k dispozici, zpráva o události se zobrazí v dialogovém okně neošetřenou výjimku, i když není k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="429ca-203">If an MDA event is raised when a debugger is not present, the event message is presented in an unhandled exception dialog box, although it is not an unhandled exception.</span></span> <span data-ttu-id="429ca-204">Aby se zabránilo dialogových oken, odeberte nastavení MDA povolení při není provádění kódu v prostředí ladění.</span><span class="sxs-lookup"><span data-stu-id="429ca-204">To avoid the dialog box, remove the MDA-enabling settings when your code is not executing in a debugging environment.</span></span>

<span data-ttu-id="429ca-205">Když se spustí váš kód v sadě Visual Studio integrované vývojové prostředí (IDE), se můžete vyhnout, který se zobrazí pro konkrétní události MDA dialogovém okně výjimky.</span><span class="sxs-lookup"><span data-stu-id="429ca-205">When your code executes in the Visual Studio integrated development environment (IDE), you can avoid the exception dialog box that appears for specific MDA events.</span></span> <span data-ttu-id="429ca-206">K tomu, na **ladění** nabídce zvolte **Windows** > **nastavení výjimek**.</span><span class="sxs-lookup"><span data-stu-id="429ca-206">To do that, on the **Debug** menu, choose **Windows** > **Exception Settings**.</span></span> <span data-ttu-id="429ca-207">V **nastavení výjimek** okna, rozbalte **asistentů spravovaného ladění** seznamu a poté zrušte zaškrtnutí **přerušení při vyvolání** zaškrtávací políčko pro jednotlivé MDA.</span><span class="sxs-lookup"><span data-stu-id="429ca-207">In the **Exception Settings** window, expand the **Managed Debugging Assistants** list, and then clear the **Break When Thrown** check box for the individual MDA.</span></span> <span data-ttu-id="429ca-208">Můžete také použít dialogové okno k *povolit* zobrazení MDA výjimka dialogových oknech.</span><span class="sxs-lookup"><span data-stu-id="429ca-208">You can also use this dialog box to *enable* the display of MDA exception dialog boxes.</span></span>

## <a name="mda-output"></a><span data-ttu-id="429ca-209">Výstup MDA</span><span class="sxs-lookup"><span data-stu-id="429ca-209">MDA Output</span></span>

<span data-ttu-id="429ca-210">MDA výstup je podobný následujícím příkladu, který se zobrazuje výstup z `PInvokeStackImbalance` MDA:</span><span class="sxs-lookup"><span data-stu-id="429ca-210">MDA output is similar to the following example, which shows the output from the `PInvokeStackImbalance` MDA:</span></span>

<span data-ttu-id="429ca-211">**Volání funkce PInvoke "MDATest! MDATest.Program::StdCall' má nevyvážená zásobníku. To je pravděpodobné, protože spravovaný podpis PInvoke neodpovídá nespravovanému cílovému podpisu. Zkontrolujte, jestli se konvence volání a parametry podpisu PInvoke odpovídají cílovému nespravovanému podpisu.**</span><span class="sxs-lookup"><span data-stu-id="429ca-211">**A call to PInvoke function 'MDATest!MDATest.Program::StdCall' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.**</span></span>

## <a name="see-also"></a><span data-ttu-id="429ca-212">Viz také:</span><span class="sxs-lookup"><span data-stu-id="429ca-212">See also</span></span>

- [<span data-ttu-id="429ca-213">Ladění, trasování a profilace</span><span class="sxs-lookup"><span data-stu-id="429ca-213">Debugging, Tracing, and Profiling</span></span>](../../../docs/framework/debug-trace-profile/index.md)
