---
title: "IMetaDataImport::EnumMethodsWithName – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9f16e66f83925104c4be1e69a476e398f33295a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="08c3a-102">IMetaDataImport::EnumMethodsWithName – metoda</span><span class="sxs-lookup"><span data-stu-id="08c3a-102">IMetaDataImport::EnumMethodsWithName Method</span></span>
<span data-ttu-id="08c3a-103">Vytvoří výčet metod, které jsou definovány podle typu, který odkazuje zadaný token TypeDef, které mají zadaný název.</span><span class="sxs-lookup"><span data-stu-id="08c3a-103">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08c3a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08c3a-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="08c3a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="08c3a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="08c3a-106">[ve out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="08c3a-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="08c3a-107">Toto musí mít hodnotu NULL pro první volání této metody.</span><span class="sxs-lookup"><span data-stu-id="08c3a-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="08c3a-108">[v] TypeDef token představující jejichž metody pro výčet typu.</span><span class="sxs-lookup"><span data-stu-id="08c3a-108">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="08c3a-109">[v] Název, který omezuje obor výčtu.</span><span class="sxs-lookup"><span data-stu-id="08c3a-109">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="08c3a-110">[out] Pole používá k ukládání MethodDef tokenů.</span><span class="sxs-lookup"><span data-stu-id="08c3a-110">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="08c3a-111">[v] Maximální velikost `rMethods` pole.</span><span class="sxs-lookup"><span data-stu-id="08c3a-111">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="08c3a-112">[out] Počet MethodDef tokeny, vrátí se v `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="08c3a-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08c3a-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="08c3a-113">Remarks</span></span>  
 <span data-ttu-id="08c3a-114">Tato metoda zobrazí pole a metody, ale ne vlastnosti nebo události.</span><span class="sxs-lookup"><span data-stu-id="08c3a-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="08c3a-115">Na rozdíl od [imetadataimport::enummethods –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` zahodí všechny metoda tokeny, které nemají zadaný název.</span><span class="sxs-lookup"><span data-stu-id="08c3a-115">Unlike [IMetaDataImport::EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08c3a-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="08c3a-116">Return Value</span></span>  
  
|<span data-ttu-id="08c3a-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="08c3a-117">HRESULT</span></span>|<span data-ttu-id="08c3a-118">Popis</span><span class="sxs-lookup"><span data-stu-id="08c3a-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="08c3a-119">`EnumMethodsWithName`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="08c3a-119">`EnumMethodsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="08c3a-120">Neexistují žádné tokenů pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="08c3a-120">There are no tokens to enumerate.</span></span> <span data-ttu-id="08c3a-121">V takovém případě `pcTokens` je nulová.</span><span class="sxs-lookup"><span data-stu-id="08c3a-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="08c3a-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="08c3a-122">Requirements</span></span>  
 <span data-ttu-id="08c3a-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08c3a-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08c3a-124">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="08c3a-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="08c3a-125">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="08c3a-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="08c3a-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08c3a-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08c3a-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="08c3a-127">See Also</span></span>  
 [<span data-ttu-id="08c3a-128">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="08c3a-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="08c3a-129">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="08c3a-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
