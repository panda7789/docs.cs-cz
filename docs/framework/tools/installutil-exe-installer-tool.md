---
title: Installutil.exe (instalační nástroj)
ms.date: 03/30/2017
helpviewer_keywords:
- uninstalling server resources
- removing server resources
- status information for installation
- installation progress reports
- installing server resources
- Installer tool
- Installutil.exe
- files, Installer tool
- progress information for installation
- reporting installation progress
ms.assetid: 3f9d0533-f895-4897-b4ea-528284e0241d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cd7826581a8750d0c5bc87b6223d51eb2b6cce2
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221944"
---
# <a name="installutilexe-installer-tool"></a><span data-ttu-id="81d66-102">Installutil.exe (instalační nástroj)</span><span class="sxs-lookup"><span data-stu-id="81d66-102">Installutil.exe (Installer Tool)</span></span>
<span data-ttu-id="81d66-103">Instalační program je nástrojem příkazového řádku, který umožňuje nainstalovat a odinstalovat serverové zdroje spuštěním komponent nástroje v zadaných sestaveních.</span><span class="sxs-lookup"><span data-stu-id="81d66-103">The Installer tool is a command-line utility that allows you to install and uninstall server resources by executing the installer components in specified assemblies.</span></span> <span data-ttu-id="81d66-104">Tento nástroj funguje ve spojení s třídami v <xref:System.Configuration.Install> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="81d66-104">This tool works in conjunction with classes in the <xref:System.Configuration.Install> namespace.</span></span>  
  
 <span data-ttu-id="81d66-105">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="81d66-105">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="81d66-106">Ke spuštění nástroje, použijte příkazový řádek pro vývojáře pro Visual Studio (nebo příkazový řádek Visual Studio ve Windows 7).</span><span class="sxs-lookup"><span data-stu-id="81d66-106">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="81d66-107">Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="81d66-107">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="81d66-108">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="81d66-108">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81d66-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81d66-109">Syntax</span></span>  
  
