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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8d096be8eb7f966d5a79e57a3a1b7ab7f63cd5ea
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659251"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="01d5a-102">IMetaDataImport::EnumTypeRefs – metoda</span><span class="sxs-lookup"><span data-stu-id="01d5a-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="01d5a-103">Vytvoří výčet TypeRef tokeny definované v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="01d5a-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01d5a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01d5a-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,   
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTypeRefs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="01d5a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01d5a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="01d5a-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="01d5a-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="01d5a-107">První volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="01d5a-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="01d5a-108">[out] Pole pro ukládání tokenů TypeRef.</span><span class="sxs-lookup"><span data-stu-id="01d5a-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="01d5a-109">[in] Maximální velikost `rTypeRefs` pole.</span><span class="sxs-lookup"><span data-stu-id="01d5a-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="01d5a-110">[out] Ukazatel na počet tokenů TypeRef vrácené v `rTypeRefs`.</span><span class="sxs-lookup"><span data-stu-id="01d5a-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01d5a-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="01d5a-111">Return Value</span></span>  
  
|<span data-ttu-id="01d5a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="01d5a-112">HRESULT</span></span>|<span data-ttu-id="01d5a-113">Popis</span><span class="sxs-lookup"><span data-stu-id="01d5a-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="01d5a-114">`EnumTypeRefs` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="01d5a-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="01d5a-115">Neexistují žádné tokeny se vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="01d5a-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="01d5a-116">V takovém případě `pcTypeRefs` je nula.</span><span class="sxs-lookup"><span data-stu-id="01d5a-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01d5a-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01d5a-117">Remarks</span></span>  
 <span data-ttu-id="01d5a-118">TypeRef token představuje odkaz na typ.</span><span class="sxs-lookup"><span data-stu-id="01d5a-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01d5a-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="01d5a-119">Requirements</span></span>  
 <span data-ttu-id="01d5a-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01d5a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01d5a-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="01d5a-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="01d5a-122">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="01d5a-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="01d5a-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01d5a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01d5a-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01d5a-124">See also</span></span>
- [<span data-ttu-id="01d5a-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01d5a-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="01d5a-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01d5a-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
