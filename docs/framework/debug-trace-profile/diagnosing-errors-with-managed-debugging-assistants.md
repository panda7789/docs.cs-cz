---
title: Diagnostikování chyb pomocí asistentů spravovaného ladění
description: Diagnostikujte chyby v .NET pomocí asistentů spravovaného ladění. MDA jsou pomocné pomůcky při spolupráci s CLR a poskytují běhové informace o stavu.
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
ms.openlocfilehash: ac6fdc09fb057cc55659ce076d37ab96fe2354d1
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416093"
---
# <a name="diagnose-errors-with-managed-debugging-assistants"></a><span data-ttu-id="fad5b-104">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="fad5b-104">Diagnose Errors with Managed Debugging Assistants</span></span>

<span data-ttu-id="fad5b-105">Asistenti spravovaného ladění (MDA) jsou pomůcky pro ladění, které spolupracují s modulem CLR (Common Language Runtime) k poskytování informací o stavu modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="fad5b-105">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span> <span data-ttu-id="fad5b-106">Pomocníci generují informativní zprávy o událostech modulu runtime, které nemůžete jinak zachytávat.</span><span class="sxs-lookup"><span data-stu-id="fad5b-106">The assistants generate informational messages about runtime events that you cannot otherwise trap.</span></span> <span data-ttu-id="fad5b-107">MDA můžete použít k izolaci chyb aplikace, ke kterým dochází při přechodu mezi spravovaným a nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="fad5b-107">You can use MDAs to isolate hard-to-find application bugs that occur when transitioning between managed and unmanaged code.</span></span>

