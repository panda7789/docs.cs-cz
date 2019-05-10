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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0dc05294ae762b4f896bb7f514df102c1f948fe0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623411"
---
# <a name="regsvcsexe-net-services-installation-tool"></a><span data-ttu-id="69c8b-102">Regsvcs.exe (nástroj pro instalaci služeb .NET)</span><span class="sxs-lookup"><span data-stu-id="69c8b-102">Regsvcs.exe (.NET Services Installation Tool)</span></span>
<span data-ttu-id="69c8b-103">Instalační nástroj .NET Services vykonává tyto akce:</span><span class="sxs-lookup"><span data-stu-id="69c8b-103">The .NET Services Installation tool performs the following actions:</span></span>  
  
- <span data-ttu-id="69c8b-104">Načítá a registruje sestavení.</span><span class="sxs-lookup"><span data-stu-id="69c8b-104">Loads and registers an assembly.</span></span>  
  
- <span data-ttu-id="69c8b-105">Vytváří, registruje a instaluje knihovnu typů do zadané aplikace modelu COM+.</span><span class="sxs-lookup"><span data-stu-id="69c8b-105">Generates, registers, and installs a type library into a specified COM+ application.</span></span>  
  
- <span data-ttu-id="69c8b-106">Konfiguruje služby, které jste přidali pomocí programu do vaší třídy.</span><span class="sxs-lookup"><span data-stu-id="69c8b-106">Configures services that you have added programmatically to your class.</span></span>  
  
 <span data-ttu-id="69c8b-107">Ke spuštění nástroje, použijte příkazový řádek pro vývojáře pro Visual Studio (nebo příkazový řádek Visual Studio ve Windows 7).</span><span class="sxs-lookup"><span data-stu-id="69c8b-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="69c8b-108">Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="69c8b-108">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="69c8b-109">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="69c8b-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69c8b-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69c8b-110">Syntax</span></span>  
  
```  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll   
```  
  
## <a name="parameters"></a><span data-ttu-id="69c8b-111">Parametry</span><span class="sxs-lookup"><span data-stu-id="69c8b-111">Parameters</span></span>  
  
|<span data-ttu-id="69c8b-112">Argument</span><span class="sxs-lookup"><span data-stu-id="69c8b-112">Argument</span></span>|<span data-ttu-id="69c8b-113">Popis</span><span class="sxs-lookup"><span data-stu-id="69c8b-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="69c8b-114">*assemblyFile.dll*</span><span class="sxs-lookup"><span data-stu-id="69c8b-114">*assemblyFile.dll*</span></span>|<span data-ttu-id="69c8b-115">Zdrojový soubor sestavení.</span><span class="sxs-lookup"><span data-stu-id="69c8b-115">The source assembly file.</span></span> <span data-ttu-id="69c8b-116">Sestavení musí být podepsáno silným názvem.</span><span class="sxs-lookup"><span data-stu-id="69c8b-116">The assembly must be signed with a strong name.</span></span> <span data-ttu-id="69c8b-117">Další informace najdete v tématu [podepisování sestavení silným názvem](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="69c8b-117">For more information, see [Signing an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>|  
  
