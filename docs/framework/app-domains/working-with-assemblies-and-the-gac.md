---
title: Práce se sestaveními a s globální pamětí sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, benefits
- ACLs [.NET Framework]
- GAC (global assembly cache), benefits
- access control lists [.NET Framework]
ms.assetid: 8a18e5c2-d41d-49ef-abcb-7c27e2469433
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62760cb9fe5832ee018ebdebf6275ea61691c738
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927804"
---
# <a name="working-with-assemblies-and-the-global-assembly-cache"></a><span data-ttu-id="14726-102">Práce se sestaveními a s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="14726-102">Working with Assemblies and the Global Assembly Cache</span></span>
<span data-ttu-id="14726-103">Pokud máte v úmyslu sdílet sestavení mezi několika aplikacemi, můžete jej nainstalovat do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="14726-103">If you intend to share an assembly among several applications, you can install it into the global assembly cache.</span></span> <span data-ttu-id="14726-104">Každý počítač, ve kterém je nainstalován modul CLR (Common Language Runtime), má tuto mezipaměť kódu pro všechny počítače.</span><span class="sxs-lookup"><span data-stu-id="14726-104">Each computer where the common language runtime is installed has this machine-wide code cache.</span></span> <span data-ttu-id="14726-105">Globální mezipaměť sestavení ukládá sestavení speciálně určená pro sdílení několika aplikacemi v počítači.</span><span class="sxs-lookup"><span data-stu-id="14726-105">The global assembly cache stores assemblies specifically designated to be shared by several applications on the computer.</span></span> <span data-ttu-id="14726-106">Sestavení musí mít silný název, který se má nainstalovat do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="14726-106">An assembly must have a strong name to be installed in the global assembly cache.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="14726-107">Sestavení umístěná v globální mezipaměti sestavení (GAC) musí mít stejný název sestavení a název souboru (včetně přípony názvu souboru).</span><span class="sxs-lookup"><span data-stu-id="14726-107">Assemblies placed in the global assembly cache must have the same assembly name and file name (not including the file name extension).</span></span> <span data-ttu-id="14726-108">Například sestavení s názvem sestavení myAssembly musí mít název souboru buď myAssembly. exe, nebo myAssembly. dll.</span><span class="sxs-lookup"><span data-stu-id="14726-108">For example, an assembly with the assembly name of myAssembly must have a file name of either myAssembly.exe or myAssembly.dll.</span></span>  
  
 <span data-ttu-id="14726-109">Sestavení byste měli sdílet tak, že je nainstalujete do globální mezipaměti sestavení (GAC) pouze v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="14726-109">You should share assemblies by installing them into the global assembly cache only when necessary.</span></span> <span data-ttu-id="14726-110">Obecné pokyny, udržujte závislosti sestavení soukromě a vyhledejte sestavení v adresáři aplikace, pokud není explicitně požadováno sdílení sestavení.</span><span class="sxs-lookup"><span data-stu-id="14726-110">As a general guideline, keep assembly dependencies private and locate assemblies in the application directory unless sharing an assembly is explicitly required.</span></span> <span data-ttu-id="14726-111">Kromě toho není nutné instalovat sestavení do globální mezipaměti sestavení (GAC), aby byly přístupné pro zprostředkovatele komunikace s objekty COM nebo nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="14726-111">In addition, you do not have to install assemblies into the global assembly cache to make them accessible to COM interop or unmanaged code.</span></span>  
  
 <span data-ttu-id="14726-112">Existuje několik důvodů, proč je vhodné nainstalovat sestavení do globální mezipaměti sestavení (GAC):</span><span class="sxs-lookup"><span data-stu-id="14726-112">There are several reasons why you might want to install an assembly into the global assembly cache:</span></span>  
  
- <span data-ttu-id="14726-113">Sdílené umístění.</span><span class="sxs-lookup"><span data-stu-id="14726-113">Shared location.</span></span>  
  
     <span data-ttu-id="14726-114">Sestavení, která by měla být použita aplikacemi, lze umístit do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="14726-114">Assemblies that should be used by applications can be put in the global assembly cache.</span></span> <span data-ttu-id="14726-115">Například pokud má všechny aplikace použít sestavení umístěné v globální mezipaměti sestavení (GAC), do souboru Machine. config, který přesměrovává odkazy na sestavení, lze přidat příkaz zásad verze.</span><span class="sxs-lookup"><span data-stu-id="14726-115">For example, if all applications should use an assembly located in the global assembly cache, a version policy statement can be added to the Machine.config file that redirects references to the assembly.</span></span>  
  
- <span data-ttu-id="14726-116">Zabezpečení souborů.</span><span class="sxs-lookup"><span data-stu-id="14726-116">File security.</span></span>  
  
     <span data-ttu-id="14726-117">Správci často chrání adresář kořenová_složka_systému pomocí seznamu Access Control (ACL) pro řízení přístupu pro zápis a spouštění.</span><span class="sxs-lookup"><span data-stu-id="14726-117">Administrators often protect the systemroot directory using an Access Control List (ACL) to control write and execute access.</span></span> <span data-ttu-id="14726-118">Vzhledem k tomu, že je globální mezipaměť sestavení (GAC) nainstalována v adresáři kořenová_složka_systému, zdědí seznam řízení přístupu daného adresáře.</span><span class="sxs-lookup"><span data-stu-id="14726-118">Because the global assembly cache is installed in the systemroot directory, it inherits that directory's ACL.</span></span> <span data-ttu-id="14726-119">Doporučujeme, aby odstraňování souborů z globální mezipaměti sestavení bylo povoleno pouze uživatelům s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="14726-119">It is recommended that only users with Administrator privileges be allowed to delete files from the global assembly cache.</span></span>  
  