```  
installutil [/u[ninstall]] [options] assembly [[options] assembly] ...  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81d66-110">Parametry</span><span class="sxs-lookup"><span data-stu-id="81d66-110">Parameters</span></span>  
  
|<span data-ttu-id="81d66-111">Argument</span><span class="sxs-lookup"><span data-stu-id="81d66-111">Argument</span></span>|<span data-ttu-id="81d66-112">Popis</span><span class="sxs-lookup"><span data-stu-id="81d66-112">Description</span></span>|  
|--------------|-----------------|  
|`assembly`|<span data-ttu-id="81d66-113">Název souboru sestavení, ve kterém se mají spustit komponenty instalačního programu.</span><span class="sxs-lookup"><span data-stu-id="81d66-113">The file name of the assembly in which to execute the installer components.</span></span> <span data-ttu-id="81d66-114">Tento parametr vynechat, pokud chcete zadat silný název sestavení pomocí `/AssemblyName` možnost.</span><span class="sxs-lookup"><span data-stu-id="81d66-114">Omit this parameter if you want to specify the assembly's strong name by using the `/AssemblyName` option.</span></span>|  
  
<a name="options"></a>   
## <a name="options"></a><span data-ttu-id="81d66-115">Možnosti</span><span class="sxs-lookup"><span data-stu-id="81d66-115">Options</span></span>  
  
|<span data-ttu-id="81d66-116">Možnost</span><span class="sxs-lookup"><span data-stu-id="81d66-116">Option</span></span>|<span data-ttu-id="81d66-117">Popis</span><span class="sxs-lookup"><span data-stu-id="81d66-117">Description</span></span>|  
|------------|-----------------|  
|`/h[elp]`<br /><br /> <span data-ttu-id="81d66-118">-nebo-</span><span class="sxs-lookup"><span data-stu-id="81d66-118">-or-</span></span><br /><br /> `/?`|<span data-ttu-id="81d66-119">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="81d66-119">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="81d66-120">`/help` *Sestavení*</span><span class="sxs-lookup"><span data-stu-id="81d66-120">`/help` *assembly*</span></span><br /><br /> <span data-ttu-id="81d66-121">-nebo-</span><span class="sxs-lookup"><span data-stu-id="81d66-121">-or-</span></span><br /><br /> <span data-ttu-id="81d66-122">`/?` *Sestavení*</span><span class="sxs-lookup"><span data-stu-id="81d66-122">`/?` *assembly*</span></span>|<span data-ttu-id="81d66-123">Zobrazí další možnosti, které jsou rozpoznávány jednotlivými instalačními programy v rámci zadaného sestavení, spolu se syntaxí a možnostmi příkazů pro soubor InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="81d66-123">Displays additional options recognized by individual installers within the specified assembly, along with command syntax and options for InstallUtil.exe.</span></span> <span data-ttu-id="81d66-124">Tato možnost přidá text vrácený každé komponenty instalačního programu <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> vlastnost textu nápovědy souboru InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="81d66-124">This option adds the text returned by each installer component's <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property to the help text of InstallUtil.exe.</span></span>|  
|<span data-ttu-id="81d66-125">`/AssemblyName` "*assemblyName*</span><span class="sxs-lookup"><span data-stu-id="81d66-125">`/AssemblyName` "*assemblyName*</span></span><br /><br /> <span data-ttu-id="81d66-126">,Version=*major.minor.build.revision*</span><span class="sxs-lookup"><span data-stu-id="81d66-126">,Version=*major.minor.build.revision*</span></span><br /><br /> <span data-ttu-id="81d66-127">, Jazyková verze =*národního prostředí*</span><span class="sxs-lookup"><span data-stu-id="81d66-127">,Culture=*locale*</span></span><br /><br /> <span data-ttu-id="81d66-128">,PublicKeyToken=*publicKeyToken*"</span><span class="sxs-lookup"><span data-stu-id="81d66-128">,PublicKeyToken=*publicKeyToken*"</span></span>|<span data-ttu-id="81d66-129">Udává silný název sestavení, které je třeba zaregistrovat v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="81d66-129">Specifies the strong name of an assembly, which must be registered in the global assembly cache.</span></span> <span data-ttu-id="81d66-130">Název sestavení musí být plně kvalifikovaný v souladu s verzí, jazykovou verzí a veřejným klíčem sestavení.</span><span class="sxs-lookup"><span data-stu-id="81d66-130">The assembly name must be fully qualified with the version, culture, and public key token of the assembly.</span></span> <span data-ttu-id="81d66-131">Plně kvalifikovaný název musí být v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="81d66-131">The fully qualified name must be surrounded by quotes.</span></span><br /><br /> <span data-ttu-id="81d66-132">Například „myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0“ je plně kvalifikovaný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="81d66-132">For example, "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0" is a fully qualified assembly name.</span></span>|  
|<span data-ttu-id="81d66-133">`/InstallStateDir=[` *NazevAdresare* `]`</span><span class="sxs-lookup"><span data-stu-id="81d66-133">`/InstallStateDir=[` *directoryName* `]`</span></span>|<span data-ttu-id="81d66-134">Určuje adresář souboru .InstallState, který obsahuje data používaná při odinstalování sestavení.</span><span class="sxs-lookup"><span data-stu-id="81d66-134">Specifies the directory of the .InstallState file that contains the data used to uninstall the assembly.</span></span> <span data-ttu-id="81d66-135">Ve výchozím nastavení je to adresář obsahující sestavení.</span><span class="sxs-lookup"><span data-stu-id="81d66-135">The default is the directory that contains the assembly.</span></span>|  
|<span data-ttu-id="81d66-136">`/LogFile=`[*filename*]</span><span class="sxs-lookup"><span data-stu-id="81d66-136">`/LogFile=`[*filename*]</span></span>|<span data-ttu-id="81d66-137">Určuje název souboru protokolu, do kterého je zaznamenán průběh instalace.</span><span class="sxs-lookup"><span data-stu-id="81d66-137">Specifies the name of the log file where installation progress is recorded.</span></span> <span data-ttu-id="81d66-138">Ve výchozím nastavení pokud `/LogFile` možnost vynecháte, soubor protokolu s názvem *assemblyname*. InstallLog se vytvoří.</span><span class="sxs-lookup"><span data-stu-id="81d66-138">By default, if the `/LogFile` option is omitted, a log file named *assemblyname*.InstallLog is created.</span></span> <span data-ttu-id="81d66-139">Pokud *filename* je tento parametr vynechán, je generována žádný soubor protokolu.</span><span class="sxs-lookup"><span data-stu-id="81d66-139">If *filename* is omitted, no log file is generated.</span></span>|  
|<span data-ttu-id="81d66-140">`/LogToConsole`={`true`&#124;`false`}</span><span class="sxs-lookup"><span data-stu-id="81d66-140">`/LogToConsole`={`true`&#124;`false`}</span></span>|<span data-ttu-id="81d66-141">Pokud `true`, výstup se vypíše do konzoly.</span><span class="sxs-lookup"><span data-stu-id="81d66-141">If `true`, displays output to the console.</span></span> <span data-ttu-id="81d66-142">Pokud `false` (výchozí), potlačí výstup na konzolu.</span><span class="sxs-lookup"><span data-stu-id="81d66-142">If `false` (the default), suppresses output to the console.</span></span>|  
|`/ShowCallStack`|<span data-ttu-id="81d66-143">Vypíše zásobník volání do souboru protokolu, jestliže v kterémkoli bodu instalace dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="81d66-143">Outputs the call stack to the log file if an exception occurs at any point during installation.</span></span>|  
|<span data-ttu-id="81d66-144">`/u`[`ninstall`]</span><span class="sxs-lookup"><span data-stu-id="81d66-144">`/u`[`ninstall`]</span></span>|<span data-ttu-id="81d66-145">Odinstaluje zadaná sestavení.</span><span class="sxs-lookup"><span data-stu-id="81d66-145">Uninstalls the specified assemblies.</span></span> <span data-ttu-id="81d66-146">Na rozdíl od ostatních možností `/u` vztahuje na všechna sestavení bez ohledu na to, kde se zobrazí možnost na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="81d66-146">Unlike the other options, `/u` applies to all assemblies regardless of where the option appears on the command line.</span></span>|  
  
<a name="cmdline"></a>   
## <a name="additional-installer-options"></a><span data-ttu-id="81d66-147">Další možnosti instalačního programu</span><span class="sxs-lookup"><span data-stu-id="81d66-147">Additional Installer Options</span></span>  
 <span data-ttu-id="81d66-148">Jednotlivé instalační programy používané v rámci sestavení pravděpodobně rozpoznávají možnosti kromě oprávnění uvedených v seznamu [možnosti](#options) oddílu.</span><span class="sxs-lookup"><span data-stu-id="81d66-148">Individual installers used within an assembly may recognize options in addition to those listed in the [Options](#options) section.</span></span> <span data-ttu-id="81d66-149">Další informace o těchto možnostech, spusťte soubor InstallUtil.exe s cestami sestavení na příkazovém řádku spolu s `/?` nebo `/help` možnost.</span><span class="sxs-lookup"><span data-stu-id="81d66-149">To learn about these options, run InstallUtil.exe with the paths of the assemblies on the command line along with the `/?` or `/help` option.</span></span> <span data-ttu-id="81d66-150">Chcete-li zadat tyto možnosti, přidejte je do příkazového řádku spolu s možnostmi rozeznávanými souborem InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="81d66-150">To specify these options, you include them on the command line along with the options recognized by InstallUtil.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81d66-151">Text nápovědy týkající se možností podporovaných jednotlivými komponentami instalačního programu je vrácený <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="81d66-151">Help text on the options supported by individual installer components is returned by the <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="81d66-152">Jsou přístupné prostřednictvím kódu programu z jednotlivých možností, které byly zadány v příkazovém řádku <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="81d66-152">The individual options that have been entered on the command line are accessible programmatically from the <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="81d66-153">Všechny možnosti a parametry příkazového řádku jsou zapsány do souboru protokolu instalace.</span><span class="sxs-lookup"><span data-stu-id="81d66-153">All options and command-line parameters are written to the installation log file.</span></span> <span data-ttu-id="81d66-154">Nicméně pokud použijete `/Password` parametr, který je rozpoznáván některými komponentami instalačního programu, informace o hesle se nahradí osmi hvězdičkami (\*) a nezobrazí se v souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="81d66-154">However, if you use the `/Password` parameter, which is recognized by some installer components, the password information will be replaced by eight asterisks (\*) and will not appear in the log file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="81d66-155">V některých případech parametry předávané instalačním programem mohou obsahovat citlivé údaje nebo informace umožňující identifikaci konkrétní osoby, které jsou ve výchozím nastavení zapsány do souboru protokolu jako prostý text.</span><span class="sxs-lookup"><span data-stu-id="81d66-155">In some cases, parameters passed to the installer may include sensitive or personally identifiable information, which, by default, is written to a plain text log file.</span></span> <span data-ttu-id="81d66-156">K takovému chování můžete potlačit soubor protokolu zadáním `/LogFile=` (bez *filename* argument) za Installutil.exe v příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="81d66-156">To prevent this behavior, you can suppress the log file by specifying `/LogFile=` (with no *filename* argument) after Installutil.exe on the command line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81d66-157">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81d66-157">Remarks</span></span>  
 <span data-ttu-id="81d66-158">Aplikace rozhraní .NET Framework se skládají z tradičních programových souborů a souvisejících zdrojů, jako jsou například fronty zpráv, protokoly událostí a čítače výkonu, které musí být vytvořeny při zavedení aplikace.</span><span class="sxs-lookup"><span data-stu-id="81d66-158">.NET Framework applications consist of traditional program files and associated resources, such as message queues, event logs, and performance counters that must be created when the application is deployed.</span></span> <span data-ttu-id="81d66-159">Pomocí komponent instalačního programu sestavení můžete vytvořit tyto zdroje při instalaci vaší aplikace a odstranit je při odinstalaci aplikace.</span><span class="sxs-lookup"><span data-stu-id="81d66-159">You can use an assembly's installer components to create these resources when your application is installed and to remove them when your application is uninstalled.</span></span> <span data-ttu-id="81d66-160">InstallUtil.exe rozpozná a spustí tyto komponenty instalačního programu.</span><span class="sxs-lookup"><span data-stu-id="81d66-160">Installutil.exe detects and executes these installer components.</span></span>  
  
 <span data-ttu-id="81d66-161">Do příkazového řádku můžete zadat několik sestavení najednou.</span><span class="sxs-lookup"><span data-stu-id="81d66-161">You can specify multiple assemblies on the same command line.</span></span> <span data-ttu-id="81d66-162">Každá možnost, která předchází název sestavení, se vztahuje na instalaci tohoto sestavení.</span><span class="sxs-lookup"><span data-stu-id="81d66-162">Any option that occurs before an assembly name applies to that assembly's installation.</span></span> <span data-ttu-id="81d66-163">S výjimkou `/u` a `/AssemblyName`, jsou možnosti kumulativní, ale overridable.</span><span class="sxs-lookup"><span data-stu-id="81d66-163">Except for `/u` and `/AssemblyName`, options are cumulative but overridable.</span></span> <span data-ttu-id="81d66-164">To znamená, že možnosti zadané pro jedno sestavení se vztahují na všechna následující sestavení, pokud dané možnosti není přidělena jiná hodnota.</span><span class="sxs-lookup"><span data-stu-id="81d66-164">That is, options specified for one assembly apply to all subsequent assemblies unless the option is specified with a new value.</span></span>  
  
 <span data-ttu-id="81d66-165">Pokud spustíte Installutil.exe proti sestavení bez zadání jakékoli možnosti, do adresáře sestavení se umístí následující tři soubory:</span><span class="sxs-lookup"><span data-stu-id="81d66-165">If you run Installutil.exe against an assembly without specifying any options, it places the following three files into the assembly's directory:</span></span>  
  
-   <span data-ttu-id="81d66-166">InstallUtil.InstallLog – obsahuje obecný popis průběhu instalace.</span><span class="sxs-lookup"><span data-stu-id="81d66-166">InstallUtil.InstallLog - Contains a general description of the installation progress.</span></span>  
  
-   <span data-ttu-id="81d66-167">*AssemblyName*. InstallLog – obsahuje informace specifické pro potvrzovací fáze procesu instalace.</span><span class="sxs-lookup"><span data-stu-id="81d66-167">*assemblyname*.InstallLog - Contains information specific to the commit phase of the installation process.</span></span> <span data-ttu-id="81d66-168">Další informace o potvrzovací fázi naleznete v tématu <xref:System.Configuration.Install.Installer.Commit%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="81d66-168">For more information about the commit phase, see the <xref:System.Configuration.Install.Installer.Commit%2A> method.</span></span>  
  
-   <span data-ttu-id="81d66-169">*AssemblyName*. InstallState - obsahuje data používaná při odinstalování sestavení.</span><span class="sxs-lookup"><span data-stu-id="81d66-169">*assemblyname*.InstallState - Contains data used to uninstall the assembly.</span></span>  
  
 <span data-ttu-id="81d66-170">InstallUtil.exe používá reflexi ke kontrole zadaného sestavení a k nalezení všech <xref:System.Configuration.Install.Installer> typy, které mají <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> atribut nastaven na `true`.</span><span class="sxs-lookup"><span data-stu-id="81d66-170">Installutil.exe uses reflection to inspect the specified assemblies and to find all <xref:System.Configuration.Install.Installer> types that have the <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> attribute set to `true`.</span></span> <span data-ttu-id="81d66-171">Tento nástroj poté spustí buď <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> nebo <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> metoda pro každou instanci <xref:System.Configuration.Install.Installer> typu.</span><span class="sxs-lookup"><span data-stu-id="81d66-171">The tool then executes either the <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> or the <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> method on each instance of the <xref:System.Configuration.Install.Installer> type.</span></span> <span data-ttu-id="81d66-172">InstallUtil.exe provede instalaci transakčním způsobem; to znamená, že pokud instalace jednoho sestavení selže, zruší instalace všech ostatních sestavení.</span><span class="sxs-lookup"><span data-stu-id="81d66-172">Installutil.exe performs installation in a transactional manner; that is, if one of the assemblies fails to install, it rolls back the installations of all other assemblies.</span></span> <span data-ttu-id="81d66-173">Odinstalování není transakční.</span><span class="sxs-lookup"><span data-stu-id="81d66-173">Uninstall is not transactional.</span></span>  
  
 <span data-ttu-id="81d66-174">Installutil.exe nemůže nainstalovat nebo odinstalovat sestavení se zpožděným podpisem, ale může nainstalovat nebo odinstalovat sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="81d66-174">Installutil.exe cannot install or uninstall delay-signed assemblies, but it can install or uninstall strong-named assemblies.</span></span>  
  
 <span data-ttu-id="81d66-175">Od rozhraní .NET Framework verze 2.0, je 32bitová verze Common Language Runtime (CLR) dodávána pouze s 32bitovou verzí instalačního programu, zatímco 64bitová verze CLR je dodávána s 32bitovou i 64bitovou verzí instalačního programu.</span><span class="sxs-lookup"><span data-stu-id="81d66-175">Starting with the .NET Framework version 2.0, the 32-bit version of the common language runtime (CLR) ships with only the 32-bit version of the Installer tool, but the 64-bit version of the CLR ships with both 32-bit and 64-bit versions of the Installer tool.</span></span> <span data-ttu-id="81d66-176">Jestliže používáte 64bitový CLR, 32bitová sestavení instalujte pomocí 32bitového instalačního programu a 64bitovou verzi instalačního programu použijte k instalaci 64bitových sestavení Microsoft Intermediate Language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="81d66-176">When using the 64-bit CLR, use the 32-bit Installer tool to install 32-bit assemblies, and the 64-bit Installer tool to install 64-bit and Microsoft intermediate language (MSIL) assemblies.</span></span> <span data-ttu-id="81d66-177">Obě verze instalačního programu se chovají stejně.</span><span class="sxs-lookup"><span data-stu-id="81d66-177">Both versions of the Installer tool behave the same.</span></span>  
  
 <span data-ttu-id="81d66-178">Installutil.exe nelze použít k nasazení služby systému Windows, která byla vytvořena pomocí C++, protože Installutil.exe nedokáže rozpoznat vložený nativní kód, který je vytvořen pomocí kompilátoru jazyka C++.</span><span class="sxs-lookup"><span data-stu-id="81d66-178">You cannot use Installutil.exe to deploy a Windows service that was created by using C++, because Installutil.exe cannot recognize the embedded native code that is produced by the C++ compiler.</span></span> <span data-ttu-id="81d66-179">Pokud se pokusíte nasadit službu C++ Windows pomocí Installutil.exe Výjimka jako například <xref:System.BadImageFormatException> bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="81d66-179">If you try to deploy a C++ Windows service with Installutil.exe, an exception such as <xref:System.BadImageFormatException> will be thrown.</span></span> <span data-ttu-id="81d66-180">V tomto případě přesuňte kód služby do modulu C++ a pak napište objekt instalačního programu v jazyce C# nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="81d66-180">To work with this scenario, move the service code to a C++ module, and then write the installer object in C# or Visual Basic.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="81d66-181">Příklady</span><span class="sxs-lookup"><span data-stu-id="81d66-181">Examples</span></span>  
 <span data-ttu-id="81d66-182">Následující příkaz zobrazí popis syntaxe příkazů a možností InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="81d66-182">The following command displays a description of the command syntax and options for InstallUtil.exe.</span></span>  
  
```  
installutil /?  
```  
  
 <span data-ttu-id="81d66-183">Následující příkaz zobrazí popis syntaxe příkazů a možností InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="81d66-183">The following command displays a description of the command syntax and options for InstallUtil.exe.</span></span> <span data-ttu-id="81d66-184">Zobrazuje také popis a seznam možností podporovaných příkazem součástmi instalačního programu v `myAssembly.exe` Pokud byla přiřazena text nápovědy instalačního programu <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="81d66-184">It also displays a description and list of options supported by the installer components in `myAssembly.exe` if help text has been assigned to the installer's <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property.</span></span>  
  
```  
installutil /? myAssembly.exe  
```  
  
 <span data-ttu-id="81d66-185">Následující příkaz spustí součásti instalačního programu v sestavení `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="81d66-185">The following command executes the installer components in the assembly `myAssembly.exe`.</span></span>  
  
