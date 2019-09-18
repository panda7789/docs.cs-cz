---
title: Globální mezipaměť sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache)
- ACLs [.NET Framework]
- global assembly cache
- cache [.NET Framework], global assembly cache
- global assembly cache, about
- access control lists [.NET Framework]
ms.assetid: cf5eacd0-d3ec-4879-b6da-5fd5e4372202
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a2ac0c7fb5f89c7d6b9daba8da7b37d1135acb6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053187"
---
# <a name="global-assembly-cache"></a><span data-ttu-id="1c87a-102">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="1c87a-102">Global Assembly Cache</span></span>
<span data-ttu-id="1c87a-103">Každý počítač, ve kterém je nainstalován modul CLR (Common Language Runtime), má mezipaměť kódu v celém počítači nazývanou globální mezipaměť sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="1c87a-103">Each computer where the Common Language Runtime is installed has a machine-wide code cache called the Global Assembly Cache.</span></span> <span data-ttu-id="1c87a-104">Globální mezipaměť sestavení ukládá sestavení speciálně určená pro sdílení několika aplikacemi v počítači.</span><span class="sxs-lookup"><span data-stu-id="1c87a-104">The Global Assembly Cache stores assemblies specifically designated to be shared by several applications on the computer.</span></span>  
  
 <span data-ttu-id="1c87a-105">Sestavení byste měli sdílet tak, že je nainstalujete do globální mezipaměti sestavení (GAC) pouze v případě, že potřebujete.</span><span class="sxs-lookup"><span data-stu-id="1c87a-105">You should share assemblies by installing them into the Global Assembly Cache only when you need to.</span></span> <span data-ttu-id="1c87a-106">V rámci obecných pokynů, udržujte závislosti sestavení soukromě a vyhledejte sestavení v adresáři aplikace, pokud není explicitně požadováno sdílení sestavení.</span><span class="sxs-lookup"><span data-stu-id="1c87a-106">As a general guideline, keep assembly dependencies private, and locate assemblies in the application directory unless sharing an assembly is explicitly required.</span></span> <span data-ttu-id="1c87a-107">Kromě toho není nutné instalovat sestavení do globální mezipaměti sestavení (GAC), aby je bylo možné zpřístupnit pro zprostředkovatele komunikace s objekty COM nebo nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="1c87a-107">In addition, it is not necessary to install assemblies into the Global Assembly Cache to make them accessible to COM interop or unmanaged code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c87a-108">Existují situace, kdy explicitně nechcete instalovat sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="1c87a-108">There are scenarios where you explicitly do not want to install an assembly into the Global Assembly Cache.</span></span> <span data-ttu-id="1c87a-109">Pokud umístíte jedno ze sestavení, které tvoří aplikaci v globální mezipaměti sestavení (GAC), již nelze replikovat nebo nainstalovat aplikaci pomocí příkazu **xcopy** pro zkopírování adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="1c87a-109">If you place one of the assemblies that make up an application in the Global Assembly Cache, you can no longer replicate or install the application by using the **xcopy** command to copy the application directory.</span></span> <span data-ttu-id="1c87a-110">Je nutné přesunout sestavení také v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="1c87a-110">You must move the assembly in the Global Assembly Cache as well.</span></span>  
  
 <span data-ttu-id="1c87a-111">Existují dva způsoby, jak nasadit sestavení do globální mezipaměti sestavení (GAC):</span><span class="sxs-lookup"><span data-stu-id="1c87a-111">There are two ways to deploy an assembly into the Global Assembly Cache:</span></span>  
  
- <span data-ttu-id="1c87a-112">Použijte instalační program navržený pro práci s globální mezipamětí sestavení.</span><span class="sxs-lookup"><span data-stu-id="1c87a-112">Use an installer designed to work with the Global Assembly Cache.</span></span> <span data-ttu-id="1c87a-113">Toto je upřednostňovaná možnost pro instalaci sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="1c87a-113">This is the preferred option for installing assemblies into the Global Assembly Cache.</span></span>  
  