- <span data-ttu-id="14726-120">Souběžná Správa verzí.</span><span class="sxs-lookup"><span data-stu-id="14726-120">Side-by-side versioning.</span></span>  
  
     <span data-ttu-id="14726-121">V globální mezipaměti sestavení (GAC) je možné uchovávat více kopií sestavení se stejným názvem, ale různé informace o verzi.</span><span class="sxs-lookup"><span data-stu-id="14726-121">Multiple copies of assemblies with the same name but different version information can be maintained in the global assembly cache.</span></span>  
  
- <span data-ttu-id="14726-122">Další umístění pro hledání.</span><span class="sxs-lookup"><span data-stu-id="14726-122">Additional search location.</span></span>  
  
     <span data-ttu-id="14726-123">Modul CLR (Common Language Runtime) kontroluje globální mezipaměť sestavení (GAC) pro sestavení, které odpovídá žádosti o sestavení, před prošetřením nebo použitím informací o základu kódu v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="14726-123">The common language runtime checks the global assembly cache for an assembly that matches the assembly request before probing or using the codebase information in a configuration file.</span></span>  
  
 <span data-ttu-id="14726-124">Všimněte si, že existují scénáře, kde explicitně nechcete instalovat sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="14726-124">Note that there are scenarios where you explicitly do not want to install an assembly into the global assembly cache.</span></span> <span data-ttu-id="14726-125">Pokud umístíte jedno ze sestavení, která tvoří aplikaci do globální mezipaměti sestavení (GAC), nelze již aplikaci replikovat nebo nainstalovat pomocí příkazu XCOPY ke zkopírování adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="14726-125">If you place one of the assemblies that make up an application into the global assembly cache, you can no longer replicate or install the application by using XCOPY to copy the application directory.</span></span> <span data-ttu-id="14726-126">V takovém případě musíte také přesunout sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="14726-126">In this case, you must also move the assembly into the global assembly cache.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="14726-127">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="14726-127">In This Section</span></span>  
 [<span data-ttu-id="14726-128">Postupy: Instalace sestavení do globální mezipaměti sestavení (GAC)</span><span class="sxs-lookup"><span data-stu-id="14726-128">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 <span data-ttu-id="14726-129">Popisuje způsoby instalace sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="14726-129">Describes the ways to install an assembly into the global assembly cache.</span></span>  
  
 [<span data-ttu-id="14726-130">Postupy: Zobrazit obsah globální mezipaměti sestavení (GAC)</span><span class="sxs-lookup"><span data-stu-id="14726-130">How to: View the Contents of the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md)  
 <span data-ttu-id="14726-131">Vysvětluje, jak použít nástroj [Gacutil. exe (nástroj Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) k zobrazení obsahu globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="14726-131">Explains how to use the [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache.</span></span>  
  
 [<span data-ttu-id="14726-132">Postupy: Odebrání sestavení z globální mezipaměti sestavení (GAC)</span><span class="sxs-lookup"><span data-stu-id="14726-132">How to: Remove an Assembly from the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 <span data-ttu-id="14726-133">Vysvětluje, jak použít nástroj [Gacutil. exe (nástroj Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) k odebrání sestavení z globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="14726-133">Explains how to use the [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to remove an assembly from the global assembly cache.</span></span>  
  
 [<span data-ttu-id="14726-134">Používání obsluhovaných komponent s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="14726-134">Using Serviced Components with the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/use-serviced-components-with-the-gac.md)  
 <span data-ttu-id="14726-135">Vysvětluje, proč se obsluhované komponenty (spravované komponenty modelu COM+) měly umístit do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="14726-135">Explains why serviced components (managed COM+ components) should be placed in the global assembly cache.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="14726-136">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="14726-136">Related Sections</span></span>  
 [<span data-ttu-id="14726-137">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="14726-137">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 <span data-ttu-id="14726-138">Poskytuje přehled o vytváření sestavení.</span><span class="sxs-lookup"><span data-stu-id="14726-138">Provides an overview of creating assemblies.</span></span>  
  
 [<span data-ttu-id="14726-139">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="14726-139">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)  
 <span data-ttu-id="14726-140">Popisuje globální mezipaměť sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="14726-140">Describes the global assembly cache.</span></span>  
  
 [<span data-ttu-id="14726-141">Postupy: Zobrazit obsah sestavení</span><span class="sxs-lookup"><span data-stu-id="14726-141">How to: View Assembly Contents</span></span>](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 <span data-ttu-id="14726-142">Vysvětluje, jak používat nástroj [Ildasm. exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) k zobrazení informací o jazyce MSIL (Microsoft Intermediate Language) v sestavení.</span><span class="sxs-lookup"><span data-stu-id="14726-142">Explains how to use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in an assembly.</span></span>  
  
 [<span data-ttu-id="14726-143">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="14726-143">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 <span data-ttu-id="14726-144">Popisuje, jak modul CLR (Common Language Runtime) vyhledá a načte sestavení, která tvoří vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="14726-144">Describes how the common language runtime locates and loads the assemblies that make up your application.</span></span>  
  
 [<span data-ttu-id="14726-145">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="14726-145">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 <span data-ttu-id="14726-146">Popisuje sestavení, stavební bloky spravovaných aplikací.</span><span class="sxs-lookup"><span data-stu-id="14726-146">Describes assemblies, the building blocks of managed applications.</span></span>
