---
title: Fuslogvw.exe (prohlížeč protokolu vazby sestavení)
description: Použijte Fuslogvw.exe, prohlížeč protokolů vazby sestavení. Tento prohlížeč zobrazuje podrobnosti vazby sestavení, které pomáhají diagnostikovat, proč rozhraní .NET nemůže najít sestavení v době běhu.
ms.date: 03/30/2017
helpviewer_keywords:
- failed assembly binds
- Fuslogvw.exe
- displaying failed assembly bind details
- assemblies [.NET Framework], failed assembly binds
- locating assemblies
- Assembly Binding Log Viewer
ms.assetid: e32fa443-0778-4cc3-bf36-5c8ea297d296
ms.openlocfilehash: 949f9cf98d5eb4e100be9837be120038f085cc40
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167120"
---
# <a name="fuslogvwexe-assembly-binding-log-viewer"></a><span data-ttu-id="87459-104">Fuslogvw.exe (prohlížeč protokolu vazby sestavení)</span><span class="sxs-lookup"><span data-stu-id="87459-104">Fuslogvw.exe (Assembly Binding Log Viewer)</span></span>

<span data-ttu-id="87459-105">Nástroj Assembly Binding Log Viewer zobrazuje podrobnosti o vazbách sestavení.</span><span class="sxs-lookup"><span data-stu-id="87459-105">The Assembly Binding Log Viewer displays details for assembly binds.</span></span> <span data-ttu-id="87459-106">Tyto informace vám pomohou diagnostikovat, proč rozhraní .NET Framework nemůže najít sestavení v době běhu.</span><span class="sxs-lookup"><span data-stu-id="87459-106">This information helps you diagnose why the .NET Framework cannot locate an assembly at run time.</span></span> <span data-ttu-id="87459-107">Tyto chyby jsou obvykle výsledkem nasazení sestavení na nesprávné místo, neplatné nativní bitové kopie nebo neshody čísel verzí nebo jazykových verzí.</span><span class="sxs-lookup"><span data-stu-id="87459-107">These failures are usually the result of an assembly deployed to the wrong location, a native image that is no longer valid, or a mismatch in version numbers or cultures.</span></span> <span data-ttu-id="87459-108">Modul CLR (Common Language Runtime) při hledání sestavení obvykle zobrazuje <xref:System.TypeLoadException> ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="87459-108">The common language runtime's failure to locate an assembly typically shows up as a <xref:System.TypeLoadException> in your application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="87459-109">Nástroj fuslogvw.exe je nutné spustit s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="87459-109">You must run fuslogvw.exe with administrator privileges.</span></span>

<span data-ttu-id="87459-110">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="87459-110">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="87459-111">Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7) s přihlašovacími údaji správce.</span><span class="sxs-lookup"><span data-stu-id="87459-111">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7) with administrator credentials.</span></span> <span data-ttu-id="87459-112">Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="87459-112">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="87459-113">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="87459-113">At the command prompt, type the following:</span></span>

```console
fuslogvw
```

<span data-ttu-id="87459-114">Prohlížeč zobrazí záznam pro každou nezdařenou vazbu sestavení.</span><span class="sxs-lookup"><span data-stu-id="87459-114">The viewer displays an entry for each failed assembly bind.</span></span> <span data-ttu-id="87459-115">Pro každou chybu prohlížeč vypíše aplikaci, která iniciovala tuto vazbu, sestavení, kterého se vazba týká, včetně názvu, verze, jazykové verze, veřejného klíče a data a času chyby.</span><span class="sxs-lookup"><span data-stu-id="87459-115">For each failure, the viewer describes the application that initiated the bind; the assembly the bind is for, including name, version, culture and public key; and the date and time of the failure.</span></span>

### <a name="to-change-the-log-location-view"></a><span data-ttu-id="87459-116">Změna umístění zobrazení protokolu</span><span class="sxs-lookup"><span data-stu-id="87459-116">To change the log location view</span></span>

1. <span data-ttu-id="87459-117">Chcete-li zobrazit selhání vazeb pro všechny typy aplikací, vyberte přepínač **výchozí** .</span><span class="sxs-lookup"><span data-stu-id="87459-117">Select the **Default** option button to view bind failures for all application types.</span></span> <span data-ttu-id="87459-118">Položky protokolu jsou ve výchozím nastavení uloženy na disku do mezipaměti rozhraní wininet v adresářích jednotlivých uživatelů.</span><span class="sxs-lookup"><span data-stu-id="87459-118">By default, log entries are stored in per-user directories on disk in the wininet cache.</span></span>

