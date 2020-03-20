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
ms.openlocfilehash: e5d4ddd43b27d733a63c2e0dc5e92ffd2ba94a7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175431"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="84626-102">IMetaDataImport::EnumTypeRefs – metoda</span><span class="sxs-lookup"><span data-stu-id="84626-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="84626-103">Zápory TypeRef tokeny definované v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="84626-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84626-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84626-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84626-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="84626-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="84626-106">[dovnitř, ven] Ukazatel na čítač výčtu.</span><span class="sxs-lookup"><span data-stu-id="84626-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="84626-107">To musí být NULL pro první volání této metody.</span><span class="sxs-lookup"><span data-stu-id="84626-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="84626-108">[out] Pole používané k uložení tokenů TypeRef.</span><span class="sxs-lookup"><span data-stu-id="84626-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="84626-109">[v] Maximální velikost `rTypeRefs` pole.</span><span class="sxs-lookup"><span data-stu-id="84626-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="84626-110">[out] Ukazatel na počet tokenů TypeRef `rTypeRefs`vrácených v .</span><span class="sxs-lookup"><span data-stu-id="84626-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84626-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="84626-111">Return Value</span></span>  
  
|<span data-ttu-id="84626-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="84626-112">HRESULT</span></span>|<span data-ttu-id="84626-113">Popis</span><span class="sxs-lookup"><span data-stu-id="84626-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="84626-114">`EnumTypeRefs`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="84626-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="84626-115">Neexistují žádné tokeny výčet.</span><span class="sxs-lookup"><span data-stu-id="84626-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="84626-116">V tom `pcTypeRefs` případě je nula.</span><span class="sxs-lookup"><span data-stu-id="84626-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84626-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="84626-117">Remarks</span></span>  
 <span data-ttu-id="84626-118">A TypeRef token představuje odkaz na typ.</span><span class="sxs-lookup"><span data-stu-id="84626-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84626-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="84626-119">Requirements</span></span>  
 <span data-ttu-id="84626-120">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84626-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84626-121">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="84626-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="84626-122">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="84626-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="84626-123">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84626-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84626-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="84626-124">See also</span></span>

- [<span data-ttu-id="84626-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="84626-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="84626-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="84626-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
