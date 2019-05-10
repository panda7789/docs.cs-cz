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
ms.openlocfilehash: 363410baea1706211acaa639f1704e91230723a8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592747"
---
# <a name="working-with-assemblies-and-the-global-assembly-cache"></a><span data-ttu-id="5c342-102">Práce se sestaveními a s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="5c342-102">Working with Assemblies and the Global Assembly Cache</span></span>
<span data-ttu-id="5c342-103">Pokud máte v úmyslu sdílení sestavení mezi více aplikacemi, můžete ji nainstalovat do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="5c342-103">If you intend to share an assembly among several applications, you can install it into the global assembly cache.</span></span> <span data-ttu-id="5c342-104">Každý počítač, kde je nainstalován modul common language runtime obsahuje tuto mezipaměť kódu celého stroje.</span><span class="sxs-lookup"><span data-stu-id="5c342-104">Each computer where the common language runtime is installed has this machine-wide code cache.</span></span> <span data-ttu-id="5c342-105">Globální mezipaměti sestavení ukládá sestavení speciálně určené ke sdílení více aplikacemi v počítači.</span><span class="sxs-lookup"><span data-stu-id="5c342-105">The global assembly cache stores assemblies specifically designated to be shared by several applications on the computer.</span></span> <span data-ttu-id="5c342-106">Sestavení musí mít nainstalovaný v globální mezipaměti sestavení silným názvem.</span><span class="sxs-lookup"><span data-stu-id="5c342-106">An assembly must have a strong name to be installed in the global assembly cache.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c342-107">Sestavení do globální mezipaměti sestavení musí mít stejný název sestavení a název souboru (bez přípony názvu souboru).</span><span class="sxs-lookup"><span data-stu-id="5c342-107">Assemblies placed in the global assembly cache must have the same assembly name and file name (not including the file name extension).</span></span> <span data-ttu-id="5c342-108">Například sestavení s názvem sestavení myAssembly musí mít název souboru, myAssembly.exe buď myAssembly.dll.</span><span class="sxs-lookup"><span data-stu-id="5c342-108">For example, an assembly with the assembly name of myAssembly must have a file name of either myAssembly.exe or myAssembly.dll.</span></span>  
  
 <span data-ttu-id="5c342-109">Sestavení by měly sdílet pomocí instalace do globální mezipaměti sestavení pouze v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="5c342-109">You should share assemblies by installing them into the global assembly cache only when necessary.</span></span> <span data-ttu-id="5c342-110">V rámci obecných pokynů udržujte soukromé závislosti sestavení a vyhledání sestavení v adresáři aplikace, pokud sdílení sestavení není explicitně vyžadováno.</span><span class="sxs-lookup"><span data-stu-id="5c342-110">As a general guideline, keep assembly dependencies private and locate assemblies in the application directory unless sharing an assembly is explicitly required.</span></span> <span data-ttu-id="5c342-111">Kromě toho není nutné instalovat sestavení do globální mezipaměti sestavení zajistíte jejich přístupnost COM interop nebo nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="5c342-111">In addition, you do not have to install assemblies into the global assembly cache to make them accessible to COM interop or unmanaged code.</span></span>  
  
 <span data-ttu-id="5c342-112">Tady je několik důvodů, proč můžete chtít instalace sestavení do globální mezipaměti sestavení:</span><span class="sxs-lookup"><span data-stu-id="5c342-112">There are several reasons why you might want to install an assembly into the global assembly cache:</span></span>  
  
- <span data-ttu-id="5c342-113">Sdílené umístění.</span><span class="sxs-lookup"><span data-stu-id="5c342-113">Shared location.</span></span>  
  
     <span data-ttu-id="5c342-114">Sestavení, které by měly být používány aplikací můžete umístit do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="5c342-114">Assemblies that should be used by applications can be put in the global assembly cache.</span></span> <span data-ttu-id="5c342-115">Například zda všechny aplikace by měly používat sestavení v globální mezipaměti sestavení, prohlášením o zásadách verze lze přidat do souboru Machine.config. ten přesměruje odkazy na sestavení.</span><span class="sxs-lookup"><span data-stu-id="5c342-115">For example, if all applications should use an assembly located in the global assembly cache, a version policy statement can be added to the Machine.config file that redirects references to the assembly.</span></span>  
  
- <span data-ttu-id="5c342-116">Soubor zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5c342-116">File security.</span></span>  
  
     <span data-ttu-id="5c342-117">Správci často chrání pomocí seznamu řízení přístupu (ACL) pro řízení zápisu a přístup pro spouštění kořenovou složku.</span><span class="sxs-lookup"><span data-stu-id="5c342-117">Administrators often protect the systemroot directory using an Access Control List (ACL) to control write and execute access.</span></span> <span data-ttu-id="5c342-118">Protože je nainstalována do globální mezipaměti sestavení v kořenové složce dědí seznamu ACL tohoto adresáře.</span><span class="sxs-lookup"><span data-stu-id="5c342-118">Because the global assembly cache is installed in the systemroot directory, it inherits that directory's ACL.</span></span> <span data-ttu-id="5c342-119">Doporučuje se, že pouze uživatelé s oprávněními správce bude moct odstranit soubory z globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="5c342-119">It is recommended that only users with Administrator privileges be allowed to delete files from the global assembly cache.</span></span>  
  
