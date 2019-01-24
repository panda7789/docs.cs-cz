---
title: IAppIdAuthority – rozhraní
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c803169f87c4033d7e231e8b0243f502b9246f70
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54493921"
---
# <a name="iappidauthority-interface"></a><span data-ttu-id="a19c8-102">IAppIdAuthority – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a19c8-102">IAppIdAuthority Interface</span></span>
<span data-ttu-id="a19c8-103">Poskytuje metody, která generují a porovnat klíče pro identity aplikací a odkazy.</span><span class="sxs-lookup"><span data-stu-id="a19c8-103">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a19c8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a19c8-104">Methods</span></span>  
  
|<span data-ttu-id="a19c8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a19c8-105">Method</span></span>|<span data-ttu-id="a19c8-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a19c8-106">Description</span></span>|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|<span data-ttu-id="a19c8-107">Získá hodnotu, která udává, zda dvě zadat [idefinitionappid –](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md) instancí jsou si rovny.</span><span class="sxs-lookup"><span data-stu-id="a19c8-107">Gets a value that indicates whether the two specified [IDefinitionAppId](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md) instances are equal.</span></span> <span data-ttu-id="a19c8-108">Můžete předat hodnotu příznaku IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION ignorovat informace o jejich příslušné verzi.</span><span class="sxs-lookup"><span data-stu-id="a19c8-108">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreReferencesEqual`|<span data-ttu-id="a19c8-109">Získá hodnotu, která udává, zda dvě zadat [ireferenceappid –](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md) instancí jsou si rovny.</span><span class="sxs-lookup"><span data-stu-id="a19c8-109">Gets a value that indicates whether the two specified [IReferenceAppId](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md) instances are equal.</span></span> <span data-ttu-id="a19c8-110">Můžete předat hodnotu příznaku IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION ignorovat informace o jejich příslušné verzi.</span><span class="sxs-lookup"><span data-stu-id="a19c8-110">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="a19c8-111">Získá hodnotu určující, zda dvě definice zadaného řetězce jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="a19c8-111">Gets a value that indicates whether the two specified string definitions are equal.</span></span> <span data-ttu-id="a19c8-112">Můžete předat hodnotu příznaku IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION ignorovat informace o jejich příslušné verzi.</span><span class="sxs-lookup"><span data-stu-id="a19c8-112">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualReferencesEqual`|<span data-ttu-id="a19c8-113">Získá hodnotu určující, zda jsou dva odkazy zadaného řetězce rovny.</span><span class="sxs-lookup"><span data-stu-id="a19c8-113">Gets a value that indicates whether the two specified string references are equal.</span></span> <span data-ttu-id="a19c8-114">Můžete předat hodnotu příznaku IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION ignorovat informace o jejich příslušné verzi.</span><span class="sxs-lookup"><span data-stu-id="a19c8-114">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::CreateDefinition`|<span data-ttu-id="a19c8-115">Získá ukazatel rozhraní k nově vygenerovaný `IDefinitionAppId` instanci, která představuje sestavení v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="a19c8-115">Gets an interface pointer to a newly generated `IDefinitionAppId` instance that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::CreateReference`|<span data-ttu-id="a19c8-116">Získá ukazatel rozhraní na nově vytvořený `IReferenceAppId` , která představuje sestavení v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="a19c8-116">Gets an interface pointer to a newly created `IReferenceAppId` that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::DefinitionToText`|<span data-ttu-id="a19c8-117">Získá řetězec verzi zadaného `IDefinitionAppId`, pomocí hodnot pro zadaný příznak.</span><span class="sxs-lookup"><span data-stu-id="a19c8-117">Gets a string version of the specified `IDefinitionAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="a19c8-118">Získá hodnotu určující, zda zadaný `IDefinitionAppId` a `IReferenceAppId` představují stejné sestavení.</span><span class="sxs-lookup"><span data-stu-id="a19c8-118">Gets a value that indicates whether the specified `IDefinitionAppId` and `IReferenceAppId` represent the same assembly.</span></span>|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="a19c8-119">Získá hodnotu určující, zda řetězec zadané definice a odkaz na řetězec představují stejné sestavení.</span><span class="sxs-lookup"><span data-stu-id="a19c8-119">Gets a value that indicates whether the specified definition string and reference string represent the same assembly.</span></span>|  
|`IAppIdAuthority::GenerateDefinitionKey`|<span data-ttu-id="a19c8-120">Získá řetězec klíče, který představuje zadaný `IDefinitionAppId` instance.</span><span class="sxs-lookup"><span data-stu-id="a19c8-120">Gets a string key that represents the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::GenerateReferenceKey`|<span data-ttu-id="a19c8-121">Získá řetězec klíče, který představuje zadaný `IReferenceAppId` instance.</span><span class="sxs-lookup"><span data-stu-id="a19c8-121">Gets a string key that represents the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::HashDefinition`|<span data-ttu-id="a19c8-122">Získá hodnotu hash klíče pro zadaný `IDefinitionAppId` instance.</span><span class="sxs-lookup"><span data-stu-id="a19c8-122">Gets a hash key for the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::HashReference`|<span data-ttu-id="a19c8-123">Získá hodnotu hash klíče pro zadaný `IReferenceAppId` instance.</span><span class="sxs-lookup"><span data-stu-id="a19c8-123">Gets a hash key for the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::ReferenceToText`|<span data-ttu-id="a19c8-124">Získá řetězec verzi zadaného `IReferenceAppId`, pomocí hodnot pro zadaný příznak.</span><span class="sxs-lookup"><span data-stu-id="a19c8-124">Gets a string version of the specified `IReferenceAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::TextToDefinition`|<span data-ttu-id="a19c8-125">Získá ukazatel rozhraní k `IDefinitionAppId` instanci, která představuje sestavení odkazováno klíčem zadaného řetězce.</span><span class="sxs-lookup"><span data-stu-id="a19c8-125">Gets an interface pointer to an `IDefinitionAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
|`IAppIdAuthority::TextToReference`|<span data-ttu-id="a19c8-126">Získá ukazatel rozhraní k `IReferenceAppId` instanci, která představuje sestavení odkazováno klíčem zadaného řetězce.</span><span class="sxs-lookup"><span data-stu-id="a19c8-126">Gets an interface pointer to an `IReferenceAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a19c8-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a19c8-127">Requirements</span></span>  
 <span data-ttu-id="a19c8-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a19c8-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a19c8-129">**Záhlaví:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="a19c8-129">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="a19c8-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a19c8-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a19c8-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a19c8-131">See also</span></span>
- [<span data-ttu-id="a19c8-132">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="a19c8-132">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
