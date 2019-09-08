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
ms.openlocfilehash: 91ab2f71e7fb74f8e0e517b566d46d61c316ebe2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796835"
---
# <a name="iappidauthority-interface"></a><span data-ttu-id="17467-102">IAppIdAuthority – rozhraní</span><span class="sxs-lookup"><span data-stu-id="17467-102">IAppIdAuthority Interface</span></span>
<span data-ttu-id="17467-103">Poskytuje metody, které generují a porovnávají klíče pro identity a odkazy aplikací.</span><span class="sxs-lookup"><span data-stu-id="17467-103">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="17467-104">Metody</span><span class="sxs-lookup"><span data-stu-id="17467-104">Methods</span></span>  
  
|<span data-ttu-id="17467-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="17467-105">Method</span></span>|<span data-ttu-id="17467-106">Popis</span><span class="sxs-lookup"><span data-stu-id="17467-106">Description</span></span>|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|<span data-ttu-id="17467-107">Získá hodnotu, která označuje, zda jsou dvě zadané instance [IDefinitionAppId –](idefinitionappid-interface.md) stejné.</span><span class="sxs-lookup"><span data-stu-id="17467-107">Gets a value that indicates whether the two specified [IDefinitionAppId](idefinitionappid-interface.md) instances are equal.</span></span> <span data-ttu-id="17467-108">Můžete předat hodnotu příznaku IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION, která ignoruje jejich příslušné informace o verzi.</span><span class="sxs-lookup"><span data-stu-id="17467-108">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreReferencesEqual`|<span data-ttu-id="17467-109">Získá hodnotu, která označuje, zda jsou dvě zadané instance [IReferenceAppId –](ireferenceappid-interface.md) stejné.</span><span class="sxs-lookup"><span data-stu-id="17467-109">Gets a value that indicates whether the two specified [IReferenceAppId](ireferenceappid-interface.md) instances are equal.</span></span> <span data-ttu-id="17467-110">Můžete předat hodnotu příznaku IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION, která ignoruje jejich příslušné informace o verzi.</span><span class="sxs-lookup"><span data-stu-id="17467-110">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="17467-111">Získá hodnotu, která označuje, zda jsou dvě zadané definice řetězce stejné.</span><span class="sxs-lookup"><span data-stu-id="17467-111">Gets a value that indicates whether the two specified string definitions are equal.</span></span> <span data-ttu-id="17467-112">Můžete předat hodnotu příznaku IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION, která ignoruje jejich příslušné informace o verzi.</span><span class="sxs-lookup"><span data-stu-id="17467-112">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualReferencesEqual`|<span data-ttu-id="17467-113">Získá hodnotu, která označuje, zda jsou dva zadané odkazy na řetězce stejné.</span><span class="sxs-lookup"><span data-stu-id="17467-113">Gets a value that indicates whether the two specified string references are equal.</span></span> <span data-ttu-id="17467-114">Můžete předat hodnotu příznaku IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION, která ignoruje jejich příslušné informace o verzi.</span><span class="sxs-lookup"><span data-stu-id="17467-114">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::CreateDefinition`|<span data-ttu-id="17467-115">Získá ukazatel rozhraní na nově vygenerovanou `IDefinitionAppId` instanci, která představuje sestavení v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="17467-115">Gets an interface pointer to a newly generated `IDefinitionAppId` instance that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::CreateReference`|<span data-ttu-id="17467-116">Získá ukazatel rozhraní na nově vytvořenou `IReferenceAppId` , která představuje sestavení v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="17467-116">Gets an interface pointer to a newly created `IReferenceAppId` that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::DefinitionToText`|<span data-ttu-id="17467-117">Načte verzi řetězce zadaného `IDefinitionAppId`pomocí zadaných hodnot příznaku.</span><span class="sxs-lookup"><span data-stu-id="17467-117">Gets a string version of the specified `IDefinitionAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="17467-118">Získá hodnotu, která označuje, zda zadané `IDefinitionAppId` a `IReferenceAppId` představující stejné sestavení.</span><span class="sxs-lookup"><span data-stu-id="17467-118">Gets a value that indicates whether the specified `IDefinitionAppId` and `IReferenceAppId` represent the same assembly.</span></span>|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="17467-119">Načte hodnotu, která označuje, jestli zadaný řetězec definice a referenční řetězec představuje stejné sestavení.</span><span class="sxs-lookup"><span data-stu-id="17467-119">Gets a value that indicates whether the specified definition string and reference string represent the same assembly.</span></span>|  
|`IAppIdAuthority::GenerateDefinitionKey`|<span data-ttu-id="17467-120">Získá klíč řetězce, který představuje zadanou `IDefinitionAppId` instanci.</span><span class="sxs-lookup"><span data-stu-id="17467-120">Gets a string key that represents the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::GenerateReferenceKey`|<span data-ttu-id="17467-121">Získá klíč řetězce, který představuje zadanou `IReferenceAppId` instanci.</span><span class="sxs-lookup"><span data-stu-id="17467-121">Gets a string key that represents the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::HashDefinition`|<span data-ttu-id="17467-122">Získá klíč hash pro zadanou `IDefinitionAppId` instanci.</span><span class="sxs-lookup"><span data-stu-id="17467-122">Gets a hash key for the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::HashReference`|<span data-ttu-id="17467-123">Získá klíč hash pro zadanou `IReferenceAppId` instanci.</span><span class="sxs-lookup"><span data-stu-id="17467-123">Gets a hash key for the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::ReferenceToText`|<span data-ttu-id="17467-124">Načte verzi řetězce zadaného `IReferenceAppId`pomocí zadaných hodnot příznaku.</span><span class="sxs-lookup"><span data-stu-id="17467-124">Gets a string version of the specified `IReferenceAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::TextToDefinition`|<span data-ttu-id="17467-125">Získá ukazatel rozhraní na `IDefinitionAppId` instanci, která představuje sestavení odkazované zadaným řetězcovým klíčem.</span><span class="sxs-lookup"><span data-stu-id="17467-125">Gets an interface pointer to an `IDefinitionAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
|`IAppIdAuthority::TextToReference`|<span data-ttu-id="17467-126">Získá ukazatel rozhraní na `IReferenceAppId` instanci, která představuje sestavení odkazované zadaným řetězcovým klíčem.</span><span class="sxs-lookup"><span data-stu-id="17467-126">Gets an interface pointer to an `IReferenceAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="17467-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="17467-127">Requirements</span></span>  
 <span data-ttu-id="17467-128">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17467-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17467-129">**Hlaviček** Izolace. h</span><span class="sxs-lookup"><span data-stu-id="17467-129">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="17467-130">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17467-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17467-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="17467-131">See also</span></span>

- [<span data-ttu-id="17467-132">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="17467-132">Fusion Interfaces</span></span>](fusion-interfaces.md)
