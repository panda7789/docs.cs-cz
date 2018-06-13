---
title: Rozhraní fúze
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework fusion]
- fusion interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], fusion
ms.assetid: e2cf98b7-40c1-4f74-86c7-8a76dd9da677
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec2fd3b309820f2bfb7f6091cc3db720db497408
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434890"
---
# <a name="fusion-interfaces"></a><span data-ttu-id="b6539-102">Rozhraní fúze</span><span class="sxs-lookup"><span data-stu-id="b6539-102">Fusion Interfaces</span></span>
<span data-ttu-id="b6539-103">Tato část popisuje nespravované rozhraní, která fusion rozhraní API používá pro přístup k vlastnostem prostředků aplikace a k nalezení správné verze tyto prostředky pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b6539-103">This section describes the unmanaged interfaces that the fusion API uses to access the properties of an application's resources and to locate the correct versions of those resources for the application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b6539-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b6539-104">In This Section</span></span>  
 [<span data-ttu-id="b6539-105">IAppIdAuthority – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6539-105">IAppIdAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)  
 <span data-ttu-id="b6539-106">Poskytuje metody, které generovat a porovnání klíče pro identity aplikace a odkazy.</span><span class="sxs-lookup"><span data-stu-id="b6539-106">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="b6539-107">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6539-107">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 <span data-ttu-id="b6539-108">Poskytuje reprezentaci globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="b6539-108">Provides a representation of the global assembly cache.</span></span>  
  
 [<span data-ttu-id="b6539-109">IAssemblyCacheItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6539-109">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)  
 <span data-ttu-id="b6539-110">Představuje jednoho sestavení v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="b6539-110">Represents a single assembly in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="b6539-111">IAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6539-111">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)  
 <span data-ttu-id="b6539-112">Představuje enumerátor pro pole `IAssemblyName` objekty.</span><span class="sxs-lookup"><span data-stu-id="b6539-112">Represents an enumerator for an array of `IAssemblyName` objects.</span></span>  
  
 [<span data-ttu-id="b6539-113">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6539-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 <span data-ttu-id="b6539-114">Poskytuje metody pro popisující a práci s jedinečnou identitu sestavení.</span><span class="sxs-lookup"><span data-stu-id="b6539-114">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
 [<span data-ttu-id="b6539-115">IDefinitionAppId – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6539-115">IDefinitionAppId Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md)  
 <span data-ttu-id="b6539-116">Představuje jedinečný identifikátor pro kód, který definuje aplikace v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="b6539-116">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="b6539-117">IDefinitionIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6539-117">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)  
 <span data-ttu-id="b6539-118">Představuje jedinečné podpis kód, který definuje aplikace v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="b6539-118">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="b6539-119">IEnumDefinitionIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6539-119">IEnumDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md)  
 <span data-ttu-id="b6539-120">Slouží jako enumerátoru pro kolekci `IDefinitionIdentity` objekty.</span><span class="sxs-lookup"><span data-stu-id="b6539-120">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
 [<span data-ttu-id="b6539-121">IEnumIDENTITY_ATTRIBUTE – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6539-121">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)  
 <span data-ttu-id="b6539-122">Slouží jako enumerátor pro atributy objektu kódu v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="b6539-122">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
 [<span data-ttu-id="b6539-123">IEnumReferenceIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6539-123">IEnumReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 <span data-ttu-id="b6539-124">Slouží jako enumerátor pro kolekci `IReferenceIdentity` objekty.</span><span class="sxs-lookup"><span data-stu-id="b6539-124">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
 [<span data-ttu-id="b6539-125">IIdentityAuthority – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6539-125">IIdentityAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)  
 <span data-ttu-id="b6539-126">Spravuje klíče identity pro objekty kódu.</span><span class="sxs-lookup"><span data-stu-id="b6539-126">Manages identity keys for code objects.</span></span>  
  
 [<span data-ttu-id="b6539-127">IInstallReferenceEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6539-127">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)  
 <span data-ttu-id="b6539-128">Představuje enumerátor pro odkazované sestavení nainstalované v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="b6539-128">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="b6539-129">IInstallReferenceItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6539-129">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)  
 <span data-ttu-id="b6539-130">Představuje položku nainstalované v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="b6539-130">Represents an item installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="b6539-131">IReferenceAppId – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6539-131">IReferenceAppId Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md)  
 <span data-ttu-id="b6539-132">Představuje odkaz na jedinečný identifikátor pro aplikaci v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="b6539-132">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
 [<span data-ttu-id="b6539-133">IReferenceIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6539-133">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)  
 <span data-ttu-id="b6539-134">Představuje odkaz na jedinečný podpis objekt kódu.</span><span class="sxs-lookup"><span data-stu-id="b6539-134">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b6539-135">Odkaz</span><span class="sxs-lookup"><span data-stu-id="b6539-135">Reference</span></span>  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
## <a name="related-sections"></a><span data-ttu-id="b6539-136">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="b6539-136">Related Sections</span></span>  
 [<span data-ttu-id="b6539-137">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="b6539-137">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
  
 [<span data-ttu-id="b6539-138">Výčty pro fúze</span><span class="sxs-lookup"><span data-stu-id="b6539-138">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)  
  
 [<span data-ttu-id="b6539-139">Struktury pro fúze</span><span class="sxs-lookup"><span data-stu-id="b6539-139">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
