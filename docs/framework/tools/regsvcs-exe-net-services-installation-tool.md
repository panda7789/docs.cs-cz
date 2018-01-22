---
title: "Regsvcs.exe (nástroj pro instalaci služeb .NET)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Regsvcs.exe
- .NET Services Installation tool
- loading assemblies
- assemblies [.NET Framework], registering
- type libraries
- registering assemblies
ms.assetid: 5220fe58-5aaf-4e8e-8bc3-b78c63025804
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bfe7c3e34c2ceaf01f89c1e54f930991ee7e0a2b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="regsvcsexe-net-services-installation-tool"></a><span data-ttu-id="47d98-102">Regsvcs.exe (nástroj pro instalaci služeb .NET)</span><span class="sxs-lookup"><span data-stu-id="47d98-102">Regsvcs.exe (.NET Services Installation Tool)</span></span>
<span data-ttu-id="47d98-103">Instalační nástroj .NET Services vykonává tyto akce:</span><span class="sxs-lookup"><span data-stu-id="47d98-103">The .NET Services Installation tool performs the following actions:</span></span>  
  
-   <span data-ttu-id="47d98-104">Načítá a registruje sestavení.</span><span class="sxs-lookup"><span data-stu-id="47d98-104">Loads and registers an assembly.</span></span>  
  
-   <span data-ttu-id="47d98-105">Vytváří, registruje a instaluje knihovnu typů do zadané aplikace modelu COM+.</span><span class="sxs-lookup"><span data-stu-id="47d98-105">Generates, registers, and installs a type library into a specified COM+ application.</span></span>  
  
-   <span data-ttu-id="47d98-106">Konfiguruje služby, které jste přidali pomocí programu do vaší třídy.</span><span class="sxs-lookup"><span data-stu-id="47d98-106">Configures services that you have added programmatically to your class.</span></span>  
  
 <span data-ttu-id="47d98-107">Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="47d98-107">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="47d98-108">Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="47d98-108">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="47d98-109">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="47d98-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47d98-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47d98-110">Syntax</span></span>  
  
```  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll   
```  
  
#### <a name="parameters"></a><span data-ttu-id="47d98-111">Parametry</span><span class="sxs-lookup"><span data-stu-id="47d98-111">Parameters</span></span>  
  
|<span data-ttu-id="47d98-112">Argument</span><span class="sxs-lookup"><span data-stu-id="47d98-112">Argument</span></span>|<span data-ttu-id="47d98-113">Popis</span><span class="sxs-lookup"><span data-stu-id="47d98-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="47d98-114">*assemblyFile.dll*</span><span class="sxs-lookup"><span data-stu-id="47d98-114">*assemblyFile.dll*</span></span>|<span data-ttu-id="47d98-115">Zdrojový soubor sestavení.</span><span class="sxs-lookup"><span data-stu-id="47d98-115">The source assembly file.</span></span> <span data-ttu-id="47d98-116">Sestavení musí být podepsáno silným názvem.</span><span class="sxs-lookup"><span data-stu-id="47d98-116">The assembly must be signed with a strong name.</span></span> <span data-ttu-id="47d98-117">Další informace najdete v tématu [podepsání sestavení se silným názvem](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="47d98-117">For more information, see [Signing an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>|  
  
