---
title: "Globální mezipaměť sestavení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache)
- ACLs [.NET Framework]
- global assembly cache
- cache [.NET Framework], global assembly cache
- global assembly cache, about
- access control lists [.NET Framework]
ms.assetid: cf5eacd0-d3ec-4879-b6da-5fd5e4372202
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9ca51a06e6e7ec89576facf3a70c789325fd893c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="global-assembly-cache"></a><span data-ttu-id="3e6db-102">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="3e6db-102">Global Assembly Cache</span></span>
<span data-ttu-id="3e6db-103">Každý počítač, kde je nainstalován modul common language runtime má mezipaměť strojový kód volá globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="3e6db-103">Each computer where the common language runtime is installed has a machine-wide code cache called the global assembly cache.</span></span> <span data-ttu-id="3e6db-104">Globální mezipaměti sestavení uchovává sestavení konkrétně určená ke sdílení více aplikacemi v počítači.</span><span class="sxs-lookup"><span data-stu-id="3e6db-104">The global assembly cache stores assemblies specifically designated to be shared by several applications on the computer.</span></span>  
  
 <span data-ttu-id="3e6db-105">Sestavení by měly sdílet instalací pouze v případě, že budete muset do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="3e6db-105">You should share assemblies by installing them into the global assembly cache only when you need to.</span></span> <span data-ttu-id="3e6db-106">V rámci obecných pokynů udržujte sestavení závislosti privátním a vyhledání sestavení v adresáři aplikace, pokud sdílení sestavení není explicitně nutné.</span><span class="sxs-lookup"><span data-stu-id="3e6db-106">As a general guideline, keep assembly dependencies private, and locate assemblies in the application directory unless sharing an assembly is explicitly required.</span></span> <span data-ttu-id="3e6db-107">Kromě toho není nutné instalovat sestavení do globální mezipaměti sestavení do zpřístupněte je COM spolupráce nebo nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="3e6db-107">In addition, it is not necessary to install assemblies into the global assembly cache to make them accessible to COM interop or unmanaged code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e6db-108">Existují scénáře, kde explicitně nechcete instalovat sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="3e6db-108">There are scenarios where you explicitly do not want to install an assembly into the global assembly cache.</span></span> <span data-ttu-id="3e6db-109">Pokud jeden z těchto sestavení, které tvoří aplikaci v globální mezipaměti sestavení, můžete už replikovat nebo nainstalujte aplikaci pomocí **xcopy** příkaz pro kopírování adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="3e6db-109">If you place one of the assemblies that make up an application in the global assembly cache, you can no longer replicate or install the application by using the **xcopy** command to copy the application directory.</span></span> <span data-ttu-id="3e6db-110">Je třeba přesunout sestavení v globální mezipaměti sestavení také.</span><span class="sxs-lookup"><span data-stu-id="3e6db-110">You must move the assembly in the global assembly cache as well.</span></span>  
  
 <span data-ttu-id="3e6db-111">Existují dva způsoby, jak nasazení sestavení do globální mezipaměti sestavení:</span><span class="sxs-lookup"><span data-stu-id="3e6db-111">There are two ways to deploy an assembly into the global assembly cache:</span></span>  
  
-   <span data-ttu-id="3e6db-112">Použijte instalační program navrženy pro práci s globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="3e6db-112">Use an installer designed to work with the global assembly cache.</span></span> <span data-ttu-id="3e6db-113">Toto je upřednostňovaná možnost pro instalace sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="3e6db-113">This is the preferred option for installing assemblies into the global assembly cache.</span></span>  
  
-   <span data-ttu-id="3e6db-114">Použijte nástroj vývojáře nazvaný [nástroj globální mezipaměti sestavení (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md), zadaný ve [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3e6db-114">Use a developer tool called the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md), provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3e6db-115">Ve scénářích nasazení použijte instalační služby systému Windows instalace sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="3e6db-115">In deployment scenarios, use Windows Installer to install assemblies into the global assembly cache.</span></span> <span data-ttu-id="3e6db-116">Používejte nástroj globální mezipaměti sestavení jenom v situacích, vývoj, protože neposkytuje počítání odkazů sestavení a další funkce poskytované při použití Instalační služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="3e6db-116">Use the Global Assembly Cache tool only in development scenarios, because it does not provide assembly reference counting and other features provided when using the Windows Installer.</span></span>  
  
 <span data-ttu-id="3e6db-117">Od verze rozhraní .NET Framework 4, je výchozím umístěním pro globální mezipaměti sestavení **%windir%\Microsoft.NET\assembly**.</span><span class="sxs-lookup"><span data-stu-id="3e6db-117">Starting with the .NET Framework 4, the default location for the global assembly cache is **%windir%\Microsoft.NET\assembly**.</span></span> <span data-ttu-id="3e6db-118">V dřívějších verzích rozhraní .NET Framework, výchozím umístěním je **%windir%\assembly**.</span><span class="sxs-lookup"><span data-stu-id="3e6db-118">In earlier versions of the .NET Framework, the default location is **%windir%\assembly**.</span></span>  
  
 <span data-ttu-id="3e6db-119">Správci často chrání kořenovou složku pomocí seznam řízení přístupu (ACL) k řízení zápisu a provést přístup.</span><span class="sxs-lookup"><span data-stu-id="3e6db-119">Administrators often protect the systemroot directory using an access control list (ACL) to control write and execute access.</span></span> <span data-ttu-id="3e6db-120">Protože globální mezipaměti sestavení je nainstalována v podadresáři kořenového adresáře systému, dědí seznamu ACL tohoto adresáře.</span><span class="sxs-lookup"><span data-stu-id="3e6db-120">Because the global assembly cache is installed in a subdirectory of the systemroot directory, it inherits that directory's ACL.</span></span> <span data-ttu-id="3e6db-121">Doporučuje se, že mohou pouze uživatelé s oprávněním správce k odstranění souborů z globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="3e6db-121">It is recommended that only users with Administrator privileges be allowed to delete files from the global assembly cache.</span></span>  
  
 <span data-ttu-id="3e6db-122">Sestavení nasazené v globální mezipaměti sestavení musí mít silný název.</span><span class="sxs-lookup"><span data-stu-id="3e6db-122">Assemblies deployed in the global assembly cache must have a strong name.</span></span> <span data-ttu-id="3e6db-123">Pokud je sestavení přidáno do globální mezipaměti sestavení, kontroly integrity se na všechny soubory, které tvoří sestavení.</span><span class="sxs-lookup"><span data-stu-id="3e6db-123">When an assembly is added to the global assembly cache, integrity checks are performed on all files that make up the assembly.</span></span> <span data-ttu-id="3e6db-124">Mezipaměť provádí tyto kontroly integrity zajistit, že sestavení nikdo neoprávněně nemanipuloval, například když došlo ke změně souboru, ale manifest nezohledňuje změnu.</span><span class="sxs-lookup"><span data-stu-id="3e6db-124">The cache performs these integrity checks to ensure that an assembly has not been tampered with, for example, when a file has changed but the manifest does not reflect the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e6db-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="3e6db-125">See Also</span></span>  
 [<span data-ttu-id="3e6db-126">Sestavení v modulu Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="3e6db-126">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [<span data-ttu-id="3e6db-127">Práce se sestaveními a globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="3e6db-127">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="3e6db-128">Sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="3e6db-128">Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/strong-named-assemblies.md)
