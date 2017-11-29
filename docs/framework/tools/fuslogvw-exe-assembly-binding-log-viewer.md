---
title: "Fuslogvw.exe (prohlížeč protokolu vazby sestavení)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- failed assembly binds
- Fuslogvw.exe
- displaying failed assembly bind details
- assemblies [.NET Framework], failed assembly binds
- locating assemblies
- Assembly Binding Log Viewer
ms.assetid: e32fa443-0778-4cc3-bf36-5c8ea297d296
caps.latest.revision: "35"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ad02ade9c9e60e53fa8fb91d9a38d6ec12bc2e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="fuslogvwexe-assembly-binding-log-viewer"></a><span data-ttu-id="fd974-102">Fuslogvw.exe (prohlížeč protokolu vazby sestavení)</span><span class="sxs-lookup"><span data-stu-id="fd974-102">Fuslogvw.exe (Assembly Binding Log Viewer)</span></span>
<span data-ttu-id="fd974-103">Nástroj Assembly Binding Log Viewer zobrazuje podrobnosti o vazbách sestavení.</span><span class="sxs-lookup"><span data-stu-id="fd974-103">The Assembly Binding Log Viewer displays details for assembly binds.</span></span> <span data-ttu-id="fd974-104">Tyto informace vám pomohou diagnostikovat, proč rozhraní .NET Framework nemůže najít sestavení v době běhu.</span><span class="sxs-lookup"><span data-stu-id="fd974-104">This information helps you diagnose why the .NET Framework cannot locate an assembly at run time.</span></span> <span data-ttu-id="fd974-105">Tyto chyby jsou obvykle výsledkem nasazení sestavení na nesprávné místo, neplatné nativní bitové kopie nebo neshody čísel verzí nebo jazykových verzí.</span><span class="sxs-lookup"><span data-stu-id="fd974-105">These failures are usually the result of an assembly deployed to the wrong location, a native image that is no longer valid, or a mismatch in version numbers or cultures.</span></span> <span data-ttu-id="fd974-106">Modul common language runtime se nezdařilo najít sestavení obvykle objeví jako <xref:System.TypeLoadException> ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fd974-106">The common language runtime's failure to locate an assembly typically shows up as a <xref:System.TypeLoadException> in your application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fd974-107">Nástroj fuslogvw.exe je nutné spustit s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="fd974-107">You must run fuslogvw.exe with administrator privileges.</span></span>  
  
 <span data-ttu-id="fd974-108">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fd974-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="fd974-109">Chcete-li spustit tento nástroj, použijte příkazový řádek pro vývojáře (nebo příkazový řádek sady Visual Studio v systému Windows 7) s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="fd974-109">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7) with administrator credentials.</span></span> <span data-ttu-id="fd974-110">Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="fd974-110">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="fd974-111">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="fd974-111">At the command prompt, type the following:</span></span>  
  
```  
fuslogvw  
```  
  
 <span data-ttu-id="fd974-112">Prohlížeč zobrazí záznam pro každou nezdařenou vazbu sestavení.</span><span class="sxs-lookup"><span data-stu-id="fd974-112">The viewer displays an entry for each failed assembly bind.</span></span> <span data-ttu-id="fd974-113">Pro každou chybu prohlížeč vypíše aplikaci, která iniciovala tuto vazbu, sestavení, kterého se vazba týká, včetně názvu, verze, jazykové verze, veřejného klíče a data a času chyby.</span><span class="sxs-lookup"><span data-stu-id="fd974-113">For each failure, the viewer describes the application that initiated the bind; the assembly the bind is for, including name, version, culture and public key; and the date and time of the failure.</span></span>  
  
### <a name="to-change-the-log-location-view"></a><span data-ttu-id="fd974-114">Změna umístění zobrazení protokolu</span><span class="sxs-lookup"><span data-stu-id="fd974-114">To change the log location view</span></span>  
  
1.  <span data-ttu-id="fd974-115">Vyberte **výchozí** tlačítko Možnosti zobrazíte selhání vazby pro všechny typy aplikací.</span><span class="sxs-lookup"><span data-stu-id="fd974-115">Select the **Default** option button to view bind failures for all application types.</span></span> <span data-ttu-id="fd974-116">Položky protokolu jsou ve výchozím nastavení uloženy na disku do mezipaměti rozhraní wininet v adresářích jednotlivých uživatelů.</span><span class="sxs-lookup"><span data-stu-id="fd974-116">By default, log entries are stored in per-user directories on disk in the wininet cache.</span></span>  
  