2. <span data-ttu-id="87459-119">Pokud chcete zobrazit chyby vazeb ve vlastním adresáři, který určíte, vyberte **vlastní** přepínač.</span><span class="sxs-lookup"><span data-stu-id="87459-119">Select the **Custom** option button to view bind failures in a custom directory that you specify.</span></span> <span data-ttu-id="87459-120">Je nutné zadat vlastní umístění, kam má modul runtime ukládat protokoly, nastavením umístění vlastního protokolu v dialogovém okně **nastavení protokolu** na platný název adresáře.</span><span class="sxs-lookup"><span data-stu-id="87459-120">You must specify the custom location where you want the runtime to store the logs by setting the custom log location in the **Log Settings** dialog to a valid directory name.</span></span> <span data-ttu-id="87459-121">Tento adresář by měl být prázdný a měl by obsahovat pouze soubory, které generuje modul runtime.</span><span class="sxs-lookup"><span data-stu-id="87459-121">This directory should be clean, and only contain files that the runtime generates.</span></span> <span data-ttu-id="87459-122">Pokud obsahuje spustitelný soubor, který generuje chybu do protokolu, tato chyba nebude protokolována, protože se nástroj pokusí vytvořit adresář se stejným názvem jako tento spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="87459-122">If it contains an executable that generates a failure to be logged, the failure will not be logged because the tool tries to create a directory with the same name as the executable.</span></span> <span data-ttu-id="87459-123">Kromě toho se nezdaří pokus o spuštění spustitelného souboru z umístění protokolu.</span><span class="sxs-lookup"><span data-stu-id="87459-123">In addition, an attempt to run an executable from the log location will fail.</span></span>

    > [!NOTE]
    > <span data-ttu-id="87459-124">Výchozí umístění vazby je vhodnější než vlastní umístění vazby.</span><span class="sxs-lookup"><span data-stu-id="87459-124">The default bind location is preferable to the custom bind location.</span></span> <span data-ttu-id="87459-125">Modul runtime ukládá výchozí umístění vazby v mezipaměti WinInet a proto ho automaticky vyčistí. Pokud zadáte vlastní umístění vazby, zodpovídáte za jeho vyčištění.</span><span class="sxs-lookup"><span data-stu-id="87459-125">The runtime stores the default bind location in the wininet cache, and therefore automatically cleans it out. If you specify a custom bind location, you are responsible for cleaning it out.</span></span>

### <a name="to-view-details-about-a-specific-failure"></a><span data-ttu-id="87459-126">Zobrazení podrobností o konkrétní chybě</span><span class="sxs-lookup"><span data-stu-id="87459-126">To view details about a specific failure</span></span>

1. <span data-ttu-id="87459-127">V prohlížeči vyberte název aplikace požadovaného záznamu.</span><span class="sxs-lookup"><span data-stu-id="87459-127">Select the application name of the desired entry in the viewer.</span></span>

