---
title: "IAppIdAuthority – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IAppIdAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAppIdAuthority
helpviewer_keywords:
- IAppIdAuthority interface [.NET Framework fusion]
ms.assetid: ec354fa1-1efd-41b0-bc43-b90597b6e253
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c51aac28864cba5f538f7829ba4112b141c9a3c8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iappidauthority-interface"></a><span data-ttu-id="70890-102">IAppIdAuthority – rozhraní</span><span class="sxs-lookup"><span data-stu-id="70890-102">IAppIdAuthority Interface</span></span>
<span data-ttu-id="70890-103">Poskytuje metody, které generovat a porovnání klíče pro identity aplikace a odkazy.</span><span class="sxs-lookup"><span data-stu-id="70890-103">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="70890-104">Metody</span><span class="sxs-lookup"><span data-stu-id="70890-104">Methods</span></span>  
  
|<span data-ttu-id="70890-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="70890-105">Method</span></span>|<span data-ttu-id="70890-106">Popis</span><span class="sxs-lookup"><span data-stu-id="70890-106">Description</span></span>|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|<span data-ttu-id="70890-107">Získá hodnotu, která určuje, zda jsou obě zadané [idefinitionappid –](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md) instance jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="70890-107">Gets a value that indicates whether the two specified [IDefinitionAppId](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md) instances are equal.</span></span> <span data-ttu-id="70890-108">Může předat hodnotu příznak IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION ignorovat své informace odpovídající verze.</span><span class="sxs-lookup"><span data-stu-id="70890-108">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreReferencesEqual`|<span data-ttu-id="70890-109">Získá hodnotu, která určuje, zda jsou obě zadané [ireferenceappid –](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md) instance jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="70890-109">Gets a value that indicates whether the two specified [IReferenceAppId](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md) instances are equal.</span></span> <span data-ttu-id="70890-110">Může předat hodnotu příznak IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION ignorovat své informace odpovídající verze.</span><span class="sxs-lookup"><span data-stu-id="70890-110">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="70890-111">Získá hodnotu, která určuje, zda jsou si rovny dvě definice zadaný řetězec.</span><span class="sxs-lookup"><span data-stu-id="70890-111">Gets a value that indicates whether the two specified string definitions are equal.</span></span> <span data-ttu-id="70890-112">Může předat hodnotu příznak IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION ignorovat své informace odpovídající verze.</span><span class="sxs-lookup"><span data-stu-id="70890-112">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualReferencesEqual`|<span data-ttu-id="70890-113">Získá hodnotu, která určuje, zda jsou dva odkazy zadaný řetězec stejné.</span><span class="sxs-lookup"><span data-stu-id="70890-113">Gets a value that indicates whether the two specified string references are equal.</span></span> <span data-ttu-id="70890-114">Může předat hodnotu příznak IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION ignorovat své informace odpovídající verze.</span><span class="sxs-lookup"><span data-stu-id="70890-114">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::CreateDefinition`|<span data-ttu-id="70890-115">Získá ukazatele rozhraní k nově vygenerovaný `IDefinitionAppId` instanci, která představuje sestavení v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="70890-115">Gets an interface pointer to a newly generated `IDefinitionAppId` instance that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::CreateReference`|<span data-ttu-id="70890-116">Získá ukazatele rozhraní pro nově vytvořený `IReferenceAppId` představující sestavení v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="70890-116">Gets an interface pointer to a newly created `IReferenceAppId` that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::DefinitionToText`|<span data-ttu-id="70890-117">Získá řetězec verze zadaného `IDefinitionAppId`, pomocí zadaný příznak hodnot.</span><span class="sxs-lookup"><span data-stu-id="70890-117">Gets a string version of the specified `IDefinitionAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="70890-118">Získá hodnotu, která určuje, zda zadaný `IDefinitionAppId` a `IReferenceAppId` představují do stejného sestavení.</span><span class="sxs-lookup"><span data-stu-id="70890-118">Gets a value that indicates whether the specified `IDefinitionAppId` and `IReferenceAppId` represent the same assembly.</span></span>|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="70890-119">Získá hodnotu, která určuje, zda jsou určená definice řetězec a odkaz na řetězec představují do stejného sestavení.</span><span class="sxs-lookup"><span data-stu-id="70890-119">Gets a value that indicates whether the specified definition string and reference string represent the same assembly.</span></span>|  
|`IAppIdAuthority::GenerateDefinitionKey`|<span data-ttu-id="70890-120">Získá řetězec klíč, který představuje zadaný `IDefinitionAppId` instance.</span><span class="sxs-lookup"><span data-stu-id="70890-120">Gets a string key that represents the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::GenerateReferenceKey`|<span data-ttu-id="70890-121">Získá řetězec klíč, který představuje zadaný `IReferenceAppId` instance.</span><span class="sxs-lookup"><span data-stu-id="70890-121">Gets a string key that represents the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::HashDefinition`|<span data-ttu-id="70890-122">Získá klíč algoritmu hash pro zadaná `IDefinitionAppId` instance.</span><span class="sxs-lookup"><span data-stu-id="70890-122">Gets a hash key for the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::HashReference`|<span data-ttu-id="70890-123">Získá klíč algoritmu hash pro zadaná `IReferenceAppId` instance.</span><span class="sxs-lookup"><span data-stu-id="70890-123">Gets a hash key for the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::ReferenceToText`|<span data-ttu-id="70890-124">Získá řetězec verze zadaného `IReferenceAppId`, pomocí zadaný příznak hodnot.</span><span class="sxs-lookup"><span data-stu-id="70890-124">Gets a string version of the specified `IReferenceAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::TextToDefinition`|<span data-ttu-id="70890-125">Získá ukazatele rozhraní k `IDefinitionAppId` instanci, která představuje sestavení odkazuje klíč zadaný řetězec.</span><span class="sxs-lookup"><span data-stu-id="70890-125">Gets an interface pointer to an `IDefinitionAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
|`IAppIdAuthority::TextToReference`|<span data-ttu-id="70890-126">Získá ukazatele rozhraní k `IReferenceAppId` instanci, která představuje sestavení odkazuje klíč zadaný řetězec.</span><span class="sxs-lookup"><span data-stu-id="70890-126">Gets an interface pointer to an `IReferenceAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="70890-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="70890-127">Requirements</span></span>  
 <span data-ttu-id="70890-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70890-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70890-129">**Záhlaví:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="70890-129">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="70890-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70890-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70890-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="70890-131">See Also</span></span>  
 [<span data-ttu-id="70890-132">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="70890-132">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
