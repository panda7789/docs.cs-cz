---
title: "IMetaDataImport::EnumTypeRefs – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumTypeRefs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumTypeRefs
helpviewer_keywords:
- EnumTypeRefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeRefs method [.NET Framework metadata]
ms.assetid: b4896b8f-8e97-469c-8089-e72a025661b5
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3099f129abd3477aeb08526b9f0dcd5b701d4dc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="1e331-102">IMetaDataImport::EnumTypeRefs – metoda</span><span class="sxs-lookup"><span data-stu-id="1e331-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="1e331-103">Vytvoří výčet Odkaz TypeRef tokeny definované v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="1e331-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e331-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e331-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,   
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTypeRefs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1e331-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1e331-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="1e331-106">[ve out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="1e331-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="1e331-107">Toto musí mít hodnotu NULL pro první volání této metody.</span><span class="sxs-lookup"><span data-stu-id="1e331-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="1e331-108">[out] Pole používá k ukládání Odkaz TypeRef tokenů.</span><span class="sxs-lookup"><span data-stu-id="1e331-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="1e331-109">[v] Maximální velikost `rTypeRefs` pole.</span><span class="sxs-lookup"><span data-stu-id="1e331-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="1e331-110">[out] Ukazatel na počet Odkaz TypeRef tokeny, vrátí se v `rTypeRefs`.</span><span class="sxs-lookup"><span data-stu-id="1e331-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e331-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1e331-111">Return Value</span></span>  
  
|<span data-ttu-id="1e331-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1e331-112">HRESULT</span></span>|<span data-ttu-id="1e331-113">Popis</span><span class="sxs-lookup"><span data-stu-id="1e331-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="1e331-114">`EnumTypeRefs`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="1e331-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="1e331-115">Neexistují žádné tokenů pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="1e331-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="1e331-116">V takovém případě `pcTypeRefs` je nulová.</span><span class="sxs-lookup"><span data-stu-id="1e331-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e331-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1e331-117">Remarks</span></span>  
 <span data-ttu-id="1e331-118">Token Odkaz TypeRef představuje odkaz na typ.</span><span class="sxs-lookup"><span data-stu-id="1e331-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e331-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1e331-119">Requirements</span></span>  
 <span data-ttu-id="1e331-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e331-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e331-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1e331-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1e331-122">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1e331-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1e331-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e331-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e331-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="1e331-124">See Also</span></span>  
 [<span data-ttu-id="1e331-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1e331-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="1e331-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1e331-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