```  
installutil myAssembly.exe  
```  
  
 <span data-ttu-id="81d66-186">Následující příkaz spustí součásti instalačního programu v sestavení s použitím `/AssemblyName` přepínače a plně kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="81d66-186">The following command executes the installer components in an assembly by using the `/AssemblyName` switch and a fully qualified name.</span></span>  
  
```  
installutil /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"  
```  
  
 <span data-ttu-id="81d66-187">Následující příkaz spustí součásti instalačního programu v sestavení určeném názvem souboru a v sestavení určeném silným názvem.</span><span class="sxs-lookup"><span data-stu-id="81d66-187">The following command executes the installer components in an assembly specified by file name and in an assembly specified by strong name.</span></span> <span data-ttu-id="81d66-188">Všimněte si, že všechna sestavení určená názvem souboru musí být uvedena před sestaveními určenými silným názvem v příkazovém řádku vzhledem k tomu, `/AssemblyName` možnost se nedá přepsat.</span><span class="sxs-lookup"><span data-stu-id="81d66-188">Note that all assemblies specified by file name must precede assemblies specified by strong name on the command line, because the `/AssemblyName` option cannot be overridden.</span></span>  
  
```  
installutil myAssembly.exe /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"  
```  
  
 <span data-ttu-id="81d66-189">Následující příkaz spustí součásti odinstalačního programu v sestavení `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="81d66-189">The following command executes the uninstaller components in the assembly `myAssembly.exe`.</span></span>  
  
```  
installutil /u myAssembly.exe   
```  
  
 <span data-ttu-id="81d66-190">Následující příkaz spustí součásti odinstalačního programu v sestaveních `myAssembly1.exe` a `myAssembly2.exe`.</span><span class="sxs-lookup"><span data-stu-id="81d66-190">The following command executes the uninistaller components in the assemblies `myAssembly1.exe` and `myAssembly2.exe`.</span></span>  
  
```  
installutil myAssembly1.exe /u myAssembly2.exe  
```  
  
 <span data-ttu-id="81d66-191">Protože pozice `/u` možnost na příkazovém řádku není důležitá, jedná se o ekvivalent následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="81d66-191">Because the position of the `/u` option on the command line is not important, this is equivalent to the following command.</span></span>  
  
```  
installutil /u myAssembly1.exe myAssembly2.exe  
```  
  
 <span data-ttu-id="81d66-192">Následující příkaz spustí instalační programy v sestavení `myAssembly.exe` a určuje, že informace o průběhu budou zapsány do `myLog.InstallLog`.</span><span class="sxs-lookup"><span data-stu-id="81d66-192">The following command executes the installers in the assembly `myAssembly.exe` and specifies that progress information will be written to `myLog.InstallLog`.</span></span>  
  
```  
installutil /LogFile=myLog.InstallLog myAssembly.exe   
```  
  
 <span data-ttu-id="81d66-193">Následující příkaz spustí instalační programy v sestavení `myAssembly.exe`, určuje, že informace o průběhu mají být zapsána do `myLog.InstallLog`a používá vlastní `/reg` možnost určit, zda má být aktualizován v systému registru.</span><span class="sxs-lookup"><span data-stu-id="81d66-193">The following command executes the installers in the assembly `myAssembly.exe`, specifies that progress information should be written to `myLog.InstallLog`, and uses the installers' custom `/reg` option to specify that updates should be made to the system registry.</span></span>  
  
```  
installutil /LogFile=myLog.InstallLog /reg=true myAssembly.exe  
```  
  
 <span data-ttu-id="81d66-194">Následující příkaz spustí instalační programy v sestavení `myAssembly.exe`, použití instalačního programu vlastní `/email` možnost zadat e-mailovou adresu uživatele a potlačuje výstup do souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="81d66-194">The following command executes the installers in the assembly `myAssembly.exe`, uses the installer's custom `/email` option to specify the user's email address, and suppresses output to the log file.</span></span>  
  
```  
installutil /LogFile= /email=admin@mycompany.com myAssembly.exe  
```  
  
 <span data-ttu-id="81d66-195">Následující příkaz zapíše postup instalace pro `myAssembly.exe` k `myLog.InstallLog` a zapíše postup pro `myTestAssembly.exe` k `myTestLog.InstallLog`.</span><span class="sxs-lookup"><span data-stu-id="81d66-195">The following command writes the installation progress for `myAssembly.exe` to `myLog.InstallLog` and writes the progress for `myTestAssembly.exe` to `myTestLog.InstallLog`.</span></span>  
  
```  
installutil /LogFile=myLog.InstallLog myAssembly.exe /LogFile=myTestLog.InstallLog myTestAssembly.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="81d66-196">Viz také</span><span class="sxs-lookup"><span data-stu-id="81d66-196">See Also</span></span>  
 <xref:System.Configuration.Install>  
 [<span data-ttu-id="81d66-197">Nástroje</span><span class="sxs-lookup"><span data-stu-id="81d66-197">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="81d66-198">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="81d66-198">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
