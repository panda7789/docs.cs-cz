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
ms.openlocfilehash: 6a8f15bc862c0486311960f7567c49424859846e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795315"
---
# <a name="fusion-global-static-functions"></a><span data-ttu-id="b32ef-102">Fúze globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="b32ef-102">Fusion Global Static Functions</span></span>
<span data-ttu-id="b32ef-103">Tato část popisuje nespravované globální statické funkce, které používá rozhraní API pro syntézu.</span><span class="sxs-lookup"><span data-stu-id="b32ef-103">This section describes the unmanaged global static functions that the fusion API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b32ef-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b32ef-104">In This Section</span></span>  
 [<span data-ttu-id="b32ef-105">ClearDownloadCache – funkce</span><span class="sxs-lookup"><span data-stu-id="b32ef-105">ClearDownloadCache Function</span></span>](cleardownloadcache-function.md)  
 <span data-ttu-id="b32ef-106">Vymaže globální mezipaměť sestavení (GAC) pro stažená sestavení.</span><span class="sxs-lookup"><span data-stu-id="b32ef-106">Clears the global assembly cache of downloaded assemblies.</span></span>  
  
 [<span data-ttu-id="b32ef-107">CompareAssemblyIdentity – funkce</span><span class="sxs-lookup"><span data-stu-id="b32ef-107">CompareAssemblyIdentity Function</span></span>](compareassemblyidentity-function.md)  
 <span data-ttu-id="b32ef-108">Porovná dvě identity sestavení a určí, zda jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="b32ef-108">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
 [<span data-ttu-id="b32ef-109">CreateApplicationContext – funkce</span><span class="sxs-lookup"><span data-stu-id="b32ef-109">CreateApplicationContext Function</span></span>](createapplicationcontext-function.md)  
 <span data-ttu-id="b32ef-110">Pouze interní.</span><span class="sxs-lookup"><span data-stu-id="b32ef-110">Internal only.</span></span> <span data-ttu-id="b32ef-111">(Tato funkce podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.)</span><span class="sxs-lookup"><span data-stu-id="b32ef-111">(This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="b32ef-112">CreateAssemblyCache – funkce</span><span class="sxs-lookup"><span data-stu-id="b32ef-112">CreateAssemblyCache Function</span></span>](createassemblycache-function.md)  
 <span data-ttu-id="b32ef-113">Získá ukazatel na novou instanci [IAssemblyCache](iassemblycache-interface.md) , která představuje globální mezipaměť sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="b32ef-113">Gets a pointer to a new [IAssemblyCache](iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
 [<span data-ttu-id="b32ef-114">CreateAssemblyEnum – funkce</span><span class="sxs-lookup"><span data-stu-id="b32ef-114">CreateAssemblyEnum Function</span></span>](createassemblyenum-function.md)  
 <span data-ttu-id="b32ef-115">Získá ukazatel na instanci [IAssemblyEnum](iassemblyenum-interface.md) , která představuje seznam objektů, které existují v zadaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="b32ef-115">Gets a pointer to an [IAssemblyEnum](iassemblyenum-interface.md) instance that represents a list of objects that exist in the specified assembly.</span></span>  
  
 [<span data-ttu-id="b32ef-116">CreateAssemblyNameObject – funkce</span><span class="sxs-lookup"><span data-stu-id="b32ef-116">CreateAssemblyNameObject Function</span></span>](createassemblynameobject-function.md)  
 <span data-ttu-id="b32ef-117">Získá ukazatel na instanci [IAssemblyName](iassemblyname-interface.md) , která představuje jedinečnou identitu sestavení se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="b32ef-117">Gets a pointer to an [IAssemblyName](iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
 [<span data-ttu-id="b32ef-118">CreateHistoryReader – funkce</span><span class="sxs-lookup"><span data-stu-id="b32ef-118">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)  
 <span data-ttu-id="b32ef-119">Vytvoří čtečku historie pro zadaný soubor.</span><span class="sxs-lookup"><span data-stu-id="b32ef-119">Creates a history reader for the specified file.</span></span>  
  
 [<span data-ttu-id="b32ef-120">CreateInstallReferenceEnum – funkce</span><span class="sxs-lookup"><span data-stu-id="b32ef-120">CreateInstallReferenceEnum Function</span></span>](createinstallreferenceenum-function.md)  
 <span data-ttu-id="b32ef-121">Získá ukazatel na instanci [IInstallReferenceEnum –](iinstallreferenceenum-interface.md) , která představuje seznam odkazů aplikace na zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="b32ef-121">Gets a pointer to an [IInstallReferenceEnum](iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
 [<span data-ttu-id="b32ef-122">GetAppIdAuthority – funkce</span><span class="sxs-lookup"><span data-stu-id="b32ef-122">GetAppIdAuthority Function</span></span>](getappidauthority-function.md)  
 <span data-ttu-id="b32ef-123">Získá ukazatel na instanci [IAppIdAuthority –](iappidauthority-interface.md) , která spravuje klíče pro identity aplikace a odkazy.</span><span class="sxs-lookup"><span data-stu-id="b32ef-123">Gets a pointer to an [IAppIdAuthority](iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="b32ef-124">GetAssemblyIdentityFromFile – funkce</span><span class="sxs-lookup"><span data-stu-id="b32ef-124">GetAssemblyIdentityFromFile Function</span></span>](getassemblyidentityfromfile-function.md)  
 <span data-ttu-id="b32ef-125">Získá ukazatel na `IUnknown` objekt, který je zadaný `IID` v sestavení v zadané cestě k souboru.</span><span class="sxs-lookup"><span data-stu-id="b32ef-125">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
 [<span data-ttu-id="b32ef-126">GetCachePath – funkce</span><span class="sxs-lookup"><span data-stu-id="b32ef-126">GetCachePath Function</span></span>](getcachepath-function.md)  
 <span data-ttu-id="b32ef-127">Načte cestu k sestavení v mezipaměti pomocí zadaných příznaků.</span><span class="sxs-lookup"><span data-stu-id="b32ef-127">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
 [<span data-ttu-id="b32ef-128">GetHistoryFileDirectory – funkce</span><span class="sxs-lookup"><span data-stu-id="b32ef-128">GetHistoryFileDirectory Function</span></span>](gethistoryfiledirectory-function.md)  
 <span data-ttu-id="b32ef-129">Načte cestu k adresáři historie aplikace.</span><span class="sxs-lookup"><span data-stu-id="b32ef-129">Retrieves the path of the application history directory.</span></span>  
  
 [<span data-ttu-id="b32ef-130">GetIdentityAuthority – funkce</span><span class="sxs-lookup"><span data-stu-id="b32ef-130">GetIdentityAuthority Function</span></span>](getidentityauthority-function.md)  
 <span data-ttu-id="b32ef-131">Získá ukazatel na instanci [IIdentityAuthority –](iidentityauthority-interface.md) , která spravuje klíče pro objekty kódu.</span><span class="sxs-lookup"><span data-stu-id="b32ef-131">Gets a pointer to an [IIdentityAuthority](iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
 [<span data-ttu-id="b32ef-132">IsFrameworkAssembly – funkce</span><span class="sxs-lookup"><span data-stu-id="b32ef-132">IsFrameworkAssembly Function</span></span>](isframeworkassembly-function.md)  
 <span data-ttu-id="b32ef-133">Získá hodnotu, která označuje, zda je zadané sestavení spravováno.</span><span class="sxs-lookup"><span data-stu-id="b32ef-133">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
 [<span data-ttu-id="b32ef-134">NukeDownloadedCache – funkce</span><span class="sxs-lookup"><span data-stu-id="b32ef-134">NukeDownloadedCache Function</span></span>](nukedownloadedcache-function.md)  
 <span data-ttu-id="b32ef-135">Odstraní mezipaměť pro stažení modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="b32ef-135">Deletes the common language runtime download cache.</span></span>  
  
 [<span data-ttu-id="b32ef-136">PreBindAssemblyEx – funkce</span><span class="sxs-lookup"><span data-stu-id="b32ef-136">PreBindAssemblyEx Function</span></span>](prebindassemblyex-function.md)  
 <span data-ttu-id="b32ef-137">Načte zobrazovaný název po zásadě pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="b32ef-137">Gets the post-policy display name for an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b32ef-138">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="b32ef-138">Related Sections</span></span>  
 [<span data-ttu-id="b32ef-139">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="b32ef-139">Fusion Interfaces</span></span>](fusion-interfaces.md)  
  
 [<span data-ttu-id="b32ef-140">Výčty pro fúze</span><span class="sxs-lookup"><span data-stu-id="b32ef-140">Fusion Enumerations</span></span>](fusion-enumerations.md)  
  
 [<span data-ttu-id="b32ef-141">Struktury pro fúze</span><span class="sxs-lookup"><span data-stu-id="b32ef-141">Fusion Structures</span></span>](fusion-structures.md)  
  
 [<span data-ttu-id="b32ef-142">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="b32ef-142">Global Assembly Cache</span></span>](../../app-domains/gac.md)
