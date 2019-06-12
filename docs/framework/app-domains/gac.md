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
ms.openlocfilehash: 858d651523ac6196aa2dcad008ea53674eb01b04
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2019
ms.locfileid: "66832844"
---
# <a name="global-assembly-cache"></a><span data-ttu-id="4ffa9-102">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="4ffa9-102">Global Assembly Cache</span></span>
<span data-ttu-id="4ffa9-103">Každý počítač, kde je nainstalován modul Common Language Runtime obsahuje mezipaměť kódu celého stroje názvem do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-103">Each computer where the Common Language Runtime is installed has a machine-wide code cache called the Global Assembly Cache.</span></span> <span data-ttu-id="4ffa9-104">Global Assembly Cache ukládá sestavení speciálně určené ke sdílení více aplikacemi v počítači.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-104">The Global Assembly Cache stores assemblies specifically designated to be shared by several applications on the computer.</span></span>  
  
 <span data-ttu-id="4ffa9-105">Sestavení by měly sdílet prostřednictvím instalace pouze v případě, že budete muset do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-105">You should share assemblies by installing them into the Global Assembly Cache only when you need to.</span></span> <span data-ttu-id="4ffa9-106">V rámci obecných pokynů udržujte soukromé závislosti sestavení a vyhledání sestavení v adresáři aplikace, pokud sdílení sestavení není explicitně vyžadováno.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-106">As a general guideline, keep assembly dependencies private, and locate assemblies in the application directory unless sharing an assembly is explicitly required.</span></span> <span data-ttu-id="4ffa9-107">Kromě toho není nutné pro instalaci sestavení do globální mezipaměti sestavení zajistíte jejich přístupnost COM interop nebo nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-107">In addition, it is not necessary to install assemblies into the Global Assembly Cache to make them accessible to COM interop or unmanaged code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4ffa9-108">Existují scénáře, ve kterém můžete explicitně nechcete, aby instalace sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-108">There are scenarios where you explicitly do not want to install an assembly into the Global Assembly Cache.</span></span> <span data-ttu-id="4ffa9-109">Pokud umístíte jednoho sestavení, které tvoří aplikaci v globální mezipaměti sestavení, můžete už replikovat nebo instalaci aplikace s použitím **xcopy** příkazu kopírování adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-109">If you place one of the assemblies that make up an application in the Global Assembly Cache, you can no longer replicate or install the application by using the **xcopy** command to copy the application directory.</span></span> <span data-ttu-id="4ffa9-110">Sestavení je nutné přesunout i globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-110">You must move the assembly in the Global Assembly Cache as well.</span></span>  
  
 <span data-ttu-id="4ffa9-111">Existují dva způsoby, jak nasadit sestavení do globální mezipaměti sestavení:</span><span class="sxs-lookup"><span data-stu-id="4ffa9-111">There are two ways to deploy an assembly into the Global Assembly Cache:</span></span>  
  
- <span data-ttu-id="4ffa9-112">Pomocí instalačního programu navržené pro práci s globální pamětí sestavení.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-112">Use an installer designed to work with the Global Assembly Cache.</span></span> <span data-ttu-id="4ffa9-113">Toto je upřednostňovaná možnost pro instalaci sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-113">This is the preferred option for installing assemblies into the Global Assembly Cache.</span></span>  
  
- <span data-ttu-id="4ffa9-114">Použijte nástroj pro vývojáře, volá se, [nástroj Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md), k dispozici ve Windows Software Development Kit (SDK).</span><span class="sxs-lookup"><span data-stu-id="4ffa9-114">Use a developer tool called the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md), provided by the Windows Software Development Kit (SDK).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4ffa9-115">Ve scénářích nasazení použijte instalační služby systému Windows pro instalaci sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-115">In deployment scenarios, use Windows Installer to install assemblies into the Global Assembly Cache.</span></span> <span data-ttu-id="4ffa9-116">Použijte nástroj Global Assembly Cache pouze ve vývojové scénáře, protože neposkytuje počítání odkazů sestavení a další funkce, které poskytuje při použití Instalační služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-116">Use the Global Assembly Cache tool only in development scenarios, because it does not provide assembly reference counting and other features provided when using the Windows Installer.</span></span>  
  
 <span data-ttu-id="4ffa9-117">Od verze rozhraní .NET Framework 4, výchozím umístěním pro globální mezipaměť sestavení je **%windir%\Microsoft.NET\assembly**.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-117">Starting with the .NET Framework 4, the default location for the Global Assembly Cache is **%windir%\Microsoft.NET\assembly**.</span></span> <span data-ttu-id="4ffa9-118">V dřívějších verzích rozhraní .NET Framework, výchozí umístění je **%windir%\assembly**.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-118">In earlier versions of the .NET Framework, the default location is **%windir%\assembly**.</span></span>  
  
 <span data-ttu-id="4ffa9-119">Správci často chrání pomocí seznam řízení přístupu (ACL) pro řízení zápisu a přístup pro spouštění kořenovou složku.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-119">Administrators often protect the systemroot directory using an access control list (ACL) to control write and execute access.</span></span> <span data-ttu-id="4ffa9-120">Protože je nainstalována do globální mezipaměti sestavení v podadresáři kořenového adresáře dědí seznamu ACL tohoto adresáře.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-120">Because the Global Assembly Cache is installed in a subdirectory of the systemroot directory, it inherits that directory's ACL.</span></span> <span data-ttu-id="4ffa9-121">Doporučuje se, že pouze uživatelé s oprávněními správce bude moct odstranit soubory z globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-121">It is recommended that only users with Administrator privileges be allowed to delete files from the Global Assembly Cache.</span></span>  
  
 <span data-ttu-id="4ffa9-122">Sestavení, které jsou nasazené v globální mezipaměti sestavení musí mít silný název.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-122">Assemblies deployed in the Global Assembly Cache must have a strong name.</span></span> <span data-ttu-id="4ffa9-123">Pokud je sestavení přidáno do globální mezipaměti sestavení, kontroly integrity probíhají na všechny soubory, které tvoří sestavení.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-123">When an assembly is added to the Global Assembly Cache, integrity checks are performed on all files that make up the assembly.</span></span> <span data-ttu-id="4ffa9-124">Mezipaměť provádí tyto kontroly integrity zajistit, že sestavení nebylo manipulováno, například když došlo ke změně souboru, ale manifest neodráží změny.</span><span class="sxs-lookup"><span data-stu-id="4ffa9-124">The cache performs these integrity checks to ensure that an assembly has not been tampered with, for example, when a file has changed but the manifest does not reflect the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ffa9-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ffa9-125">See also</span></span>

- [<span data-ttu-id="4ffa9-126">Sestavení v modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="4ffa9-126">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [<span data-ttu-id="4ffa9-127">Práce se sestaveními a s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="4ffa9-127">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="4ffa9-128">Sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="4ffa9-128">Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/strong-named-assemblies.md)
