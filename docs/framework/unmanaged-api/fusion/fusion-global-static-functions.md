---
title: Fúze globálních statických funkcí
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged global static functions [.NET Framework], fusion
- fusion global static functions [.NET Framework]
- global static functions [.NET Framework fusion]
ms.assetid: 229b2188-9168-4b44-a987-e1f515494688
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86cb59c0935c193a9865d5ace5fe11c96226d9e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697716"
---
# <a name="fusion-global-static-functions"></a><span data-ttu-id="6790b-102">Fúze globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="6790b-102">Fusion Global Static Functions</span></span>
<span data-ttu-id="6790b-103">Tato část popisuje nespravované globální statické funkce, které používá fusion rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="6790b-103">This section describes the unmanaged global static functions that the fusion API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6790b-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6790b-104">In This Section</span></span>  
 [<span data-ttu-id="6790b-105">ClearDownloadCache – funkce</span><span class="sxs-lookup"><span data-stu-id="6790b-105">ClearDownloadCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/cleardownloadcache-function.md)  
 <span data-ttu-id="6790b-106">Vymaže globální mezipaměti sestavení stažené sestavení.</span><span class="sxs-lookup"><span data-stu-id="6790b-106">Clears the global assembly cache of downloaded assemblies.</span></span>  
  
 [<span data-ttu-id="6790b-107">CompareAssemblyIdentity – funkce</span><span class="sxs-lookup"><span data-stu-id="6790b-107">CompareAssemblyIdentity Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)  
 <span data-ttu-id="6790b-108">Porovná dvě identit sestavení pro určení, zda jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="6790b-108">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
 [<span data-ttu-id="6790b-109">CreateApplicationContext – funkce</span><span class="sxs-lookup"><span data-stu-id="6790b-109">CreateApplicationContext Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createapplicationcontext-function.md)  
 <span data-ttu-id="6790b-110">Pouze pro interní účely.</span><span class="sxs-lookup"><span data-stu-id="6790b-110">Internal only.</span></span> <span data-ttu-id="6790b-111">(Tato funkce podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.)</span><span class="sxs-lookup"><span data-stu-id="6790b-111">(This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="6790b-112">CreateAssemblyCache – funkce</span><span class="sxs-lookup"><span data-stu-id="6790b-112">CreateAssemblyCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblycache-function.md)  
 <span data-ttu-id="6790b-113">Získá ukazatel na novou [iassemblycache –](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instance, který představuje globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="6790b-113">Gets a pointer to a new [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
 [<span data-ttu-id="6790b-114">CreateAssemblyEnum – funkce</span><span class="sxs-lookup"><span data-stu-id="6790b-114">CreateAssemblyEnum Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblyenum-function.md)  
 <span data-ttu-id="6790b-115">Získá ukazatel [iassemblyenum –](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instance, která reprezentuje seznam objektů, které existují v zadaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="6790b-115">Gets a pointer to an [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instance that represents a list of objects that exist in the specified assembly.</span></span>  
  
 [<span data-ttu-id="6790b-116">CreateAssemblyNameObject – funkce</span><span class="sxs-lookup"><span data-stu-id="6790b-116">CreateAssemblyNameObject Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)  
 <span data-ttu-id="6790b-117">Získá ukazatel [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instanci, která představuje jedinečné identity sestavení se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="6790b-117">Gets a pointer to an [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
 [<span data-ttu-id="6790b-118">CreateHistoryReader – funkce</span><span class="sxs-lookup"><span data-stu-id="6790b-118">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 <span data-ttu-id="6790b-119">Vytvoří čtečku historie pro zadaný soubor.</span><span class="sxs-lookup"><span data-stu-id="6790b-119">Creates a history reader for the specified file.</span></span>  
  
 [<span data-ttu-id="6790b-120">CreateInstallReferenceEnum – funkce</span><span class="sxs-lookup"><span data-stu-id="6790b-120">CreateInstallReferenceEnum Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createinstallreferenceenum-function.md)  
 <span data-ttu-id="6790b-121">Získá ukazatel [iinstallreferenceenum –](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) instanci, která představuje seznam aplikace odkazy na zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="6790b-121">Gets a pointer to an [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
 [<span data-ttu-id="6790b-122">GetAppIdAuthority – funkce</span><span class="sxs-lookup"><span data-stu-id="6790b-122">GetAppIdAuthority Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getappidauthority-function.md)  
 <span data-ttu-id="6790b-123">Získá ukazatel [iappidauthority –](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instance, která spravuje klíče pro identity aplikací a odkazy.</span><span class="sxs-lookup"><span data-stu-id="6790b-123">Gets a pointer to an [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="6790b-124">GetAssemblyIdentityFromFile – funkce</span><span class="sxs-lookup"><span data-stu-id="6790b-124">GetAssemblyIdentityFromFile Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getassemblyidentityfromfile-function.md)  
 <span data-ttu-id="6790b-125">Získá ukazatel `IUnknown` objekt se zadaným `IID` v sestavení v cestě zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="6790b-125">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
 [<span data-ttu-id="6790b-126">GetCachePath – funkce</span><span class="sxs-lookup"><span data-stu-id="6790b-126">GetCachePath Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)  
 <span data-ttu-id="6790b-127">Získá cestu k sestavení v mezipaměti, pomocí zadané příznaky.</span><span class="sxs-lookup"><span data-stu-id="6790b-127">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
 [<span data-ttu-id="6790b-128">GetHistoryFileDirectory – funkce</span><span class="sxs-lookup"><span data-stu-id="6790b-128">GetHistoryFileDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 <span data-ttu-id="6790b-129">Načte cestu adresáře historie aplikace.</span><span class="sxs-lookup"><span data-stu-id="6790b-129">Retrieves the path of the application history directory.</span></span>  
  
 [<span data-ttu-id="6790b-130">GetIdentityAuthority – funkce</span><span class="sxs-lookup"><span data-stu-id="6790b-130">GetIdentityAuthority Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getidentityauthority-function.md)  
 <span data-ttu-id="6790b-131">Získá ukazatel [iidentityauthority –](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) instance, která spravuje klíče pro objekty kódu.</span><span class="sxs-lookup"><span data-stu-id="6790b-131">Gets a pointer to an [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
 [<span data-ttu-id="6790b-132">IsFrameworkAssembly – funkce</span><span class="sxs-lookup"><span data-stu-id="6790b-132">IsFrameworkAssembly Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/isframeworkassembly-function.md)  
 <span data-ttu-id="6790b-133">Získá hodnotu, která určuje, zda se spravuje zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="6790b-133">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
 [<span data-ttu-id="6790b-134">NukeDownloadedCache – funkce</span><span class="sxs-lookup"><span data-stu-id="6790b-134">NukeDownloadedCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)  
 <span data-ttu-id="6790b-135">Odstraní běžné mezipaměť pro stahování modulu runtime jazyka.</span><span class="sxs-lookup"><span data-stu-id="6790b-135">Deletes the common language runtime download cache.</span></span>  
  
 [<span data-ttu-id="6790b-136">PreBindAssemblyEx – funkce</span><span class="sxs-lookup"><span data-stu-id="6790b-136">PreBindAssemblyEx Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/prebindassemblyex-function.md)  
 <span data-ttu-id="6790b-137">Získá po zpracování zásad zobrazovaný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="6790b-137">Gets the post-policy display name for an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6790b-138">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="6790b-138">Related Sections</span></span>  
 [<span data-ttu-id="6790b-139">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="6790b-139">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
  
 [<span data-ttu-id="6790b-140">Výčty pro fúze</span><span class="sxs-lookup"><span data-stu-id="6790b-140">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)  
  
 [<span data-ttu-id="6790b-141">Struktury pro fúze</span><span class="sxs-lookup"><span data-stu-id="6790b-141">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
  
 [<span data-ttu-id="6790b-142">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="6790b-142">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
