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
ms.openlocfilehash: 263dc0f9d686440aaa23e359c26db1b4d3d09b1e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375962"
---
# <a name="iidentityauthority-interface"></a><span data-ttu-id="61442-102">IIdentityAuthority – rozhraní</span><span class="sxs-lookup"><span data-stu-id="61442-102">IIdentityAuthority Interface</span></span>

<span data-ttu-id="61442-103">Spravuje klíče identity pro objekty kódu.</span><span class="sxs-lookup"><span data-stu-id="61442-103">Manages identity keys for code objects.</span></span>

## <a name="methods"></a><span data-ttu-id="61442-104">Metody</span><span class="sxs-lookup"><span data-stu-id="61442-104">Methods</span></span>

|<span data-ttu-id="61442-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="61442-105">Method</span></span>|<span data-ttu-id="61442-106">Popis</span><span class="sxs-lookup"><span data-stu-id="61442-106">Description</span></span>|
|------------|-----------------|
|`IIdentityAuthority::AreDefinitionsEqual`|<span data-ttu-id="61442-107">Získá hodnotu, která udává, zda dvě zadat [idefinitionidentity –](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instancí jsou si rovny.</span><span class="sxs-lookup"><span data-stu-id="61442-107">Gets a value that indicates whether the two specified [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreReferencesEqual`|<span data-ttu-id="61442-108">Získá hodnotu, která udává, zda dvě zadat [ireferenceidentity –](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) instancí jsou si rovny.</span><span class="sxs-lookup"><span data-stu-id="61442-108">Gets a value that indicates whether the two specified [IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="61442-109">Získá hodnotu určující, zda jsou dvě zadané řetězcové vyjádření identity definice stejné.</span><span class="sxs-lookup"><span data-stu-id="61442-109">Gets a value that indicates whether the two specified string definition identity representations are equal.</span></span>|
|`IIdentityAuthority::AreTextualReferencesEqual`|<span data-ttu-id="61442-110">Získá hodnotu, která určuje, zda dvě zadané řetězcové vyjádření identity odkazu jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="61442-110">Gets a value that indicates whether the two specified string reference identity representations are equal.</span></span>|
|`IIdentityAuthority::CreateDefinition`|<span data-ttu-id="61442-111">Získá ukazatel na novou `IDefinitionIdentity` instanci, která představuje objekt kódu v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="61442-111">Gets a pointer to a new `IDefinitionIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::CreateReference`|<span data-ttu-id="61442-112">Získá ukazatel na novou `IReferenceIdentity` instanci, která představuje objekt kódu v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="61442-112">Gets a pointer to a new `IReferenceIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::DefinitionToText`|<span data-ttu-id="61442-113">Získá verzi formátovaný řetězec zadaného `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="61442-113">Gets a formatted string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DefinitionToTextBuffer`|<span data-ttu-id="61442-114">Vyplní vyrovnávací paměti zadaná široký znak s verzí řetězce zadaného `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="61442-114">Fills the specified wide character buffer with a string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="61442-115">Získá hodnotu určující, zda zadaný `IDefinitionIdentity` a `IReferenceIdentity` instance odkazují na stejný objekt kódu.</span><span class="sxs-lookup"><span data-stu-id="61442-115">Gets a value that indicates whether the specified `IDefinitionIdentity` and `IReferenceIdentity` instances refer to the same code object.</span></span>|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="61442-116">Získá hodnotu určující, zda jsou zadané řetězce odkazují na stejný objekt kódu.</span><span class="sxs-lookup"><span data-stu-id="61442-116">Gets a value that indicates whether the specified strings refer to the same code object.</span></span>|
|`IIdentityAuthority::GenerateDefinitionKey`|<span data-ttu-id="61442-117">Získá ukazatel na nově vytvořený řetězec klíče pro zadaný rozbočovač `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="61442-117">Gets a pointer to a newly created string key for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::GenerateReferenceKey`|<span data-ttu-id="61442-118">Získá ukazatel na nově vytvořený řetězec klíče pro zadaný rozbočovač `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="61442-118">Gets a pointer to a newly created string key for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::HashDefinition`|<span data-ttu-id="61442-119">Získá hodnotu hash pro zadaná `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="61442-119">Gets a hash value for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::HashReference`|<span data-ttu-id="61442-120">Získá hodnotu hash pro zadaná `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="61442-120">Gets a hash value for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToText`|<span data-ttu-id="61442-121">Získá verzi formátovaný řetězec zadaného `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="61442-121">Gets a formatted string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToTextBuffer`|<span data-ttu-id="61442-122">Vyplní vyrovnávací paměti zadaná široký znak s verzí řetězce zadaného `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="61442-122">Fills the specified wide character buffer with a string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::TextToDefinition`|<span data-ttu-id="61442-123">Získá ukazatel rozhraní k `IDefinitionIdentity` instance generované ze zadané ve formátu řetězce.</span><span class="sxs-lookup"><span data-stu-id="61442-123">Gets an interface pointer to an `IDefinitionIdentity` instance generated from the specified formatted string.</span></span>|
|`IIdentityAuthority::TextToReference`|<span data-ttu-id="61442-124">Získá ukazatel rozhraní k `IReferenceIdentity` instance generované ze zadané ve formátu řetězce.</span><span class="sxs-lookup"><span data-stu-id="61442-124">Gets an interface pointer to an `IReferenceIdentity` instance generated from the specified formatted string.</span></span>|

## <a name="requirements"></a><span data-ttu-id="61442-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="61442-125">Requirements</span></span>

<span data-ttu-id="61442-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61442-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="61442-127">**Záhlaví:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="61442-127">**Header:** Isolation.h</span></span>

<span data-ttu-id="61442-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61442-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="61442-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="61442-129">See also</span></span>

- [<span data-ttu-id="61442-130">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="61442-130">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
