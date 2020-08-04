---
title: Regsvcs.exe (nástroj pro instalaci služeb .NET)
description: Použijte Regsvcs.exe nástroje pro instalaci služeb .NET. Načíst a zaregistrovat sestavení, nakonfigurovat služby, které jste přidali programově do třídy a další.
ms.date: 03/30/2017
helpviewer_keywords:
- Regsvcs.exe
- .NET Services Installation tool
- loading assemblies
- assemblies [.NET Framework], registering
- type libraries
- registering assemblies
ms.assetid: 5220fe58-5aaf-4e8e-8bc3-b78c63025804
ms.openlocfilehash: 6d0090eda764113407e35a3bcec139f1c7cfb050
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517240"
---
# <a name="regsvcsexe-net-services-installation-tool"></a><span data-ttu-id="1c252-104">Regsvcs.exe (nástroj pro instalaci služeb .NET)</span><span class="sxs-lookup"><span data-stu-id="1c252-104">Regsvcs.exe (.NET Services Installation Tool)</span></span>
<span data-ttu-id="1c252-105">Instalační nástroj .NET Services vykonává tyto akce:</span><span class="sxs-lookup"><span data-stu-id="1c252-105">The .NET Services Installation tool performs the following actions:</span></span>  
  
- <span data-ttu-id="1c252-106">Načítá a registruje sestavení.</span><span class="sxs-lookup"><span data-stu-id="1c252-106">Loads and registers an assembly.</span></span>  
  
- <span data-ttu-id="1c252-107">Vytváří, registruje a instaluje knihovnu typů do zadané aplikace modelu COM+.</span><span class="sxs-lookup"><span data-stu-id="1c252-107">Generates, registers, and installs a type library into a specified COM+ application.</span></span>  
  
- <span data-ttu-id="1c252-108">Konfiguruje služby, které jste přidali pomocí programu do vaší třídy.</span><span class="sxs-lookup"><span data-stu-id="1c252-108">Configures services that you have added programmatically to your class.</span></span>  
  
 <span data-ttu-id="1c252-109">Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="1c252-109">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="1c252-110">Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="1c252-110">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="1c252-111">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="1c252-111">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c252-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c252-112">Syntax</span></span>  
  
```console  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll
```  
  
## <a name="parameters"></a><span data-ttu-id="1c252-113">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c252-113">Parameters</span></span>  
  