- <span data-ttu-id="5c342-120">Správa verzí vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="5c342-120">Side-by-side versioning.</span></span>  
  
     <span data-ttu-id="5c342-121">V globální mezipaměti sestavení může být udržuje několik kopií sestavení se stejným názvem, ale informace o různých verzích.</span><span class="sxs-lookup"><span data-stu-id="5c342-121">Multiple copies of assemblies with the same name but different version information can be maintained in the global assembly cache.</span></span>  
  
- <span data-ttu-id="5c342-122">Poloha při hledání další.</span><span class="sxs-lookup"><span data-stu-id="5c342-122">Additional search location.</span></span>  
  
     <span data-ttu-id="5c342-123">Modul common language runtime vyhledává sestavení, které odpovídá požadavku sestavení před použitím informací o kódu v konfiguračním souboru do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="5c342-123">The common language runtime checks the global assembly cache for an assembly that matches the assembly request before probing or using the codebase information in a configuration file.</span></span>  
  
 <span data-ttu-id="5c342-124">Všimněte si, že jsou scénáře, kdy explicitně nechcete instalace sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="5c342-124">Note that there are scenarios where you explicitly do not want to install an assembly into the global assembly cache.</span></span> <span data-ttu-id="5c342-125">Pokud umístíte jednoho sestavení, které tvoří aplikaci do globální mezipaměti sestavení, můžete už replikovat nebo nainstalujte aplikaci pomocí příkazu XCOPY zkopírovat adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="5c342-125">If you place one of the assemblies that make up an application into the global assembly cache, you can no longer replicate or install the application by using XCOPY to copy the application directory.</span></span> <span data-ttu-id="5c342-126">V takovém případě musíte také přesunout sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="5c342-126">In this case, you must also move the assembly into the global assembly cache.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5c342-127">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="5c342-127">In This Section</span></span>  
 [<span data-ttu-id="5c342-128">Postupy: Instalace sestavení do globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="5c342-128">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 <span data-ttu-id="5c342-129">Popisuje způsoby instalace sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="5c342-129">Describes the ways to install an assembly into the global assembly cache.</span></span>  
  
 [<span data-ttu-id="5c342-130">Postupy: Zobrazení obsahu globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="5c342-130">How to: View the Contents of the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md)  
 <span data-ttu-id="5c342-131">Vysvětluje způsob používání [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) k zobrazení obsahu globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="5c342-131">Explains how to use the [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache.</span></span>  
  
 [<span data-ttu-id="5c342-132">Postupy: Odebrání sestavení z globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="5c342-132">How to: Remove an Assembly from the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 <span data-ttu-id="5c342-133">Vysvětluje způsob používání [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) odebrání sestavení z globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="5c342-133">Explains how to use the [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to remove an assembly from the global assembly cache.</span></span>  
  
 [<span data-ttu-id="5c342-134">Používání obsluhovaných komponent s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="5c342-134">Using Serviced Components with the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/use-serviced-components-with-the-gac.md)  
 <span data-ttu-id="5c342-135">Vysvětluje, proč obsluhované komponenty (spravované komponenty COM +.) umístit do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="5c342-135">Explains why serviced components (managed COM+ components) should be placed in the global assembly cache.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5c342-136">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="5c342-136">Related Sections</span></span>  
 [<span data-ttu-id="5c342-137">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="5c342-137">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 <span data-ttu-id="5c342-138">Poskytuje přehled o vytváření sestavení.</span><span class="sxs-lookup"><span data-stu-id="5c342-138">Provides an overview of creating assemblies.</span></span>  
  
 [<span data-ttu-id="5c342-139">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="5c342-139">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)  
 <span data-ttu-id="5c342-140">Popisuje globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="5c342-140">Describes the global assembly cache.</span></span>  
  
 [<span data-ttu-id="5c342-141">Postupy: Zobrazení obsahu sestavení</span><span class="sxs-lookup"><span data-stu-id="5c342-141">How to: View Assembly Contents</span></span>](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 <span data-ttu-id="5c342-142">Vysvětluje způsob používání [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) k zobrazení informací Microsoft intermediate language (MSIL) v sestavení.</span><span class="sxs-lookup"><span data-stu-id="5c342-142">Explains how to use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in an assembly.</span></span>  
  
 [<span data-ttu-id="5c342-143">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="5c342-143">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 <span data-ttu-id="5c342-144">Popisuje, jak modul common language runtime vyhledá a načte sestavení, které tvoří vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5c342-144">Describes how the common language runtime locates and loads the assemblies that make up your application.</span></span>  
  
 [<span data-ttu-id="5c342-145">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="5c342-145">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 <span data-ttu-id="5c342-146">Popisuje sestavení, stavební bloky spravovaných aplikací.</span><span class="sxs-lookup"><span data-stu-id="5c342-146">Describes assemblies, the building blocks of managed applications.</span></span>
