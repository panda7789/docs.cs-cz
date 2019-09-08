---
title: IIdentityAuthority – rozhraní
ms.date: 03/30/2017
api_name:
- IIdentityAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IIdentityAuthority
helpviewer_keywords:
- IIdentityAuthority interface [.NET Framework fusion]
ms.assetid: 6277f914-51a8-49be-bec6-52d6d648527d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7421e0d0e1a1f0e1a5fbe0d0eb7d5a0ab2a48b9a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796419"
---
# <a name="iidentityauthority-interface"></a><span data-ttu-id="c2d2b-102">IIdentityAuthority – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2d2b-102">IIdentityAuthority Interface</span></span>

<span data-ttu-id="c2d2b-103">Spravuje klíče identity pro objekty kódu.</span><span class="sxs-lookup"><span data-stu-id="c2d2b-103">Manages identity keys for code objects.</span></span>

## <a name="methods"></a><span data-ttu-id="c2d2b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c2d2b-104">Methods</span></span>

|<span data-ttu-id="c2d2b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c2d2b-105">Method</span></span>|<span data-ttu-id="c2d2b-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c2d2b-106">Description</span></span>|
|------------|-----------------|
|`IIdentityAuthority::AreDefinitionsEqual`|<span data-ttu-id="c2d2b-107">Získá hodnotu, která označuje, zda jsou dvě zadané instance [IDefinitionIdentity –](idefinitionidentity-interface.md) stejné.</span><span class="sxs-lookup"><span data-stu-id="c2d2b-107">Gets a value that indicates whether the two specified [IDefinitionIdentity](idefinitionidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreReferencesEqual`|<span data-ttu-id="c2d2b-108">Získá hodnotu, která označuje, zda jsou dvě zadané instance [IReferenceIdentity –](ireferenceidentity-interface.md) stejné.</span><span class="sxs-lookup"><span data-stu-id="c2d2b-108">Gets a value that indicates whether the two specified [IReferenceIdentity](ireferenceidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="c2d2b-109">Získá hodnotu, která označuje, zda jsou dva zadané reprezentace identity definice řetězce stejné.</span><span class="sxs-lookup"><span data-stu-id="c2d2b-109">Gets a value that indicates whether the two specified string definition identity representations are equal.</span></span>|
|`IIdentityAuthority::AreTextualReferencesEqual`|<span data-ttu-id="c2d2b-110">Získá hodnotu, která označuje, zda jsou dva zadané řetězce odkazu na identitu stejné.</span><span class="sxs-lookup"><span data-stu-id="c2d2b-110">Gets a value that indicates whether the two specified string reference identity representations are equal.</span></span>|
|`IIdentityAuthority::CreateDefinition`|<span data-ttu-id="c2d2b-111">Získá ukazatel na novou `IDefinitionIdentity` instanci, která představuje objekt kódu v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="c2d2b-111">Gets a pointer to a new `IDefinitionIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::CreateReference`|<span data-ttu-id="c2d2b-112">Získá ukazatel na novou `IReferenceIdentity` instanci, která představuje objekt kódu v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="c2d2b-112">Gets a pointer to a new `IReferenceIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::DefinitionToText`|<span data-ttu-id="c2d2b-113">Načte formátovanou verzi zadaného `IDefinitionIdentity`řetězce.</span><span class="sxs-lookup"><span data-stu-id="c2d2b-113">Gets a formatted string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DefinitionToTextBuffer`|<span data-ttu-id="c2d2b-114">Vyplní zadanou vyrovnávací paměť s velkým počtem znaků zadanou `IDefinitionIdentity`verzí řetězce.</span><span class="sxs-lookup"><span data-stu-id="c2d2b-114">Fills the specified wide character buffer with a string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="c2d2b-115">Získá hodnotu, která označuje, zda zadané `IDefinitionIdentity` instance `IReferenceIdentity` a odkazují na stejný objekt kódu.</span><span class="sxs-lookup"><span data-stu-id="c2d2b-115">Gets a value that indicates whether the specified `IDefinitionIdentity` and `IReferenceIdentity` instances refer to the same code object.</span></span>|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="c2d2b-116">Získá hodnotu, která označuje, zda zadané řetězce odkazují na stejný objekt kódu.</span><span class="sxs-lookup"><span data-stu-id="c2d2b-116">Gets a value that indicates whether the specified strings refer to the same code object.</span></span>|
|`IIdentityAuthority::GenerateDefinitionKey`|<span data-ttu-id="c2d2b-117">Získá ukazatel na nově vytvořený klíč řetězce pro zadaný `IDefinitionIdentity`objekt.</span><span class="sxs-lookup"><span data-stu-id="c2d2b-117">Gets a pointer to a newly created string key for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::GenerateReferenceKey`|<span data-ttu-id="c2d2b-118">Získá ukazatel na nově vytvořený klíč řetězce pro zadaný `IReferenceIdentity`objekt.</span><span class="sxs-lookup"><span data-stu-id="c2d2b-118">Gets a pointer to a newly created string key for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::HashDefinition`|<span data-ttu-id="c2d2b-119">Načte hodnotu hash zadaného `IDefinitionIdentity`typu.</span><span class="sxs-lookup"><span data-stu-id="c2d2b-119">Gets a hash value for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::HashReference`|<span data-ttu-id="c2d2b-120">Načte hodnotu hash zadaného `IReferenceIdentity`typu.</span><span class="sxs-lookup"><span data-stu-id="c2d2b-120">Gets a hash value for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToText`|<span data-ttu-id="c2d2b-121">Načte formátovanou verzi zadaného `IReferenceIdentity`řetězce.</span><span class="sxs-lookup"><span data-stu-id="c2d2b-121">Gets a formatted string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToTextBuffer`|<span data-ttu-id="c2d2b-122">Vyplní zadanou vyrovnávací paměť s velkým počtem znaků zadanou `IReferenceIdentity`verzí řetězce.</span><span class="sxs-lookup"><span data-stu-id="c2d2b-122">Fills the specified wide character buffer with a string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::TextToDefinition`|<span data-ttu-id="c2d2b-123">Získá ukazatel rozhraní na `IDefinitionIdentity` instanci generovanou ze zadaného formátovaného řetězce.</span><span class="sxs-lookup"><span data-stu-id="c2d2b-123">Gets an interface pointer to an `IDefinitionIdentity` instance generated from the specified formatted string.</span></span>|
|`IIdentityAuthority::TextToReference`|<span data-ttu-id="c2d2b-124">Získá ukazatel rozhraní na `IReferenceIdentity` instanci generovanou ze zadaného formátovaného řetězce.</span><span class="sxs-lookup"><span data-stu-id="c2d2b-124">Gets an interface pointer to an `IReferenceIdentity` instance generated from the specified formatted string.</span></span>|

## <a name="requirements"></a><span data-ttu-id="c2d2b-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c2d2b-125">Requirements</span></span>

<span data-ttu-id="c2d2b-126">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2d2b-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="c2d2b-127">**Hlaviček** Izolace. h</span><span class="sxs-lookup"><span data-stu-id="c2d2b-127">**Header:** Isolation.h</span></span>

<span data-ttu-id="c2d2b-128">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2d2b-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c2d2b-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2d2b-129">See also</span></span>

- [<span data-ttu-id="c2d2b-130">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="c2d2b-130">Fusion Interfaces</span></span>](fusion-interfaces.md)
