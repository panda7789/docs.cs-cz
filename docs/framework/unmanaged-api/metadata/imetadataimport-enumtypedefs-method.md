---
title: IMetaDataImport::EnumTypeDefs – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeDefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type:
- apiref
ms.openlocfilehash: 3854cb4aa3d229c87466c0a35a72447ceb235624
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449991"
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="56430-102">IMetaDataImport::EnumTypeDefs – metoda</span><span class="sxs-lookup"><span data-stu-id="56430-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="56430-103">Enumerates TypeDef tokens representing all types within the current scope.</span><span class="sxs-lookup"><span data-stu-id="56430-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56430-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56430-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,   
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,   
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56430-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="56430-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="56430-106">[out] A pointer to the new enumerator.</span><span class="sxs-lookup"><span data-stu-id="56430-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="56430-107">This must be NULL for the first call of this method.</span><span class="sxs-lookup"><span data-stu-id="56430-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="56430-108">[in] The array used to store the TypeDef tokens.</span><span class="sxs-lookup"><span data-stu-id="56430-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="56430-109">[in] The maximum size of the `rTypeDefs` array.</span><span class="sxs-lookup"><span data-stu-id="56430-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="56430-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="56430-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56430-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="56430-111">Return Value</span></span>  
  
|<span data-ttu-id="56430-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="56430-112">HRESULT</span></span>|<span data-ttu-id="56430-113">Popis</span><span class="sxs-lookup"><span data-stu-id="56430-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="56430-114">`EnumTypeDefs` returned successfully.</span><span class="sxs-lookup"><span data-stu-id="56430-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="56430-115">There are no tokens to enumerate.</span><span class="sxs-lookup"><span data-stu-id="56430-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="56430-116">In that case, `pcTypeDefs` is zero.</span><span class="sxs-lookup"><span data-stu-id="56430-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56430-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="56430-117">Remarks</span></span>  
 <span data-ttu-id="56430-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span><span class="sxs-lookup"><span data-stu-id="56430-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56430-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="56430-119">Requirements</span></span>  
 <span data-ttu-id="56430-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56430-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56430-121">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="56430-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="56430-122">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="56430-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="56430-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56430-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56430-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56430-124">See also</span></span>

- [<span data-ttu-id="56430-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="56430-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="56430-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="56430-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