|<span data-ttu-id="69c8b-118">Možnost</span><span class="sxs-lookup"><span data-stu-id="69c8b-118">Option</span></span>|<span data-ttu-id="69c8b-119">Popis</span><span class="sxs-lookup"><span data-stu-id="69c8b-119">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="69c8b-120">**/appdir:** *cesta*</span><span class="sxs-lookup"><span data-stu-id="69c8b-120">**/appdir:** *path*</span></span>|<span data-ttu-id="69c8b-121">Určuje kořenový adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="69c8b-121">Specifies the root directory of the application.</span></span>|  
|<span data-ttu-id="69c8b-122">**příkazy/appname:** *applicationName*</span><span class="sxs-lookup"><span data-stu-id="69c8b-122">**/appname:** *applicationName*</span></span>|<span data-ttu-id="69c8b-123">Určuje název aplikace modelu COM+, která se má vyhledat nebo vytvořit.</span><span class="sxs-lookup"><span data-stu-id="69c8b-123">Specifies the name of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="69c8b-124">**/c**</span><span class="sxs-lookup"><span data-stu-id="69c8b-124">**/c**</span></span>|<span data-ttu-id="69c8b-125">Vytvoří cílovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="69c8b-125">Creates the target application.</span></span>|  
|<span data-ttu-id="69c8b-126">**RegSvcs**</span><span class="sxs-lookup"><span data-stu-id="69c8b-126">**/componly**</span></span>|<span data-ttu-id="69c8b-127">Nakonfiguruje pouze součásti; ignoruje metody a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="69c8b-127">Configures components only; ignores methods and interfaces.</span></span>|  
|<span data-ttu-id="69c8b-128">**/exapp**</span><span class="sxs-lookup"><span data-stu-id="69c8b-128">**/exapp**</span></span>|<span data-ttu-id="69c8b-129">Určuje, že nástroj má očekávat existující aplikaci.</span><span class="sxs-lookup"><span data-stu-id="69c8b-129">Specifies to the tool to expect an existing application.</span></span>|  
|<span data-ttu-id="69c8b-130">**/extlb**</span><span class="sxs-lookup"><span data-stu-id="69c8b-130">**/extlb**</span></span>|<span data-ttu-id="69c8b-131">Použije existující knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="69c8b-131">Uses an existing type library.</span></span>|  
|<span data-ttu-id="69c8b-132">**/fc**</span><span class="sxs-lookup"><span data-stu-id="69c8b-132">**/fc**</span></span>|<span data-ttu-id="69c8b-133">Vyhledá nebo vytvoří cílovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="69c8b-133">Finds or creates the target application.</span></span>|  
|<span data-ttu-id="69c8b-134">**/ Help**</span><span class="sxs-lookup"><span data-stu-id="69c8b-134">**/help**</span></span>|<span data-ttu-id="69c8b-135">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="69c8b-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="69c8b-136">**/noreconfig**</span><span class="sxs-lookup"><span data-stu-id="69c8b-136">**/noreconfig**</span></span>|<span data-ttu-id="69c8b-137">Znovu nekonfiguruje existující cílovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="69c8b-137">Does not reconfigure an existing target application.</span></span>|  
|<span data-ttu-id="69c8b-138">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="69c8b-138">**/nologo**</span></span>|<span data-ttu-id="69c8b-139">Potlačí zobrazení úvodního nápisu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="69c8b-139">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="69c8b-140">**/parname:** *název*</span><span class="sxs-lookup"><span data-stu-id="69c8b-140">**/parname:** *name*</span></span>|<span data-ttu-id="69c8b-141">Určuje název nebo ID aplikace modelu COM+, která se má vyhledat nebo vytvořit.</span><span class="sxs-lookup"><span data-stu-id="69c8b-141">Specifies the name or id of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="69c8b-142">**/reconfig**</span><span class="sxs-lookup"><span data-stu-id="69c8b-142">**/reconfig**</span></span>|<span data-ttu-id="69c8b-143">Znovu nakonfiguruje existující cílovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="69c8b-143">Reconfigures an existing target application.</span></span> <span data-ttu-id="69c8b-144">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="69c8b-144">This is the default.</span></span>|  
|<span data-ttu-id="69c8b-145">**/ TLB:** *souborknihovnytypů*</span><span class="sxs-lookup"><span data-stu-id="69c8b-145">**/tlb:** *typelibraryfile*</span></span>|<span data-ttu-id="69c8b-146">Určuje soubor knihovny typů instalace, který se má nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="69c8b-146">Specifies the type library file to install.</span></span>|  
|<span data-ttu-id="69c8b-147">**/u**</span><span class="sxs-lookup"><span data-stu-id="69c8b-147">**/u**</span></span>|<span data-ttu-id="69c8b-148">Odinstaluje cílovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="69c8b-148">Uninstalls the target application.</span></span>|  
|<span data-ttu-id="69c8b-149">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="69c8b-149">**/quiet**</span></span>|<span data-ttu-id="69c8b-150">Určuje použití tichého režimu; potlačí zobrazování loga a zpráv o úspěchu.</span><span class="sxs-lookup"><span data-stu-id="69c8b-150">Specifies quiet mode; suppresses the logo and success message display.</span></span>|  
|<span data-ttu-id="69c8b-151">**/?**</span><span class="sxs-lookup"><span data-stu-id="69c8b-151">**/?**</span></span>|<span data-ttu-id="69c8b-152">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="69c8b-152">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69c8b-153">Poznámky</span><span class="sxs-lookup"><span data-stu-id="69c8b-153">Remarks</span></span>  
 <span data-ttu-id="69c8b-154">RegSvcs.exe vyžaduje zdrojový soubor sestavení určený *assemblyFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="69c8b-154">Regsvcs.exe requires a source assembly file specified by *assemblyFile.dll*.</span></span> <span data-ttu-id="69c8b-155">Toto sestavení musí být podepsáno silným názvem.</span><span class="sxs-lookup"><span data-stu-id="69c8b-155">This assembly must be signed with a strong name.</span></span> <span data-ttu-id="69c8b-156">Další informace o podepisování silným názvem naleznete v tématu [podepisování sestavení silným názvem](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="69c8b-156">For more information on strong name signing, see [Signing an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span> <span data-ttu-id="69c8b-157">Názvy cílové aplikace a souboru knihovny typů jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="69c8b-157">The names of the target application and the type library file are optional.</span></span> <span data-ttu-id="69c8b-158">*ApplicationName* argument se dá vygenerovat na zdrojový soubor sestavení a, bude vytvořen pomocí Regsvcs.exe, pokud ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="69c8b-158">The *applicationName* argument can be generated from the source assembly file and will be created by Regsvcs.exe, if it does not already exist.</span></span> <span data-ttu-id="69c8b-159">*Souborknihovnytypů* argument můžete zadat název knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="69c8b-159">The *typelibraryfile* argument can specify a type library name.</span></span> <span data-ttu-id="69c8b-160">Pokud název knihovny typů nezadáte, nástroj Regsvcs.exe použije jako výchozí název sestavení.</span><span class="sxs-lookup"><span data-stu-id="69c8b-160">If you do not specify a type library name, Regsvcs.exe uses the assembly name as the default.</span></span>  
  
 <span data-ttu-id="69c8b-161">Pokud Regsvcs.exe registruje metody, se vztahuje [požadavky](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) a [požadavky na propojení](../../../docs/framework/misc/link-demands.md) na tyto metody.</span><span class="sxs-lookup"><span data-stu-id="69c8b-161">When Regsvcs.exe registers a component's methods, it is subject to the [demands](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) and [link demands](../../../docs/framework/misc/link-demands.md) on those methods.</span></span> <span data-ttu-id="69c8b-162">Vzhledem k tomu, že se nástroj spouští v plně důvěryhodném prostředí, většina požadavků na oprávnění je splněna.</span><span class="sxs-lookup"><span data-stu-id="69c8b-162">Because the tool executes in a fully-trusted environment, most demands for a permission succeed.</span></span> <span data-ttu-id="69c8b-163">Regsvcs.exe však nemůže zaregistrovat prvky pomocí metod chráněných požadavkem nebo odkazem pro <xref:System.Security.Permissions.StrongNameIdentityPermission> nebo <xref:System.Security.Permissions.PublisherIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="69c8b-163">However, Regsvcs.exe cannot register components with methods protected by a demand or link demand for the <xref:System.Security.Permissions.StrongNameIdentityPermission> or the <xref:System.Security.Permissions.PublisherIdentityPermission>.</span></span>  
  
 <span data-ttu-id="69c8b-164">Pro použití Regsvcs.exe musíte mít administrátorská oprávnění na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="69c8b-164">You must have administrative privileges on the local computer to use Regsvcs.exe.</span></span>  
  
 <span data-ttu-id="69c8b-165">Pokud Regsvcs.exe selže při provádění kterékoli z těchto akcí, zobrazí se odpovídající chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="69c8b-165">If Regsvcs.exe fails while performing any of these actions, it displays corresponding error messages.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="69c8b-166">Příklady</span><span class="sxs-lookup"><span data-stu-id="69c8b-166">Examples</span></span>  
 <span data-ttu-id="69c8b-167">Následující příkaz přidá všechny veřejné třídy obsažené v `myTest.dll` k `myTargetApp` (existující aplikace modelu COM +) a vytvoří `myTest.tlb` knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="69c8b-167">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `myTest.tlb` type library.</span></span>  
  
```  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 <span data-ttu-id="69c8b-168">Následující příkaz přidá všechny veřejné třídy obsažené v `myTest.dll` k `myTargetApp` (existující aplikace modelu COM +) a vytvoří `newTest.tlb` knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="69c8b-168">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `newTest.tlb` type library.</span></span>  
  
```  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="69c8b-169">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69c8b-169">See also</span></span>

- [<span data-ttu-id="69c8b-170">Nástroje</span><span class="sxs-lookup"><span data-stu-id="69c8b-170">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="69c8b-171">Postupy: Podepsání sestavení silným názvem</span><span class="sxs-lookup"><span data-stu-id="69c8b-171">How to: Sign an Assembly with a Strong Name</span></span>](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)
- [<span data-ttu-id="69c8b-172">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="69c8b-172">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
