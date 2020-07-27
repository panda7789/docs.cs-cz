---
title: Installutil.exe (instalační nástroj)
description: Použijte Installutil.exe nástroj Installer Tool. Tento nástroj umožňuje nainstalovat nebo odinstalovat prostředky serveru spuštěním součástí instalačního programu v zadaných sestaveních.
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
ms.openlocfilehash: 042e5f64a7a863173db9c4e601d3152b0df46d97
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164445"
---
# <a name="installutilexe-installer-tool"></a><span data-ttu-id="5b1fc-104">Installutil.exe (instalační nástroj)</span><span class="sxs-lookup"><span data-stu-id="5b1fc-104">Installutil.exe (Installer Tool)</span></span>

<span data-ttu-id="5b1fc-105">Instalační program je nástrojem příkazového řádku, který umožňuje nainstalovat a odinstalovat serverové zdroje spuštěním komponent nástroje v zadaných sestaveních.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-105">The Installer tool is a command-line utility that allows you to install and uninstall server resources by executing the installer components in specified assemblies.</span></span> <span data-ttu-id="5b1fc-106">Tento nástroj funguje ve spojení se třídami v <xref:System.Configuration.Install> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-106">This tool works in conjunction with classes in the <xref:System.Configuration.Install> namespace.</span></span>

<span data-ttu-id="5b1fc-107">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="5b1fc-108">Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="5b1fc-108">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="5b1fc-109">Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="5b1fc-109">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="5b1fc-110">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="5b1fc-110">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="5b1fc-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b1fc-111">Syntax</span></span>

```console
installutil [/u[ninstall]] [options] assembly [[options] assembly] ...
```

## <a name="parameters"></a><span data-ttu-id="5b1fc-112">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b1fc-112">Parameters</span></span>

|<span data-ttu-id="5b1fc-113">Argument</span><span class="sxs-lookup"><span data-stu-id="5b1fc-113">Argument</span></span>|<span data-ttu-id="5b1fc-114">Popis</span><span class="sxs-lookup"><span data-stu-id="5b1fc-114">Description</span></span>|
|--------------|-----------------|
|`assembly`|<span data-ttu-id="5b1fc-115">Název souboru sestavení, ve kterém se mají spustit komponenty instalačního programu.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-115">The file name of the assembly in which to execute the installer components.</span></span> <span data-ttu-id="5b1fc-116">Tento parametr vynechejte, pokud chcete zadat silný název sestavení pomocí `/AssemblyName` Možnosti.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-116">Omit this parameter if you want to specify the assembly's strong name by using the `/AssemblyName` option.</span></span>|

<a name="options"></a>

## <a name="options"></a><span data-ttu-id="5b1fc-117">Možnosti</span><span class="sxs-lookup"><span data-stu-id="5b1fc-117">Options</span></span>

