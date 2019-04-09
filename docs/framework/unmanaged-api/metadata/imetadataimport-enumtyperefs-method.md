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
ms.openlocfilehash: de0fe4a51fbb49e80377b6b434bf3b72ddb90f02
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081616"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="e69b7-102">IMetaDataImport::EnumTypeRefs – metoda</span><span class="sxs-lookup"><span data-stu-id="e69b7-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="e69b7-103">Vytvoří výčet TypeRef tokeny definované v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="e69b7-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e69b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e69b7-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,   
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e69b7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e69b7-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e69b7-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="e69b7-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="e69b7-107">První volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="e69b7-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="e69b7-108">[out] Pole pro ukládání tokenů TypeRef.</span><span class="sxs-lookup"><span data-stu-id="e69b7-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e69b7-109">[in] Maximální velikost `rTypeRefs` pole.</span><span class="sxs-lookup"><span data-stu-id="e69b7-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="e69b7-110">[out] Ukazatel na počet tokenů TypeRef vrácené v `rTypeRefs`.</span><span class="sxs-lookup"><span data-stu-id="e69b7-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e69b7-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e69b7-111">Return Value</span></span>  
  
|<span data-ttu-id="e69b7-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e69b7-112">HRESULT</span></span>|<span data-ttu-id="e69b7-113">Popis</span><span class="sxs-lookup"><span data-stu-id="e69b7-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeRefs` <span data-ttu-id="e69b7-114">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="e69b7-114">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e69b7-115">Neexistují žádné tokeny se vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="e69b7-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="e69b7-116">V takovém případě `pcTypeRefs` je nula.</span><span class="sxs-lookup"><span data-stu-id="e69b7-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e69b7-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e69b7-117">Remarks</span></span>  
 <span data-ttu-id="e69b7-118">TypeRef token představuje odkaz na typ.</span><span class="sxs-lookup"><span data-stu-id="e69b7-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e69b7-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e69b7-119">Requirements</span></span>  
 <span data-ttu-id="e69b7-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e69b7-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e69b7-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e69b7-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e69b7-122">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e69b7-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="e69b7-123">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e69b7-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e69b7-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e69b7-124">See also</span></span>

- [<span data-ttu-id="e69b7-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e69b7-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e69b7-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e69b7-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
