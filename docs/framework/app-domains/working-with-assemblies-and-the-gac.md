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
ms.openlocfilehash: 91e780ed7e841809f21130822babe55ad4935670
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="working-with-assemblies-and-the-global-assembly-cache"></a><span data-ttu-id="18328-102">Práce se sestaveními a s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="18328-102">Working with Assemblies and the Global Assembly Cache</span></span>
<span data-ttu-id="18328-103">Pokud máte v úmyslu sdílet sestavení mezi více aplikacemi, můžete ji nainstalovat do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="18328-103">If you intend to share an assembly among several applications, you can install it into the global assembly cache.</span></span> <span data-ttu-id="18328-104">Každý počítač, kde je nainstalován modul common language runtime má tato mezipaměť strojový kód.</span><span class="sxs-lookup"><span data-stu-id="18328-104">Each computer where the common language runtime is installed has this machine-wide code cache.</span></span> <span data-ttu-id="18328-105">Globální mezipaměti sestavení uchovává sestavení konkrétně určená ke sdílení více aplikacemi v počítači.</span><span class="sxs-lookup"><span data-stu-id="18328-105">The global assembly cache stores assemblies specifically designated to be shared by several applications on the computer.</span></span> <span data-ttu-id="18328-106">Sestavení musí mít silným názvem být nainstalovaný v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="18328-106">An assembly must have a strong name to be installed in the global assembly cache.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18328-107">Sestavení, které jsou umístěny v globální mezipaměti sestavení musí mít stejný název sestavení a název souboru (bez zahrnutí příponu názvu souboru).</span><span class="sxs-lookup"><span data-stu-id="18328-107">Assemblies placed in the global assembly cache must have the same assembly name and file name (not including the file name extension).</span></span> <span data-ttu-id="18328-108">Sestavení s názvem sestavení myAssembly musí mít například název souboru myAssembly.exe nebo myAssembly.dll.</span><span class="sxs-lookup"><span data-stu-id="18328-108">For example, an assembly with the assembly name of myAssembly must have a file name of either myAssembly.exe or myAssembly.dll.</span></span>  
  
 <span data-ttu-id="18328-109">Sestavení by měly sdílet pomocí jejich instalace do globální mezipaměti sestavení pouze v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="18328-109">You should share assemblies by installing them into the global assembly cache only when necessary.</span></span> <span data-ttu-id="18328-110">V rámci obecných pokynů udržujte sestavení závislosti privátním a vyhledání sestavení v adresáři aplikace, pokud sdílení sestavení není explicitně nutné.</span><span class="sxs-lookup"><span data-stu-id="18328-110">As a general guideline, keep assembly dependencies private and locate assemblies in the application directory unless sharing an assembly is explicitly required.</span></span> <span data-ttu-id="18328-111">Kromě toho nemáte instalace sestavení do globální mezipaměti sestavení do zpřístupněte je COM spolupráce nebo nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="18328-111">In addition, you do not have to install assemblies into the global assembly cache to make them accessible to COM interop or unmanaged code.</span></span>  
  
 <span data-ttu-id="18328-112">Tady je několik důvodů, proč můžete chtít instalace sestavení do globální mezipaměti sestavení:</span><span class="sxs-lookup"><span data-stu-id="18328-112">There are several reasons why you might want to install an assembly into the global assembly cache:</span></span>  
  
-   <span data-ttu-id="18328-113">Sdílené umístění.</span><span class="sxs-lookup"><span data-stu-id="18328-113">Shared location.</span></span>  
  
     <span data-ttu-id="18328-114">Sestavení, která má být používána aplikace může být uvedena v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="18328-114">Assemblies that should be used by applications can be put in the global assembly cache.</span></span> <span data-ttu-id="18328-115">Například pokud všechny aplikace by měly používat sestavení v globální mezipaměti sestavení, prohlášení o zásadách verze lze přidat do souboru Machine.config, který přesměruje odkazy na sestavení.</span><span class="sxs-lookup"><span data-stu-id="18328-115">For example, if all applications should use an assembly located in the global assembly cache, a version policy statement can be added to the Machine.config file that redirects references to the assembly.</span></span>  
  
-   <span data-ttu-id="18328-116">Soubor zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="18328-116">File security.</span></span>  
  
     <span data-ttu-id="18328-117">Správci často chrání kořenovou složku pomocí seznamu řízení přístupu (ACL) k řízení zápisu a provést přístup.</span><span class="sxs-lookup"><span data-stu-id="18328-117">Administrators often protect the systemroot directory using an Access Control List (ACL) to control write and execute access.</span></span> <span data-ttu-id="18328-118">Protože globální mezipaměti sestavení je nainstalována v kořenové složce systému, dědí řízení přístupu tohoto adresáře.</span><span class="sxs-lookup"><span data-stu-id="18328-118">Because the global assembly cache is installed in the systemroot directory, it inherits that directory's ACL.</span></span> <span data-ttu-id="18328-119">Doporučuje se, že mohou pouze uživatelé s oprávněním správce k odstranění souborů z globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="18328-119">It is recommended that only users with Administrator privileges be allowed to delete files from the global assembly cache.</span></span>  
  
