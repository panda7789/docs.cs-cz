---
title: Fuslogvw.exe (prohlížeč protokolu vazby sestavení)
ms.date: 03/30/2017
helpviewer_keywords:
- failed assembly binds
- Fuslogvw.exe
- displaying failed assembly bind details
- assemblies [.NET Framework], failed assembly binds
- locating assemblies
- Assembly Binding Log Viewer
ms.assetid: e32fa443-0778-4cc3-bf36-5c8ea297d296
ms.openlocfilehash: 2f0018dca6e5add2c5bc531103a4078307a8c8c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73129851"
---
# <a name="fuslogvwexe-assembly-binding-log-viewer"></a><span data-ttu-id="82bea-102">Fuslogvw.exe (prohlížeč protokolu vazby sestavení)</span><span class="sxs-lookup"><span data-stu-id="82bea-102">Fuslogvw.exe (Assembly Binding Log Viewer)</span></span>

<span data-ttu-id="82bea-103">Nástroj Assembly Binding Log Viewer zobrazuje podrobnosti o vazbách sestavení.</span><span class="sxs-lookup"><span data-stu-id="82bea-103">The Assembly Binding Log Viewer displays details for assembly binds.</span></span> <span data-ttu-id="82bea-104">Tyto informace vám pomohou diagnostikovat, proč rozhraní .NET Framework nemůže najít sestavení v době běhu.</span><span class="sxs-lookup"><span data-stu-id="82bea-104">This information helps you diagnose why the .NET Framework cannot locate an assembly at run time.</span></span> <span data-ttu-id="82bea-105">Tyto chyby jsou obvykle výsledkem nasazení sestavení na nesprávné místo, neplatné nativní bitové kopie nebo neshody čísel verzí nebo jazykových verzí.</span><span class="sxs-lookup"><span data-stu-id="82bea-105">These failures are usually the result of an assembly deployed to the wrong location, a native image that is no longer valid, or a mismatch in version numbers or cultures.</span></span> <span data-ttu-id="82bea-106">Selhání běžného jazyka runtime vyhledejte sestavení se obvykle <xref:System.TypeLoadException> zobrazí jako ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="82bea-106">The common language runtime's failure to locate an assembly typically shows up as a <xref:System.TypeLoadException> in your application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="82bea-107">Nástroj fuslogvw.exe je nutné spustit s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="82bea-107">You must run fuslogvw.exe with administrator privileges.</span></span>

<span data-ttu-id="82bea-108">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="82bea-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="82bea-109">Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře pro sadu Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7) s pověřeními správce.</span><span class="sxs-lookup"><span data-stu-id="82bea-109">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7) with administrator credentials.</span></span> <span data-ttu-id="82bea-110">Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="82bea-110">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="82bea-111">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="82bea-111">At the command prompt, type the following:</span></span>

```console
fuslogvw
```

<span data-ttu-id="82bea-112">Prohlížeč zobrazí záznam pro každou nezdařenou vazbu sestavení.</span><span class="sxs-lookup"><span data-stu-id="82bea-112">The viewer displays an entry for each failed assembly bind.</span></span> <span data-ttu-id="82bea-113">Pro každou chybu prohlížeč vypíše aplikaci, která iniciovala tuto vazbu, sestavení, kterého se vazba týká, včetně názvu, verze, jazykové verze, veřejného klíče a data a času chyby.</span><span class="sxs-lookup"><span data-stu-id="82bea-113">For each failure, the viewer describes the application that initiated the bind; the assembly the bind is for, including name, version, culture and public key; and the date and time of the failure.</span></span>

### <a name="to-change-the-log-location-view"></a><span data-ttu-id="82bea-114">Změna umístění zobrazení protokolu</span><span class="sxs-lookup"><span data-stu-id="82bea-114">To change the log location view</span></span>

1. <span data-ttu-id="82bea-115">Výběrem **možnosti Výchozí** tlačítko zobrazíte selhání vazby pro všechny typy aplikací.</span><span class="sxs-lookup"><span data-stu-id="82bea-115">Select the **Default** option button to view bind failures for all application types.</span></span> <span data-ttu-id="82bea-116">Položky protokolu jsou ve výchozím nastavení uloženy na disku do mezipaměti rozhraní wininet v adresářích jednotlivých uživatelů.</span><span class="sxs-lookup"><span data-stu-id="82bea-116">By default, log entries are stored in per-user directories on disk in the wininet cache.</span></span>