2. <span data-ttu-id="87459-128">Klikněte na tlačítko **Zobrazit protokol** .</span><span class="sxs-lookup"><span data-stu-id="87459-128">Click the **View Log** button.</span></span> <span data-ttu-id="87459-129">Záznam lze vybrat také dvojitým kliknutím.</span><span class="sxs-lookup"><span data-stu-id="87459-129">Alternately, you can double-click the selected entry.</span></span>

    <span data-ttu-id="87459-130">Nástroj zobrazí následující podrobnosti o vybrané chybě vazby:</span><span class="sxs-lookup"><span data-stu-id="87459-130">The tool displays the following details about the selected bind failure:</span></span>

    - <span data-ttu-id="87459-131">Konkrétní důvod selhání vazby, například „soubor nebyl nalezen“ nebo „neshoda verzí“.</span><span class="sxs-lookup"><span data-stu-id="87459-131">The specific reason the bind failed, such as "file not found" or "version mismatch".</span></span>

    - <span data-ttu-id="87459-132">Informace o aplikaci, která iniciovala tuto vazbu, včetně jejího názvu, kořenového adresáře aplikace (AppBase) a popisu soukromé cesty hledání, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="87459-132">Information about the application that initiated the bind, including its name, the application's root directory (AppBase), and a description of the private search path, if there is one.</span></span>

    - <span data-ttu-id="87459-133">Identitu sestavení, které tento nástroj hledá.</span><span class="sxs-lookup"><span data-stu-id="87459-133">The identity of the assembly the tool is looking for.</span></span>

    - <span data-ttu-id="87459-134">Popis všech zásad aplikace, vydavatele nebo správce, které byly použity.</span><span class="sxs-lookup"><span data-stu-id="87459-134">A description of any Application, Publisher, or Administrator version policies that have been applied.</span></span>

    - <span data-ttu-id="87459-135">Zda bylo sestavení nalezeno v [globální mezipaměti sestavení (GAC](../app-domains/gac.md)).</span><span class="sxs-lookup"><span data-stu-id="87459-135">Whether the assembly was found in the [global assembly cache](../app-domains/gac.md).</span></span>

    - <span data-ttu-id="87459-136">Seznam všech zjišťovaných adres URL.</span><span class="sxs-lookup"><span data-stu-id="87459-136">A list of all probing URLs.</span></span>

<span data-ttu-id="87459-137">Následující ukázka položky protokolu zobrazuje detailní informace o selhání vazby sestavení.</span><span class="sxs-lookup"><span data-stu-id="87459-137">The following sample log entry shows detailed information about a failed assembly bind.</span></span>

```output
*** Assembly Binder Log Entry  (3/5/2007 @ 12:54:20 PM) ***

The operation failed.
Bind result: hr = 0x80070002. The system cannot find the file specified.

Assembly manager loaded from:  C:\WINNT\Microsoft.NET\Framework\v2.0.50727\fusion.dll
Running under executable  C:\Program Files\Microsoft.NET\FrameworkSDK\Samples\Tutorials\resourcesandlocalization\graphic\cs\graphicfailtest.exe
--- A detailed error log follows.

=== Pre-bind state information ===
LOG: DisplayName = graphicfailtest.resources, Version=0.0.0.0, Culture=en-US, PublicKeyToken=null
 (Fully-specified)
LOG: Appbase = C:\Program Files\Microsoft.NET\FrameworkSDK\Samples\Tutorials\resourcesandlocalization\graphic\cs\
LOG: Initial PrivatePath = NULL
LOG: Dynamic Base = NULL
LOG: Cache Base = NULL
LOG: AppName = NULL
Calling assembly : graphicfailtest, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
===

LOG: Processing DEVPATH.
LOG: DEVPATH is not set. Falling through to regular bind.
LOG: Policy not being applied to reference at this time (private, custom, partial, or location-based assembly bind).
LOG: Post-policy reference: graphicfailtest.resources, Version=0.0.0.0, Culture=en-US, PublicKeyToken=null
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources.DLL.
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources/graphicfailtest.resources.DLL.
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources.EXE.
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources/graphicfailtest.resources.EXE.
LOG: All probing URLs attempted and failed.
```

### <a name="to-delete-a-single-entry-from-the-log"></a><span data-ttu-id="87459-138">Odstranění jednoho záznamu z protokolu</span><span class="sxs-lookup"><span data-stu-id="87459-138">To delete a single entry from the log</span></span>

1. <span data-ttu-id="87459-139">Vyberte záznam v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="87459-139">Select an entry in the viewer.</span></span>

2. <span data-ttu-id="87459-140">Klikněte na tlačítko **Odstranit položku** .</span><span class="sxs-lookup"><span data-stu-id="87459-140">Click the **Delete Entry** button.</span></span>

### <a name="to-delete-all-entries-from-the-log"></a><span data-ttu-id="87459-141">Odstranění všech záznamů z protokolu</span><span class="sxs-lookup"><span data-stu-id="87459-141">To delete all entries from the log</span></span>

- <span data-ttu-id="87459-142">Klikněte na tlačítko **Odstranit vše** .</span><span class="sxs-lookup"><span data-stu-id="87459-142">Click the **Delete All** button.</span></span>

### <a name="to-refresh-the-user-interface"></a><span data-ttu-id="87459-143">Obnovení uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="87459-143">To refresh the user interface</span></span>

