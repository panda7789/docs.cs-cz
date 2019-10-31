---
title: Regsvcs.exe (nástroj pro instalaci služeb .NET)
ms.date: 03/30/2017
helpviewer_keywords:
- Regsvcs.exe
- .NET Services Installation tool
- loading assemblies
- assemblies [.NET Framework], registering
- type libraries
- registering assemblies
ms.assetid: 5220fe58-5aaf-4e8e-8bc3-b78c63025804
ms.openlocfilehash: 1af93ae89d027bccdd52b9cd9c49f8e620303677
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73104945"
---
# <a name="regsvcsexe-net-services-installation-tool"></a><span data-ttu-id="9ca76-102">Regsvcs.exe (nástroj pro instalaci služeb .NET)</span><span class="sxs-lookup"><span data-stu-id="9ca76-102">Regsvcs.exe (.NET Services Installation Tool)</span></span>
<span data-ttu-id="9ca76-103">Instalační nástroj .NET Services vykonává tyto akce:</span><span class="sxs-lookup"><span data-stu-id="9ca76-103">The .NET Services Installation tool performs the following actions:</span></span>  
  
- <span data-ttu-id="9ca76-104">Načítá a registruje sestavení.</span><span class="sxs-lookup"><span data-stu-id="9ca76-104">Loads and registers an assembly.</span></span>  
  
- <span data-ttu-id="9ca76-105">Vytváří, registruje a instaluje knihovnu typů do zadané aplikace modelu COM+.</span><span class="sxs-lookup"><span data-stu-id="9ca76-105">Generates, registers, and installs a type library into a specified COM+ application.</span></span>  
  
- <span data-ttu-id="9ca76-106">Konfiguruje služby, které jste přidali pomocí programu do vaší třídy.</span><span class="sxs-lookup"><span data-stu-id="9ca76-106">Configures services that you have added programmatically to your class.</span></span>  
  
 <span data-ttu-id="9ca76-107">Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="9ca76-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="9ca76-108">Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="9ca76-108">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="9ca76-109">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="9ca76-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ca76-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ca76-110">Syntax</span></span>  
  
```console  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll   
```  
  
## <a name="parameters"></a><span data-ttu-id="9ca76-111">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ca76-111">Parameters</span></span>  
  
|<span data-ttu-id="9ca76-112">Argument</span><span class="sxs-lookup"><span data-stu-id="9ca76-112">Argument</span></span>|<span data-ttu-id="9ca76-113">Popis</span><span class="sxs-lookup"><span data-stu-id="9ca76-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="9ca76-114">*assemblyFile. dll*</span><span class="sxs-lookup"><span data-stu-id="9ca76-114">*assemblyFile.dll*</span></span>|<span data-ttu-id="9ca76-115">Zdrojový soubor sestavení.</span><span class="sxs-lookup"><span data-stu-id="9ca76-115">The source assembly file.</span></span> <span data-ttu-id="9ca76-116">Sestavení musí být podepsáno silným názvem.</span><span class="sxs-lookup"><span data-stu-id="9ca76-116">The assembly must be signed with a strong name.</span></span> <span data-ttu-id="9ca76-117">Další informace naleznete v tématu [podepisování sestavení silným názvem](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="9ca76-117">For more information, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span>|  
  