2.  <span data-ttu-id="fd974-117">Vyberte **vlastní** tlačítko zobrazíte selhání vazby v vlastní adresář, který zadáte.</span><span class="sxs-lookup"><span data-stu-id="fd974-117">Select the **Custom** option button to view bind failures in a custom directory that you specify.</span></span> <span data-ttu-id="fd974-118">Je nutné zadat vlastní umístění, kam chcete ukládat protokoly nastavením umístění vlastní protokolu v modulu runtime **nastavení protokolu** dialogovém okně můžete platný název adresáře.</span><span class="sxs-lookup"><span data-stu-id="fd974-118">You must specify the custom location where you want the runtime to store the logs by setting the custom log location in the **Log Settings** dialog to a valid directory name.</span></span> <span data-ttu-id="fd974-119">Tento adresář by měl být prázdný a měl by obsahovat pouze soubory, které generuje modul runtime.</span><span class="sxs-lookup"><span data-stu-id="fd974-119">This directory should be clean, and only contain files that the runtime generates.</span></span> <span data-ttu-id="fd974-120">Pokud obsahuje spustitelný soubor, který generuje chybu do protokolu, tato chyba nebude protokolována, protože se nástroj pokusí vytvořit adresář se stejným názvem jako tento spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="fd974-120">If it contains an executable that generates a failure to be logged, the failure will not be logged because the tool tries to create a directory with the same name as the executable.</span></span> <span data-ttu-id="fd974-121">Kromě toho se nezdaří pokus o spuštění spustitelného souboru z umístění protokolu.</span><span class="sxs-lookup"><span data-stu-id="fd974-121">In addition, an attempt to run an executable from the log location will fail.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fd974-122">Výchozí umístění vazby je vhodnější než vlastní umístění vazby.</span><span class="sxs-lookup"><span data-stu-id="fd974-122">The default bind location is preferable to the custom bind location.</span></span> <span data-ttu-id="fd974-123">Modul runtime ukládá výchozí umístění vazby do mezipaměti rozhraní wininet, a proto vazbu automaticky odstraní. Pokud určíte vlastní umístění vazby, zodpovídáte za její odstranění.</span><span class="sxs-lookup"><span data-stu-id="fd974-123">The runtime stores the default bind location in the wininet cache, and therefore automatically cleans it out. If you specify a custom bind location, you are responsible for cleaning it out.</span></span>  
  
### <a name="to-view-details-about-a-specific-failure"></a><span data-ttu-id="fd974-124">Zobrazení podrobností o konkrétní chybě</span><span class="sxs-lookup"><span data-stu-id="fd974-124">To view details about a specific failure</span></span>  
  
1.  <span data-ttu-id="fd974-125">V prohlížeči vyberte název aplikace požadovaného záznamu.</span><span class="sxs-lookup"><span data-stu-id="fd974-125">Select the application name of the desired entry in the viewer.</span></span>  
  