- <span data-ttu-id="87459-144">Klikněte na tlačítko **aktualizovat** .</span><span class="sxs-lookup"><span data-stu-id="87459-144">Click the **Refresh** button.</span></span> <span data-ttu-id="87459-145">Prohlížeč automaticky nerozpozná nové položky protokolu, pokud je spuštěn.</span><span class="sxs-lookup"><span data-stu-id="87459-145">The viewer does not automatically detect new log entries while it is running.</span></span> <span data-ttu-id="87459-146">K jejich zobrazení musíte použít tlačítko **aktualizovat** .</span><span class="sxs-lookup"><span data-stu-id="87459-146">You must use the **Refresh** button to display them.</span></span>

### <a name="to-change-the-log-settings"></a><span data-ttu-id="87459-147">Změna nastavení protokolu</span><span class="sxs-lookup"><span data-stu-id="87459-147">To change the log settings</span></span>

- <span data-ttu-id="87459-148">Kliknutím na tlačítko **Nastavení** otevřete dialogové okno **nastavení protokolu** .</span><span class="sxs-lookup"><span data-stu-id="87459-148">Click the **Settings** button to open the **Log Settings** dialog.</span></span>

### <a name="to-view-the-about-dialog"></a><span data-ttu-id="87459-149">Zobrazení dialogového okna O programu</span><span class="sxs-lookup"><span data-stu-id="87459-149">To view the About dialog</span></span>

- <span data-ttu-id="87459-150">Klikněte na tlačítko **o produktu** .</span><span class="sxs-lookup"><span data-stu-id="87459-150">Click the **About** button.</span></span>

## <a name="binding-logs-for-native-images"></a><span data-ttu-id="87459-151">Protokoly vazeb nativních bitových kopií</span><span class="sxs-lookup"><span data-stu-id="87459-151">Binding Logs for Native Images</span></span>