-   <span data-ttu-id="18328-120">Správa verzí vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="18328-120">Side-by-side versioning.</span></span>  
  
     <span data-ttu-id="18328-121">Více kopií sestavení se stejným názvem, ale s jinou verzi informace je možné udržovat v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="18328-121">Multiple copies of assemblies with the same name but different version information can be maintained in the global assembly cache.</span></span>  
  
-   <span data-ttu-id="18328-122">Další hledání umístění.</span><span class="sxs-lookup"><span data-stu-id="18328-122">Additional search location.</span></span>  
  
     <span data-ttu-id="18328-123">Modul CLR ověří globální mezipaměti sestavení pro sestavení, které odpovídají požadavku sestavení před použitím informací o kódu v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="18328-123">The common language runtime checks the global assembly cache for an assembly that matches the assembly request before probing or using the codebase information in a configuration file.</span></span>  
  
 <span data-ttu-id="18328-124">Všimněte si, že jsou scénáře, kde explicitně nechcete instalovat sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="18328-124">Note that there are scenarios where you explicitly do not want to install an assembly into the global assembly cache.</span></span> <span data-ttu-id="18328-125">Pokud jeden z těchto sestavení, které tvoří aplikaci do globální mezipaměti sestavení, můžete už replikovat nebo nainstalovat aplikaci pomocí příkazu XCOPY pro kopírování adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="18328-125">If you place one of the assemblies that make up an application into the global assembly cache, you can no longer replicate or install the application by using XCOPY to copy the application directory.</span></span> <span data-ttu-id="18328-126">V takovém případě musíte také přesunout sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="18328-126">In this case, you must also move the assembly into the global assembly cache.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="18328-127">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="18328-127">In This Section</span></span>  
 [<span data-ttu-id="18328-128">Postupy: Instalace sestavení do globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="18328-128">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 <span data-ttu-id="18328-129">Popisuje způsoby instalace sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="18328-129">Describes the ways to install an assembly into the global assembly cache.</span></span>  
  
 [<span data-ttu-id="18328-130">Postupy: Zobrazení obsahu globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="18328-130">How to: View the Contents of the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md)  
 <span data-ttu-id="18328-131">Vysvětluje, jak používat [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) zobrazení obsahu globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="18328-131">Explains how to use the [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache.</span></span>  
  
 [<span data-ttu-id="18328-132">Postupy: Odebrání sestavení z globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="18328-132">How to: Remove an Assembly from the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 <span data-ttu-id="18328-133">Vysvětluje, jak používat [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) pro odebrání sestavení z globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="18328-133">Explains how to use the [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to remove an assembly from the global assembly cache.</span></span>  
  
 [<span data-ttu-id="18328-134">Používání obsluhovaných komponent s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="18328-134">Using Serviced Components with the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/use-serviced-components-with-the-gac.md)  
 <span data-ttu-id="18328-135">Vysvětluje, proč obsluhované komponenty (spravované komponenty modelu COM +) musí být umístěny v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="18328-135">Explains why serviced components (managed COM+ components) should be placed in the global assembly cache.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="18328-136">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="18328-136">Related Sections</span></span>  
 [<span data-ttu-id="18328-137">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="18328-137">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 <span data-ttu-id="18328-138">Poskytuje přehled vytváření sestavení.</span><span class="sxs-lookup"><span data-stu-id="18328-138">Provides an overview of creating assemblies.</span></span>  
  
 [<span data-ttu-id="18328-139">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="18328-139">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)  
 <span data-ttu-id="18328-140">Popisuje globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="18328-140">Describes the global assembly cache.</span></span>  
  
 [<span data-ttu-id="18328-141">Postupy: Zobrazení obsahu sestavení</span><span class="sxs-lookup"><span data-stu-id="18328-141">How to: View Assembly Contents</span></span>](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 <span data-ttu-id="18328-142">Vysvětluje, jak používat [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) pro zobrazení informací (MSIL intermediate language) Microsoft v sestavení.</span><span class="sxs-lookup"><span data-stu-id="18328-142">Explains how to use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in an assembly.</span></span>  
  
 [<span data-ttu-id="18328-143">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="18328-143">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 <span data-ttu-id="18328-144">Popisuje, jak modul common language runtime vyhledá a načte sestavení, které tvoří vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="18328-144">Describes how the common language runtime locates and loads the assemblies that make up your application.</span></span>  
  
 [<span data-ttu-id="18328-145">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="18328-145">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 <span data-ttu-id="18328-146">Popisuje sestavení, stavební bloky spravovaných aplikací.</span><span class="sxs-lookup"><span data-stu-id="18328-146">Describes assemblies, the building blocks of managed applications.</span></span>
