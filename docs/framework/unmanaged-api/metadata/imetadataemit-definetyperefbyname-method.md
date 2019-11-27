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
ms.openlocfilehash: 3dfdd473b01bfe83def52f957c52e0f4d11375ad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434379"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="b648b-102">IMetaDataEmit::DefineTypeRefByName – metoda</span><span class="sxs-lookup"><span data-stu-id="b648b-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>
<span data-ttu-id="b648b-103">Získá token metadat pro typ, který je definován v zadaném oboru, který je mimo aktuální obor.</span><span class="sxs-lookup"><span data-stu-id="b648b-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b648b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b648b-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b648b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b648b-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="b648b-106">pro Token určující rozlišovací obor.</span><span class="sxs-lookup"><span data-stu-id="b648b-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="b648b-107">Platné jsou následující typy tokenů:</span><span class="sxs-lookup"><span data-stu-id="b648b-107">The following token types are valid:</span></span>  
  
- <span data-ttu-id="b648b-108">`mdModuleRef`, pokud je typ definován ve stejném sestavení, ve kterém je definován volající.</span><span class="sxs-lookup"><span data-stu-id="b648b-108">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
- <span data-ttu-id="b648b-109">`mdAssemblyRef`, pokud je typ definován v jiném sestavení, než v němž je definován volající.</span><span class="sxs-lookup"><span data-stu-id="b648b-109">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
- <span data-ttu-id="b648b-110">`mdTypeRef`, pokud je typ vnořený typ.</span><span class="sxs-lookup"><span data-stu-id="b648b-110">`mdTypeRef`, if the type is a nested type.</span></span>  
  
- <span data-ttu-id="b648b-111">`mdModule`, pokud je typ definován ve stejném modulu, ve kterém je definován volající.</span><span class="sxs-lookup"><span data-stu-id="b648b-111">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
- <span data-ttu-id="b648b-112">Null, pokud je typ definován globálně.</span><span class="sxs-lookup"><span data-stu-id="b648b-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="b648b-113">pro Název cílového typu v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="b648b-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="b648b-114">mimo Ukazatel na token `mdTypeRef`, který je přiřazen k typu.</span><span class="sxs-lookup"><span data-stu-id="b648b-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b648b-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b648b-115">Requirements</span></span>  
 <span data-ttu-id="b648b-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b648b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b648b-117">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b648b-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b648b-118">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="b648b-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b648b-119">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b648b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b648b-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b648b-120">See also</span></span>

- [<span data-ttu-id="b648b-121">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b648b-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b648b-122">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b648b-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