|<span data-ttu-id="9ca76-118">Možnost</span><span class="sxs-lookup"><span data-stu-id="9ca76-118">Option</span></span>|<span data-ttu-id="9ca76-119">Popis</span><span class="sxs-lookup"><span data-stu-id="9ca76-119">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="9ca76-120">**/appdir:** *cesta*</span><span class="sxs-lookup"><span data-stu-id="9ca76-120">**/appdir:** *path*</span></span>|<span data-ttu-id="9ca76-121">Určuje kořenový adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="9ca76-121">Specifies the root directory of the application.</span></span>|  
|<span data-ttu-id="9ca76-122">**/AppName:** *ApplicationName*</span><span class="sxs-lookup"><span data-stu-id="9ca76-122">**/appname:** *applicationName*</span></span>|<span data-ttu-id="9ca76-123">Určuje název aplikace modelu COM+, která se má vyhledat nebo vytvořit.</span><span class="sxs-lookup"><span data-stu-id="9ca76-123">Specifies the name of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="9ca76-124">**/c**</span><span class="sxs-lookup"><span data-stu-id="9ca76-124">**/c**</span></span>|<span data-ttu-id="9ca76-125">Vytvoří cílovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9ca76-125">Creates the target application.</span></span>|  
|<span data-ttu-id="9ca76-126">**/componly**</span><span class="sxs-lookup"><span data-stu-id="9ca76-126">**/componly**</span></span>|<span data-ttu-id="9ca76-127">Nakonfiguruje pouze součásti; ignoruje metody a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9ca76-127">Configures components only; ignores methods and interfaces.</span></span>|  
|<span data-ttu-id="9ca76-128">**/exapp**</span><span class="sxs-lookup"><span data-stu-id="9ca76-128">**/exapp**</span></span>|<span data-ttu-id="9ca76-129">Určuje, že nástroj má očekávat existující aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9ca76-129">Specifies to the tool to expect an existing application.</span></span>|  
|<span data-ttu-id="9ca76-130">**/extlb**</span><span class="sxs-lookup"><span data-stu-id="9ca76-130">**/extlb**</span></span>|<span data-ttu-id="9ca76-131">Použije existující knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="9ca76-131">Uses an existing type library.</span></span>|  
|<span data-ttu-id="9ca76-132">**/FC**</span><span class="sxs-lookup"><span data-stu-id="9ca76-132">**/fc**</span></span>|<span data-ttu-id="9ca76-133">Vyhledá nebo vytvoří cílovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9ca76-133">Finds or creates the target application.</span></span>|  
|<span data-ttu-id="9ca76-134">**/Help**</span><span class="sxs-lookup"><span data-stu-id="9ca76-134">**/help**</span></span>|<span data-ttu-id="9ca76-135">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="9ca76-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="9ca76-136">**/noreconfig**</span><span class="sxs-lookup"><span data-stu-id="9ca76-136">**/noreconfig**</span></span>|<span data-ttu-id="9ca76-137">Znovu nekonfiguruje existující cílovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9ca76-137">Does not reconfigure an existing target application.</span></span>|  
|<span data-ttu-id="9ca76-138">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="9ca76-138">**/nologo**</span></span>|<span data-ttu-id="9ca76-139">Potlačí zobrazení úvodního nápisu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9ca76-139">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="9ca76-140">**/parName:** *název*</span><span class="sxs-lookup"><span data-stu-id="9ca76-140">**/parname:** *name*</span></span>|<span data-ttu-id="9ca76-141">Určuje název nebo ID aplikace modelu COM+, která se má vyhledat nebo vytvořit.</span><span class="sxs-lookup"><span data-stu-id="9ca76-141">Specifies the name or id of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="9ca76-142">**/reconfig**</span><span class="sxs-lookup"><span data-stu-id="9ca76-142">**/reconfig**</span></span>|<span data-ttu-id="9ca76-143">Znovu nakonfiguruje existující cílovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9ca76-143">Reconfigures an existing target application.</span></span> <span data-ttu-id="9ca76-144">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="9ca76-144">This is the default.</span></span>|  
|<span data-ttu-id="9ca76-145">**/TLB:** *souborKnihovnyTypů*</span><span class="sxs-lookup"><span data-stu-id="9ca76-145">**/tlb:** *typelibraryfile*</span></span>|<span data-ttu-id="9ca76-146">Určuje soubor knihovny typů instalace, který se má nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="9ca76-146">Specifies the type library file to install.</span></span>|  
|<span data-ttu-id="9ca76-147">**přepínač**</span><span class="sxs-lookup"><span data-stu-id="9ca76-147">**/u**</span></span>|<span data-ttu-id="9ca76-148">Odinstaluje cílovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9ca76-148">Uninstalls the target application.</span></span>|  
|<span data-ttu-id="9ca76-149">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="9ca76-149">**/quiet**</span></span>|<span data-ttu-id="9ca76-150">Určuje použití tichého režimu; potlačí zobrazování loga a zpráv o úspěchu.</span><span class="sxs-lookup"><span data-stu-id="9ca76-150">Specifies quiet mode; suppresses the logo and success message display.</span></span>|  
|<span data-ttu-id="9ca76-151">**/?**</span><span class="sxs-lookup"><span data-stu-id="9ca76-151">**/?**</span></span>|<span data-ttu-id="9ca76-152">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="9ca76-152">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ca76-153">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9ca76-153">Remarks</span></span>  
 <span data-ttu-id="9ca76-154">Regsvcs. exe vyžaduje zdrojový soubor sestavení určený pomocí *assemblyFile. dll*.</span><span class="sxs-lookup"><span data-stu-id="9ca76-154">Regsvcs.exe requires a source assembly file specified by *assemblyFile.dll*.</span></span> <span data-ttu-id="9ca76-155">Toto sestavení musí být podepsáno silným názvem.</span><span class="sxs-lookup"><span data-stu-id="9ca76-155">This assembly must be signed with a strong name.</span></span> <span data-ttu-id="9ca76-156">Další informace o podepisování silným názvem naleznete v tématu [podepisování sestavení silným názvem](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="9ca76-156">For more information on strong name signing, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span> <span data-ttu-id="9ca76-157">Názvy cílové aplikace a souboru knihovny typů jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="9ca76-157">The names of the target application and the type library file are optional.</span></span> <span data-ttu-id="9ca76-158">Argument *ApplicationName* lze vygenerovat ze zdrojového souboru sestavení a vytvoří jej pomocí Regsvcs. exe, pokud ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="9ca76-158">The *applicationName* argument can be generated from the source assembly file and will be created by Regsvcs.exe, if it does not already exist.</span></span> <span data-ttu-id="9ca76-159">Argument *souborKnihovnyTypů* může určovat název knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="9ca76-159">The *typelibraryfile* argument can specify a type library name.</span></span> <span data-ttu-id="9ca76-160">Pokud název knihovny typů nezadáte, nástroj Regsvcs.exe použije jako výchozí název sestavení.</span><span class="sxs-lookup"><span data-stu-id="9ca76-160">If you do not specify a type library name, Regsvcs.exe uses the assembly name as the default.</span></span>  
  
 <span data-ttu-id="9ca76-161">Pokud Regsvcs. exe zaregistruje metody komponenty, vztahuje se na ně [požadavky](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) a [požadavky propojení](../misc/link-demands.md) na tyto metody.</span><span class="sxs-lookup"><span data-stu-id="9ca76-161">When Regsvcs.exe registers a component's methods, it is subject to the [demands](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) and [link demands](../misc/link-demands.md) on those methods.</span></span> <span data-ttu-id="9ca76-162">Vzhledem k tomu, že se nástroj spouští v plně důvěryhodném prostředí, většina požadavků na oprávnění je splněna.</span><span class="sxs-lookup"><span data-stu-id="9ca76-162">Because the tool executes in a fully-trusted environment, most demands for a permission succeed.</span></span> <span data-ttu-id="9ca76-163">Regsvcs. exe však nemůže registrovat součásti s metodami chráněnými požadavkem nebo odkazem na poptávku pro <xref:System.Security.Permissions.StrongNameIdentityPermission> nebo <xref:System.Security.Permissions.PublisherIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="9ca76-163">However, Regsvcs.exe cannot register components with methods protected by a demand or link demand for the <xref:System.Security.Permissions.StrongNameIdentityPermission> or the <xref:System.Security.Permissions.PublisherIdentityPermission>.</span></span>  
  
 <span data-ttu-id="9ca76-164">Pro použití Regsvcs.exe musíte mít administrátorská oprávnění na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="9ca76-164">You must have administrative privileges on the local computer to use Regsvcs.exe.</span></span>  
  
 <span data-ttu-id="9ca76-165">Pokud Regsvcs.exe selže při provádění kterékoli z těchto akcí, zobrazí se odpovídající chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="9ca76-165">If Regsvcs.exe fails while performing any of these actions, it displays corresponding error messages.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="9ca76-166">Příklady</span><span class="sxs-lookup"><span data-stu-id="9ca76-166">Examples</span></span>  
 <span data-ttu-id="9ca76-167">Následující příkaz přidá všechny veřejné třídy obsažené v `myTest.dll` do `myTargetApp` (existující aplikace COM+) a vytvoří knihovnu typů `myTest.tlb`.</span><span class="sxs-lookup"><span data-stu-id="9ca76-167">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `myTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 <span data-ttu-id="9ca76-168">Následující příkaz přidá všechny veřejné třídy obsažené v `myTest.dll` do `myTargetApp` (existující aplikace COM+) a vytvoří knihovnu typů `newTest.tlb`.</span><span class="sxs-lookup"><span data-stu-id="9ca76-168">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `newTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="9ca76-169">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ca76-169">See also</span></span>

- [<span data-ttu-id="9ca76-170">Nástroje</span><span class="sxs-lookup"><span data-stu-id="9ca76-170">Tools</span></span>](index.md)
- [<span data-ttu-id="9ca76-171">Postupy: Podepsání sestavení silným názvem</span><span class="sxs-lookup"><span data-stu-id="9ca76-171">How to: Sign an Assembly with a Strong Name</span></span>](../../standard/assembly/sign-strong-name.md)
- [<span data-ttu-id="9ca76-172">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="9ca76-172">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
