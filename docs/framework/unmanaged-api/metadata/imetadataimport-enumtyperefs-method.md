---
title: IMetaDataImport::EnumTypeRefs – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeRefs
helpviewer_keywords:
- EnumTypeRefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeRefs method [.NET Framework metadata]
ms.assetid: b4896b8f-8e97-469c-8089-e72a025661b5
topic_type:
- apiref
ms.openlocfilehash: 778ebf1d4fad0c8703964be88fdc3ff8c033bc28
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449981"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="f1bae-102">IMetaDataImport::EnumTypeRefs – metoda</span><span class="sxs-lookup"><span data-stu-id="f1bae-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="f1bae-103">Enumerates TypeRef tokens defined in the current metadata scope.</span><span class="sxs-lookup"><span data-stu-id="f1bae-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1bae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1bae-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,   
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1bae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f1bae-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="f1bae-106">[in, out] A pointer to the enumerator.</span><span class="sxs-lookup"><span data-stu-id="f1bae-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="f1bae-107">This must be NULL for the first call of this method.</span><span class="sxs-lookup"><span data-stu-id="f1bae-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="f1bae-108">[out] The array used to store the TypeRef tokens.</span><span class="sxs-lookup"><span data-stu-id="f1bae-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f1bae-109">[in] The maximum size of the `rTypeRefs` array.</span><span class="sxs-lookup"><span data-stu-id="f1bae-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="f1bae-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span><span class="sxs-lookup"><span data-stu-id="f1bae-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1bae-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f1bae-111">Return Value</span></span>  
  
|<span data-ttu-id="f1bae-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f1bae-112">HRESULT</span></span>|<span data-ttu-id="f1bae-113">Popis</span><span class="sxs-lookup"><span data-stu-id="f1bae-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f1bae-114">`EnumTypeRefs` returned successfully.</span><span class="sxs-lookup"><span data-stu-id="f1bae-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f1bae-115">There are no tokens to enumerate.</span><span class="sxs-lookup"><span data-stu-id="f1bae-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="f1bae-116">In that case, `pcTypeRefs` is zero.</span><span class="sxs-lookup"><span data-stu-id="f1bae-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1bae-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f1bae-117">Remarks</span></span>  
 <span data-ttu-id="f1bae-118">A TypeRef token represents a reference to a type.</span><span class="sxs-lookup"><span data-stu-id="f1bae-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1bae-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f1bae-119">Requirements</span></span>  
 <span data-ttu-id="f1bae-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1bae-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1bae-121">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f1bae-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f1bae-122">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f1bae-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f1bae-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1bae-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1bae-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1bae-124">See also</span></span>

- [<span data-ttu-id="f1bae-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1bae-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f1bae-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1bae-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