2. <span data-ttu-id="82bea-117">Výběrem tlačítka **Vlastní** možnost i pro zobrazení selhání vazby ve vlastním adresáři, který zadáte.</span><span class="sxs-lookup"><span data-stu-id="82bea-117">Select the **Custom** option button to view bind failures in a custom directory that you specify.</span></span> <span data-ttu-id="82bea-118">Je nutné zadat vlastní umístění, kam má mít runtime ukládání protokolů, nastavením vlastního umístění protokolu v dialogovém okně **Nastavení protokolu** na platný název adresáře.</span><span class="sxs-lookup"><span data-stu-id="82bea-118">You must specify the custom location where you want the runtime to store the logs by setting the custom log location in the **Log Settings** dialog to a valid directory name.</span></span> <span data-ttu-id="82bea-119">Tento adresář by měl být prázdný a měl by obsahovat pouze soubory, které generuje modul runtime.</span><span class="sxs-lookup"><span data-stu-id="82bea-119">This directory should be clean, and only contain files that the runtime generates.</span></span> <span data-ttu-id="82bea-120">Pokud obsahuje spustitelný soubor, který generuje chybu do protokolu, tato chyba nebude protokolována, protože se nástroj pokusí vytvořit adresář se stejným názvem jako tento spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="82bea-120">If it contains an executable that generates a failure to be logged, the failure will not be logged because the tool tries to create a directory with the same name as the executable.</span></span> <span data-ttu-id="82bea-121">Kromě toho se nezdaří pokus o spuštění spustitelného souboru z umístění protokolu.</span><span class="sxs-lookup"><span data-stu-id="82bea-121">In addition, an attempt to run an executable from the log location will fail.</span></span>

    > [!NOTE]
    > <span data-ttu-id="82bea-122">Výchozí umístění vazby je vhodnější než vlastní umístění vazby.</span><span class="sxs-lookup"><span data-stu-id="82bea-122">The default bind location is preferable to the custom bind location.</span></span> <span data-ttu-id="82bea-123">Runtime ukládá výchozí umístění vazby v mezipaměti wininet a proto jej automaticky vyčistí. Pokud zadáte vlastní umístění vazby, jste zodpovědní za jeho vyčištění.</span><span class="sxs-lookup"><span data-stu-id="82bea-123">The runtime stores the default bind location in the wininet cache, and therefore automatically cleans it out. If you specify a custom bind location, you are responsible for cleaning it out.</span></span>

### <a name="to-view-details-about-a-specific-failure"></a><span data-ttu-id="82bea-124">Zobrazení podrobností o konkrétní chybě</span><span class="sxs-lookup"><span data-stu-id="82bea-124">To view details about a specific failure</span></span>

1. <span data-ttu-id="82bea-125">V prohlížeči vyberte název aplikace požadovaného záznamu.</span><span class="sxs-lookup"><span data-stu-id="82bea-125">Select the application name of the desired entry in the viewer.</span></span>

2. <span data-ttu-id="82bea-126">Klepněte na tlačítko **Zobrazit protokol.**</span><span class="sxs-lookup"><span data-stu-id="82bea-126">Click the **View Log** button.</span></span> <span data-ttu-id="82bea-127">Záznam lze vybrat také dvojitým kliknutím.</span><span class="sxs-lookup"><span data-stu-id="82bea-127">Alternately, you can double-click the selected entry.</span></span>

    <span data-ttu-id="82bea-128">Nástroj zobrazí následující podrobnosti o vybrané chybě vazby:</span><span class="sxs-lookup"><span data-stu-id="82bea-128">The tool displays the following details about the selected bind failure:</span></span>

    - <span data-ttu-id="82bea-129">Konkrétní důvod selhání vazby, například „soubor nebyl nalezen“ nebo „neshoda verzí“.</span><span class="sxs-lookup"><span data-stu-id="82bea-129">The specific reason the bind failed, such as "file not found" or "version mismatch".</span></span>

    - <span data-ttu-id="82bea-130">Informace o aplikaci, která iniciovala tuto vazbu, včetně jejího názvu, kořenového adresáře aplikace (AppBase) a popisu soukromé cesty hledání, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="82bea-130">Information about the application that initiated the bind, including its name, the application's root directory (AppBase), and a description of the private search path, if there is one.</span></span>

    - <span data-ttu-id="82bea-131">Identitu sestavení, které tento nástroj hledá.</span><span class="sxs-lookup"><span data-stu-id="82bea-131">The identity of the assembly the tool is looking for.</span></span>

    - <span data-ttu-id="82bea-132">Popis všech zásad aplikace, vydavatele nebo správce, které byly použity.</span><span class="sxs-lookup"><span data-stu-id="82bea-132">A description of any Application, Publisher, or Administrator version policies that have been applied.</span></span>

    - <span data-ttu-id="82bea-133">Zda bylo sestavení nalezeno v [globální mezipaměti sestavení](../app-domains/gac.md).</span><span class="sxs-lookup"><span data-stu-id="82bea-133">Whether the assembly was found in the [global assembly cache](../app-domains/gac.md).</span></span>

    - <span data-ttu-id="82bea-134">Seznam všech zjišťovaných adres URL.</span><span class="sxs-lookup"><span data-stu-id="82bea-134">A list of all probing URLs.</span></span>