|<span data-ttu-id="1c252-114">Argument</span><span class="sxs-lookup"><span data-stu-id="1c252-114">Argument</span></span>|<span data-ttu-id="1c252-115">Description</span><span class="sxs-lookup"><span data-stu-id="1c252-115">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="1c252-116">*assemblyFile.dll*</span><span class="sxs-lookup"><span data-stu-id="1c252-116">*assemblyFile.dll*</span></span>|<span data-ttu-id="1c252-117">Zdrojový soubor sestavení.</span><span class="sxs-lookup"><span data-stu-id="1c252-117">The source assembly file.</span></span> <span data-ttu-id="1c252-118">Sestavení musí být podepsáno silným názvem.</span><span class="sxs-lookup"><span data-stu-id="1c252-118">The assembly must be signed with a strong name.</span></span> <span data-ttu-id="1c252-119">Další informace naleznete v tématu [podepisování sestavení silným názvem](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="1c252-119">For more information, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span>|  
  
|<span data-ttu-id="1c252-120">Možnost</span><span class="sxs-lookup"><span data-stu-id="1c252-120">Option</span></span>|<span data-ttu-id="1c252-121">Popis</span><span class="sxs-lookup"><span data-stu-id="1c252-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="1c252-122">**/appdir:** *cesta*</span><span class="sxs-lookup"><span data-stu-id="1c252-122">**/appdir:** *path*</span></span>|<span data-ttu-id="1c252-123">Určuje kořenový adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="1c252-123">Specifies the root directory of the application.</span></span>|  
|<span data-ttu-id="1c252-124">**/AppName:** *ApplicationName*</span><span class="sxs-lookup"><span data-stu-id="1c252-124">**/appname:** *applicationName*</span></span>|<span data-ttu-id="1c252-125">Určuje název aplikace modelu COM+, která se má vyhledat nebo vytvořit.</span><span class="sxs-lookup"><span data-stu-id="1c252-125">Specifies the name of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="1c252-126">**/c**</span><span class="sxs-lookup"><span data-stu-id="1c252-126">**/c**</span></span>|<span data-ttu-id="1c252-127">Vytvoří cílovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1c252-127">Creates the target application.</span></span>|  
|<span data-ttu-id="1c252-128">**/componly**</span><span class="sxs-lookup"><span data-stu-id="1c252-128">**/componly**</span></span>|<span data-ttu-id="1c252-129">Nakonfiguruje pouze součásti; ignoruje metody a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1c252-129">Configures components only; ignores methods and interfaces.</span></span>|  
|<span data-ttu-id="1c252-130">**/exapp**</span><span class="sxs-lookup"><span data-stu-id="1c252-130">**/exapp**</span></span>|<span data-ttu-id="1c252-131">Určuje, že nástroj má očekávat existující aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1c252-131">Specifies to the tool to expect an existing application.</span></span>|  
|<span data-ttu-id="1c252-132">**/extlb**</span><span class="sxs-lookup"><span data-stu-id="1c252-132">**/extlb**</span></span>|<span data-ttu-id="1c252-133">Použije existující knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="1c252-133">Uses an existing type library.</span></span>|  
|<span data-ttu-id="1c252-134">**/FC**</span><span class="sxs-lookup"><span data-stu-id="1c252-134">**/fc**</span></span>|<span data-ttu-id="1c252-135">Vyhledá nebo vytvoří cílovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1c252-135">Finds or creates the target application.</span></span>|  
|<span data-ttu-id="1c252-136">**/Help**</span><span class="sxs-lookup"><span data-stu-id="1c252-136">**/help**</span></span>|<span data-ttu-id="1c252-137">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="1c252-137">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="1c252-138">**/noreconfig**</span><span class="sxs-lookup"><span data-stu-id="1c252-138">**/noreconfig**</span></span>|<span data-ttu-id="1c252-139">Znovu nekonfiguruje existující cílovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1c252-139">Does not reconfigure an existing target application.</span></span>|  
|<span data-ttu-id="1c252-140">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="1c252-140">**/nologo**</span></span>|<span data-ttu-id="1c252-141">Potlačí zobrazení úvodního nápisu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1c252-141">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="1c252-142">**/parName:** *název*</span><span class="sxs-lookup"><span data-stu-id="1c252-142">**/parname:** *name*</span></span>|<span data-ttu-id="1c252-143">Určuje název nebo ID aplikace modelu COM+, která se má vyhledat nebo vytvořit.</span><span class="sxs-lookup"><span data-stu-id="1c252-143">Specifies the name or id of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="1c252-144">**/reconfig**</span><span class="sxs-lookup"><span data-stu-id="1c252-144">**/reconfig**</span></span>|<span data-ttu-id="1c252-145">Znovu nakonfiguruje existující cílovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1c252-145">Reconfigures an existing target application.</span></span> <span data-ttu-id="1c252-146">Tato možnost je výchozí.</span><span class="sxs-lookup"><span data-stu-id="1c252-146">This is the default.</span></span>|  
|<span data-ttu-id="1c252-147">**/TLB:** *souborKnihovnyTypů*</span><span class="sxs-lookup"><span data-stu-id="1c252-147">**/tlb:** *typelibraryfile*</span></span>|<span data-ttu-id="1c252-148">Určuje soubor knihovny typů instalace, který se má nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="1c252-148">Specifies the type library file to install.</span></span>|  
|<span data-ttu-id="1c252-149">**přepínač**</span><span class="sxs-lookup"><span data-stu-id="1c252-149">**/u**</span></span>|<span data-ttu-id="1c252-150">Odinstaluje cílovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1c252-150">Uninstalls the target application.</span></span>|  
|<span data-ttu-id="1c252-151">**parametr**</span><span class="sxs-lookup"><span data-stu-id="1c252-151">**/quiet**</span></span>|<span data-ttu-id="1c252-152">Určuje použití tichého režimu; potlačí zobrazování loga a zpráv o úspěchu.</span><span class="sxs-lookup"><span data-stu-id="1c252-152">Specifies quiet mode; suppresses the logo and success message display.</span></span>|  
|<span data-ttu-id="1c252-153">**/?**</span><span class="sxs-lookup"><span data-stu-id="1c252-153">**/?**</span></span>|<span data-ttu-id="1c252-154">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="1c252-154">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c252-155">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1c252-155">Remarks</span></span>  
 <span data-ttu-id="1c252-156">Regsvcs.exe vyžaduje zdrojový soubor sestavení určený pomocí *assemblyFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="1c252-156">Regsvcs.exe requires a source assembly file specified by *assemblyFile.dll*.</span></span> <span data-ttu-id="1c252-157">Toto sestavení musí být podepsáno silným názvem.</span><span class="sxs-lookup"><span data-stu-id="1c252-157">This assembly must be signed with a strong name.</span></span> <span data-ttu-id="1c252-158">Další informace o podepisování silným názvem naleznete v tématu [podepisování sestavení silným názvem](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="1c252-158">For more information on strong name signing, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span> <span data-ttu-id="1c252-159">Názvy cílové aplikace a souboru knihovny typů jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="1c252-159">The names of the target application and the type library file are optional.</span></span> <span data-ttu-id="1c252-160">Argument *ApplicationName* lze vygenerovat ze zdrojového souboru sestavení a bude vytvořen pomocí Regsvcs.exe, pokud ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="1c252-160">The *applicationName* argument can be generated from the source assembly file and will be created by Regsvcs.exe, if it does not already exist.</span></span> <span data-ttu-id="1c252-161">Argument *souborKnihovnyTypů* může určovat název knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="1c252-161">The *typelibraryfile* argument can specify a type library name.</span></span> <span data-ttu-id="1c252-162">Pokud název knihovny typů nezadáte, nástroj Regsvcs.exe použije jako výchozí název sestavení.</span><span class="sxs-lookup"><span data-stu-id="1c252-162">If you do not specify a type library name, Regsvcs.exe uses the assembly name as the default.</span></span>  
  
 <span data-ttu-id="1c252-163">Když Regsvcs.exe zaregistruje metody komponenty, vztahuje se na ně [požadavky](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) a [požadavky propojení](../misc/link-demands.md) na tyto metody.</span><span class="sxs-lookup"><span data-stu-id="1c252-163">When Regsvcs.exe registers a component's methods, it is subject to the [demands](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) and [link demands](../misc/link-demands.md) on those methods.</span></span> <span data-ttu-id="1c252-164">Vzhledem k tomu, že se nástroj spouští v plně důvěryhodném prostředí, většina požadavků na oprávnění je splněna.</span><span class="sxs-lookup"><span data-stu-id="1c252-164">Because the tool executes in a fully-trusted environment, most demands for a permission succeed.</span></span> <span data-ttu-id="1c252-165">Regsvcs.exe ale nemůže registrovat komponenty s metodami chráněnými požadavkem nebo odkazem na aplikaci <xref:System.Security.Permissions.StrongNameIdentityPermission> nebo <xref:System.Security.Permissions.PublisherIdentityPermission> .</span><span class="sxs-lookup"><span data-stu-id="1c252-165">However, Regsvcs.exe cannot register components with methods protected by a demand or link demand for the <xref:System.Security.Permissions.StrongNameIdentityPermission> or the <xref:System.Security.Permissions.PublisherIdentityPermission>.</span></span>  
  
 <span data-ttu-id="1c252-166">Pro použití Regsvcs.exe musíte mít administrátorská oprávnění na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="1c252-166">You must have administrative privileges on the local computer to use Regsvcs.exe.</span></span>  
  
 <span data-ttu-id="1c252-167">Pokud Regsvcs.exe selže při provádění kterékoli z těchto akcí, zobrazí se odpovídající chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="1c252-167">If Regsvcs.exe fails while performing any of these actions, it displays corresponding error messages.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="1c252-168">Příklady</span><span class="sxs-lookup"><span data-stu-id="1c252-168">Examples</span></span>  
 <span data-ttu-id="1c252-169">Následující příkaz přidá všechny veřejné třídy obsažené v `myTest.dll` do `myTargetApp` (existující aplikace com+) a vytvoří `myTest.tlb` knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="1c252-169">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `myTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 <span data-ttu-id="1c252-170">Následující příkaz přidá všechny veřejné třídy obsažené v `myTest.dll` do `myTargetApp` (existující aplikace com+) a vytvoří `newTest.tlb` knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="1c252-170">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `newTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="1c252-171">Viz také</span><span class="sxs-lookup"><span data-stu-id="1c252-171">See also</span></span>

- [<span data-ttu-id="1c252-172">Nástroje</span><span class="sxs-lookup"><span data-stu-id="1c252-172">Tools</span></span>](index.md)
- [<span data-ttu-id="1c252-173">Postupy: Podepsání sestavení silným názvem</span><span class="sxs-lookup"><span data-stu-id="1c252-173">How to: Sign an Assembly with a Strong Name</span></span>](../../standard/assembly/sign-strong-name.md)
- [<span data-ttu-id="1c252-174">Výzvy příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="1c252-174">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
