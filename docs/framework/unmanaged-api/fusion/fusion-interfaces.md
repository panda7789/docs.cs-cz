---
title: Rozhraní fúze
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework fusion]
- fusion interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], fusion
ms.assetid: e2cf98b7-40c1-4f74-86c7-8a76dd9da677
ms.openlocfilehash: 81c66825e69d9526abddfe06133426a2274ad08f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108184"
---
# <a name="fusion-interfaces"></a><span data-ttu-id="37a52-102">Rozhraní fúze</span><span class="sxs-lookup"><span data-stu-id="37a52-102">Fusion Interfaces</span></span>
<span data-ttu-id="37a52-103">Tato část popisuje nespravovaná rozhraní, která rozhraní API pro syntézu používá pro přístup k vlastnostem prostředků aplikace a k vyhledání správné verze těchto prostředků pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="37a52-103">This section describes the unmanaged interfaces that the fusion API uses to access the properties of an application's resources and to locate the correct versions of those resources for the application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="37a52-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="37a52-104">In This Section</span></span>  
 [<span data-ttu-id="37a52-105">IAppIdAuthority – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37a52-105">IAppIdAuthority Interface</span></span>](iappidauthority-interface.md)  
 <span data-ttu-id="37a52-106">Poskytuje metody, které generují a porovnávají klíče pro identity a odkazy aplikací.</span><span class="sxs-lookup"><span data-stu-id="37a52-106">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="37a52-107">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37a52-107">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)  
 <span data-ttu-id="37a52-108">Poskytuje reprezentace globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="37a52-108">Provides a representation of the global assembly cache.</span></span>  
  
 [<span data-ttu-id="37a52-109">IAssemblyCacheItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37a52-109">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)  
 <span data-ttu-id="37a52-110">Představuje jedno sestavení v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="37a52-110">Represents a single assembly in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="37a52-111">IAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37a52-111">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)  
 <span data-ttu-id="37a52-112">Představuje enumerátor pro pole objektů `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="37a52-112">Represents an enumerator for an array of `IAssemblyName` objects.</span></span>  
  
 [<span data-ttu-id="37a52-113">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37a52-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)  
 <span data-ttu-id="37a52-114">Poskytuje metody pro popis a práci s jedinečnou identitou sestavení.</span><span class="sxs-lookup"><span data-stu-id="37a52-114">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
 [<span data-ttu-id="37a52-115">IDefinitionAppId – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37a52-115">IDefinitionAppId Interface</span></span>](idefinitionappid-interface.md)  
 <span data-ttu-id="37a52-116">Představuje jedinečný identifikátor kódu, který definuje aplikaci v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="37a52-116">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="37a52-117">IDefinitionIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37a52-117">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)  
 <span data-ttu-id="37a52-118">Představuje jedinečný podpis kódu, který definuje aplikaci v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="37a52-118">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="37a52-119">IEnumDefinitionIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37a52-119">IEnumDefinitionIdentity Interface</span></span>](ienumdefinitionidentity-interface.md)  
 <span data-ttu-id="37a52-120">Slouží jako enumerátor pro kolekci `IDefinitionIdentity` objektů.</span><span class="sxs-lookup"><span data-stu-id="37a52-120">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
 [<span data-ttu-id="37a52-121">IEnumIDENTITY_ATTRIBUTE – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37a52-121">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](ienumidentity-attribute-interface.md)  
 <span data-ttu-id="37a52-122">Slouží jako enumerátor pro atributy objektu kódu v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="37a52-122">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
 [<span data-ttu-id="37a52-123">IEnumReferenceIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37a52-123">IEnumReferenceIdentity Interface</span></span>](ienumreferenceidentity-interface.md)  
 <span data-ttu-id="37a52-124">Slouží jako enumerátor pro kolekci `IReferenceIdentity` objektů.</span><span class="sxs-lookup"><span data-stu-id="37a52-124">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
 [<span data-ttu-id="37a52-125">IIdentityAuthority – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37a52-125">IIdentityAuthority Interface</span></span>](iidentityauthority-interface.md)  
 <span data-ttu-id="37a52-126">Spravuje klíče identity pro objekty kódu.</span><span class="sxs-lookup"><span data-stu-id="37a52-126">Manages identity keys for code objects.</span></span>  
  
 [<span data-ttu-id="37a52-127">IInstallReferenceEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37a52-127">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)  
 <span data-ttu-id="37a52-128">Představuje enumerátor pro odkazovaná sestavení nainstalovaná v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="37a52-128">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="37a52-129">IInstallReferenceItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37a52-129">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)  
 <span data-ttu-id="37a52-130">Představuje položku nainstalovanou v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="37a52-130">Represents an item installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="37a52-131">IReferenceAppId – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37a52-131">IReferenceAppId Interface</span></span>](ireferenceappid-interface.md)  
 <span data-ttu-id="37a52-132">Představuje odkaz na jedinečný identifikátor aplikace v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="37a52-132">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
 [<span data-ttu-id="37a52-133">IReferenceIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37a52-133">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)  
 <span data-ttu-id="37a52-134">Představuje odkaz na jedinečný podpis objektu kódu.</span><span class="sxs-lookup"><span data-stu-id="37a52-134">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="37a52-135">Odkaz</span><span class="sxs-lookup"><span data-stu-id="37a52-135">Reference</span></span>  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
## <a name="related-sections"></a><span data-ttu-id="37a52-136">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="37a52-136">Related Sections</span></span>  
 [<span data-ttu-id="37a52-137">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="37a52-137">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)  
  
 [<span data-ttu-id="37a52-138">Výčty pro fúze</span><span class="sxs-lookup"><span data-stu-id="37a52-138">Fusion Enumerations</span></span>](fusion-enumerations.md)  
  
 [<span data-ttu-id="37a52-139">Struktury pro fúze</span><span class="sxs-lookup"><span data-stu-id="37a52-139">Fusion Structures</span></span>](fusion-structures.md)
