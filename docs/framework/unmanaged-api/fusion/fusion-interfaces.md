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
ms.openlocfilehash: 1605605f8510f7ccf5f0bbf2f3f6b09050a16025
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795299"
---
# <a name="fusion-interfaces"></a><span data-ttu-id="0a204-102">Rozhraní fúze</span><span class="sxs-lookup"><span data-stu-id="0a204-102">Fusion Interfaces</span></span>
<span data-ttu-id="0a204-103">Tato část popisuje nespravovaná rozhraní, která rozhraní API pro syntézu používá pro přístup k vlastnostem prostředků aplikace a k vyhledání správné verze těchto prostředků pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0a204-103">This section describes the unmanaged interfaces that the fusion API uses to access the properties of an application's resources and to locate the correct versions of those resources for the application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0a204-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0a204-104">In This Section</span></span>  
 [<span data-ttu-id="0a204-105">IAppIdAuthority – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a204-105">IAppIdAuthority Interface</span></span>](iappidauthority-interface.md)  
 <span data-ttu-id="0a204-106">Poskytuje metody, které generují a porovnávají klíče pro identity a odkazy aplikací.</span><span class="sxs-lookup"><span data-stu-id="0a204-106">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="0a204-107">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a204-107">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)  
 <span data-ttu-id="0a204-108">Poskytuje reprezentace globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="0a204-108">Provides a representation of the global assembly cache.</span></span>  
  
 [<span data-ttu-id="0a204-109">IAssemblyCacheItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a204-109">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)  
 <span data-ttu-id="0a204-110">Představuje jedno sestavení v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="0a204-110">Represents a single assembly in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="0a204-111">IAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a204-111">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)  
 <span data-ttu-id="0a204-112">Představuje enumerátor pro pole `IAssemblyName` objektů.</span><span class="sxs-lookup"><span data-stu-id="0a204-112">Represents an enumerator for an array of `IAssemblyName` objects.</span></span>  
  
 [<span data-ttu-id="0a204-113">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a204-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)  
 <span data-ttu-id="0a204-114">Poskytuje metody pro popis a práci s jedinečnou identitou sestavení.</span><span class="sxs-lookup"><span data-stu-id="0a204-114">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
 [<span data-ttu-id="0a204-115">IDefinitionAppId – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a204-115">IDefinitionAppId Interface</span></span>](idefinitionappid-interface.md)  
 <span data-ttu-id="0a204-116">Představuje jedinečný identifikátor kódu, který definuje aplikaci v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="0a204-116">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="0a204-117">IDefinitionIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a204-117">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)  
 <span data-ttu-id="0a204-118">Představuje jedinečný podpis kódu, který definuje aplikaci v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="0a204-118">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="0a204-119">IEnumDefinitionIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a204-119">IEnumDefinitionIdentity Interface</span></span>](ienumdefinitionidentity-interface.md)  
 <span data-ttu-id="0a204-120">Slouží jako enumerátor pro kolekci `IDefinitionIdentity` objektů.</span><span class="sxs-lookup"><span data-stu-id="0a204-120">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
 [<span data-ttu-id="0a204-121">IEnumIDENTITY_ATTRIBUTE – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a204-121">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](ienumidentity-attribute-interface.md)  
 <span data-ttu-id="0a204-122">Slouží jako enumerátor pro atributy objektu kódu v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="0a204-122">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
 [<span data-ttu-id="0a204-123">IEnumReferenceIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a204-123">IEnumReferenceIdentity Interface</span></span>](ienumreferenceidentity-interface.md)  
 <span data-ttu-id="0a204-124">Slouží jako enumerátor pro kolekci `IReferenceIdentity` objektů.</span><span class="sxs-lookup"><span data-stu-id="0a204-124">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
 [<span data-ttu-id="0a204-125">IIdentityAuthority – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a204-125">IIdentityAuthority Interface</span></span>](iidentityauthority-interface.md)  
 <span data-ttu-id="0a204-126">Spravuje klíče identity pro objekty kódu.</span><span class="sxs-lookup"><span data-stu-id="0a204-126">Manages identity keys for code objects.</span></span>  
  
 [<span data-ttu-id="0a204-127">IInstallReferenceEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a204-127">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)  
 <span data-ttu-id="0a204-128">Představuje enumerátor pro odkazovaná sestavení nainstalovaná v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="0a204-128">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="0a204-129">IInstallReferenceItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a204-129">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)  
 <span data-ttu-id="0a204-130">Představuje položku nainstalovanou v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="0a204-130">Represents an item installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="0a204-131">IReferenceAppId – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a204-131">IReferenceAppId Interface</span></span>](ireferenceappid-interface.md)  
 <span data-ttu-id="0a204-132">Představuje odkaz na jedinečný identifikátor aplikace v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="0a204-132">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
 [<span data-ttu-id="0a204-133">IReferenceIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a204-133">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)  
 <span data-ttu-id="0a204-134">Představuje odkaz na jedinečný podpis objektu kódu.</span><span class="sxs-lookup"><span data-stu-id="0a204-134">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0a204-135">Reference</span><span class="sxs-lookup"><span data-stu-id="0a204-135">Reference</span></span>  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
## <a name="related-sections"></a><span data-ttu-id="0a204-136">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="0a204-136">Related Sections</span></span>  
 [<span data-ttu-id="0a204-137">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="0a204-137">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)  
  
 [<span data-ttu-id="0a204-138">Výčty pro fúze</span><span class="sxs-lookup"><span data-stu-id="0a204-138">Fusion Enumerations</span></span>](fusion-enumerations.md)  
  
 [<span data-ttu-id="0a204-139">Struktury pro fúze</span><span class="sxs-lookup"><span data-stu-id="0a204-139">Fusion Structures</span></span>](fusion-structures.md)