<span data-ttu-id="fad5b-108">Všechny MDA můžete [Povolit nebo zakázat](#enable-and-disable-mdas) přidáním klíče do registru systému Windows nebo nastavením proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="fad5b-108">You can [enable or disable](#enable-and-disable-mdas) all MDAs by adding a key to the Windows registry or by setting an environment variable.</span></span> <span data-ttu-id="fad5b-109">Můžete povolit konkrétní MDA pomocí nastavení konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="fad5b-109">You can enable specific MDAs by using application configuration settings.</span></span> <span data-ttu-id="fad5b-110">V konfiguračním souboru aplikace můžete nastavit další nastavení konfigurace pro konkrétní MDA.</span><span class="sxs-lookup"><span data-stu-id="fad5b-110">You can set additional configuration settings for some individual MDAs in the application's configuration file.</span></span> <span data-ttu-id="fad5b-111">Vzhledem k tomu, že jsou tyto konfigurační soubory analyzovány při načtení modulu runtime, je nutné povolit modul MDA před spuštěním spravované aplikace.</span><span class="sxs-lookup"><span data-stu-id="fad5b-111">Because these configuration files are parsed when the runtime is loaded, you must enable the MDA before the managed application starts.</span></span> <span data-ttu-id="fad5b-112">Nemůžete ho povolit pro aplikace, které už jsou spuštěné.</span><span class="sxs-lookup"><span data-stu-id="fad5b-112">You cannot enable it for applications that have already started.</span></span>

<span data-ttu-id="fad5b-113">V následující tabulce jsou uvedeny Mday dodávané s .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="fad5b-113">The following table lists the MDAs that ship with the .NET Framework:</span></span>

|||
|-|-|
|[<span data-ttu-id="fad5b-114">asynchronousThreadAbort</span><span class="sxs-lookup"><span data-stu-id="fad5b-114">asynchronousThreadAbort</span></span>](asynchronousthreadabort-mda.md)|[<span data-ttu-id="fad5b-115">bindingFailure</span><span class="sxs-lookup"><span data-stu-id="fad5b-115">bindingFailure</span></span>](bindingfailure-mda.md)|
|[<span data-ttu-id="fad5b-116">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="fad5b-116">callbackOnCollectedDelegate</span></span>](callbackoncollecteddelegate-mda.md)|[<span data-ttu-id="fad5b-117">contextSwitchDeadlock</span><span class="sxs-lookup"><span data-stu-id="fad5b-117">contextSwitchDeadlock</span></span>](contextswitchdeadlock-mda.md)|
|[<span data-ttu-id="fad5b-118">dangerousThreadingAPI</span><span class="sxs-lookup"><span data-stu-id="fad5b-118">dangerousThreadingAPI</span></span>](dangerousthreadingapi-mda.md)|[<span data-ttu-id="fad5b-119">dateTimeInvalidLocalFormat</span><span class="sxs-lookup"><span data-stu-id="fad5b-119">dateTimeInvalidLocalFormat</span></span>](datetimeinvalidlocalformat-mda.md)|
|[<span data-ttu-id="fad5b-120">dirtyCastAndCallOnInterface</span><span class="sxs-lookup"><span data-stu-id="fad5b-120">dirtyCastAndCallOnInterface</span></span>](dirtycastandcalloninterface-mda.md)|[<span data-ttu-id="fad5b-121">disconnectedContext</span><span class="sxs-lookup"><span data-stu-id="fad5b-121">disconnectedContext</span></span>](disconnectedcontext-mda.md)|
|[<span data-ttu-id="fad5b-122">dllMainReturnsFalse</span><span class="sxs-lookup"><span data-stu-id="fad5b-122">dllMainReturnsFalse</span></span>](dllmainreturnsfalse-mda.md)|[<span data-ttu-id="fad5b-123">exceptionSwallowedOnCallFromCom</span><span class="sxs-lookup"><span data-stu-id="fad5b-123">exceptionSwallowedOnCallFromCom</span></span>](exceptionswallowedoncallfromcom-mda.md)|
|[<span data-ttu-id="fad5b-124">failedQI</span><span class="sxs-lookup"><span data-stu-id="fad5b-124">failedQI</span></span>](failedqi-mda.md)|[<span data-ttu-id="fad5b-125">fatalExecutionEngineError</span><span class="sxs-lookup"><span data-stu-id="fad5b-125">fatalExecutionEngineError</span></span>](fatalexecutionengineerror-mda.md)|
|[<span data-ttu-id="fad5b-126">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="fad5b-126">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)|[<span data-ttu-id="fad5b-127">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="fad5b-127">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)|
|[<span data-ttu-id="fad5b-128">illegalPrepareConstrainedRegion</span><span class="sxs-lookup"><span data-stu-id="fad5b-128">illegalPrepareConstrainedRegion</span></span>](illegalprepareconstrainedregion-mda.md)|[<span data-ttu-id="fad5b-129">invalidApartmentStateChange</span><span class="sxs-lookup"><span data-stu-id="fad5b-129">invalidApartmentStateChange</span></span>](invalidapartmentstatechange-mda.md)|
|[<span data-ttu-id="fad5b-130">invalidCERCall</span><span class="sxs-lookup"><span data-stu-id="fad5b-130">invalidCERCall</span></span>](invalidcercall-mda.md)|[<span data-ttu-id="fad5b-131">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="fad5b-131">invalidFunctionPointerInDelegate</span></span>](invalidfunctionpointerindelegate-mda.md)|
|[<span data-ttu-id="fad5b-132">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="fad5b-132">invalidGCHandleCookie</span></span>](invalidgchandlecookie-mda.md)|[<span data-ttu-id="fad5b-133">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="fad5b-133">invalidIUnknown</span></span>](invalidiunknown-mda.md)|
|[<span data-ttu-id="fad5b-134">invalidMemberDeclaration</span><span class="sxs-lookup"><span data-stu-id="fad5b-134">invalidMemberDeclaration</span></span>](invalidmemberdeclaration-mda.md)|[<span data-ttu-id="fad5b-135">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="fad5b-135">invalidOverlappedToPinvoke</span></span>](invalidoverlappedtopinvoke-mda.md)|
|[<span data-ttu-id="fad5b-136">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="fad5b-136">invalidVariant</span></span>](invalidvariant-mda.md)|[<span data-ttu-id="fad5b-137">jitCompilationStart</span><span class="sxs-lookup"><span data-stu-id="fad5b-137">jitCompilationStart</span></span>](jitcompilationstart-mda.md)|
|[<span data-ttu-id="fad5b-138">loaderLock</span><span class="sxs-lookup"><span data-stu-id="fad5b-138">loaderLock</span></span>](loaderlock-mda.md)|[<span data-ttu-id="fad5b-139">loadFromContext</span><span class="sxs-lookup"><span data-stu-id="fad5b-139">loadFromContext</span></span>](loadfromcontext-mda.md)|
|[<span data-ttu-id="fad5b-140">marshalCleanupError</span><span class="sxs-lookup"><span data-stu-id="fad5b-140">marshalCleanupError</span></span>](marshalcleanuperror-mda.md)|[<span data-ttu-id="fad5b-141">zařazování</span><span class="sxs-lookup"><span data-stu-id="fad5b-141">marshaling</span></span>](marshaling-mda.md)|
|[<span data-ttu-id="fad5b-142">memberInfoCacheCreation</span><span class="sxs-lookup"><span data-stu-id="fad5b-142">memberInfoCacheCreation</span></span>](memberinfocachecreation-mda.md)|[<span data-ttu-id="fad5b-143">moduloObjectHashcode</span><span class="sxs-lookup"><span data-stu-id="fad5b-143">moduloObjectHashcode</span></span>](moduloobjecthashcode-mda.md)|
|[<span data-ttu-id="fad5b-144">nonComVisibleBaseClass</span><span class="sxs-lookup"><span data-stu-id="fad5b-144">nonComVisibleBaseClass</span></span>](noncomvisiblebaseclass-mda.md)|[<span data-ttu-id="fad5b-145">notMarshalable</span><span class="sxs-lookup"><span data-stu-id="fad5b-145">notMarshalable</span></span>](notmarshalable-mda.md)|
|[<span data-ttu-id="fad5b-146">openGenericCERCall</span><span class="sxs-lookup"><span data-stu-id="fad5b-146">openGenericCERCall</span></span>](opengenericcercall-mda.md)|[<span data-ttu-id="fad5b-147">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="fad5b-147">overlappedFreeError</span></span>](overlappedfreeerror-mda.md)|
|[<span data-ttu-id="fad5b-148">pInvokeLog</span><span class="sxs-lookup"><span data-stu-id="fad5b-148">pInvokeLog</span></span>](pinvokelog-mda.md)|[<span data-ttu-id="fad5b-149">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="fad5b-149">pInvokeStackImbalance</span></span>](pinvokestackimbalance-mda.md)|
|[<span data-ttu-id="fad5b-150">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="fad5b-150">raceOnRCWCleanup</span></span>](raceonrcwcleanup-mda.md)|[<span data-ttu-id="fad5b-151">Vícenásobný přístup</span><span class="sxs-lookup"><span data-stu-id="fad5b-151">reentrancy</span></span>](reentrancy-mda.md)|
|[<span data-ttu-id="fad5b-152">releaseHandleFailed</span><span class="sxs-lookup"><span data-stu-id="fad5b-152">releaseHandleFailed</span></span>](releasehandlefailed-mda.md)|[<span data-ttu-id="fad5b-153">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="fad5b-153">reportAvOnComRelease</span></span>](reportavoncomrelease-mda.md)|
|[<span data-ttu-id="fad5b-154">streamWriterBufferedDataLost</span><span class="sxs-lookup"><span data-stu-id="fad5b-154">streamWriterBufferedDataLost</span></span>](streamwriterbuffereddatalost-mda.md)|[<span data-ttu-id="fad5b-155">virtualCERCall</span><span class="sxs-lookup"><span data-stu-id="fad5b-155">virtualCERCall</span></span>](virtualcercall-mda.md)|

<span data-ttu-id="fad5b-156">Ve výchozím nastavení .NET Framework aktivuje podmnožinu MDA pro všechny spravované ladicí programy.</span><span class="sxs-lookup"><span data-stu-id="fad5b-156">By default, the .NET Framework activates a subset of MDAs for all managed debuggers.</span></span> <span data-ttu-id="fad5b-157">Můžete zobrazit výchozí sadu v sadě Visual Studio výběrem **Windows**  >  **Možnosti nastavení výjimek** systému Windows v nabídce **ladění** a následným rozbalením seznamu **asistentů spravovaného ladění** .</span><span class="sxs-lookup"><span data-stu-id="fad5b-157">You can view the default set in Visual Studio by choosing **Windows** > **Exception Settings** on the **Debug** menu, and then expanding the **Managed Debugging Assistants** list.</span></span>

![Okno Nastavení výjimek v aplikaci Visual Studio](./media/diagnosing-errors-with-managed-debugging-assistants/exception-settings-mdas.png)

## <a name="enable-and-disable-mdas"></a><span data-ttu-id="fad5b-159">Povolit a zakázat MDA</span><span class="sxs-lookup"><span data-stu-id="fad5b-159">Enable and Disable MDAs</span></span>

<span data-ttu-id="fad5b-160">MDA můžete povolit a zakázat pomocí klíče registru, proměnné prostředí a nastavení konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="fad5b-160">You can enable and disable MDAs by using a registry key, an environment variable, and application configuration settings.</span></span> <span data-ttu-id="fad5b-161">Chcete-li použít nastavení konfigurace aplikace, musíte povolit buď klíč registru, nebo proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="fad5b-161">You must enable either the registry key or the environment variable to use the application configuration settings.</span></span>

> [!TIP]
> <span data-ttu-id="fad5b-162">Místo zakázání MDA můžete aplikaci Visual Studio zabránit v zobrazení dialogového okna MDA vždy, když se přijme oznámení MDA.</span><span class="sxs-lookup"><span data-stu-id="fad5b-162">Instead of disabling MDAs, you can prevent Visual Studio from displaying the MDA dialog box whenever an MDA notification is received.</span></span> <span data-ttu-id="fad5b-163">To provedete tak **Windows**, že  >  v nabídce **ladění** zvolíte možnost**Nastavení výjimek** systému Windows, rozbalíte seznam **asistenti spravovaného ladění** a potom zaškrtnutím nebo zrušením zaškrtnutí políčka **přerušit při vyvolání** pro jednotlivý MDA.</span><span class="sxs-lookup"><span data-stu-id="fad5b-163">To do that, choose **Windows** > **Exception Settings** on the **Debug** menu, expand the **Managed Debugging Assistants** list, and then select or clear the **Break When Thrown** check box for the individual MDA.</span></span>

### <a name="registry-key"></a><span data-ttu-id="fad5b-164">Klíč registru</span><span class="sxs-lookup"><span data-stu-id="fad5b-164">Registry Key</span></span>

<span data-ttu-id="fad5b-165">Pokud chcete povolit MDA, přidejte **HKEY_LOCAL_MACHINE \software\microsoft \\ . NETFramework\MDA** podklíč (typ REG_SZ, hodnota 1) v registru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="fad5b-165">To enable MDAs, add the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\MDA** subkey (type REG_SZ, value 1) in the Windows registry.</span></span> <span data-ttu-id="fad5b-166">Zkopírujte následující příklad do textového souboru s názvem *MDAEnable. reg*. Otevřete Editor registru systému Windows (RegEdit.exe) a v nabídce **soubor** vyberte **importovat**.</span><span class="sxs-lookup"><span data-stu-id="fad5b-166">Copy the following example into a text file named *MDAEnable.reg*. Open the Windows Registry Editor (RegEdit.exe), and from the **File** menu choose **Import**.</span></span> <span data-ttu-id="fad5b-167">Vyberte soubor *MDAEnable. reg* , který povolí MDA na tomto počítači.</span><span class="sxs-lookup"><span data-stu-id="fad5b-167">Select the *MDAEnable.reg* file to enable MDAs on that computer.</span></span> <span data-ttu-id="fad5b-168">Nastavení podklíče na řetězcovou hodnotu **1** (nejedná se o hodnotu typu DWORD s hodnotou **1**) umožňuje číst nastavení MDA z.mda.config souboru *ApplicationName. přípona* .</span><span class="sxs-lookup"><span data-stu-id="fad5b-168">Setting the subkey to string value of **1** (not DWORD value of **1**) enables the reading of MDA settings from the *ApplicationName.suffix*.mda.config file.</span></span> <span data-ttu-id="fad5b-169">Například konfigurační soubor MDA pro Poznámkový blok by byl pojmenovaný notepad.exe.mda.config.</span><span class="sxs-lookup"><span data-stu-id="fad5b-169">For example, the MDA configuration file for Notepad would be named notepad.exe.mda.config.</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="fad5b-170">Pokud je v počítači spuštěná 32 aplikace na 64 operačním systému, klíč MDA by měl být nastaven jako následující:</span><span class="sxs-lookup"><span data-stu-id="fad5b-170">If the computer is running a 32-bit application on a 64-bit operating system, then the MDA key should be set like the following:</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="fad5b-171">Další informace najdete v tématu [nastavení konfigurace specifické pro aplikaci](#application-specific-configuration-settings) .</span><span class="sxs-lookup"><span data-stu-id="fad5b-171">See [Application-Specific Configuration Settings](#application-specific-configuration-settings) for more information.</span></span> <span data-ttu-id="fad5b-172">Nastavení registru lze přepsat proměnnou prostředí COMPLUS_MDA.</span><span class="sxs-lookup"><span data-stu-id="fad5b-172">The registry setting can be overridden by the COMPLUS_MDA environment variable.</span></span> <span data-ttu-id="fad5b-173">Další informace naleznete v tématu [Proměnná prostředí](#environment-variable) .</span><span class="sxs-lookup"><span data-stu-id="fad5b-173">See [Environment Variable](#environment-variable) for more information.</span></span>

<span data-ttu-id="fad5b-174">Pokud chcete zakázat MDA, nastavte podklíč MDA na **hodnotu 0** (nula) pomocí Editoru registru Windows.</span><span class="sxs-lookup"><span data-stu-id="fad5b-174">To disable MDAs, set the MDA subkey to **0** (zero) using the Windows Registry Editor.</span></span>

<span data-ttu-id="fad5b-175">Ve výchozím nastavení jsou některé MDA povolené, když spustíte aplikaci, která je připojená k ladicímu programu, a to i bez přidání klíče registru.</span><span class="sxs-lookup"><span data-stu-id="fad5b-175">By default, some MDAs are enabled when you run an application that is attached to a debugger, even without adding the registry key.</span></span> <span data-ttu-id="fad5b-176">Tyto asistenty můžete zakázat spuštěním souboru *MDADisable. reg* , jak je popsáno výše v této části.</span><span class="sxs-lookup"><span data-stu-id="fad5b-176">You can disable these assistants by running the *MDADisable.reg* file as described earlier in this section.</span></span>

### <a name="environment-variable"></a><span data-ttu-id="fad5b-177">Proměnná prostředí</span><span class="sxs-lookup"><span data-stu-id="fad5b-177">Environment Variable</span></span>

<span data-ttu-id="fad5b-178">Aktivaci MDA můžete také ovládat pomocí proměnné prostředí COMPLUS_MDA, která přepisuje klíč registru.</span><span class="sxs-lookup"><span data-stu-id="fad5b-178">MDA activation can also controlled by the environment variable COMPLUS_MDA, which overrides the registry key.</span></span> <span data-ttu-id="fad5b-179">COMPLUS_MDA řetězec rozlišuje malá a velká písmena, čárkami oddělený seznam názvů MDA nebo jiné speciální řetězce ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="fad5b-179">The COMPLUS_MDA string is a case-insensitive, semicolon-delimited list of MDA names or other special control strings.</span></span> <span data-ttu-id="fad5b-180">Od spravovaného nebo nespravovaného ladicího programu je ve výchozím nastavení povolená sada MDA.</span><span class="sxs-lookup"><span data-stu-id="fad5b-180">Starting under a managed or unmanaged debugger enables a set of MDAs by default.</span></span> <span data-ttu-id="fad5b-181">To se provádí implicitně předem vydaným seznamem MDA, který je ve výchozím nastavení povolený, v části Debuggery na hodnotu proměnné prostředí nebo klíče registru.</span><span class="sxs-lookup"><span data-stu-id="fad5b-181">This is done by implicitly prepending the semicolon-delimited list of MDAs enabled by default under debuggers to the value of the environment variable or registry key.</span></span> <span data-ttu-id="fad5b-182">Speciální řetězce ovládacích prvků jsou následující:</span><span class="sxs-lookup"><span data-stu-id="fad5b-182">The special control strings are the following:</span></span>

- <span data-ttu-id="fad5b-183">`0`-Deaktivuje všechny MDA.</span><span class="sxs-lookup"><span data-stu-id="fad5b-183">`0` - Deactivates all MDAs.</span></span>

- <span data-ttu-id="fad5b-184">`1`-Přečte nastavení MDA z.mda.config *ApplicationName* .</span><span class="sxs-lookup"><span data-stu-id="fad5b-184">`1` - Reads MDA settings from *ApplicationName*.mda.config.</span></span>

- <span data-ttu-id="fad5b-185">`managedDebugger`– Explicitně aktivuje všechny MDA, které jsou implicitně aktivované při spuštění spravovaného spustitelného souboru v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="fad5b-185">`managedDebugger` - Explicitly activates all MDAs that are implicitly activated when a managed executable is started under a debugger.</span></span>

- <span data-ttu-id="fad5b-186">`unmanagedDebugger`– Explicitně aktivuje všechny MDA, které jsou implicitně aktivované při spuštění nespravovaného spustitelného souboru v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="fad5b-186">`unmanagedDebugger` - Explicitly activates all MDAs that are implicitly activated when an unmanaged executable is started under a debugger.</span></span>

<span data-ttu-id="fad5b-187">Pokud existují konfliktní nastavení, přepíše předchozí nastavení poslední nastavení:</span><span class="sxs-lookup"><span data-stu-id="fad5b-187">If there are conflicting settings, the most recent settings override previous settings:</span></span>

- <span data-ttu-id="fad5b-188">`COMPLUS_MDA=0`zakáže všechny MDA, včetně těch, které jsou implicitně povolené v rámci ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="fad5b-188">`COMPLUS_MDA=0` disables all MDAs, including those implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="fad5b-189">`COMPLUS_MDA=gcUnmanagedToManaged`povoluje se `gcUnmanagedToManaged` kromě všech MDA, které jsou implicitně povoleny v rámci ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="fad5b-189">`COMPLUS_MDA=gcUnmanagedToManaged` enables `gcUnmanagedToManaged` in addition to any MDAs that are implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="fad5b-190">`COMPLUS_MDA=0;gcUnmanagedToManaged`povoluje `gcUnmanagedToManaged` , ale zakáže MDA, které by jinak byly implicitně povoleny v rámci ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="fad5b-190">`COMPLUS_MDA=0;gcUnmanagedToManaged` enables `gcUnmanagedToManaged` but disables MDAs that would otherwise be implicitly enabled under a debugger.</span></span>

### <a name="application-specific-configuration-settings"></a><span data-ttu-id="fad5b-191">Nastavení konfigurace specifické pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="fad5b-191">Application-Specific Configuration Settings</span></span>

<span data-ttu-id="fad5b-192">V konfiguračním souboru MDA pro aplikaci můžete povolit, zakázat a nakonfigurovat některé pomocníky jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="fad5b-192">You can enable, disable, and configure some assistants individually in the MDA configuration file for the application.</span></span> <span data-ttu-id="fad5b-193">Pokud chcete povolit použití konfiguračního souboru aplikace pro konfiguraci MDA, musí být nastaven buď klíč registru MDA, nebo proměnná prostředí COMPLUS_MDA.</span><span class="sxs-lookup"><span data-stu-id="fad5b-193">To enable the use of an application configuration file for configuring MDAs, either the MDA registry key or the COMPLUS_MDA environment variable must be set.</span></span> <span data-ttu-id="fad5b-194">Konfigurační soubor aplikace je obvykle umístěn ve stejném adresáři jako spustitelný soubor aplikace (. exe).</span><span class="sxs-lookup"><span data-stu-id="fad5b-194">The application configuration file is typically located in the same directory as the application's executable (.exe) file.</span></span> <span data-ttu-id="fad5b-195">Název souboru má podobu.mda.config *ApplicationName* ; například notepad.exe.mda.config. Asistenti, kteří jsou povoleni v konfiguračním souboru aplikace, mohou mít atributy nebo prvky specificky navržené pro řízení chování tohoto asistenta.</span><span class="sxs-lookup"><span data-stu-id="fad5b-195">The file name takes the form *ApplicationName*.mda.config; for example, notepad.exe.mda.config. Assistants that are enabled in the application configuration file may have attributes or elements specifically designed to control that assistant's behavior.</span></span>

<span data-ttu-id="fad5b-196">Následující příklad ukazuje, jak povolit a nakonfigurovat [zařazování](marshaling-mda.md):</span><span class="sxs-lookup"><span data-stu-id="fad5b-196">The following example shows how to enable and configure the [marshaling](marshaling-mda.md):</span></span>

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

<span data-ttu-id="fad5b-197">`Marshaling`MDA generuje informace o spravovaném typu, který je zařazen do nespravovaného typu pro každý spravovaný a nespravovaný přechod v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fad5b-197">The `Marshaling` MDA emits information about the managed type that is being marshaled to an unmanaged type for each managed-to-unmanaged transition in the application.</span></span> <span data-ttu-id="fad5b-198">`Marshaling`MDA může také filtrovat názvy polí metody a struktury, které jsou zadány v podřízených prvcích **MethodFilter** a **FieldFilter** v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="fad5b-198">The `Marshaling` MDA can also filter the names of the method and structure fields supplied in the **methodFilter** and **fieldFilter** child elements, respectively.</span></span>

<span data-ttu-id="fad5b-199">Následující příklad ukazuje, jak povolit více MDA pomocí jejich výchozích nastavení:</span><span class="sxs-lookup"><span data-stu-id="fad5b-199">The following example shows how to enable multiple MDAs by using their default settings:</span></span>

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
> <span data-ttu-id="fad5b-200">Pokud v konfiguračním souboru zadáte více než jednoho pomocníka, je nutné je uvést v abecedním pořadí.</span><span class="sxs-lookup"><span data-stu-id="fad5b-200">When you specify more than one assistant in a configuration file, you must list them in alphabetical order.</span></span> <span data-ttu-id="fad5b-201">Například pokud chcete povolit i `virtualCERCall` `invalidCERCall` MDA, musíte přidat `<invalidCERCall />` položku před `<virtualCERCall />` zadáním.</span><span class="sxs-lookup"><span data-stu-id="fad5b-201">For example, if you want to enable both the `virtualCERCall` and the `invalidCERCall` MDAs, you must add the `<invalidCERCall />` entry before the `<virtualCERCall />` entry.</span></span> <span data-ttu-id="fad5b-202">Pokud položky nejsou v abecedním pořadí, zobrazí se Neošetřená neplatná zpráva o výjimce konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="fad5b-202">If the entries are not in alphabetical order, an unhandled invalid configuration file exception message is displayed.</span></span>

## <a name="mda-exceptions"></a><span data-ttu-id="fad5b-203">MDA – výjimky</span><span class="sxs-lookup"><span data-stu-id="fad5b-203">MDA exceptions</span></span>

<span data-ttu-id="fad5b-204">Když je povolený MDA, je aktivní, a to i v případě, že váš kód není spuštěný v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="fad5b-204">When an MDA is enabled, it's active even when your code is not executing under a debugger.</span></span> <span data-ttu-id="fad5b-205">Je-li událost MDA vyvolána, když není k dispozici ladicí program, zpráva o události je uvedena v dialogovém okně Neošetřená výjimka, i když se nejedná o neošetřenou výjimku.</span><span class="sxs-lookup"><span data-stu-id="fad5b-205">If an MDA event is raised when a debugger is not present, the event message is presented in an unhandled exception dialog box, although it is not an unhandled exception.</span></span> <span data-ttu-id="fad5b-206">Chcete-li se vyhnout dialogovému oknu, odeberte nastavení MDA-povolování, když váš kód není spuštěn v ladicím prostředí.</span><span class="sxs-lookup"><span data-stu-id="fad5b-206">To avoid the dialog box, remove the MDA-enabling settings when your code is not executing in a debugging environment.</span></span>

<span data-ttu-id="fad5b-207">Když se váš kód spustí v integrovaném vývojovém prostředí (IDE) sady Visual Studio, můžete se vyhnout dialogovému oknu výjimky, která se zobrazí pro konkrétní události MDA.</span><span class="sxs-lookup"><span data-stu-id="fad5b-207">When your code executes in the Visual Studio integrated development environment (IDE), you can avoid the exception dialog box that appears for specific MDA events.</span></span> <span data-ttu-id="fad5b-208">Chcete-li to provést, v nabídce **ladění** vyberte možnost **Windows**  >  **Nastavení výjimek**systému Windows.</span><span class="sxs-lookup"><span data-stu-id="fad5b-208">To do that, on the **Debug** menu, choose **Windows** > **Exception Settings**.</span></span> <span data-ttu-id="fad5b-209">V okně **Nastavení výjimek** rozbalte seznam **asistenti spravovaného ladění** a potom zrušte zaškrtnutí políčka **přerušit při vyvolání** pro jednotlivý MDA.</span><span class="sxs-lookup"><span data-stu-id="fad5b-209">In the **Exception Settings** window, expand the **Managed Debugging Assistants** list, and then clear the **Break When Thrown** check box for the individual MDA.</span></span> <span data-ttu-id="fad5b-210">Pomocí tohoto dialogového okna můžete také *Povolit* zobrazení dialogových oken s výjimkou MDA.</span><span class="sxs-lookup"><span data-stu-id="fad5b-210">You can also use this dialog box to *enable* the display of MDA exception dialog boxes.</span></span>

## <a name="mda-output"></a><span data-ttu-id="fad5b-211">Výstup MDA</span><span class="sxs-lookup"><span data-stu-id="fad5b-211">MDA Output</span></span>

<span data-ttu-id="fad5b-212">Výstup MDA je podobný následujícímu příkladu, který zobrazuje výstup z `PInvokeStackImbalance` MDA:</span><span class="sxs-lookup"><span data-stu-id="fad5b-212">MDA output is similar to the following example, which shows the output from the `PInvokeStackImbalance` MDA:</span></span>

<span data-ttu-id="fad5b-213">**Volání funkce PInvoke ' MDATest! MDATest. program:: StdCall zrušil vyvážení zásobníku. To je pravděpodobně způsobeno tím, že spravovaný podpis PInvoke neodpovídá nespravovanému cílovému podpisu. Ověřte, že konvence volání a parametry signatury PInvoke odpovídají cílovému nespravovanému podpisu.**</span><span class="sxs-lookup"><span data-stu-id="fad5b-213">**A call to PInvoke function 'MDATest!MDATest.Program::StdCall' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.**</span></span>

## <a name="see-also"></a><span data-ttu-id="fad5b-214">Viz také</span><span class="sxs-lookup"><span data-stu-id="fad5b-214">See also</span></span>

- [<span data-ttu-id="fad5b-215">Ladění, trasování a profilace</span><span class="sxs-lookup"><span data-stu-id="fad5b-215">Debugging, Tracing, and Profiling</span></span>](index.md)