- <span data-ttu-id="1c87a-114">Použijte vývojářský nástroj nazvaný [Global Assembly Cache (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md), který poskytuje Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="1c87a-114">Use a developer tool called the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md), provided by the Windows SDK.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="1c87a-115">V rámci scénářů nasazení použijte Instalační služba systému Windows k instalaci sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="1c87a-115">In deployment scenarios, use Windows Installer to install assemblies into the Global Assembly Cache.</span></span> <span data-ttu-id="1c87a-116">Použijte nástroj globální mezipaměť sestavení (GAC) pouze ve scénářích vývoje, protože neposkytuje počítání odkazů na sestavení a další funkce, které jsou k dispozici při použití Instalační služba systému Windows.</span><span class="sxs-lookup"><span data-stu-id="1c87a-116">Use the Global Assembly Cache tool only in development scenarios, because it does not provide assembly reference counting and other features provided when using the Windows Installer.</span></span>  
  
 <span data-ttu-id="1c87a-117">Počínaje .NET Framework 4 je výchozí umístění pro globální mezipaměť sestavení **%windir%\Microsoft.NET\assembly**.</span><span class="sxs-lookup"><span data-stu-id="1c87a-117">Starting with the .NET Framework 4, the default location for the Global Assembly Cache is **%windir%\Microsoft.NET\assembly**.</span></span> <span data-ttu-id="1c87a-118">V dřívějších verzích .NET Framework je výchozí umístění **%windir%\assembly**.</span><span class="sxs-lookup"><span data-stu-id="1c87a-118">In earlier versions of the .NET Framework, the default location is **%windir%\assembly**.</span></span>  
  
 <span data-ttu-id="1c87a-119">Správci často chrání adresář kořenová_složka_systému pomocí seznamu řízení přístupu (ACL) k řízení přístupu pro zápis a spouštění.</span><span class="sxs-lookup"><span data-stu-id="1c87a-119">Administrators often protect the systemroot directory using an access control list (ACL) to control write and execute access.</span></span> <span data-ttu-id="1c87a-120">Vzhledem k tomu, že je globální mezipaměť sestavení (GAC) nainstalovaná v podadresáři kořenové složky adresáře, zdědí seznam ACL tohoto adresáře.</span><span class="sxs-lookup"><span data-stu-id="1c87a-120">Because the Global Assembly Cache is installed in a subdirectory of the systemroot directory, it inherits that directory's ACL.</span></span> <span data-ttu-id="1c87a-121">Doporučujeme, aby odstraňování souborů z globální mezipaměti sestavení bylo povoleno pouze uživatelům s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="1c87a-121">It is recommended that only users with Administrator privileges be allowed to delete files from the Global Assembly Cache.</span></span>  
  
 <span data-ttu-id="1c87a-122">Sestavení nasazená v globální mezipaměti sestavení (GAC) musí mít silný název.</span><span class="sxs-lookup"><span data-stu-id="1c87a-122">Assemblies deployed in the Global Assembly Cache must have a strong name.</span></span> <span data-ttu-id="1c87a-123">Když je sestavení přidáno do globální mezipaměti sestavení (GAC), kontroly integrity se provádí na všech souborech, které tvoří sestavení.</span><span class="sxs-lookup"><span data-stu-id="1c87a-123">When an assembly is added to the Global Assembly Cache, integrity checks are performed on all files that make up the assembly.</span></span> <span data-ttu-id="1c87a-124">Mezipaměť provádí tyto kontroly integrity, aby bylo zajištěno, že sestavení nebylo manipulováno, například když došlo ke změně souboru, ale manifest neodráží změnu.</span><span class="sxs-lookup"><span data-stu-id="1c87a-124">The cache performs these integrity checks to ensure that an assembly has not been tampered with, for example, when a file has changed but the manifest does not reflect the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c87a-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1c87a-125">See also</span></span>

- [<span data-ttu-id="1c87a-126">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="1c87a-126">Assemblies in .NET</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="1c87a-127">Práce se sestaveními a s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="1c87a-127">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="1c87a-128">Sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="1c87a-128">Strong-Named Assemblies</span></span>](../../standard/assembly/strong-named.md)