2.  <span data-ttu-id="fd974-126">Klikněte **zobrazit protokol** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="fd974-126">Click the **View Log** button.</span></span> <span data-ttu-id="fd974-127">Záznam lze vybrat také dvojitým kliknutím.</span><span class="sxs-lookup"><span data-stu-id="fd974-127">Alternately, you can double-click the selected entry.</span></span>  
  
     <span data-ttu-id="fd974-128">Nástroj zobrazí následující podrobnosti o vybrané chybě vazby:</span><span class="sxs-lookup"><span data-stu-id="fd974-128">The tool displays the following details about the selected bind failure:</span></span>  
  
    -   <span data-ttu-id="fd974-129">Konkrétní důvod selhání vazby, například „soubor nebyl nalezen“ nebo „neshoda verzí“.</span><span class="sxs-lookup"><span data-stu-id="fd974-129">The specific reason the bind failed, such as "file not found" or "version mismatch".</span></span>  
  
    -   <span data-ttu-id="fd974-130">Informace o aplikaci, která iniciovala tuto vazbu, včetně jejího názvu, kořenového adresáře aplikace (AppBase) a popisu soukromé cesty hledání, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="fd974-130">Information about the application that initiated the bind, including its name, the application's root directory (AppBase), and a description of the private search path, if there is one.</span></span>  
  
    -   <span data-ttu-id="fd974-131">Identitu sestavení, které tento nástroj hledá.</span><span class="sxs-lookup"><span data-stu-id="fd974-131">The identity of the assembly the tool is looking for.</span></span>  
  
    -   <span data-ttu-id="fd974-132">Popis všech zásad aplikace, vydavatele nebo správce, které byly použity.</span><span class="sxs-lookup"><span data-stu-id="fd974-132">A description of any Application, Publisher, or Administrator version policies that have been applied.</span></span>  
  
    -   <span data-ttu-id="fd974-133">Zda je sestavení byl nalezen v [globální mezipaměť sestavení](../../../docs/framework/app-domains/gac.md).</span><span class="sxs-lookup"><span data-stu-id="fd974-133">Whether the assembly was found in the [global assembly cache](../../../docs/framework/app-domains/gac.md).</span></span>  
  
    -   <span data-ttu-id="fd974-134">Seznam všech zjišťovaných adres URL.</span><span class="sxs-lookup"><span data-stu-id="fd974-134">A list of all probing URLs.</span></span>  
  
 <span data-ttu-id="fd974-135">Následující ukázka položky protokolu zobrazuje detailní informace o selhání vazby sestavení.</span><span class="sxs-lookup"><span data-stu-id="fd974-135">The following sample log entry shows detailed information about a failed assembly bind.</span></span>  
  
```  
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
  
### <a name="to-delete-a-single-entry-from-the-log"></a><span data-ttu-id="fd974-136">Odstranění jednoho záznamu z protokolu</span><span class="sxs-lookup"><span data-stu-id="fd974-136">To delete a single entry from the log</span></span>  
  
1.  <span data-ttu-id="fd974-137">Vyberte záznam v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="fd974-137">Select an entry in the viewer.</span></span>  
  
2.  <span data-ttu-id="fd974-138">Klikněte **odstranit položku** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="fd974-138">Click the **Delete Entry** button.</span></span>  
  
### <a name="to-delete-all-entries-from-the-log"></a><span data-ttu-id="fd974-139">Odstranění všech záznamů z protokolu</span><span class="sxs-lookup"><span data-stu-id="fd974-139">To delete all entries from the log</span></span>  
  
-   <span data-ttu-id="fd974-140">Klikněte **odstranit všechny** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="fd974-140">Click the **Delete All** button.</span></span>  
  
### <a name="to-refresh-the-user-interface"></a><span data-ttu-id="fd974-141">Obnovení uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="fd974-141">To refresh the user interface</span></span>  
  
-   <span data-ttu-id="fd974-142">Klikněte **aktualizovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="fd974-142">Click the **Refresh** button.</span></span> <span data-ttu-id="fd974-143">Prohlížeč automaticky nerozpozná nové položky protokolu, pokud je spuštěn.</span><span class="sxs-lookup"><span data-stu-id="fd974-143">The viewer does not automatically detect new log entries while it is running.</span></span> <span data-ttu-id="fd974-144">Je nutné použít **aktualizovat** tlačítko zobrazit.</span><span class="sxs-lookup"><span data-stu-id="fd974-144">You must use the **Refresh** button to display them.</span></span>  
  
### <a name="to-change-the-log-settings"></a><span data-ttu-id="fd974-145">Změna nastavení protokolu</span><span class="sxs-lookup"><span data-stu-id="fd974-145">To change the log settings</span></span>  
  
-   <span data-ttu-id="fd974-146">Klikněte **nastavení** tlačítko Otevřít **nastavení protokolu** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="fd974-146">Click the **Settings** button to open the **Log Settings** dialog.</span></span>  
  
### <a name="to-view-the-about-dialog"></a><span data-ttu-id="fd974-147">Zobrazení dialogového okna O programu</span><span class="sxs-lookup"><span data-stu-id="fd974-147">To view the About dialog</span></span>  
  
-   <span data-ttu-id="fd974-148">Klikněte **o** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="fd974-148">Click the **About** button.</span></span>  
  
## <a name="binding-logs-for-native-images"></a><span data-ttu-id="fd974-149">Protokoly vazeb nativních bitových kopií</span><span class="sxs-lookup"><span data-stu-id="fd974-149">Binding Logs for Native Images</span></span>  
 <span data-ttu-id="fd974-150">Ve výchozím nastavení nástroj Fuslogvw.exe zaznamenává normální požadavky vazby sestavení.</span><span class="sxs-lookup"><span data-stu-id="fd974-150">By default, Fuslogvw.exe logs normal assembly bind requests.</span></span> <span data-ttu-id="fd974-151">Alternativně můžete protokolu vazby sestavení pro nativní bitové kopie, které byly vytvořené pomocí [Ngen.exe (Generátor nativních obrázků)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="fd974-151">Alternatively, you can log assembly binds for native images that were created using the [Ngen.exe (Native Image Generator)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>  
  
#### <a name="to-log-assembly-binds-for-native-images"></a><span data-ttu-id="fd974-152">Protokolování vazeb sestavení nativních bitových kopií</span><span class="sxs-lookup"><span data-stu-id="fd974-152">To log assembly binds for native images</span></span>  
  
-   <span data-ttu-id="fd974-153">V **kategorií protokolu** skupiny, vyberte **nativní bitové kopie** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="fd974-153">In the **Log Categories** group, select the **Native Images** option button.</span></span>  
  
 <span data-ttu-id="fd974-154">Následující protokol zobrazuje chybu způsobenou neexistující závislostí při vytvoření nativní bitové kopie pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fd974-154">The following log shows a failure caused by a dependency that did not exist when the native image was created for the application.</span></span> <span data-ttu-id="fd974-155">Pokud se tyto závislosti v době běhu liší od závislostí při spuštění nástroje Ngen.exe, vazba na nativní bitovou kopii není povolena.</span><span class="sxs-lookup"><span data-stu-id="fd974-155">If the dependencies at run time differ from the dependencies when Ngen.exe is run, binding to a native image is not allowed.</span></span>  
  
```  
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
  
 <span data-ttu-id="fd974-156">Následující protokol zobrazuje selhání vazby nativní bitové kopie, ke kterému došlo, protože nastavení zabezpečení počítače při spuštění aplikace se liší od nastavení zabezpečení v době, kdy byla tato nativní bitová kopie vytvořena.</span><span class="sxs-lookup"><span data-stu-id="fd974-156">The following log shows a native image binding failure that occurred because the security settings on the computer when the application was run were different from the security settings at the time the native image was created.</span></span>  
  