<span data-ttu-id="82bea-135">Následující ukázka položky protokolu zobrazuje detailní informace o selhání vazby sestavení.</span><span class="sxs-lookup"><span data-stu-id="82bea-135">The following sample log entry shows detailed information about a failed assembly bind.</span></span>

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

### <a name="to-delete-a-single-entry-from-the-log"></a><span data-ttu-id="82bea-136">Odstranění jednoho záznamu z protokolu</span><span class="sxs-lookup"><span data-stu-id="82bea-136">To delete a single entry from the log</span></span>

1. <span data-ttu-id="82bea-137">Vyberte záznam v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="82bea-137">Select an entry in the viewer.</span></span>

2. <span data-ttu-id="82bea-138">Klepněte na tlačítko **Odstranit položku.**</span><span class="sxs-lookup"><span data-stu-id="82bea-138">Click the **Delete Entry** button.</span></span>

### <a name="to-delete-all-entries-from-the-log"></a><span data-ttu-id="82bea-139">Odstranění všech záznamů z protokolu</span><span class="sxs-lookup"><span data-stu-id="82bea-139">To delete all entries from the log</span></span>

- <span data-ttu-id="82bea-140">Klepněte na tlačítko **Odstranit vše.**</span><span class="sxs-lookup"><span data-stu-id="82bea-140">Click the **Delete All** button.</span></span>

### <a name="to-refresh-the-user-interface"></a><span data-ttu-id="82bea-141">Obnovení uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="82bea-141">To refresh the user interface</span></span>

- <span data-ttu-id="82bea-142">Klepněte na tlačítko **Aktualizovat.**</span><span class="sxs-lookup"><span data-stu-id="82bea-142">Click the **Refresh** button.</span></span> <span data-ttu-id="82bea-143">Prohlížeč automaticky nerozpozná nové položky protokolu, pokud je spuštěn.</span><span class="sxs-lookup"><span data-stu-id="82bea-143">The viewer does not automatically detect new log entries while it is running.</span></span> <span data-ttu-id="82bea-144">K jejich zobrazení je nutné použít tlačítko **Aktualizovat.**</span><span class="sxs-lookup"><span data-stu-id="82bea-144">You must use the **Refresh** button to display them.</span></span>

### <a name="to-change-the-log-settings"></a><span data-ttu-id="82bea-145">Změna nastavení protokolu</span><span class="sxs-lookup"><span data-stu-id="82bea-145">To change the log settings</span></span>

- <span data-ttu-id="82bea-146">Klepnutím na tlačítko **Nastavení** otevřete dialogové okno **Nastavení protokolu.**</span><span class="sxs-lookup"><span data-stu-id="82bea-146">Click the **Settings** button to open the **Log Settings** dialog.</span></span>

### <a name="to-view-the-about-dialog"></a><span data-ttu-id="82bea-147">Zobrazení dialogového okna O programu</span><span class="sxs-lookup"><span data-stu-id="82bea-147">To view the About dialog</span></span>

- <span data-ttu-id="82bea-148">Klikněte na tlačítko **O.**</span><span class="sxs-lookup"><span data-stu-id="82bea-148">Click the **About** button.</span></span>

## <a name="binding-logs-for-native-images"></a><span data-ttu-id="82bea-149">Protokoly vazeb nativních bitových kopií</span><span class="sxs-lookup"><span data-stu-id="82bea-149">Binding Logs for Native Images</span></span>