<span data-ttu-id="87459-152">Ve výchozím nastavení nástroj Fuslogvw.exe zaznamenává normální požadavky vazby sestavení.</span><span class="sxs-lookup"><span data-stu-id="87459-152">By default, Fuslogvw.exe logs normal assembly bind requests.</span></span> <span data-ttu-id="87459-153">Alternativně můžete protokolovat vazby sestavení pro nativní bitové kopie, které byly vytvořeny pomocí [Ngen.exe (generátor nativních imagí)](ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="87459-153">Alternatively, you can log assembly binds for native images that were created using the [Ngen.exe (Native Image Generator)](ngen-exe-native-image-generator.md).</span></span>

#### <a name="to-log-assembly-binds-for-native-images"></a><span data-ttu-id="87459-154">Protokolování vazeb sestavení nativních bitových kopií</span><span class="sxs-lookup"><span data-stu-id="87459-154">To log assembly binds for native images</span></span>

- <span data-ttu-id="87459-155">Ve skupině **Kategorie protokolů** vyberte přepínač **nativní bitové kopie** .</span><span class="sxs-lookup"><span data-stu-id="87459-155">In the **Log Categories** group, select the **Native Images** option button.</span></span>

<span data-ttu-id="87459-156">Následující protokol zobrazuje chybu způsobenou neexistující závislostí při vytvoření nativní bitové kopie pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="87459-156">The following log shows a failure caused by a dependency that did not exist when the native image was created for the application.</span></span> <span data-ttu-id="87459-157">Pokud se tyto závislosti v době běhu liší od závislostí při spuštění nástroje Ngen.exe, vazba na nativní bitovou kopii není povolena.</span><span class="sxs-lookup"><span data-stu-id="87459-157">If the dependencies at run time differ from the dependencies when Ngen.exe is run, binding to a native image is not allowed.</span></span>

```output
*** Assembly Binder Log Entry  (12/8/2006 @ 5:22:07 PM) ***

The operation failed.
Bind result: hr = 0x80070002. The system cannot find the file specified.

Assembly manager loaded from:  E:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscorwks.dll
Running under executable  E:\test\App.exe
--- A detailed error log follows.

LOG: Start binding of native image App, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: IL assembly loaded from E:\test\App.exe.
LOG: Start validating native image App, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: Start validating all the dependencies.
LOG: [Level 1]Start validating native image dependency mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089.
LOG: Dependency evaluation succeeded.
LOG: [Level 1]Start validating IL dependency b, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
WRN: Dependency assembly was not found at ngen time, but is found at binding time. Disallow using this native image.
WRN: No matching native image found.
LOG: Bind to native image assembly did not succeed. Use IL image.
```

<span data-ttu-id="87459-158">Následující protokol zobrazuje selhání vazby nativní bitové kopie, ke kterému došlo, protože nastavení zabezpečení počítače při spuštění aplikace se liší od nastavení zabezpečení v době, kdy byla tato nativní bitová kopie vytvořena.</span><span class="sxs-lookup"><span data-stu-id="87459-158">The following log shows a native image binding failure that occurred because the security settings on the computer when the application was run were different from the security settings at the time the native image was created.</span></span>

```output
*** Assembly Binder Log Entry  (12/8/2006 @ 5:29:09 PM) ***

The operation failed.
Bind result: hr = 0x80004005. Unspecified error

Assembly manager loaded from:  E:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscorwks.dll
Running under executable  E:\test\Application101622.exe
--- A detailed error log follows.

LOG: Start binding of native image Application101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: IL assembly loaded from E:\test\Application101622.exe.
LOG: Start validating native image Application101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: Start validating all the dependencies.
LOG: [Level 1]Start validating native image dependency mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089.
LOG: Dependency evaluation succeeded.
LOG: [Level 1]Start validating IL dependency Dependency101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: Dependency evaluation succeeded.
LOG: Validation of dependencies succeeded.
LOG: Start loading all the dependencies into load context.
LOG: Loading of dependencies succeeded.
LOG: Bind to native image succeeded.
Native image has correct version information.
Attempting to use native image E:\Windows\assembly\NativeImages_v2.0.50727_64\Application101622\1ac7fadabec4f72575d807501e9fdc72\Application101622.ni.exe.
Rejecting native image because it failed the security check. The assembly's permissions must have changed since the time it was ngenned, or it is running with a different security context.
Discarding native image.
```

## <a name="the-log-settings-dialog"></a><span data-ttu-id="87459-159">Dialogové okno nastavení protokolu</span><span class="sxs-lookup"><span data-stu-id="87459-159">The Log Settings Dialog</span></span>

<span data-ttu-id="87459-160">Pomocí dialogového okna **nastavení protokolu** můžete provést následující akce.</span><span class="sxs-lookup"><span data-stu-id="87459-160">You can use the **Log Settings** dialog to perform the following actions.</span></span>

#### <a name="to-disable-logging"></a><span data-ttu-id="87459-161">Zákaz protokolování</span><span class="sxs-lookup"><span data-stu-id="87459-161">To disable logging</span></span>

- <span data-ttu-id="87459-162">Vyberte přepínač **protokol zakázán** .</span><span class="sxs-lookup"><span data-stu-id="87459-162">Select the **Log disabled** option button.</span></span>  <span data-ttu-id="87459-163">Tato možnost je ve výchozím stavu zvolena.</span><span class="sxs-lookup"><span data-stu-id="87459-163">Note that this option is selected by default.</span></span>

#### <a name="to-log-assembly-binds-in-exceptions"></a><span data-ttu-id="87459-164">Protokolování vazby sestavení ve výjimkách</span><span class="sxs-lookup"><span data-stu-id="87459-164">To log assembly binds in exceptions</span></span>

- <span data-ttu-id="87459-165">Vyberte přepínač **Protokolovat text výjimky** .</span><span class="sxs-lookup"><span data-stu-id="87459-165">Select the **Log in exception text** option button.</span></span> <span data-ttu-id="87459-166">Pouze nejméně podrobné informace protokolu jsou zaznamenány v textu výjimky.</span><span class="sxs-lookup"><span data-stu-id="87459-166">Only the least detailed fusion log information is logged in exception text.</span></span> <span data-ttu-id="87459-167">Chcete-li zobrazit úplné informace, použijte některé z dalších nastavení.</span><span class="sxs-lookup"><span data-stu-id="87459-167">To view full information, use one of the other settings.</span></span>

  <span data-ttu-id="87459-168">Prohlédněte si důležitou poznámku týkající se sestavení, která jsou načtena jako doménově neutrální.</span><span class="sxs-lookup"><span data-stu-id="87459-168">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>

#### <a name="to-log-assembly-bind-failures"></a><span data-ttu-id="87459-169">Protokolování selhání vazby sestavení</span><span class="sxs-lookup"><span data-stu-id="87459-169">To log assembly bind failures</span></span>

- <span data-ttu-id="87459-170">Vyberte přepínač **Protokolovat chyby vazby na disk** .</span><span class="sxs-lookup"><span data-stu-id="87459-170">Select the **Log bind failures to disk** option button.</span></span>

  <span data-ttu-id="87459-171">Prohlédněte si důležitou poznámku týkající se sestavení, která jsou načtena jako doménově neutrální.</span><span class="sxs-lookup"><span data-stu-id="87459-171">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>

#### <a name="to-log-all-assembly-binds"></a><span data-ttu-id="87459-172">Protokolování všech vazeb sestavení</span><span class="sxs-lookup"><span data-stu-id="87459-172">To log all assembly binds</span></span>

- <span data-ttu-id="87459-173">Vyberte přepínač **Protokolovat všechny vazby na disk** .</span><span class="sxs-lookup"><span data-stu-id="87459-173">Select the **Log all binds to disk** option button.</span></span>

  <span data-ttu-id="87459-174">Prohlédněte si důležitou poznámku týkající se sestavení, která jsou načtena jako doménově neutrální.</span><span class="sxs-lookup"><span data-stu-id="87459-174">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="87459-175">Když je sestavení načteno jako doménově neutrální, například nastavením <xref:System.AppDomainSetup.LoaderOptimization%2A> vlastnosti na <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> nebo <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType> , zapnutí protokolování může v některých případech způsobit nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="87459-175">When an assembly is loaded as domain neutral, for example by setting the <xref:System.AppDomainSetup.LoaderOptimization%2A> property to <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> or <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>, turning on logging might leak memory in some cases.</span></span> <span data-ttu-id="87459-176">K tomu může dojít, pokud je položka protokolu vytvořena při načtení doménově neutrálního modulu do domény aplikace a později, když je doména aplikace uvolněna.</span><span class="sxs-lookup"><span data-stu-id="87459-176">This can happen if a log entry is made when a domain-neutral module is loaded into an application domain, and later the application domain is unloaded.</span></span> <span data-ttu-id="87459-177">Položka protokolu nemusí být uvolněna až do ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="87459-177">The log entry might not be released until the process ends.</span></span> <span data-ttu-id="87459-178">Některé ladicí programy automaticky zapínají protokolování.</span><span class="sxs-lookup"><span data-stu-id="87459-178">Some debuggers automatically turn on logging.</span></span>

#### <a name="to-enable-a-custom-log-path"></a><span data-ttu-id="87459-179">Povolení vlastní cesty protokolu</span><span class="sxs-lookup"><span data-stu-id="87459-179">To enable a custom log path</span></span>

1. <span data-ttu-id="87459-180">Vyberte přepínač **Povolit vlastní cestu protokolu** .</span><span class="sxs-lookup"><span data-stu-id="87459-180">Select the **Enable custom log path** option button.</span></span>

2. <span data-ttu-id="87459-181">Zadejte cestu do textového pole **vlastní cesta protokolu** .</span><span class="sxs-lookup"><span data-stu-id="87459-181">Enter the path into the **Custom log path** text box.</span></span>

> [!NOTE]
> <span data-ttu-id="87459-182">[Prohlížeč protokolů vazby sestavení (Fuslogvw.exe)](fuslogvw-exe-assembly-binding-log-viewer.md) používá mezipaměť aplikace Internet Explorer (IE) k uložení protokolu vazby.</span><span class="sxs-lookup"><span data-stu-id="87459-182">The [Assembly Binding Log Viewer (Fuslogvw.exe)](fuslogvw-exe-assembly-binding-log-viewer.md) uses the Internet Explorer (IE) cache to store its binding log.</span></span> <span data-ttu-id="87459-183">V důsledku příležitostného poškození mezipaměti IE může [Prohlížeč protokolu vazeb sestavení (Fuslogvw.exe)](fuslogvw-exe-assembly-binding-log-viewer.md) někdy zastavit zobrazování nových protokolů vazby v okně zobrazení.</span><span class="sxs-lookup"><span data-stu-id="87459-183">Due to occasional corruption in the IE cache, the [Assembly Binding Log Viewer (Fuslogvw.exe)](fuslogvw-exe-assembly-binding-log-viewer.md) can sometimes stop showing new binding logs in the viewing window.</span></span> <span data-ttu-id="87459-184">V důsledku tohoto poškození infrastruktura vazeb rozhraní .NET (Fusion) nemůže do protokolu vazeb zapisovat nebo číst.</span><span class="sxs-lookup"><span data-stu-id="87459-184">As a result of this corruption, the .NET binding infrastructure (fusion) cannot write to or read from the binding log.</span></span> <span data-ttu-id="87459-185">(K tomuto problému nedochází, pokud použijete vlastní cestu protokolu.)  Chcete-li opravit poškození a dovolit, aby fúze znovu zobrazovala protokoly vazby, vymažte mezipaměť IE odstraněním dočasných internetových souborů z dialogového okna Internet možnosti Internetu.</span><span class="sxs-lookup"><span data-stu-id="87459-185">(This issue is not encountered if you use a custom log path.)  To fix the corruption and allow fusion to show binding logs again, clear the IE cache by deleting temporary internet files from within the IE Internet Options dialog.</span></span>
>
> <span data-ttu-id="87459-186">Pokud vaše nespravovaná aplikace je hostitelem modulu CLR (Common Language Runtime) implementací `IHostAssemblyManager` `IHostAssemblyStore` rozhraní a, položky protokolu nelze ukládat do mezipaměti WinInet.</span><span class="sxs-lookup"><span data-stu-id="87459-186">If your unmanaged application hosts the common language runtime by implementing the `IHostAssemblyManager` and `IHostAssemblyStore` interfaces, log entries can't be stored in the wininet cache.</span></span>  <span data-ttu-id="87459-187">Chcete-li zobrazit položky protokolu pro vlastní hostitele implementující tato rozhraní, je nutné zadat alternativní cestu k protokolu.</span><span class="sxs-lookup"><span data-stu-id="87459-187">To view log entries for custom hosts that implement these interfaces, you must specify an alternate log path.</span></span>

#### <a name="to-enable-logging-for-apps-running-in-the-windows-app-container"></a><span data-ttu-id="87459-188">Povolení protokolování pro aplikace spuštěné v kontejneru pro aplikace systému Windows</span><span class="sxs-lookup"><span data-stu-id="87459-188">To enable logging for apps running in the Windows app container</span></span>

1. <span data-ttu-id="87459-189">Povolte vlastní cestu protokolu, jak je popsáno v předchozí proceduře.</span><span class="sxs-lookup"><span data-stu-id="87459-189">Enable a custom log path, as described in the previous procedure.</span></span> <span data-ttu-id="87459-190">Ve výchozím nastavení mají aplikace spuštěné v kontejneru pro aplikace systému Windows omezený přístup na pevný disk.</span><span class="sxs-lookup"><span data-stu-id="87459-190">By default, apps that are running in the Windows app container have limited access to the hard disk.</span></span> <span data-ttu-id="87459-191">Zadaný adresář bude mít přístup pro čtení a zápis pro všechny aplikace v kontejneru aplikace.</span><span class="sxs-lookup"><span data-stu-id="87459-191">The directory you specify will have read/write access for all apps in the app container.</span></span>

2. <span data-ttu-id="87459-192">Zaškrtněte políčko **Povolit moderní protokolování** .</span><span class="sxs-lookup"><span data-stu-id="87459-192">Select the **Enable immersive logging** check box.</span></span>

    > [!NOTE]
    > <span data-ttu-id="87459-193">Toto pole je povoleno pouze v systému Windows 8 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="87459-193">This box is enabled only on Windows 8 or later.</span></span>

## <a name="see-also"></a><span data-ttu-id="87459-194">Viz také</span><span class="sxs-lookup"><span data-stu-id="87459-194">See also</span></span>

- <xref:System.TypeLoadException>
- [<span data-ttu-id="87459-195">Nástroje</span><span class="sxs-lookup"><span data-stu-id="87459-195">Tools</span></span>](index.md)
- [<span data-ttu-id="87459-196">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="87459-196">Global Assembly Cache</span></span>](../app-domains/gac.md)
- [<span data-ttu-id="87459-197">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="87459-197">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="87459-198">Výzvy příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="87459-198">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
