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
ms.openlocfilehash: ae30140e69926be32570960a32524a74b850bda4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009350"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="f8e2e-102">IMetaDataEmit::DefineTypeRefByName – metoda</span><span class="sxs-lookup"><span data-stu-id="f8e2e-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>
<span data-ttu-id="f8e2e-103">Získá token metadat pro typ, který je definován v zadaném oboru, který je mimo aktuální obor.</span><span class="sxs-lookup"><span data-stu-id="f8e2e-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8e2e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8e2e-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeRefByName (
    [in]  mdToken     tkResolutionScope,
    [in]  LPCWSTR     szName,
    [out] mdTypeRef   *ptr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8e2e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8e2e-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="f8e2e-106">pro Token určující rozlišovací obor.</span><span class="sxs-lookup"><span data-stu-id="f8e2e-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="f8e2e-107">Platné jsou následující typy tokenů:</span><span class="sxs-lookup"><span data-stu-id="f8e2e-107">The following token types are valid:</span></span>  
  
- <span data-ttu-id="f8e2e-108">`mdModuleRef`, pokud je typ definován ve stejném sestavení, ve kterém je definován volající.</span><span class="sxs-lookup"><span data-stu-id="f8e2e-108">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
- <span data-ttu-id="f8e2e-109">`mdAssemblyRef`, pokud je typ definován v jiném sestavení než objekt, ve kterém je definován volající.</span><span class="sxs-lookup"><span data-stu-id="f8e2e-109">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
- <span data-ttu-id="f8e2e-110">`mdTypeRef`, pokud je typ vnořený typ.</span><span class="sxs-lookup"><span data-stu-id="f8e2e-110">`mdTypeRef`, if the type is a nested type.</span></span>  
  
- <span data-ttu-id="f8e2e-111">`mdModule`, pokud je typ definován ve stejném modulu, ve kterém je volající definován.</span><span class="sxs-lookup"><span data-stu-id="f8e2e-111">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
- <span data-ttu-id="f8e2e-112">Null, pokud je typ definován globálně.</span><span class="sxs-lookup"><span data-stu-id="f8e2e-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="f8e2e-113">pro Název cílového typu v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="f8e2e-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="f8e2e-114">mimo Ukazatel na `mdTypeRef` token, který je přiřazen k typu.</span><span class="sxs-lookup"><span data-stu-id="f8e2e-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8e2e-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f8e2e-115">Requirements</span></span>  
 <span data-ttu-id="f8e2e-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8e2e-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8e2e-117">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f8e2e-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f8e2e-118">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="f8e2e-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f8e2e-119">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8e2e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8e2e-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="f8e2e-120">See also</span></span>

- [<span data-ttu-id="f8e2e-121">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f8e2e-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="f8e2e-122">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f8e2e-122">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