|<span data-ttu-id="5b1fc-118">Možnost</span><span class="sxs-lookup"><span data-stu-id="5b1fc-118">Option</span></span>|<span data-ttu-id="5b1fc-119">Popis</span><span class="sxs-lookup"><span data-stu-id="5b1fc-119">Description</span></span>|
|------------|-----------------|
|`/h[elp]`<br /><br /> <span data-ttu-id="5b1fc-120">-nebo-</span><span class="sxs-lookup"><span data-stu-id="5b1fc-120">-or-</span></span><br /><br /> `/?`|<span data-ttu-id="5b1fc-121">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-121">Displays command syntax and options for the tool.</span></span>|
|<span data-ttu-id="5b1fc-122">`/help`*sestavení*</span><span class="sxs-lookup"><span data-stu-id="5b1fc-122">`/help` *assembly*</span></span><br /><br /> <span data-ttu-id="5b1fc-123">-nebo-</span><span class="sxs-lookup"><span data-stu-id="5b1fc-123">-or-</span></span><br /><br /> <span data-ttu-id="5b1fc-124">`/?`*sestavení*</span><span class="sxs-lookup"><span data-stu-id="5b1fc-124">`/?` *assembly*</span></span>|<span data-ttu-id="5b1fc-125">Zobrazí další možnosti, které jsou rozpoznávány jednotlivými instalačními programy v rámci zadaného sestavení, spolu se syntaxí a možnostmi příkazů pro soubor InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-125">Displays additional options recognized by individual installers within the specified assembly, along with command syntax and options for InstallUtil.exe.</span></span> <span data-ttu-id="5b1fc-126">Tato možnost přidá text vrácený každou vlastností komponenty instalačního programu <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> do textu help InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-126">This option adds the text returned by each installer component's <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property to the help text of InstallUtil.exe.</span></span>|
|<span data-ttu-id="5b1fc-127">`/AssemblyName`*AssemblyName*</span><span class="sxs-lookup"><span data-stu-id="5b1fc-127">`/AssemblyName` "*assemblyName*</span></span><br /><br /> <span data-ttu-id="5b1fc-128">, Verze = hlavní_verze. podverze *. sestavení. revize*</span><span class="sxs-lookup"><span data-stu-id="5b1fc-128">,Version=*major.minor.build.revision*</span></span><br /><br /> <span data-ttu-id="5b1fc-129">, Culture =*locale*</span><span class="sxs-lookup"><span data-stu-id="5b1fc-129">,Culture=*locale*</span></span><br /><br /> <span data-ttu-id="5b1fc-130">, PublicKeyToken =*PublicKeyToken*</span><span class="sxs-lookup"><span data-stu-id="5b1fc-130">,PublicKeyToken=*publicKeyToken*"</span></span>|<span data-ttu-id="5b1fc-131">Udává silný název sestavení, které je třeba zaregistrovat v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="5b1fc-131">Specifies the strong name of an assembly, which must be registered in the global assembly cache.</span></span> <span data-ttu-id="5b1fc-132">Název sestavení musí být plně kvalifikovaný v souladu s verzí, jazykovou verzí a veřejným klíčem sestavení.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-132">The assembly name must be fully qualified with the version, culture, and public key token of the assembly.</span></span> <span data-ttu-id="5b1fc-133">Plně kvalifikovaný název musí být v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-133">The fully qualified name must be surrounded by quotes.</span></span><br /><br /> <span data-ttu-id="5b1fc-134">Například „myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0“ je plně kvalifikovaný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-134">For example, "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0" is a fully qualified assembly name.</span></span>|
|<span data-ttu-id="5b1fc-135">`/InstallStateDir=[`*adresář*`]`</span><span class="sxs-lookup"><span data-stu-id="5b1fc-135">`/InstallStateDir=[` *directoryName* `]`</span></span>|<span data-ttu-id="5b1fc-136">Určuje adresář souboru .InstallState, který obsahuje data používaná při odinstalování sestavení.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-136">Specifies the directory of the .InstallState file that contains the data used to uninstall the assembly.</span></span> <span data-ttu-id="5b1fc-137">Ve výchozím nastavení je to adresář obsahující sestavení.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-137">The default is the directory that contains the assembly.</span></span>|
|<span data-ttu-id="5b1fc-138">`/LogFile=`[*filename*]</span><span class="sxs-lookup"><span data-stu-id="5b1fc-138">`/LogFile=`[*filename*]</span></span>|<span data-ttu-id="5b1fc-139">Určuje název souboru protokolu, do kterého je zaznamenán průběh instalace.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-139">Specifies the name of the log file where installation progress is recorded.</span></span> <span data-ttu-id="5b1fc-140">Ve výchozím nastavení, pokud `/LogFile` je tato možnost vynechána, soubor protokolu s názvem *AssemblyName*. InstallLog se vytvoří.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-140">By default, if the `/LogFile` option is omitted, a log file named *assemblyname*.InstallLog is created.</span></span> <span data-ttu-id="5b1fc-141">Pokud je *název souboru* vynechán, nevygeneruje se žádný soubor protokolu.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-141">If *filename* is omitted, no log file is generated.</span></span>|
|<span data-ttu-id="5b1fc-142">`/LogToConsole`= { `true`&#124;`false` }</span><span class="sxs-lookup"><span data-stu-id="5b1fc-142">`/LogToConsole`={`true`&#124;`false`}</span></span>|<span data-ttu-id="5b1fc-143">Pokud `true` se zobrazí výstup do konzoly nástroje.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-143">If `true`, displays output to the console.</span></span> <span data-ttu-id="5b1fc-144">Pokud `false` (výchozí), potlačí výstup do konzoly.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-144">If `false` (the default), suppresses output to the console.</span></span>|
|`/ShowCallStack`|<span data-ttu-id="5b1fc-145">Vypíše zásobník volání do souboru protokolu, jestliže v kterémkoli bodu instalace dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-145">Outputs the call stack to the log file if an exception occurs at any point during installation.</span></span>|
|<span data-ttu-id="5b1fc-146">`/u`[`ninstall`]</span><span class="sxs-lookup"><span data-stu-id="5b1fc-146">`/u`[`ninstall`]</span></span>|<span data-ttu-id="5b1fc-147">Odinstaluje zadaná sestavení.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-147">Uninstalls the specified assemblies.</span></span> <span data-ttu-id="5b1fc-148">Na rozdíl od jiných možností `/u` platí pro všechna sestavení bez ohledu na to, kde se možnost zobrazí na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-148">Unlike the other options, `/u` applies to all assemblies regardless of where the option appears on the command line.</span></span>|

<a name="cmdline"></a>

## <a name="additional-installer-options"></a><span data-ttu-id="5b1fc-149">Další možnosti instalačního programu</span><span class="sxs-lookup"><span data-stu-id="5b1fc-149">Additional Installer Options</span></span>

<span data-ttu-id="5b1fc-150">Jednotlivé instalační programy používané v rámci sestavení mohou kromě těch, které jsou uvedeny v části [Možnosti](#options) , rozpoznat i možnosti.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-150">Individual installers used within an assembly may recognize options in addition to those listed in the [Options](#options) section.</span></span> <span data-ttu-id="5b1fc-151">Chcete-li získat informace o těchto možnostech, spusťte InstallUtil.exe s cestami sestavení na příkazovém řádku spolu s `/?` možností nebo `/help` .</span><span class="sxs-lookup"><span data-stu-id="5b1fc-151">To learn about these options, run InstallUtil.exe with the paths of the assemblies on the command line along with the `/?` or `/help` option.</span></span> <span data-ttu-id="5b1fc-152">Chcete-li zadat tyto možnosti, přidejte je do příkazového řádku spolu s možnostmi rozeznávanými souborem InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-152">To specify these options, you include them on the command line along with the options recognized by InstallUtil.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="5b1fc-153">Tato vlastnost vrací text Help na možnostech podporovaných jednotlivými součástmi instalačního programu <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5b1fc-153">Help text on the options supported by individual installer components is returned by the <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="5b1fc-154">Jednotlivé možnosti, které byly zadány na příkazovém řádku, jsou přístupné z vlastnosti programově <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5b1fc-154">The individual options that have been entered on the command line are accessible programmatically from the <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="5b1fc-155">Všechny možnosti a parametry příkazového řádku jsou zapsány do souboru protokolu instalace.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-155">All options and command-line parameters are written to the installation log file.</span></span> <span data-ttu-id="5b1fc-156">Pokud však použijete `/Password` parametr, který je rozpoznáván některými komponentami instalačního programu, informace o hesle budou nahrazeny osmi hvězdičkami (\*) a nezobrazí se v souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-156">However, if you use the `/Password` parameter, which is recognized by some installer components, the password information will be replaced by eight asterisks (\*) and will not appear in the log file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b1fc-157">V některých případech parametry předávané instalačním programem mohou obsahovat citlivé údaje nebo informace umožňující identifikaci konkrétní osoby, které jsou ve výchozím nastavení zapsány do souboru protokolu jako prostý text.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-157">In some cases, parameters passed to the installer may include sensitive or personally identifiable information, which, by default, is written to a plain text log file.</span></span> <span data-ttu-id="5b1fc-158">Chcete-li zabránit tomuto chování, můžete soubor protokolu potlačit zadáním `/LogFile=` (bez argumentu *filename* ) po Installutil.exe v příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-158">To prevent this behavior, you can suppress the log file by specifying `/LogFile=` (with no *filename* argument) after Installutil.exe on the command line.</span></span>

## <a name="remarks"></a><span data-ttu-id="5b1fc-159">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b1fc-159">Remarks</span></span>

<span data-ttu-id="5b1fc-160">Aplikace rozhraní .NET Framework se skládají z tradičních programových souborů a souvisejících zdrojů, jako jsou například fronty zpráv, protokoly událostí a čítače výkonu, které musí být vytvořeny při zavedení aplikace.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-160">.NET Framework applications consist of traditional program files and associated resources, such as message queues, event logs, and performance counters that must be created when the application is deployed.</span></span> <span data-ttu-id="5b1fc-161">Pomocí komponent instalačního programu sestavení můžete vytvořit tyto zdroje při instalaci vaší aplikace a odstranit je při odinstalaci aplikace.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-161">You can use an assembly's installer components to create these resources when your application is installed and to remove them when your application is uninstalled.</span></span> <span data-ttu-id="5b1fc-162">InstallUtil.exe rozpozná a spustí tyto komponenty instalačního programu.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-162">Installutil.exe detects and executes these installer components.</span></span>

<span data-ttu-id="5b1fc-163">Do příkazového řádku můžete zadat několik sestavení najednou.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-163">You can specify multiple assemblies on the same command line.</span></span> <span data-ttu-id="5b1fc-164">Každá možnost, která předchází název sestavení, se vztahuje na instalaci tohoto sestavení.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-164">Any option that occurs before an assembly name applies to that assembly's installation.</span></span> <span data-ttu-id="5b1fc-165">S výjimkou `/u` a `/AssemblyName` jsou možnosti kumulativní, ale lze přepsat.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-165">Except for `/u` and `/AssemblyName`, options are cumulative but overridable.</span></span> <span data-ttu-id="5b1fc-166">To znamená, že možnosti zadané pro jedno sestavení se vztahují na všechna následující sestavení, pokud dané možnosti není přidělena jiná hodnota.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-166">That is, options specified for one assembly apply to all subsequent assemblies unless the option is specified with a new value.</span></span>

<span data-ttu-id="5b1fc-167">Pokud spustíte Installutil.exe proti sestavení bez zadání jakékoli možnosti, do adresáře sestavení se umístí následující tři soubory:</span><span class="sxs-lookup"><span data-stu-id="5b1fc-167">If you run Installutil.exe against an assembly without specifying any options, it places the following three files into the assembly's directory:</span></span>

- <span data-ttu-id="5b1fc-168">InstallUtil.InstallLog – obsahuje obecný popis průběhu instalace.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-168">InstallUtil.InstallLog - Contains a general description of the installation progress.</span></span>

- <span data-ttu-id="5b1fc-169">*AssemblyName*. InstallLog – obsahuje informace specifické pro potvrzovací fázi procesu instalace.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-169">*assemblyname*.InstallLog - Contains information specific to the commit phase of the installation process.</span></span> <span data-ttu-id="5b1fc-170">Další informace o potvrzovací fázi naleznete v <xref:System.Configuration.Install.Installer.Commit%2A> metodě.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-170">For more information about the commit phase, see the <xref:System.Configuration.Install.Installer.Commit%2A> method.</span></span>

- <span data-ttu-id="5b1fc-171">*AssemblyName*. InstallState – obsahuje data, která se používají k odinstalování sestavení.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-171">*assemblyname*.InstallState - Contains data used to uninstall the assembly.</span></span>

<span data-ttu-id="5b1fc-172">Installutil.exe používá reflexi ke kontrole zadaných sestavení a k nalezení všech <xref:System.Configuration.Install.Installer> typů, které mají <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> atribut nastaven na `true` .</span><span class="sxs-lookup"><span data-stu-id="5b1fc-172">Installutil.exe uses reflection to inspect the specified assemblies and to find all <xref:System.Configuration.Install.Installer> types that have the <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> attribute set to `true`.</span></span> <span data-ttu-id="5b1fc-173">Nástroj pak provede buď metodu, <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> nebo <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> v každé instanci <xref:System.Configuration.Install.Installer> typu.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-173">The tool then executes either the <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> or the <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> method on each instance of the <xref:System.Configuration.Install.Installer> type.</span></span> <span data-ttu-id="5b1fc-174">InstallUtil.exe provede instalaci transakčním způsobem; to znamená, že pokud instalace jednoho sestavení selže, zruší instalace všech ostatních sestavení.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-174">Installutil.exe performs installation in a transactional manner; that is, if one of the assemblies fails to install, it rolls back the installations of all other assemblies.</span></span> <span data-ttu-id="5b1fc-175">Odinstalování není transakční.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-175">Uninstall is not transactional.</span></span>

<span data-ttu-id="5b1fc-176">Installutil.exe nemůže nainstalovat nebo odinstalovat sestavení se zpožděným podpisem, ale může nainstalovat nebo odinstalovat sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-176">Installutil.exe cannot install or uninstall delay-signed assemblies, but it can install or uninstall strong-named assemblies.</span></span>

<span data-ttu-id="5b1fc-177">Od rozhraní .NET Framework verze 2.0, je 32bitová verze Common Language Runtime (CLR) dodávána pouze s 32bitovou verzí instalačního programu, zatímco 64bitová verze CLR je dodávána s 32bitovou i 64bitovou verzí instalačního programu.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-177">Starting with the .NET Framework version 2.0, the 32-bit version of the common language runtime (CLR) ships with only the 32-bit version of the Installer tool, but the 64-bit version of the CLR ships with both 32-bit and 64-bit versions of the Installer tool.</span></span> <span data-ttu-id="5b1fc-178">Jestliže používáte 64bitový CLR, 32bitová sestavení instalujte pomocí 32bitového instalačního programu a 64bitovou verzi instalačního programu použijte k instalaci 64bitových sestavení Microsoft Intermediate Language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="5b1fc-178">When using the 64-bit CLR, use the 32-bit Installer tool to install 32-bit assemblies, and the 64-bit Installer tool to install 64-bit and Microsoft intermediate language (MSIL) assemblies.</span></span> <span data-ttu-id="5b1fc-179">Obě verze instalačního programu se chovají stejně.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-179">Both versions of the Installer tool behave the same.</span></span>

<span data-ttu-id="5b1fc-180">Installutil.exe nelze použít k nasazení služby systému Windows, která byla vytvořena pomocí C++, protože Installutil.exe nedokáže rozpoznat vložený nativní kód, který je vytvořen pomocí kompilátoru jazyka C++.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-180">You cannot use Installutil.exe to deploy a Windows service that was created by using C++, because Installutil.exe cannot recognize the embedded native code that is produced by the C++ compiler.</span></span> <span data-ttu-id="5b1fc-181">Pokud se pokusíte nasadit službu Windows C++ pomocí Installutil.exe, bude vyvolána výjimka, jako například <xref:System.BadImageFormatException> .</span><span class="sxs-lookup"><span data-stu-id="5b1fc-181">If you try to deploy a C++ Windows service with Installutil.exe, an exception such as <xref:System.BadImageFormatException> will be thrown.</span></span> <span data-ttu-id="5b1fc-182">V tomto případě přesuňte kód služby do modulu C++ a pak napište objekt instalačního programu v jazyce C# nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-182">To work with this scenario, move the service code to a C++ module, and then write the installer object in C# or Visual Basic.</span></span>

## <a name="examples"></a><span data-ttu-id="5b1fc-183">Příklady</span><span class="sxs-lookup"><span data-stu-id="5b1fc-183">Examples</span></span>

<span data-ttu-id="5b1fc-184">Následující příkaz zobrazí popis syntaxe příkazů a možností InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-184">The following command displays a description of the command syntax and options for InstallUtil.exe.</span></span>

```console
installutil /?
```

<span data-ttu-id="5b1fc-185">Následující příkaz zobrazí popis syntaxe příkazů a možností InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-185">The following command displays a description of the command syntax and options for InstallUtil.exe.</span></span> <span data-ttu-id="5b1fc-186">Také se zobrazí popis a seznam možností podporovaných součástmi instalační služby v nástroji, `myAssembly.exe` Pokud byl text zprávy přiřazen vlastnosti instalačního programu <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5b1fc-186">It also displays a description and list of options supported by the installer components in `myAssembly.exe` if help text has been assigned to the installer's <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property.</span></span>

```console
installutil /? myAssembly.exe
```

<span data-ttu-id="5b1fc-187">Následující příkaz spustí součásti instalačního programu v sestavení `myAssembly.exe` .</span><span class="sxs-lookup"><span data-stu-id="5b1fc-187">The following command executes the installer components in the assembly `myAssembly.exe`.</span></span>

```console
installutil myAssembly.exe
```

<span data-ttu-id="5b1fc-188">Následující příkaz spustí komponenty instalačního programu v sestavení pomocí `/AssemblyName` přepínače a plně kvalifikovaného názvu.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-188">The following command executes the installer components in an assembly by using the `/AssemblyName` switch and a fully qualified name.</span></span>

```console
installutil /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

<span data-ttu-id="5b1fc-189">Následující příkaz spustí součásti instalačního programu v sestavení určeném názvem souboru a v sestavení určeném silným názvem.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-189">The following command executes the installer components in an assembly specified by file name and in an assembly specified by strong name.</span></span> <span data-ttu-id="5b1fc-190">Všimněte si, že všechna sestavení určená názvem souboru musí předcházet sestavení zadaným silným názvem na příkazovém řádku, protože `/AssemblyName` možnost nelze přepsat.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-190">Note that all assemblies specified by file name must precede assemblies specified by strong name on the command line, because the `/AssemblyName` option cannot be overridden.</span></span>

```console
installutil myAssembly.exe /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

<span data-ttu-id="5b1fc-191">Následující příkaz spustí součásti odinstalačního nástroje v sestavení `myAssembly.exe` .</span><span class="sxs-lookup"><span data-stu-id="5b1fc-191">The following command executes the uninstaller components in the assembly `myAssembly.exe`.</span></span>

```console
installutil /u myAssembly.exe
```

<span data-ttu-id="5b1fc-192">Následující příkaz spustí součásti odinstalačního nástroje v sestaveních `myAssembly1.exe` a `myAssembly2.exe` .</span><span class="sxs-lookup"><span data-stu-id="5b1fc-192">The following command executes the uninstaller components in the assemblies `myAssembly1.exe` and `myAssembly2.exe`.</span></span>

```console
installutil myAssembly1.exe /u myAssembly2.exe
```

<span data-ttu-id="5b1fc-193">Protože pozice `/u` Možnosti na příkazovém řádku není důležitá, jedná se o ekvivalent následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-193">Because the position of the `/u` option on the command line is not important, this is equivalent to the following command.</span></span>

```console
installutil /u myAssembly1.exe myAssembly2.exe
```

<span data-ttu-id="5b1fc-194">Následující příkaz spustí instalační programy v sestavení `myAssembly.exe` a určí, že informace o průběhu budou zapsány do `myLog.InstallLog` .</span><span class="sxs-lookup"><span data-stu-id="5b1fc-194">The following command executes the installers in the assembly `myAssembly.exe` and specifies that progress information will be written to `myLog.InstallLog`.</span></span>

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe
```

<span data-ttu-id="5b1fc-195">Následující příkaz spustí instalační programy v sestavení `myAssembly.exe` , určí, zda mají být do nástroje zapisovány informace o průběhu `myLog.InstallLog` , a pomocí vlastní možnosti instalační program `/reg` určí, zda mají být aktualizace provedeny v registru systému.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-195">The following command executes the installers in the assembly `myAssembly.exe`, specifies that progress information should be written to `myLog.InstallLog`, and uses the installers' custom `/reg` option to specify that updates should be made to the system registry.</span></span>

```console
installutil /LogFile=myLog.InstallLog /reg=true myAssembly.exe
```

<span data-ttu-id="5b1fc-196">Následující příkaz spustí instalační programy v sestavení `myAssembly.exe` , použije vlastní možnost instalačního programu `/email` k zadání e-mailové adresy uživatele a potlačí výstup do souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="5b1fc-196">The following command executes the installers in the assembly `myAssembly.exe`, uses the installer's custom `/email` option to specify the user's email address, and suppresses output to the log file.</span></span>

```console
installutil /LogFile= /email=admin@mycompany.com myAssembly.exe
```

<span data-ttu-id="5b1fc-197">Následující příkaz zapíše průběh instalace pro a `myAssembly.exe` `myLog.InstallLog` zapíše průběh pro `myTestAssembly.exe` do `myTestLog.InstallLog` .</span><span class="sxs-lookup"><span data-stu-id="5b1fc-197">The following command writes the installation progress for `myAssembly.exe` to `myLog.InstallLog` and writes the progress for `myTestAssembly.exe` to `myTestLog.InstallLog`.</span></span>

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe /LogFile=myTestLog.InstallLog myTestAssembly.exe
```

## <a name="see-also"></a><span data-ttu-id="5b1fc-198">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b1fc-198">See also</span></span>

- <xref:System.Configuration.Install>
- [<span data-ttu-id="5b1fc-199">Nástroje</span><span class="sxs-lookup"><span data-stu-id="5b1fc-199">Tools</span></span>](index.md)
- [<span data-ttu-id="5b1fc-200">Výzvy příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="5b1fc-200">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