<span data-ttu-id="82bea-150">Ve výchozím nastavení nástroj Fuslogvw.exe zaznamenává normální požadavky vazby sestavení.</span><span class="sxs-lookup"><span data-stu-id="82bea-150">By default, Fuslogvw.exe logs normal assembly bind requests.</span></span> <span data-ttu-id="82bea-151">Alternativně můžete protokolovat vazby sestavení pro nativní bitové kopie, které byly vytvořeny pomocí [Ngen.exe (Native Image Generator)](ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="82bea-151">Alternatively, you can log assembly binds for native images that were created using the [Ngen.exe (Native Image Generator)](ngen-exe-native-image-generator.md).</span></span>

#### <a name="to-log-assembly-binds-for-native-images"></a><span data-ttu-id="82bea-152">Protokolování vazeb sestavení nativních bitových kopií</span><span class="sxs-lookup"><span data-stu-id="82bea-152">To log assembly binds for native images</span></span>

- <span data-ttu-id="82bea-153">Ve skupině **Kategorie protokolů** vyberte přepínač **Možnost Nativní obrazy.**</span><span class="sxs-lookup"><span data-stu-id="82bea-153">In the **Log Categories** group, select the **Native Images** option button.</span></span>

<span data-ttu-id="82bea-154">Následující protokol zobrazuje chybu způsobenou neexistující závislostí při vytvoření nativní bitové kopie pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="82bea-154">The following log shows a failure caused by a dependency that did not exist when the native image was created for the application.</span></span> <span data-ttu-id="82bea-155">Pokud se tyto závislosti v době běhu liší od závislostí při spuštění nástroje Ngen.exe, vazba na nativní bitovou kopii není povolena.</span><span class="sxs-lookup"><span data-stu-id="82bea-155">If the dependencies at run time differ from the dependencies when Ngen.exe is run, binding to a native image is not allowed.</span></span>

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

<span data-ttu-id="82bea-156">Následující protokol zobrazuje selhání vazby nativní bitové kopie, ke kterému došlo, protože nastavení zabezpečení počítače při spuštění aplikace se liší od nastavení zabezpečení v době, kdy byla tato nativní bitová kopie vytvořena.</span><span class="sxs-lookup"><span data-stu-id="82bea-156">The following log shows a native image binding failure that occurred because the security settings on the computer when the application was run were different from the security settings at the time the native image was created.</span></span>

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

## <a name="the-log-settings-dialog"></a><span data-ttu-id="82bea-157">Dialogové okno nastavení protokolu</span><span class="sxs-lookup"><span data-stu-id="82bea-157">The Log Settings Dialog</span></span>

<span data-ttu-id="82bea-158">Pomocí dialogového okna **Nastavení protokolu** můžete provést následující akce.</span><span class="sxs-lookup"><span data-stu-id="82bea-158">You can use the **Log Settings** dialog to perform the following actions.</span></span>

#### <a name="to-disable-logging"></a><span data-ttu-id="82bea-159">Zákaz protokolování</span><span class="sxs-lookup"><span data-stu-id="82bea-159">To disable logging</span></span>

- <span data-ttu-id="82bea-160">Vyberte přepínač **Zakázat protokol.**</span><span class="sxs-lookup"><span data-stu-id="82bea-160">Select the **Log disabled** option button.</span></span>  <span data-ttu-id="82bea-161">Tato možnost je ve výchozím stavu zvolena.</span><span class="sxs-lookup"><span data-stu-id="82bea-161">Note that this option is selected by default.</span></span>

#### <a name="to-log-assembly-binds-in-exceptions"></a><span data-ttu-id="82bea-162">Protokolování vazby sestavení ve výjimkách</span><span class="sxs-lookup"><span data-stu-id="82bea-162">To log assembly binds in exceptions</span></span>

- <span data-ttu-id="82bea-163">Vyberte přepínač **Možnost Přihlásit se k textu výjimky.**</span><span class="sxs-lookup"><span data-stu-id="82bea-163">Select the **Log in exception text** option button.</span></span> <span data-ttu-id="82bea-164">Pouze nejméně podrobné informace protokolu jsou zaznamenány v textu výjimky.</span><span class="sxs-lookup"><span data-stu-id="82bea-164">Only the least detailed fusion log information is logged in exception text.</span></span> <span data-ttu-id="82bea-165">Chcete-li zobrazit úplné informace, použijte některé z dalších nastavení.</span><span class="sxs-lookup"><span data-stu-id="82bea-165">To view full information, use one of the other settings.</span></span>

  <span data-ttu-id="82bea-166">Prohlédněte si důležitou poznámku týkající se sestavení, která jsou načtena jako doménově neutrální.</span><span class="sxs-lookup"><span data-stu-id="82bea-166">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>

#### <a name="to-log-assembly-bind-failures"></a><span data-ttu-id="82bea-167">Protokolování selhání vazby sestavení</span><span class="sxs-lookup"><span data-stu-id="82bea-167">To log assembly bind failures</span></span>

- <span data-ttu-id="82bea-168">Vyberte tlačítko s **vazbou protokolu na** přepínač disk.</span><span class="sxs-lookup"><span data-stu-id="82bea-168">Select the **Log bind failures to disk** option button.</span></span>

  <span data-ttu-id="82bea-169">Prohlédněte si důležitou poznámku týkající se sestavení, která jsou načtena jako doménově neutrální.</span><span class="sxs-lookup"><span data-stu-id="82bea-169">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>

#### <a name="to-log-all-assembly-binds"></a><span data-ttu-id="82bea-170">Protokolování všech vazeb sestavení</span><span class="sxs-lookup"><span data-stu-id="82bea-170">To log all assembly binds</span></span>

- <span data-ttu-id="82bea-171">Vyberte přepínač **Protokolu všech vazeb s diskem.**</span><span class="sxs-lookup"><span data-stu-id="82bea-171">Select the **Log all binds to disk** option button.</span></span>

  <span data-ttu-id="82bea-172">Prohlédněte si důležitou poznámku týkající se sestavení, která jsou načtena jako doménově neutrální.</span><span class="sxs-lookup"><span data-stu-id="82bea-172">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="82bea-173">Při načtení sestavení jako neutrální domény, <xref:System.AppDomainSetup.LoaderOptimization%2A> například <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>nastavením vlastnosti nebo , zapnutí protokolování může unikat paměti v některých případech.</span><span class="sxs-lookup"><span data-stu-id="82bea-173">When an assembly is loaded as domain neutral, for example by setting the <xref:System.AppDomainSetup.LoaderOptimization%2A> property to <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> or <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>, turning on logging might leak memory in some cases.</span></span> <span data-ttu-id="82bea-174">K tomu může dojít, pokud je položka protokolu vytvořena při načtení doménově neutrálního modulu do domény aplikace a později, když je doména aplikace uvolněna.</span><span class="sxs-lookup"><span data-stu-id="82bea-174">This can happen if a log entry is made when a domain-neutral module is loaded into an application domain, and later the application domain is unloaded.</span></span> <span data-ttu-id="82bea-175">Položka protokolu nemusí být uvolněna až do ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="82bea-175">The log entry might not be released until the process ends.</span></span> <span data-ttu-id="82bea-176">Některé ladicí programy automaticky zapínají protokolování.</span><span class="sxs-lookup"><span data-stu-id="82bea-176">Some debuggers automatically turn on logging.</span></span>

#### <a name="to-enable-a-custom-log-path"></a><span data-ttu-id="82bea-177">Povolení vlastní cesty protokolu</span><span class="sxs-lookup"><span data-stu-id="82bea-177">To enable a custom log path</span></span>

1. <span data-ttu-id="82bea-178">Vyberte tlačítko **Povolit vlastní cestu protokolu.**</span><span class="sxs-lookup"><span data-stu-id="82bea-178">Select the **Enable custom log path** option button.</span></span>

2. <span data-ttu-id="82bea-179">Zadejte cestu do textového pole **Vlastní cesta protokolu.**</span><span class="sxs-lookup"><span data-stu-id="82bea-179">Enter the path into the **Custom log path** text box.</span></span>

> [!NOTE]
> <span data-ttu-id="82bea-180">[Prohlížeč protokolů vazby sestavení (Fuslogvw.exe)](fuslogvw-exe-assembly-binding-log-viewer.md) používá mezipaměť aplikace Internet Explorer (IE) k ukládání protokolu vazby.</span><span class="sxs-lookup"><span data-stu-id="82bea-180">The [Assembly Binding Log Viewer (Fuslogvw.exe)](fuslogvw-exe-assembly-binding-log-viewer.md) uses the Internet Explorer (IE) cache to store its binding log.</span></span> <span data-ttu-id="82bea-181">Z důvodu občasného poškození mezipaměti aplikace IE může [prohlížeč protokolů vazby sestavení (Fuslogvw.exe)](fuslogvw-exe-assembly-binding-log-viewer.md) někdy přestat zobrazovat nové protokoly vazby v okně zobrazení.</span><span class="sxs-lookup"><span data-stu-id="82bea-181">Due to occasional corruption in the IE cache, the [Assembly Binding Log Viewer (Fuslogvw.exe)](fuslogvw-exe-assembly-binding-log-viewer.md) can sometimes stop showing new binding logs in the viewing window.</span></span> <span data-ttu-id="82bea-182">V důsledku tohoto poškození infrastruktura vazeb rozhraní .NET (Fusion) nemůže do protokolu vazeb zapisovat nebo číst.</span><span class="sxs-lookup"><span data-stu-id="82bea-182">As a result of this corruption, the .NET binding infrastructure (fusion) cannot write to or read from the binding log.</span></span> <span data-ttu-id="82bea-183">(Tento problém není zjištěn, pokud používáte vlastní cestu protokolu.)  Chcete-li opravit poškození a umožnit fúzi znovu zobrazit protokoly vazby, zrušte mezipaměť aplikace Internet odstraněním dočasných souborů Internetu z dialogového okna Možnosti Internetu aplikace Internet.</span><span class="sxs-lookup"><span data-stu-id="82bea-183">(This issue is not encountered if you use a custom log path.)  To fix the corruption and allow fusion to show binding logs again, clear the IE cache by deleting temporary internet files from within the IE Internet Options dialog.</span></span>
>
> <span data-ttu-id="82bea-184">Pokud vaše nespravovaná aplikace hostuje `IHostAssemblyManager` `IHostAssemblyStore` modul runtime společného jazyka implementací rozhraní a, položky protokolu nelze uložit do mezipaměti wininet.</span><span class="sxs-lookup"><span data-stu-id="82bea-184">If your unmanaged application hosts the common language runtime by implementing the `IHostAssemblyManager` and `IHostAssemblyStore` interfaces, log entries can't be stored in the wininet cache.</span></span>  <span data-ttu-id="82bea-185">Chcete-li zobrazit položky protokolu pro vlastní hostitele implementující tato rozhraní, je nutné zadat alternativní cestu k protokolu.</span><span class="sxs-lookup"><span data-stu-id="82bea-185">To view log entries for custom hosts that implement these interfaces, you must specify an alternate log path.</span></span>

#### <a name="to-enable-logging-for-apps-running-in-the-windows-app-container"></a><span data-ttu-id="82bea-186">Povolení protokolování pro aplikace spuštěné v kontejneru pro aplikace systému Windows</span><span class="sxs-lookup"><span data-stu-id="82bea-186">To enable logging for apps running in the Windows app container</span></span>

1. <span data-ttu-id="82bea-187">Povolte vlastní cestu protokolu, jak je popsáno v předchozí proceduře.</span><span class="sxs-lookup"><span data-stu-id="82bea-187">Enable a custom log path, as described in the previous procedure.</span></span> <span data-ttu-id="82bea-188">Ve výchozím nastavení mají aplikace spuštěné v kontejneru pro aplikace systému Windows omezený přístup na pevný disk.</span><span class="sxs-lookup"><span data-stu-id="82bea-188">By default, apps that are running in the Windows app container have limited access to the hard disk.</span></span> <span data-ttu-id="82bea-189">Zadaný adresář bude mít přístup pro čtení a zápis pro všechny aplikace v kontejneru aplikace.</span><span class="sxs-lookup"><span data-stu-id="82bea-189">The directory you specify will have read/write access for all apps in the app container.</span></span>

2. <span data-ttu-id="82bea-190">Zaškrtněte políčko Povolit pohlcující **protokolování.**</span><span class="sxs-lookup"><span data-stu-id="82bea-190">Select the **Enable immersive logging** check box.</span></span>

    > [!NOTE]
    > <span data-ttu-id="82bea-191">Toto pole je povoleno pouze v systému Windows 8 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="82bea-191">This box is enabled only on Windows 8 or later.</span></span>

## <a name="see-also"></a><span data-ttu-id="82bea-192">Viz také</span><span class="sxs-lookup"><span data-stu-id="82bea-192">See also</span></span>

- <xref:System.TypeLoadException>
- [<span data-ttu-id="82bea-193">Nástroje</span><span class="sxs-lookup"><span data-stu-id="82bea-193">Tools</span></span>](index.md)
- [<span data-ttu-id="82bea-194">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="82bea-194">Global Assembly Cache</span></span>](../app-domains/gac.md)
- [<span data-ttu-id="82bea-195">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="82bea-195">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="82bea-196">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="82bea-196">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