|<span data-ttu-id="47d98-118">Možnost</span><span class="sxs-lookup"><span data-stu-id="47d98-118">Option</span></span>|<span data-ttu-id="47d98-119">Popis</span><span class="sxs-lookup"><span data-stu-id="47d98-119">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="47d98-120">**/appdir:** *cesta*</span><span class="sxs-lookup"><span data-stu-id="47d98-120">**/appdir:** *path*</span></span>|<span data-ttu-id="47d98-121">Určuje kořenový adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="47d98-121">Specifies the root directory of the application.</span></span>|  
|<span data-ttu-id="47d98-122">**příkazy/appname:** *applicationName*</span><span class="sxs-lookup"><span data-stu-id="47d98-122">**/appname:** *applicationName*</span></span>|<span data-ttu-id="47d98-123">Určuje název aplikace modelu COM+, která se má vyhledat nebo vytvořit.</span><span class="sxs-lookup"><span data-stu-id="47d98-123">Specifies the name of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="47d98-124">**/c**</span><span class="sxs-lookup"><span data-stu-id="47d98-124">**/c**</span></span>|<span data-ttu-id="47d98-125">Vytvoří cílovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="47d98-125">Creates the target application.</span></span>|  
|<span data-ttu-id="47d98-126">**0}, nejsou**</span><span class="sxs-lookup"><span data-stu-id="47d98-126">**/componly**</span></span>|<span data-ttu-id="47d98-127">Nakonfiguruje pouze součásti; ignoruje metody a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="47d98-127">Configures components only; ignores methods and interfaces.</span></span>|  
|<span data-ttu-id="47d98-128">**/exapp**</span><span class="sxs-lookup"><span data-stu-id="47d98-128">**/exapp**</span></span>|<span data-ttu-id="47d98-129">Určuje, že nástroj má očekávat existující aplikaci.</span><span class="sxs-lookup"><span data-stu-id="47d98-129">Specifies to the tool to expect an existing application.</span></span>|  
|<span data-ttu-id="47d98-130">**/extlb**</span><span class="sxs-lookup"><span data-stu-id="47d98-130">**/extlb**</span></span>|<span data-ttu-id="47d98-131">Použije existující knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="47d98-131">Uses an existing type library.</span></span>|  
|<span data-ttu-id="47d98-132">**/fc**</span><span class="sxs-lookup"><span data-stu-id="47d98-132">**/fc**</span></span>|<span data-ttu-id="47d98-133">Vyhledá nebo vytvoří cílovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="47d98-133">Finds or creates the target application.</span></span>|  
|<span data-ttu-id="47d98-134">**/help**</span><span class="sxs-lookup"><span data-stu-id="47d98-134">**/help**</span></span>|<span data-ttu-id="47d98-135">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="47d98-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="47d98-136">**/noreconfig**</span><span class="sxs-lookup"><span data-stu-id="47d98-136">**/noreconfig**</span></span>|<span data-ttu-id="47d98-137">Znovu nekonfiguruje existující cílovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="47d98-137">Does not reconfigure an existing target application.</span></span>|  
|<span data-ttu-id="47d98-138">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="47d98-138">**/nologo**</span></span>|<span data-ttu-id="47d98-139">Potlačí zobrazení úvodního nápisu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="47d98-139">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="47d98-140">**/parname:** *název*</span><span class="sxs-lookup"><span data-stu-id="47d98-140">**/parname:** *name*</span></span>|<span data-ttu-id="47d98-141">Určuje název nebo ID aplikace modelu COM+, která se má vyhledat nebo vytvořit.</span><span class="sxs-lookup"><span data-stu-id="47d98-141">Specifies the name or id of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="47d98-142">**/reconfig**</span><span class="sxs-lookup"><span data-stu-id="47d98-142">**/reconfig**</span></span>|<span data-ttu-id="47d98-143">Znovu nakonfiguruje existující cílovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="47d98-143">Reconfigures an existing target application.</span></span> <span data-ttu-id="47d98-144">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="47d98-144">This is the default.</span></span>|  
|<span data-ttu-id="47d98-145">**/ TLB:** *typelibraryfile*</span><span class="sxs-lookup"><span data-stu-id="47d98-145">**/tlb:** *typelibraryfile*</span></span>|<span data-ttu-id="47d98-146">Určuje soubor knihovny typů instalace, který se má nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="47d98-146">Specifies the type library file to install.</span></span>|  
|<span data-ttu-id="47d98-147">**/u**</span><span class="sxs-lookup"><span data-stu-id="47d98-147">**/u**</span></span>|<span data-ttu-id="47d98-148">Odinstaluje cílovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="47d98-148">Uninstalls the target application.</span></span>|  
|<span data-ttu-id="47d98-149">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="47d98-149">**/quiet**</span></span>|<span data-ttu-id="47d98-150">Určuje použití tichého režimu; potlačí zobrazování loga a zpráv o úspěchu.</span><span class="sxs-lookup"><span data-stu-id="47d98-150">Specifies quiet mode; suppresses the logo and success message display.</span></span>|  
|<span data-ttu-id="47d98-151">**/?**</span><span class="sxs-lookup"><span data-stu-id="47d98-151">**/?**</span></span>|<span data-ttu-id="47d98-152">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="47d98-152">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47d98-153">Poznámky</span><span class="sxs-lookup"><span data-stu-id="47d98-153">Remarks</span></span>  
 <span data-ttu-id="47d98-154">RegSvcs.exe vyžaduje zdrojového souboru sestavení určeného *assemblyFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="47d98-154">Regsvcs.exe requires a source assembly file specified by *assemblyFile.dll*.</span></span> <span data-ttu-id="47d98-155">Toto sestavení musí být podepsáno silným názvem.</span><span class="sxs-lookup"><span data-stu-id="47d98-155">This assembly must be signed with a strong name.</span></span> <span data-ttu-id="47d98-156">Další informace o podepisování silným názvem naleznete v tématu [podepsání sestavení se silným názvem](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="47d98-156">For more information on strong name signing, see [Signing an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span> <span data-ttu-id="47d98-157">Názvy cílové aplikace a souboru knihovny typů jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="47d98-157">The names of the target application and the type library file are optional.</span></span> <span data-ttu-id="47d98-158">*ApplicationName* argument může být generována ze zdrojového souboru sestavení a vytvoří Regsvcs.exe, pokud ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="47d98-158">The *applicationName* argument can be generated from the source assembly file and will be created by Regsvcs.exe, if it does not already exist.</span></span> <span data-ttu-id="47d98-159">*Typelibraryfile* argument můžete zadat název typu knihovny.</span><span class="sxs-lookup"><span data-stu-id="47d98-159">The *typelibraryfile* argument can specify a type library name.</span></span> <span data-ttu-id="47d98-160">Pokud název knihovny typů nezadáte, nástroj Regsvcs.exe použije jako výchozí název sestavení.</span><span class="sxs-lookup"><span data-stu-id="47d98-160">If you do not specify a type library name, Regsvcs.exe uses the assembly name as the default.</span></span>  
  
 <span data-ttu-id="47d98-161">Při Regsvcs.exe zaregistruje komponenty metody, je podléhají [požadavky](http://msdn.microsoft.com/library/e5283e28-2366-4519-b27d-ef5c1ddc1f48) a [požadavky na propojení](../../../docs/framework/misc/link-demands.md) na těchto metod.</span><span class="sxs-lookup"><span data-stu-id="47d98-161">When Regsvcs.exe registers a component's methods, it is subject to the [demands](http://msdn.microsoft.com/library/e5283e28-2366-4519-b27d-ef5c1ddc1f48) and [link demands](../../../docs/framework/misc/link-demands.md) on those methods.</span></span> <span data-ttu-id="47d98-162">Vzhledem k tomu, že se nástroj spouští v plně důvěryhodném prostředí, většina požadavků na oprávnění je splněna.</span><span class="sxs-lookup"><span data-stu-id="47d98-162">Because the tool executes in a fully-trusted environment, most demands for a permission succeed.</span></span> <span data-ttu-id="47d98-163">Regsvcs.exe však nelze zaregistrovat součásti pomocí metod, které jsou chráněny požadavku na vyžádání nebo odkaz pro <xref:System.Security.Permissions.StrongNameIdentityPermission> nebo <xref:System.Security.Permissions.PublisherIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="47d98-163">However, Regsvcs.exe cannot register components with methods protected by a demand or link demand for the <xref:System.Security.Permissions.StrongNameIdentityPermission> or the <xref:System.Security.Permissions.PublisherIdentityPermission>.</span></span>  
  
 <span data-ttu-id="47d98-164">Pro použití Regsvcs.exe musíte mít administrátorská oprávnění na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="47d98-164">You must have administrative privileges on the local computer to use Regsvcs.exe.</span></span>  
  
 <span data-ttu-id="47d98-165">Pokud Regsvcs.exe selže při provádění kterékoli z těchto akcí, zobrazí se odpovídající chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="47d98-165">If Regsvcs.exe fails while performing any of these actions, it displays corresponding error messages.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="47d98-166">Příklady</span><span class="sxs-lookup"><span data-stu-id="47d98-166">Examples</span></span>  
 <span data-ttu-id="47d98-167">Následující příkaz přidá všechny veřejné třídy, které jsou obsažené v `myTest.dll` k `myTargetApp` (stávající modelu COM + aplikaci) a vytvoří `myTest.tlb` knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="47d98-167">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `myTest.tlb` type library.</span></span>  
  
```  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 <span data-ttu-id="47d98-168">Následující příkaz přidá všechny veřejné třídy, které jsou obsažené v `myTest.dll` k `myTargetApp` (stávající modelu COM + aplikaci) a vytvoří `newTest.tlb` knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="47d98-168">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `newTest.tlb` type library.</span></span>  
  
```  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="47d98-169">Viz také</span><span class="sxs-lookup"><span data-stu-id="47d98-169">See Also</span></span>  
 [<span data-ttu-id="47d98-170">Nástroje</span><span class="sxs-lookup"><span data-stu-id="47d98-170">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="47d98-171">Postupy: Podepsání sestavení silným názvem</span><span class="sxs-lookup"><span data-stu-id="47d98-171">How to: Sign an Assembly with a Strong Name</span></span>](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [<span data-ttu-id="47d98-172">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="47d98-172">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