```  
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
  
## <a name="the-log-settings-dialog"></a><span data-ttu-id="fd974-157">Dialogové okno nastavení protokolu</span><span class="sxs-lookup"><span data-stu-id="fd974-157">The Log Settings Dialog</span></span>  
 <span data-ttu-id="fd974-158">Můžete použít **nastavení protokolu** dialogovém okně můžete provádět následující akce.</span><span class="sxs-lookup"><span data-stu-id="fd974-158">You can use the **Log Settings** dialog to perform the following actions.</span></span>  
  
#### <a name="to-disable-logging"></a><span data-ttu-id="fd974-159">Zákaz protokolování</span><span class="sxs-lookup"><span data-stu-id="fd974-159">To disable logging</span></span>  
  
-   <span data-ttu-id="fd974-160">Vyberte **protokolu zakázáno** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="fd974-160">Select the **Log disabled** option button.</span></span>  <span data-ttu-id="fd974-161">Tato možnost je ve výchozím stavu zvolena.</span><span class="sxs-lookup"><span data-stu-id="fd974-161">Note that this option is selected by default.</span></span>  
  
#### <a name="to-log-assembly-binds-in-exceptions"></a><span data-ttu-id="fd974-162">Protokolování vazby sestavení ve výjimkách</span><span class="sxs-lookup"><span data-stu-id="fd974-162">To log assembly binds in exceptions</span></span>  
  
-   <span data-ttu-id="fd974-163">Vyberte **přihlásit text výjimky** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="fd974-163">Select the **Log in exception text** option button.</span></span> <span data-ttu-id="fd974-164">Pouze nejméně podrobné informace protokolu jsou zaznamenány v textu výjimky.</span><span class="sxs-lookup"><span data-stu-id="fd974-164">Only the least detailed fusion log information is logged in exception text.</span></span> <span data-ttu-id="fd974-165">Chcete-li zobrazit úplné informace, použijte některé z dalších nastavení.</span><span class="sxs-lookup"><span data-stu-id="fd974-165">To view full information, use one of the other settings.</span></span>  
  
     <span data-ttu-id="fd974-166">Prohlédněte si důležitou poznámku týkající se sestavení, která jsou načtena jako doménově neutrální.</span><span class="sxs-lookup"><span data-stu-id="fd974-166">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>  
  
#### <a name="to-log-assembly-bind-failures"></a><span data-ttu-id="fd974-167">Protokolování selhání vazby sestavení</span><span class="sxs-lookup"><span data-stu-id="fd974-167">To log assembly bind failures</span></span>  
  
-   <span data-ttu-id="fd974-168">Vyberte **selhání vazby protokolu na disk** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="fd974-168">Select the **Log bind failures to disk** option button.</span></span>  
  
     <span data-ttu-id="fd974-169">Prohlédněte si důležitou poznámku týkající se sestavení, která jsou načtena jako doménově neutrální.</span><span class="sxs-lookup"><span data-stu-id="fd974-169">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>  
  
#### <a name="to-log-all-assembly-binds"></a><span data-ttu-id="fd974-170">Protokolování všech vazeb sestavení</span><span class="sxs-lookup"><span data-stu-id="fd974-170">To log all assembly binds</span></span>  
  
-   <span data-ttu-id="fd974-171">Vyberte **protokolu všechny vazby na disk** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="fd974-171">Select the **Log all binds to disk** option button.</span></span>  
  
     <span data-ttu-id="fd974-172">Prohlédněte si důležitou poznámku týkající se sestavení, která jsou načtena jako doménově neutrální.</span><span class="sxs-lookup"><span data-stu-id="fd974-172">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fd974-173">Když je načteno sestavení jako doména neutrální, například nastavením <xref:System.AppDomainSetup.LoaderOptimization%2A> vlastnost <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> nebo <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>, zapnout protokolování může nastat únik paměti v některých případech.</span><span class="sxs-lookup"><span data-stu-id="fd974-173">When an assembly is loaded as domain neutral, for example by setting the <xref:System.AppDomainSetup.LoaderOptimization%2A> property to <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> or <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>, turning on logging might leak memory in some cases.</span></span> <span data-ttu-id="fd974-174">K tomu může dojít, pokud je položka protokolu vytvořena při načtení doménově neutrálního modulu do domény aplikace a později, když je doména aplikace uvolněna.</span><span class="sxs-lookup"><span data-stu-id="fd974-174">This can happen if a log entry is made when a domain-neutral module is loaded into an application domain, and later the application domain is unloaded.</span></span> <span data-ttu-id="fd974-175">Položka protokolu nemusí být uvolněna až do ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="fd974-175">The log entry might not be released until the process ends.</span></span> <span data-ttu-id="fd974-176">Některé ladicí programy automaticky zapínají protokolování.</span><span class="sxs-lookup"><span data-stu-id="fd974-176">Some debuggers automatically turn on logging.</span></span>  
  
#### <a name="to-enable-a-custom-log-path"></a><span data-ttu-id="fd974-177">Povolení vlastní cesty protokolu</span><span class="sxs-lookup"><span data-stu-id="fd974-177">To enable a custom log path</span></span>  
  
1.  <span data-ttu-id="fd974-178">Vyberte **povolit vlastní protokol cesta** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="fd974-178">Select the **Enable custom log path** option button.</span></span>  
  
2.  <span data-ttu-id="fd974-179">Zadejte cestu do **cesta protokolu vlastní** textové pole.</span><span class="sxs-lookup"><span data-stu-id="fd974-179">Enter the path into the **Custom log path** text box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd974-180">[Prohlížeč protokolu vazby sestavení (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) používá mezipaměť Internet Explorer (IE) k uložení protokol vazby.</span><span class="sxs-lookup"><span data-stu-id="fd974-180">The [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) uses the Internet Explorer (IE) cache to store its binding log.</span></span> <span data-ttu-id="fd974-181">Kvůli příležitostně poškození v mezipaměti IE [Prohlížeč protokolu vazby sestavení (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) může někdy přestane zobrazovat text nové protokoly vazby v okně zobrazení.</span><span class="sxs-lookup"><span data-stu-id="fd974-181">Due to occasional corruption in the IE cache, the [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) can sometimes stop showing new binding logs in the viewing window.</span></span> <span data-ttu-id="fd974-182">V důsledku tohoto poškození infrastruktura vazeb rozhraní .NET (Fusion) nemůže do protokolu vazeb zapisovat nebo číst.</span><span class="sxs-lookup"><span data-stu-id="fd974-182">As a result of this corruption, the .NET binding infrastructure (fusion) cannot write to or read from the binding log.</span></span> <span data-ttu-id="fd974-183">(Při použití vlastní cesty protokolu k tomuto problému nedochází.)  Chcete-li opravit toto poškození a umožnit zobrazení protokolů vazeb, vymažte mezipaměť aplikace Internet Explorer (IE) odstraněním dočasných souborů internetu v dialogovém okně Možnosti Internetu.</span><span class="sxs-lookup"><span data-stu-id="fd974-183">(This issue is not encountered if you use a custom log path.)  To fix the corruption and allow fusion to show binding logs again, clear the IE cache by deleting temporary internet files from within the IE Internet Options dialog.</span></span>  
>   
>  <span data-ttu-id="fd974-184">Pokud vaše nespravované aplikace je hostitelem modul common language runtime implementací `IHostAssemblyManager` a `IHostAssemblyStore` rozhraní, položky protokolu nemůže být uložen do mezipaměti wininet.</span><span class="sxs-lookup"><span data-stu-id="fd974-184">If your unmanaged application hosts the common language runtime by implementing the `IHostAssemblyManager` and `IHostAssemblyStore` interfaces, log entries can't be stored in the wininet cache.</span></span>  <span data-ttu-id="fd974-185">Chcete-li zobrazit položky protokolu pro vlastní hostitele implementující tato rozhraní, je nutné zadat alternativní cestu k protokolu.</span><span class="sxs-lookup"><span data-stu-id="fd974-185">To view log entries for custom hosts that implement these interfaces, you must specify an alternate log path.</span></span>  
  
#### <a name="to-enable-logging-for-apps-running-in-the-windows-app-container"></a><span data-ttu-id="fd974-186">Povolení protokolování pro aplikace spuštěné v kontejneru pro aplikace systému Windows</span><span class="sxs-lookup"><span data-stu-id="fd974-186">To enable logging for apps running in the Windows app container</span></span>  
  
1.  <span data-ttu-id="fd974-187">Povolte vlastní cestu protokolu, jak je popsáno v předchozí proceduře.</span><span class="sxs-lookup"><span data-stu-id="fd974-187">Enable a custom log path, as described in the previous procedure.</span></span> <span data-ttu-id="fd974-188">Ve výchozím nastavení mají aplikace spuštěné v kontejneru pro aplikace systému Windows omezený přístup na pevný disk.</span><span class="sxs-lookup"><span data-stu-id="fd974-188">By default, apps that are running in the Windows app container have limited access to the hard disk.</span></span> <span data-ttu-id="fd974-189">Zadaný adresář bude mít přístup pro čtení a zápis pro všechny aplikace v kontejneru aplikace.</span><span class="sxs-lookup"><span data-stu-id="fd974-189">The directory you specify will have read/write access for all apps in the app container.</span></span>  
  
2.  <span data-ttu-id="fd974-190">Vyberte **dokonalé protokolování** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="fd974-190">Select the **Enable immersive logging** check box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fd974-191">Toto pole je povoleno pouze v systému Windows 8 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="fd974-191">This box is enabled only on Windows 8 or later.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd974-192">Viz také</span><span class="sxs-lookup"><span data-stu-id="fd974-192">See Also</span></span>  
 <xref:System.TypeLoadException>  
 [<span data-ttu-id="fd974-193">Nástroje</span><span class="sxs-lookup"><span data-stu-id="fd974-193">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="fd974-194">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="fd974-194">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)  
 [<span data-ttu-id="fd974-195">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="fd974-195">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="fd974-196">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="fd974-196">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
