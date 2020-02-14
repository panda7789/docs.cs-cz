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
ms.openlocfilehash: 712fbbe9e0ad291385e8eef321c5e8a2fa092a5d
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216561"
---
# <a name="diagnose-errors-with-managed-debugging-assistants"></a><span data-ttu-id="444ff-102">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="444ff-102">Diagnose Errors with Managed Debugging Assistants</span></span>

<span data-ttu-id="444ff-103">Asistenti spravovaného ladění (MDA) jsou pomůcky pro ladění, které spolupracují s modulem CLR (Common Language Runtime) k poskytování informací o stavu modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="444ff-103">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span> <span data-ttu-id="444ff-104">Pomocníci generují informativní zprávy o událostech modulu runtime, které nemůžete jinak zachytávat.</span><span class="sxs-lookup"><span data-stu-id="444ff-104">The assistants generate informational messages about runtime events that you cannot otherwise trap.</span></span> <span data-ttu-id="444ff-105">MDA můžete použít k izolaci chyb aplikace, ke kterým dochází při přechodu mezi spravovaným a nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="444ff-105">You can use MDAs to isolate hard-to-find application bugs that occur when transitioning between managed and unmanaged code.</span></span>

<span data-ttu-id="444ff-106">Všechny MDA můžete [Povolit nebo zakázat](#enable-and-disable-mdas) přidáním klíče do registru systému Windows nebo nastavením proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="444ff-106">You can [enable or disable](#enable-and-disable-mdas) all MDAs by adding a key to the Windows registry or by setting an environment variable.</span></span> <span data-ttu-id="444ff-107">Můžete povolit konkrétní MDA pomocí nastavení konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="444ff-107">You can enable specific MDAs by using application configuration settings.</span></span> <span data-ttu-id="444ff-108">V konfiguračním souboru aplikace můžete nastavit další nastavení konfigurace pro konkrétní MDA.</span><span class="sxs-lookup"><span data-stu-id="444ff-108">You can set additional configuration settings for some individual MDAs in the application's configuration file.</span></span> <span data-ttu-id="444ff-109">Vzhledem k tomu, že jsou tyto konfigurační soubory analyzovány při načtení modulu runtime, je nutné povolit modul MDA před spuštěním spravované aplikace.</span><span class="sxs-lookup"><span data-stu-id="444ff-109">Because these configuration files are parsed when the runtime is loaded, you must enable the MDA before the managed application starts.</span></span> <span data-ttu-id="444ff-110">Nemůžete ho povolit pro aplikace, které už jsou spuštěné.</span><span class="sxs-lookup"><span data-stu-id="444ff-110">You cannot enable it for applications that have already started.</span></span>

<span data-ttu-id="444ff-111">V následující tabulce jsou uvedeny Mday dodávané s .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="444ff-111">The following table lists the MDAs that ship with the .NET Framework:</span></span>

|||
|-|-|
|[<span data-ttu-id="444ff-112">asynchronousThreadAbort</span><span class="sxs-lookup"><span data-stu-id="444ff-112">asynchronousThreadAbort</span></span>](asynchronousthreadabort-mda.md)|[<span data-ttu-id="444ff-113">bindingFailure</span><span class="sxs-lookup"><span data-stu-id="444ff-113">bindingFailure</span></span>](bindingfailure-mda.md)|
|[<span data-ttu-id="444ff-114">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="444ff-114">callbackOnCollectedDelegate</span></span>](callbackoncollecteddelegate-mda.md)|[<span data-ttu-id="444ff-115">contextSwitchDeadlock</span><span class="sxs-lookup"><span data-stu-id="444ff-115">contextSwitchDeadlock</span></span>](contextswitchdeadlock-mda.md)|
|[<span data-ttu-id="444ff-116">dangerousThreadingAPI</span><span class="sxs-lookup"><span data-stu-id="444ff-116">dangerousThreadingAPI</span></span>](dangerousthreadingapi-mda.md)|[<span data-ttu-id="444ff-117">dateTimeInvalidLocalFormat</span><span class="sxs-lookup"><span data-stu-id="444ff-117">dateTimeInvalidLocalFormat</span></span>](datetimeinvalidlocalformat-mda.md)|
|[<span data-ttu-id="444ff-118">dirtyCastAndCallOnInterface</span><span class="sxs-lookup"><span data-stu-id="444ff-118">dirtyCastAndCallOnInterface</span></span>](dirtycastandcalloninterface-mda.md)|[<span data-ttu-id="444ff-119">disconnectedContext</span><span class="sxs-lookup"><span data-stu-id="444ff-119">disconnectedContext</span></span>](disconnectedcontext-mda.md)|
|[<span data-ttu-id="444ff-120">dllMainReturnsFalse</span><span class="sxs-lookup"><span data-stu-id="444ff-120">dllMainReturnsFalse</span></span>](dllmainreturnsfalse-mda.md)|[<span data-ttu-id="444ff-121">exceptionSwallowedOnCallFromCom</span><span class="sxs-lookup"><span data-stu-id="444ff-121">exceptionSwallowedOnCallFromCom</span></span>](exceptionswallowedoncallfromcom-mda.md)|
|[<span data-ttu-id="444ff-122">failedQI</span><span class="sxs-lookup"><span data-stu-id="444ff-122">failedQI</span></span>](failedqi-mda.md)|[<span data-ttu-id="444ff-123">fatalExecutionEngineError</span><span class="sxs-lookup"><span data-stu-id="444ff-123">fatalExecutionEngineError</span></span>](fatalexecutionengineerror-mda.md)|
|[<span data-ttu-id="444ff-124">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="444ff-124">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)|[<span data-ttu-id="444ff-125">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="444ff-125">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)|
|[<span data-ttu-id="444ff-126">illegalPrepareConstrainedRegion</span><span class="sxs-lookup"><span data-stu-id="444ff-126">illegalPrepareConstrainedRegion</span></span>](illegalprepareconstrainedregion-mda.md)|[<span data-ttu-id="444ff-127">invalidApartmentStateChange</span><span class="sxs-lookup"><span data-stu-id="444ff-127">invalidApartmentStateChange</span></span>](invalidapartmentstatechange-mda.md)|
|[<span data-ttu-id="444ff-128">invalidCERCall</span><span class="sxs-lookup"><span data-stu-id="444ff-128">invalidCERCall</span></span>](invalidcercall-mda.md)|[<span data-ttu-id="444ff-129">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="444ff-129">invalidFunctionPointerInDelegate</span></span>](invalidfunctionpointerindelegate-mda.md)|
|[<span data-ttu-id="444ff-130">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="444ff-130">invalidGCHandleCookie</span></span>](invalidgchandlecookie-mda.md)|[<span data-ttu-id="444ff-131">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="444ff-131">invalidIUnknown</span></span>](invalidiunknown-mda.md)|
|[<span data-ttu-id="444ff-132">invalidMemberDeclaration</span><span class="sxs-lookup"><span data-stu-id="444ff-132">invalidMemberDeclaration</span></span>](invalidmemberdeclaration-mda.md)|[<span data-ttu-id="444ff-133">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="444ff-133">invalidOverlappedToPinvoke</span></span>](invalidoverlappedtopinvoke-mda.md)|
|[<span data-ttu-id="444ff-134">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="444ff-134">invalidVariant</span></span>](invalidvariant-mda.md)|[<span data-ttu-id="444ff-135">jitCompilationStart</span><span class="sxs-lookup"><span data-stu-id="444ff-135">jitCompilationStart</span></span>](jitcompilationstart-mda.md)|
|[<span data-ttu-id="444ff-136">loaderLock</span><span class="sxs-lookup"><span data-stu-id="444ff-136">loaderLock</span></span>](loaderlock-mda.md)|[<span data-ttu-id="444ff-137">loadFromContext</span><span class="sxs-lookup"><span data-stu-id="444ff-137">loadFromContext</span></span>](loadfromcontext-mda.md)|
|[<span data-ttu-id="444ff-138">marshalCleanupError</span><span class="sxs-lookup"><span data-stu-id="444ff-138">marshalCleanupError</span></span>](marshalcleanuperror-mda.md)|[<span data-ttu-id="444ff-139">marshaling</span><span class="sxs-lookup"><span data-stu-id="444ff-139">marshaling</span></span>](marshaling-mda.md)|
|[<span data-ttu-id="444ff-140">memberInfoCacheCreation</span><span class="sxs-lookup"><span data-stu-id="444ff-140">memberInfoCacheCreation</span></span>](memberinfocachecreation-mda.md)|[<span data-ttu-id="444ff-141">moduloObjectHashcode</span><span class="sxs-lookup"><span data-stu-id="444ff-141">moduloObjectHashcode</span></span>](moduloobjecthashcode-mda.md)|
|[<span data-ttu-id="444ff-142">nonComVisibleBaseClass</span><span class="sxs-lookup"><span data-stu-id="444ff-142">nonComVisibleBaseClass</span></span>](noncomvisiblebaseclass-mda.md)|[<span data-ttu-id="444ff-143">notMarshalable</span><span class="sxs-lookup"><span data-stu-id="444ff-143">notMarshalable</span></span>](notmarshalable-mda.md)|
|[<span data-ttu-id="444ff-144">openGenericCERCall</span><span class="sxs-lookup"><span data-stu-id="444ff-144">openGenericCERCall</span></span>](opengenericcercall-mda.md)|[<span data-ttu-id="444ff-145">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="444ff-145">overlappedFreeError</span></span>](overlappedfreeerror-mda.md)|
|[<span data-ttu-id="444ff-146">pInvokeLog</span><span class="sxs-lookup"><span data-stu-id="444ff-146">pInvokeLog</span></span>](pinvokelog-mda.md)|[<span data-ttu-id="444ff-147">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="444ff-147">pInvokeStackImbalance</span></span>](pinvokestackimbalance-mda.md)|
|[<span data-ttu-id="444ff-148">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="444ff-148">raceOnRCWCleanup</span></span>](raceonrcwcleanup-mda.md)|[<span data-ttu-id="444ff-149">reentrancy</span><span class="sxs-lookup"><span data-stu-id="444ff-149">reentrancy</span></span>](reentrancy-mda.md)|
|[<span data-ttu-id="444ff-150">releaseHandleFailed</span><span class="sxs-lookup"><span data-stu-id="444ff-150">releaseHandleFailed</span></span>](releasehandlefailed-mda.md)|[<span data-ttu-id="444ff-151">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="444ff-151">reportAvOnComRelease</span></span>](reportavoncomrelease-mda.md)|
|[<span data-ttu-id="444ff-152">streamWriterBufferedDataLost</span><span class="sxs-lookup"><span data-stu-id="444ff-152">streamWriterBufferedDataLost</span></span>](streamwriterbuffereddatalost-mda.md)|[<span data-ttu-id="444ff-153">virtualCERCall</span><span class="sxs-lookup"><span data-stu-id="444ff-153">virtualCERCall</span></span>](virtualcercall-mda.md)|

<span data-ttu-id="444ff-154">Ve výchozím nastavení .NET Framework aktivuje podmnožinu MDA pro všechny spravované ladicí programy.</span><span class="sxs-lookup"><span data-stu-id="444ff-154">By default, the .NET Framework activates a subset of MDAs for all managed debuggers.</span></span> <span data-ttu-id="444ff-155">Výchozí sadu v sadě Visual Studio můžete zobrazit tak, že v nabídce **ladění** zvolíte možnost **Windows** > **výjimka** a potom rozbalíte seznam **asistenti spravovaného ladění** .</span><span class="sxs-lookup"><span data-stu-id="444ff-155">You can view the default set in Visual Studio by choosing **Windows** > **Exception Settings** on the **Debug** menu, and then expanding the **Managed Debugging Assistants** list.</span></span>

![Okno Nastavení výjimek v aplikaci Visual Studio](./media/diagnosing-errors-with-managed-debugging-assistants/exception-settings-mdas.png)

## <a name="enable-and-disable-mdas"></a><span data-ttu-id="444ff-157">Povolit a zakázat MDA</span><span class="sxs-lookup"><span data-stu-id="444ff-157">Enable and Disable MDAs</span></span>

<span data-ttu-id="444ff-158">MDA můžete povolit a zakázat pomocí klíče registru, proměnné prostředí a nastavení konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="444ff-158">You can enable and disable MDAs by using a registry key, an environment variable, and application configuration settings.</span></span> <span data-ttu-id="444ff-159">Chcete-li použít nastavení konfigurace aplikace, musíte povolit buď klíč registru, nebo proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="444ff-159">You must enable either the registry key or the environment variable to use the application configuration settings.</span></span>

> [!TIP]
> <span data-ttu-id="444ff-160">Místo zakázání MDA můžete aplikaci Visual Studio zabránit v zobrazení dialogového okna MDA vždy, když se přijme oznámení MDA.</span><span class="sxs-lookup"><span data-stu-id="444ff-160">Instead of disabling MDAs, you can prevent Visual Studio from displaying the MDA dialog box whenever an MDA notification is received.</span></span> <span data-ttu-id="444ff-161">Provedete to tak, že v nabídce **ladění** zvolíte možnost **Windows** > **výjimka** , rozbalíte seznam **asistenti spravovaného ladění** a potom zaškrtnutím nebo zrušením zaškrtnutí políčka **přerušit při vyvolání** pro jednotlivý MDA.</span><span class="sxs-lookup"><span data-stu-id="444ff-161">To do that, choose **Windows** > **Exception Settings** on the **Debug** menu, expand the **Managed Debugging Assistants** list, and then select or clear the **Break When Thrown** check box for the individual MDA.</span></span>

### <a name="registry-key"></a><span data-ttu-id="444ff-162">Klíč registru</span><span class="sxs-lookup"><span data-stu-id="444ff-162">Registry Key</span></span>

<span data-ttu-id="444ff-163">Pokud chcete povolit MDA, přidejte **\\HKEY_LOCAL_MACHINE \software\microsoft. NETFramework\MDA** podklíč (typ REG_SZ, hodnota 1) v registru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="444ff-163">To enable MDAs, add the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\MDA** subkey (type REG_SZ, value 1) in the Windows registry.</span></span> <span data-ttu-id="444ff-164">Zkopírujte následující příklad do textového souboru s názvem *MDAEnable. reg*. Otevřete Editor registru systému Windows (Regedit. exe) a v nabídce **soubor** vyberte **importovat**.</span><span class="sxs-lookup"><span data-stu-id="444ff-164">Copy the following example into a text file named *MDAEnable.reg*. Open the Windows Registry Editor (RegEdit.exe), and from the **File** menu choose **Import**.</span></span> <span data-ttu-id="444ff-165">Vyberte soubor *MDAEnable. reg* , který povolí MDA na tomto počítači.</span><span class="sxs-lookup"><span data-stu-id="444ff-165">Select the *MDAEnable.reg* file to enable MDAs on that computer.</span></span> <span data-ttu-id="444ff-166">Nastavení podklíče na řetězcovou hodnotu **1** (ne hodnota DWORD **1**) umožňuje číst nastavení MDA ze souboru *ApplicationName. přípon*. MDA. config.</span><span class="sxs-lookup"><span data-stu-id="444ff-166">Setting the subkey to string value of **1** (not DWORD value of **1**) enables the reading of MDA settings from the *ApplicationName.suffix*.mda.config file.</span></span> <span data-ttu-id="444ff-167">Například konfigurační soubor MDA pro Poznámkový blok by měl název Notepad. exe. MDA. config.</span><span class="sxs-lookup"><span data-stu-id="444ff-167">For example, the MDA configuration file for Notepad would be named notepad.exe.mda.config.</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="444ff-168">Pokud je v počítači spuštěná 32 aplikace na 64 operačním systému, klíč MDA by měl být nastaven jako následující:</span><span class="sxs-lookup"><span data-stu-id="444ff-168">If the computer is running a 32-bit application on a 64-bit operating system, then the MDA key should be set like the following:</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="444ff-169">Další informace najdete v tématu [nastavení konfigurace specifické pro aplikaci](#application-specific-configuration-settings) .</span><span class="sxs-lookup"><span data-stu-id="444ff-169">See [Application-Specific Configuration Settings](#application-specific-configuration-settings) for more information.</span></span> <span data-ttu-id="444ff-170">Nastavení registru lze přepsat proměnnou prostředí COMPLUS_MDA.</span><span class="sxs-lookup"><span data-stu-id="444ff-170">The registry setting can be overridden by the COMPLUS_MDA environment variable.</span></span> <span data-ttu-id="444ff-171">Další informace naleznete v tématu [Proměnná prostředí](#environment-variable) .</span><span class="sxs-lookup"><span data-stu-id="444ff-171">See [Environment Variable](#environment-variable) for more information.</span></span>

<span data-ttu-id="444ff-172">Pokud chcete zakázat MDA, nastavte podklíč MDA na **hodnotu 0** (nula) pomocí Editoru registru Windows.</span><span class="sxs-lookup"><span data-stu-id="444ff-172">To disable MDAs, set the MDA subkey to **0** (zero) using the Windows Registry Editor.</span></span>

<span data-ttu-id="444ff-173">Ve výchozím nastavení jsou některé MDA povolené, když spustíte aplikaci, která je připojená k ladicímu programu, a to i bez přidání klíče registru.</span><span class="sxs-lookup"><span data-stu-id="444ff-173">By default, some MDAs are enabled when you run an application that is attached to a debugger, even without adding the registry key.</span></span> <span data-ttu-id="444ff-174">Tyto asistenty můžete zakázat spuštěním souboru *MDADisable. reg* , jak je popsáno výše v této části.</span><span class="sxs-lookup"><span data-stu-id="444ff-174">You can disable these assistants by running the *MDADisable.reg* file as described earlier in this section.</span></span>

### <a name="environment-variable"></a><span data-ttu-id="444ff-175">Proměnná prostředí</span><span class="sxs-lookup"><span data-stu-id="444ff-175">Environment Variable</span></span>

<span data-ttu-id="444ff-176">Aktivaci MDA můžete také ovládat pomocí proměnné prostředí COMPLUS_MDA, která přepisuje klíč registru.</span><span class="sxs-lookup"><span data-stu-id="444ff-176">MDA activation can also controlled by the environment variable COMPLUS_MDA, which overrides the registry key.</span></span> <span data-ttu-id="444ff-177">COMPLUS_MDA řetězec rozlišuje malá a velká písmena, čárkami oddělený seznam názvů MDA nebo jiné speciální řetězce ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="444ff-177">The COMPLUS_MDA string is a case-insensitive, semicolon-delimited list of MDA names or other special control strings.</span></span> <span data-ttu-id="444ff-178">Od spravovaného nebo nespravovaného ladicího programu je ve výchozím nastavení povolená sada MDA.</span><span class="sxs-lookup"><span data-stu-id="444ff-178">Starting under a managed or unmanaged debugger enables a set of MDAs by default.</span></span> <span data-ttu-id="444ff-179">To se provádí implicitně předem vydaným seznamem MDA, který je ve výchozím nastavení povolený, v části Debuggery na hodnotu proměnné prostředí nebo klíče registru.</span><span class="sxs-lookup"><span data-stu-id="444ff-179">This is done by implicitly prepending the semicolon-delimited list of MDAs enabled by default under debuggers to the value of the environment variable or registry key.</span></span> <span data-ttu-id="444ff-180">Speciální řetězce ovládacích prvků jsou následující:</span><span class="sxs-lookup"><span data-stu-id="444ff-180">The special control strings are the following:</span></span>

- <span data-ttu-id="444ff-181">`0` – deaktivuje všechny MDA.</span><span class="sxs-lookup"><span data-stu-id="444ff-181">`0` - Deactivates all MDAs.</span></span>

- <span data-ttu-id="444ff-182">`1` – přečte nastavení MDA z *ApplicationName*. MDA. config.</span><span class="sxs-lookup"><span data-stu-id="444ff-182">`1` - Reads MDA settings from *ApplicationName*.mda.config.</span></span>

- <span data-ttu-id="444ff-183">`managedDebugger` – explicitně aktivuje všechny MDA, které jsou implicitně aktivované při spuštění spravovaného spustitelného souboru v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="444ff-183">`managedDebugger` - Explicitly activates all MDAs that are implicitly activated when a managed executable is started under a debugger.</span></span>

- <span data-ttu-id="444ff-184">`unmanagedDebugger` – explicitně aktivuje všechny MDA, které jsou implicitně aktivované při spuštění nespravovaného spustitelného souboru v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="444ff-184">`unmanagedDebugger` - Explicitly activates all MDAs that are implicitly activated when an unmanaged executable is started under a debugger.</span></span>

<span data-ttu-id="444ff-185">Pokud existují konfliktní nastavení, přepíše předchozí nastavení poslední nastavení:</span><span class="sxs-lookup"><span data-stu-id="444ff-185">If there are conflicting settings, the most recent settings override previous settings:</span></span>

- <span data-ttu-id="444ff-186">`COMPLUS_MDA=0` zakáže všechny MDA, včetně těch, které jsou implicitně povolené v rámci ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="444ff-186">`COMPLUS_MDA=0` disables all MDAs, including those implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="444ff-187">`COMPLUS_MDA=gcUnmanagedToManaged` umožňuje `gcUnmanagedToManaged` kromě všech MDA, které jsou implicitně povoleny v rámci ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="444ff-187">`COMPLUS_MDA=gcUnmanagedToManaged` enables `gcUnmanagedToManaged` in addition to any MDAs that are implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="444ff-188">`COMPLUS_MDA=0;gcUnmanagedToManaged` povoluje `gcUnmanagedToManaged`, ale zakáže MDA, které by jinak byly implicitně povoleny v rámci ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="444ff-188">`COMPLUS_MDA=0;gcUnmanagedToManaged` enables `gcUnmanagedToManaged` but disables MDAs that would otherwise be implicitly enabled under a debugger.</span></span>

### <a name="application-specific-configuration-settings"></a><span data-ttu-id="444ff-189">Nastavení konfigurace specifické pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="444ff-189">Application-Specific Configuration Settings</span></span>

<span data-ttu-id="444ff-190">V konfiguračním souboru MDA pro aplikaci můžete povolit, zakázat a nakonfigurovat některé pomocníky jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="444ff-190">You can enable, disable, and configure some assistants individually in the MDA configuration file for the application.</span></span> <span data-ttu-id="444ff-191">Pokud chcete povolit použití konfiguračního souboru aplikace pro konfiguraci MDA, musí být nastaven buď klíč registru MDA, nebo proměnná prostředí COMPLUS_MDA.</span><span class="sxs-lookup"><span data-stu-id="444ff-191">To enable the use of an application configuration file for configuring MDAs, either the MDA registry key or the COMPLUS_MDA environment variable must be set.</span></span> <span data-ttu-id="444ff-192">Konfigurační soubor aplikace je obvykle umístěn ve stejném adresáři jako spustitelný soubor aplikace (. exe).</span><span class="sxs-lookup"><span data-stu-id="444ff-192">The application configuration file is typically located in the same directory as the application's executable (.exe) file.</span></span> <span data-ttu-id="444ff-193">Název souboru má formát *ApplicationName*. MDA. config; například Notepad. exe. MDA. config. Asistenti, kteří jsou povoleni v konfiguračním souboru aplikace, mohou mít atributy nebo prvky specificky navržené pro řízení chování tohoto asistenta.</span><span class="sxs-lookup"><span data-stu-id="444ff-193">The file name takes the form *ApplicationName*.mda.config; for example, notepad.exe.mda.config. Assistants that are enabled in the application configuration file may have attributes or elements specifically designed to control that assistant's behavior.</span></span>

<span data-ttu-id="444ff-194">Následující příklad ukazuje, jak povolit a nakonfigurovat [zařazování](marshaling-mda.md):</span><span class="sxs-lookup"><span data-stu-id="444ff-194">The following example shows how to enable and configure the [marshaling](marshaling-mda.md):</span></span>

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

<span data-ttu-id="444ff-195">`Marshaling` MDA generuje informace o spravovaném typu, který je zařazen do nespravovaného typu pro každý spravovaný a nespravovaný přechod v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="444ff-195">The `Marshaling` MDA emits information about the managed type that is being marshaled to an unmanaged type for each managed-to-unmanaged transition in the application.</span></span> <span data-ttu-id="444ff-196">`Marshaling` MDA může také filtrovat názvy polí metody a struktury, které jsou zadány v podřízených prvcích **methodFilter** a **FieldFilter** v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="444ff-196">The `Marshaling` MDA can also filter the names of the method and structure fields supplied in the **methodFilter** and **fieldFilter** child elements, respectively.</span></span>

<span data-ttu-id="444ff-197">Následující příklad ukazuje, jak povolit více MDA pomocí jejich výchozích nastavení:</span><span class="sxs-lookup"><span data-stu-id="444ff-197">The following example shows how to enable multiple MDAs by using their default settings:</span></span>

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
> <span data-ttu-id="444ff-198">Pokud v konfiguračním souboru zadáte více než jednoho pomocníka, je nutné je uvést v abecedním pořadí.</span><span class="sxs-lookup"><span data-stu-id="444ff-198">When you specify more than one assistant in a configuration file, you must list them in alphabetical order.</span></span> <span data-ttu-id="444ff-199">Například pokud chcete povolit `virtualCERCall` i `invalidCERCall` MDA, musíte přidat položku `<invalidCERCall />` před `<virtualCERCall />` položku.</span><span class="sxs-lookup"><span data-stu-id="444ff-199">For example, if you want to enable both the `virtualCERCall` and the `invalidCERCall` MDAs, you must add the `<invalidCERCall />` entry before the `<virtualCERCall />` entry.</span></span> <span data-ttu-id="444ff-200">Pokud položky nejsou v abecedním pořadí, zobrazí se Neošetřená neplatná zpráva o výjimce konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="444ff-200">If the entries are not in alphabetical order, an unhandled invalid configuration file exception message is displayed.</span></span>

## <a name="mda-exceptions"></a><span data-ttu-id="444ff-201">MDA – výjimky</span><span class="sxs-lookup"><span data-stu-id="444ff-201">MDA exceptions</span></span>

<span data-ttu-id="444ff-202">Když je povolený MDA, je aktivní, a to i v případě, že váš kód není spuštěný v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="444ff-202">When an MDA is enabled, it's active even when your code is not executing under a debugger.</span></span> <span data-ttu-id="444ff-203">Je-li událost MDA vyvolána, když není k dispozici ladicí program, zpráva o události je uvedena v dialogovém okně Neošetřená výjimka, i když se nejedná o neošetřenou výjimku.</span><span class="sxs-lookup"><span data-stu-id="444ff-203">If an MDA event is raised when a debugger is not present, the event message is presented in an unhandled exception dialog box, although it is not an unhandled exception.</span></span> <span data-ttu-id="444ff-204">Chcete-li se vyhnout dialogovému oknu, odeberte nastavení MDA-povolování, když váš kód není spuštěn v ladicím prostředí.</span><span class="sxs-lookup"><span data-stu-id="444ff-204">To avoid the dialog box, remove the MDA-enabling settings when your code is not executing in a debugging environment.</span></span>

<span data-ttu-id="444ff-205">Když se váš kód spustí v integrovaném vývojovém prostředí (IDE) sady Visual Studio, můžete se vyhnout dialogovému oknu výjimky, která se zobrazí pro konkrétní události MDA.</span><span class="sxs-lookup"><span data-stu-id="444ff-205">When your code executes in the Visual Studio integrated development environment (IDE), you can avoid the exception dialog box that appears for specific MDA events.</span></span> <span data-ttu-id="444ff-206">Chcete-li to provést, v nabídce **ladění** vyberte možnost **Windows** > **výjimka nastavení**.</span><span class="sxs-lookup"><span data-stu-id="444ff-206">To do that, on the **Debug** menu, choose **Windows** > **Exception Settings**.</span></span> <span data-ttu-id="444ff-207">V okně **Nastavení výjimek** rozbalte seznam **asistenti spravovaného ladění** a potom zrušte zaškrtnutí políčka **přerušit při vyvolání** pro jednotlivý MDA.</span><span class="sxs-lookup"><span data-stu-id="444ff-207">In the **Exception Settings** window, expand the **Managed Debugging Assistants** list, and then clear the **Break When Thrown** check box for the individual MDA.</span></span> <span data-ttu-id="444ff-208">Pomocí tohoto dialogového okna můžete také *Povolit* zobrazení dialogových oken s výjimkou MDA.</span><span class="sxs-lookup"><span data-stu-id="444ff-208">You can also use this dialog box to *enable* the display of MDA exception dialog boxes.</span></span>

## <a name="mda-output"></a><span data-ttu-id="444ff-209">Výstup MDA</span><span class="sxs-lookup"><span data-stu-id="444ff-209">MDA Output</span></span>

<span data-ttu-id="444ff-210">Výstup MDA je podobný následujícímu příkladu, který zobrazuje výstup z `PInvokeStackImbalance` MDA:</span><span class="sxs-lookup"><span data-stu-id="444ff-210">MDA output is similar to the following example, which shows the output from the `PInvokeStackImbalance` MDA:</span></span>

<span data-ttu-id="444ff-211">**Volání funkce PInvoke ' MDATest! MDATest. program:: StdCall zrušil vyvážení zásobníku. To je pravděpodobně způsobeno tím, že spravovaný podpis PInvoke neodpovídá nespravovanému cílovému podpisu. Ověřte, že konvence volání a parametry signatury PInvoke odpovídají cílovému nespravovanému podpisu.**</span><span class="sxs-lookup"><span data-stu-id="444ff-211">**A call to PInvoke function 'MDATest!MDATest.Program::StdCall' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.**</span></span>

## <a name="see-also"></a><span data-ttu-id="444ff-212">Viz také</span><span class="sxs-lookup"><span data-stu-id="444ff-212">See also</span></span>

- [<span data-ttu-id="444ff-213">Ladění, trasování a profilace</span><span class="sxs-lookup"><span data-stu-id="444ff-213">Debugging, Tracing, and Profiling</span></span>](index.md)
