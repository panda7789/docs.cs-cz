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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435900"
---
# <a name="fusion-global-static-functions"></a><span data-ttu-id="c18ad-102">Fúze globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="c18ad-102">Fusion Global Static Functions</span></span>
<span data-ttu-id="c18ad-103">Tato část popisuje nespravované globální statické funkce, které používá fusion rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="c18ad-103">This section describes the unmanaged global static functions that the fusion API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c18ad-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c18ad-104">In This Section</span></span>  
 [<span data-ttu-id="c18ad-105">ClearDownloadCache – funkce</span><span class="sxs-lookup"><span data-stu-id="c18ad-105">ClearDownloadCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/cleardownloadcache-function.md)  
 <span data-ttu-id="c18ad-106">Vymaže globální mezipaměti sestavení stažené sestavení.</span><span class="sxs-lookup"><span data-stu-id="c18ad-106">Clears the global assembly cache of downloaded assemblies.</span></span>  
  
 [<span data-ttu-id="c18ad-107">CompareAssemblyIdentity – funkce</span><span class="sxs-lookup"><span data-stu-id="c18ad-107">CompareAssemblyIdentity Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)  
 <span data-ttu-id="c18ad-108">Porovná dvě sestavení identity zjistěte, zda jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="c18ad-108">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
 [<span data-ttu-id="c18ad-109">CreateApplicationContext – funkce</span><span class="sxs-lookup"><span data-stu-id="c18ad-109">CreateApplicationContext Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createapplicationcontext-function.md)  
 <span data-ttu-id="c18ad-110">Pouze interní.</span><span class="sxs-lookup"><span data-stu-id="c18ad-110">Internal only.</span></span> <span data-ttu-id="c18ad-111">(Tato funkce podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo z vašeho kódu.)</span><span class="sxs-lookup"><span data-stu-id="c18ad-111">(This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="c18ad-112">CreateAssemblyCache – funkce</span><span class="sxs-lookup"><span data-stu-id="c18ad-112">CreateAssemblyCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblycache-function.md)  
 <span data-ttu-id="c18ad-113">Získá ukazatel na nový [iassemblycache –](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instanci, která představuje globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="c18ad-113">Gets a pointer to a new [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
 [<span data-ttu-id="c18ad-114">CreateAssemblyEnum – funkce</span><span class="sxs-lookup"><span data-stu-id="c18ad-114">CreateAssemblyEnum Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblyenum-function.md)  
 <span data-ttu-id="c18ad-115">Získá odkazy [iassemblyenum –](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instance, která reprezentuje seznam objektů, které existují v zadaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="c18ad-115">Gets a pointer to an [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instance that represents a list of objects that exist in the specified assembly.</span></span>  
  
 [<span data-ttu-id="c18ad-116">CreateAssemblyNameObject – funkce</span><span class="sxs-lookup"><span data-stu-id="c18ad-116">CreateAssemblyNameObject Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)  
 <span data-ttu-id="c18ad-117">Získá odkazy [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instanci, která představuje jedinečné identity sestavení se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="c18ad-117">Gets a pointer to an [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
 [<span data-ttu-id="c18ad-118">CreateHistoryReader – funkce</span><span class="sxs-lookup"><span data-stu-id="c18ad-118">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 <span data-ttu-id="c18ad-119">Vytvoří historie čtečky zadaný soubor.</span><span class="sxs-lookup"><span data-stu-id="c18ad-119">Creates a history reader for the specified file.</span></span>  
  
 [<span data-ttu-id="c18ad-120">CreateInstallReferenceEnum – funkce</span><span class="sxs-lookup"><span data-stu-id="c18ad-120">CreateInstallReferenceEnum Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createinstallreferenceenum-function.md)  
 <span data-ttu-id="c18ad-121">Získá odkazy [iinstallreferenceenum –](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) instanci, která představuje seznam odkazů aplikace na zadaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="c18ad-121">Gets a pointer to an [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
 [<span data-ttu-id="c18ad-122">GetAppIdAuthority – funkce</span><span class="sxs-lookup"><span data-stu-id="c18ad-122">GetAppIdAuthority Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getappidauthority-function.md)  
 <span data-ttu-id="c18ad-123">Získá odkazy [iappidauthority –](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instanci, která spravuje klíče pro identity aplikace a odkazy.</span><span class="sxs-lookup"><span data-stu-id="c18ad-123">Gets a pointer to an [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="c18ad-124">GetAssemblyIdentityFromFile – funkce</span><span class="sxs-lookup"><span data-stu-id="c18ad-124">GetAssemblyIdentityFromFile Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getassemblyidentityfromfile-function.md)  
 <span data-ttu-id="c18ad-125">Získá odkazy `IUnknown` objekt se zadaným `IID` v sestavení v zadaná cesta k souboru.</span><span class="sxs-lookup"><span data-stu-id="c18ad-125">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
 [<span data-ttu-id="c18ad-126">GetCachePath – funkce</span><span class="sxs-lookup"><span data-stu-id="c18ad-126">GetCachePath Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)  
 <span data-ttu-id="c18ad-127">Získá cestu k sestavení v mezipaměti, pomocí zadané příznaky.</span><span class="sxs-lookup"><span data-stu-id="c18ad-127">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
 [<span data-ttu-id="c18ad-128">GetHistoryFileDirectory – funkce</span><span class="sxs-lookup"><span data-stu-id="c18ad-128">GetHistoryFileDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 <span data-ttu-id="c18ad-129">Načte cestu adresáře historie aplikace.</span><span class="sxs-lookup"><span data-stu-id="c18ad-129">Retrieves the path of the application history directory.</span></span>  
  
 [<span data-ttu-id="c18ad-130">GetIdentityAuthority – funkce</span><span class="sxs-lookup"><span data-stu-id="c18ad-130">GetIdentityAuthority Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getidentityauthority-function.md)  
 <span data-ttu-id="c18ad-131">Získá odkazy [iidentityauthority –](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) instanci, která spravuje klíče pro objekty kódu.</span><span class="sxs-lookup"><span data-stu-id="c18ad-131">Gets a pointer to an [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
 [<span data-ttu-id="c18ad-132">IsFrameworkAssembly – funkce</span><span class="sxs-lookup"><span data-stu-id="c18ad-132">IsFrameworkAssembly Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/isframeworkassembly-function.md)  
 <span data-ttu-id="c18ad-133">Získá hodnotu, která určuje, jestli je zadané sestavení spravovaný.</span><span class="sxs-lookup"><span data-stu-id="c18ad-133">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
 [<span data-ttu-id="c18ad-134">NukeDownloadedCache – funkce</span><span class="sxs-lookup"><span data-stu-id="c18ad-134">NukeDownloadedCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)  
 <span data-ttu-id="c18ad-135">Odstraní běžné mezipaměti stažení runtime jazyka.</span><span class="sxs-lookup"><span data-stu-id="c18ad-135">Deletes the common language runtime download cache.</span></span>  
  
 [<span data-ttu-id="c18ad-136">PreBindAssemblyEx – funkce</span><span class="sxs-lookup"><span data-stu-id="c18ad-136">PreBindAssemblyEx Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/prebindassemblyex-function.md)  
 <span data-ttu-id="c18ad-137">Získá po zásady zobrazovaný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="c18ad-137">Gets the post-policy display name for an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c18ad-138">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="c18ad-138">Related Sections</span></span>  
 [<span data-ttu-id="c18ad-139">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="c18ad-139">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
  
 [<span data-ttu-id="c18ad-140">Výčty pro fúze</span><span class="sxs-lookup"><span data-stu-id="c18ad-140">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)  
  
 [<span data-ttu-id="c18ad-141">Struktury pro fúze</span><span class="sxs-lookup"><span data-stu-id="c18ad-141">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
  
 [<span data-ttu-id="c18ad-142">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="c18ad-142">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
