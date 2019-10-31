---
title: Fúze globálních statických funkcí
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged global static functions [.NET Framework], fusion
- fusion global static functions [.NET Framework]
- global static functions [.NET Framework fusion]
ms.assetid: 229b2188-9168-4b44-a987-e1f515494688
ms.openlocfilehash: ff94ed23f3e39888b4f7e255feece99898f8aa74
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108272"
---
# <a name="fusion-global-static-functions"></a><span data-ttu-id="66138-102">Fúze globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="66138-102">Fusion Global Static Functions</span></span>
<span data-ttu-id="66138-103">Tato část popisuje nespravované globální statické funkce, které používá rozhraní API pro syntézu.</span><span class="sxs-lookup"><span data-stu-id="66138-103">This section describes the unmanaged global static functions that the fusion API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="66138-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="66138-104">In This Section</span></span>  
 [<span data-ttu-id="66138-105">ClearDownloadCache – funkce</span><span class="sxs-lookup"><span data-stu-id="66138-105">ClearDownloadCache Function</span></span>](cleardownloadcache-function.md)  
 <span data-ttu-id="66138-106">Vymaže globální mezipaměť sestavení (GAC) pro stažená sestavení.</span><span class="sxs-lookup"><span data-stu-id="66138-106">Clears the global assembly cache of downloaded assemblies.</span></span>  
  
 [<span data-ttu-id="66138-107">CompareAssemblyIdentity – funkce</span><span class="sxs-lookup"><span data-stu-id="66138-107">CompareAssemblyIdentity Function</span></span>](compareassemblyidentity-function.md)  
 <span data-ttu-id="66138-108">Porovná dvě identity sestavení a určí, zda jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="66138-108">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
 [<span data-ttu-id="66138-109">CreateApplicationContext – funkce</span><span class="sxs-lookup"><span data-stu-id="66138-109">CreateApplicationContext Function</span></span>](createapplicationcontext-function.md)  
 <span data-ttu-id="66138-110">Pouze interní.</span><span class="sxs-lookup"><span data-stu-id="66138-110">Internal only.</span></span> <span data-ttu-id="66138-111">(Tato funkce podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.)</span><span class="sxs-lookup"><span data-stu-id="66138-111">(This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="66138-112">CreateAssemblyCache – funkce</span><span class="sxs-lookup"><span data-stu-id="66138-112">CreateAssemblyCache Function</span></span>](createassemblycache-function.md)  
 <span data-ttu-id="66138-113">Získá ukazatel na novou instanci [IAssemblyCache](iassemblycache-interface.md) , která představuje globální mezipaměť sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="66138-113">Gets a pointer to a new [IAssemblyCache](iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
 [<span data-ttu-id="66138-114">CreateAssemblyEnum – funkce</span><span class="sxs-lookup"><span data-stu-id="66138-114">CreateAssemblyEnum Function</span></span>](createassemblyenum-function.md)  
 <span data-ttu-id="66138-115">Získá ukazatel na instanci [IAssemblyEnum](iassemblyenum-interface.md) , která představuje seznam objektů, které existují v zadaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="66138-115">Gets a pointer to an [IAssemblyEnum](iassemblyenum-interface.md) instance that represents a list of objects that exist in the specified assembly.</span></span>  
  
 [<span data-ttu-id="66138-116">CreateAssemblyNameObject – funkce</span><span class="sxs-lookup"><span data-stu-id="66138-116">CreateAssemblyNameObject Function</span></span>](createassemblynameobject-function.md)  
 <span data-ttu-id="66138-117">Získá ukazatel na instanci [IAssemblyName](iassemblyname-interface.md) , která představuje jedinečnou identitu sestavení se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="66138-117">Gets a pointer to an [IAssemblyName](iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
 [<span data-ttu-id="66138-118">CreateHistoryReader – funkce</span><span class="sxs-lookup"><span data-stu-id="66138-118">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)  
 <span data-ttu-id="66138-119">Vytvoří čtečku historie pro zadaný soubor.</span><span class="sxs-lookup"><span data-stu-id="66138-119">Creates a history reader for the specified file.</span></span>  
  
 [<span data-ttu-id="66138-120">CreateInstallReferenceEnum – funkce</span><span class="sxs-lookup"><span data-stu-id="66138-120">CreateInstallReferenceEnum Function</span></span>](createinstallreferenceenum-function.md)  
 <span data-ttu-id="66138-121">Získá ukazatel na instanci [IInstallReferenceEnum –](iinstallreferenceenum-interface.md) , která představuje seznam odkazů aplikace na zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="66138-121">Gets a pointer to an [IInstallReferenceEnum](iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
 [<span data-ttu-id="66138-122">GetAppIdAuthority – funkce</span><span class="sxs-lookup"><span data-stu-id="66138-122">GetAppIdAuthority Function</span></span>](getappidauthority-function.md)  
 <span data-ttu-id="66138-123">Získá ukazatel na instanci [IAppIdAuthority –](iappidauthority-interface.md) , která spravuje klíče pro identity aplikace a odkazy.</span><span class="sxs-lookup"><span data-stu-id="66138-123">Gets a pointer to an [IAppIdAuthority](iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="66138-124">GetAssemblyIdentityFromFile – funkce</span><span class="sxs-lookup"><span data-stu-id="66138-124">GetAssemblyIdentityFromFile Function</span></span>](getassemblyidentityfromfile-function.md)  
 <span data-ttu-id="66138-125">Získá ukazatel na objekt `IUnknown` se zadaným `IID` v sestavení v zadané cestě k souboru.</span><span class="sxs-lookup"><span data-stu-id="66138-125">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
 [<span data-ttu-id="66138-126">GetCachePath – funkce</span><span class="sxs-lookup"><span data-stu-id="66138-126">GetCachePath Function</span></span>](getcachepath-function.md)  
 <span data-ttu-id="66138-127">Načte cestu k sestavení v mezipaměti pomocí zadaných příznaků.</span><span class="sxs-lookup"><span data-stu-id="66138-127">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
 [<span data-ttu-id="66138-128">GetHistoryFileDirectory – funkce</span><span class="sxs-lookup"><span data-stu-id="66138-128">GetHistoryFileDirectory Function</span></span>](gethistoryfiledirectory-function.md)  
 <span data-ttu-id="66138-129">Načte cestu k adresáři historie aplikace.</span><span class="sxs-lookup"><span data-stu-id="66138-129">Retrieves the path of the application history directory.</span></span>  
  
 [<span data-ttu-id="66138-130">GetIdentityAuthority – funkce</span><span class="sxs-lookup"><span data-stu-id="66138-130">GetIdentityAuthority Function</span></span>](getidentityauthority-function.md)  
 <span data-ttu-id="66138-131">Získá ukazatel na instanci [IIdentityAuthority –](iidentityauthority-interface.md) , která spravuje klíče pro objekty kódu.</span><span class="sxs-lookup"><span data-stu-id="66138-131">Gets a pointer to an [IIdentityAuthority](iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
 [<span data-ttu-id="66138-132">IsFrameworkAssembly – funkce</span><span class="sxs-lookup"><span data-stu-id="66138-132">IsFrameworkAssembly Function</span></span>](isframeworkassembly-function.md)  
 <span data-ttu-id="66138-133">Získá hodnotu, která označuje, zda je zadané sestavení spravováno.</span><span class="sxs-lookup"><span data-stu-id="66138-133">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
 [<span data-ttu-id="66138-134">NukeDownloadedCache – funkce</span><span class="sxs-lookup"><span data-stu-id="66138-134">NukeDownloadedCache Function</span></span>](nukedownloadedcache-function.md)  
 <span data-ttu-id="66138-135">Odstraní mezipaměť pro stažení modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="66138-135">Deletes the common language runtime download cache.</span></span>  
  
 [<span data-ttu-id="66138-136">PreBindAssemblyEx – funkce</span><span class="sxs-lookup"><span data-stu-id="66138-136">PreBindAssemblyEx Function</span></span>](prebindassemblyex-function.md)  
 <span data-ttu-id="66138-137">Načte zobrazovaný název po zásadě pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="66138-137">Gets the post-policy display name for an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="66138-138">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="66138-138">Related Sections</span></span>  
 [<span data-ttu-id="66138-139">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="66138-139">Fusion Interfaces</span></span>](fusion-interfaces.md)  
  
 [<span data-ttu-id="66138-140">Výčty pro fúze</span><span class="sxs-lookup"><span data-stu-id="66138-140">Fusion Enumerations</span></span>](fusion-enumerations.md)  
  
 [<span data-ttu-id="66138-141">Struktury pro fúze</span><span class="sxs-lookup"><span data-stu-id="66138-141">Fusion Structures</span></span>](fusion-structures.md)  
  
 [<span data-ttu-id="66138-142">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="66138-142">Global Assembly Cache</span></span>](../../app-domains/gac.md)
