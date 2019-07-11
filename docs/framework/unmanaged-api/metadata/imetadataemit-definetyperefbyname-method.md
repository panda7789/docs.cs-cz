---
title: IMetaDataEmit::DefineTypeRefByName – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeRefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f005ee9d3d9d4b8977cd6a1838fe46015e604df5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777468"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="22072-102">IMetaDataEmit::DefineTypeRefByName – metoda</span><span class="sxs-lookup"><span data-stu-id="22072-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>
<span data-ttu-id="22072-103">Získá token metadat pro typ, který je definován v zadaném rozsahu, který se nenachází v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="22072-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22072-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22072-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22072-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="22072-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="22072-106">[in] Token určující rozlišovací obor.</span><span class="sxs-lookup"><span data-stu-id="22072-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="22072-107">Platné jsou následující typy tokenů:</span><span class="sxs-lookup"><span data-stu-id="22072-107">The following token types are valid:</span></span>  
  
- <span data-ttu-id="22072-108">`mdModuleRef`, pokud je typ definován ve stejném sestavení, ve kterém je definována volající.</span><span class="sxs-lookup"><span data-stu-id="22072-108">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
- <span data-ttu-id="22072-109">`mdAssemblyRef`, pokud je typ definovaný v jiném sestavení než ten, ve kterém je definována volající.</span><span class="sxs-lookup"><span data-stu-id="22072-109">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
- <span data-ttu-id="22072-110">`mdTypeRef`, pokud je typ vnořeného typu.</span><span class="sxs-lookup"><span data-stu-id="22072-110">`mdTypeRef`, if the type is a nested type.</span></span>  
  
- <span data-ttu-id="22072-111">`mdModule`, pokud je typ definován ve stejném modulu, ve kterém je definována volající.</span><span class="sxs-lookup"><span data-stu-id="22072-111">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
- <span data-ttu-id="22072-112">Hodnota Null, pokud je typ definován globálně.</span><span class="sxs-lookup"><span data-stu-id="22072-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="22072-113">[in] Název cílového typu v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="22072-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="22072-114">[out] Ukazatel `mdTypeRef` token, který je přiřazen k typu.</span><span class="sxs-lookup"><span data-stu-id="22072-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22072-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="22072-115">Requirements</span></span>  
 <span data-ttu-id="22072-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22072-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22072-117">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="22072-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="22072-118">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="22072-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="22072-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22072-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22072-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="22072-120">See also</span></span>

- [<span data-ttu-id="22072-121">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="22072-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="22072-122">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="22072-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
