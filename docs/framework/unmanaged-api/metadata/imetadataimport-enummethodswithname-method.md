---
title: IMetaDataImport::EnumMethodsWithName – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodsWithName
helpviewer_keywords:
- IMetaDataImport::EnumMethodsWithName method [.NET Framework metadata]
- EnumMethodsWithName method [.NET Framework metadata]
ms.assetid: a8624913-2e23-46ad-a0c1-bb8eccbbf20f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f15ee906fb20cb60272cee3deffa68dbe852f689
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200178"
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="e0276-102">IMetaDataImport::EnumMethodsWithName – metoda</span><span class="sxs-lookup"><span data-stu-id="e0276-102">IMetaDataImport::EnumMethodsWithName Method</span></span>
<span data-ttu-id="e0276-103">Podává výčet metod, které mají se zadaným názvem a typem odkazuje zadaný token TypeDef, která jsou definována.</span><span class="sxs-lookup"><span data-stu-id="e0276-103">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0276-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0276-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodsWithName (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdTypeDef       cl,  
   [in]  LPCWSTR         szName,  
   [out] mdMethodDef     rMethods[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0276-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0276-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e0276-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="e0276-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="e0276-107">První volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="e0276-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="e0276-108">[in] Token TypeDef představující typ, jehož metody pro výčet.</span><span class="sxs-lookup"><span data-stu-id="e0276-108">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="e0276-109">[in] Název, který omezuje rozsah výčtu.</span><span class="sxs-lookup"><span data-stu-id="e0276-109">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="e0276-110">[out] Pole pro ukládání tokenů MethodDef.</span><span class="sxs-lookup"><span data-stu-id="e0276-110">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e0276-111">[in] Maximální velikost `rMethods` pole.</span><span class="sxs-lookup"><span data-stu-id="e0276-111">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="e0276-112">[out] Počet tokenů MethodDef vrácené v `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="e0276-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0276-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e0276-113">Remarks</span></span>  
 <span data-ttu-id="e0276-114">Tato metoda vytváří výčet polí a metod, ale nikoli vlastnosti nebo události.</span><span class="sxs-lookup"><span data-stu-id="e0276-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="e0276-115">Na rozdíl od [imetadataimport::enummethods –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` zahodí všechny tokeny metody, které nemají se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="e0276-115">Unlike [IMetaDataImport::EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0276-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e0276-116">Return Value</span></span>  
  
|<span data-ttu-id="e0276-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e0276-117">HRESULT</span></span>|<span data-ttu-id="e0276-118">Popis</span><span class="sxs-lookup"><span data-stu-id="e0276-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodsWithName` <span data-ttu-id="e0276-119">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="e0276-119">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e0276-120">Neexistují žádné tokeny se vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="e0276-120">There are no tokens to enumerate.</span></span> <span data-ttu-id="e0276-121">V takovém případě `pcTokens` je nula.</span><span class="sxs-lookup"><span data-stu-id="e0276-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e0276-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e0276-122">Requirements</span></span>  
 <span data-ttu-id="e0276-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0276-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0276-124">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e0276-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e0276-125">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e0276-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="e0276-126">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e0276-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e0276-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0276-127">See also</span></span>

- [<span data-ttu-id="e0276-128">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e0276-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e0276-129">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e0276-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
