---
title: IMetaDataEmit2::SetGenericParamProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SetGenericParamProps
helpviewer_keywords:
- IMetaDataEmit2::SetGenericParamProps method [.NET Framework metadata]
- SetGenericParamProps method [.NET Framework metadata]
ms.assetid: cd93a48d-1fed-4706-bec6-a05dc3b64fbd
topic_type:
- apiref
ms.openlocfilehash: 7a93bbe0d7a9d9e6ff7505bbc215efa79176ad1f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440447"
---
# <a name="imetadataemit2setgenericparamprops-method"></a><span data-ttu-id="c9af6-102">IMetaDataEmit2::SetGenericParamProps – metoda</span><span class="sxs-lookup"><span data-stu-id="c9af6-102">IMetaDataEmit2::SetGenericParamProps Method</span></span>
<span data-ttu-id="c9af6-103">Sets property values for the generic parameter definition referenced by the specified token.</span><span class="sxs-lookup"><span data-stu-id="c9af6-103">Sets property values for the generic parameter definition referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9af6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9af6-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,   
    [in] DWORD            dwParamFlags,   
    [in] LPCWSTR          szName,   
    [in] DWORD            reserved,   
    [in] mdToken          rtkConstraints[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9af6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9af6-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="c9af6-106">[in] The token for the generic parameter definition for which to set values.</span><span class="sxs-lookup"><span data-stu-id="c9af6-106">[in] The token for the generic parameter definition for which to set values.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="c9af6-107">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span><span class="sxs-lookup"><span data-stu-id="c9af6-107">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="c9af6-108">[in] Optional.</span><span class="sxs-lookup"><span data-stu-id="c9af6-108">[in] Optional.</span></span> <span data-ttu-id="c9af6-109">The name of the parameter for which to set values.</span><span class="sxs-lookup"><span data-stu-id="c9af6-109">The name of the parameter for which to set values.</span></span>  
  
 `reserved`  
 <span data-ttu-id="c9af6-110">[in] Reserved for future extensibility.</span><span class="sxs-lookup"><span data-stu-id="c9af6-110">[in] Reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="c9af6-111">[in] Optional.</span><span class="sxs-lookup"><span data-stu-id="c9af6-111">[in] Optional.</span></span> <span data-ttu-id="c9af6-112">A zero-terminated array of type constraints.</span><span class="sxs-lookup"><span data-stu-id="c9af6-112">A zero-terminated array of type constraints.</span></span> <span data-ttu-id="c9af6-113">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span><span class="sxs-lookup"><span data-stu-id="c9af6-113">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9af6-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c9af6-114">Requirements</span></span>  
 <span data-ttu-id="c9af6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9af6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9af6-116">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c9af6-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c9af6-117">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c9af6-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c9af6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9af6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9af6-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9af6-119">See also</span></span>

- [<span data-ttu-id="c9af6-120">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9af6-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="c9af6-121">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9af6-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
