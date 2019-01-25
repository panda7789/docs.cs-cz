---
title: IMetaDataEmit::DefineParam – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 33bff2b72f2381fea461bb043506ee78f757dea8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54504900"
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="58ec9-102">IMetaDataEmit::DefineParam – metoda</span><span class="sxs-lookup"><span data-stu-id="58ec9-102">IMetaDataEmit::DefineParam Method</span></span>
<span data-ttu-id="58ec9-103">Vytvoří definici parametru se zadaným podpisem pro metodu odkazuje zadaný token a získá token pro tuto definici parametru.</span><span class="sxs-lookup"><span data-stu-id="58ec9-103">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58ec9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58ec9-104">Syntax</span></span>  
  
```  
HRESULT DefineParam (  
    [in]  mdMethodDef md,   
    [in]  ULONG       ulParamSeq,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwParamFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,  
    [in]  ULONG       cchValue,   
    [out] mdParamDef  *ppd   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="58ec9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="58ec9-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="58ec9-106">[in] Token pro metodu, jejíž parametr se zrovna definuje.</span><span class="sxs-lookup"><span data-stu-id="58ec9-106">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="58ec9-107">[in] Pořadové číslo parametru.</span><span class="sxs-lookup"><span data-stu-id="58ec9-107">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="58ec9-108">[in] Název parametru v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="58ec9-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="58ec9-109">[in] Příznaky pro parametr.</span><span class="sxs-lookup"><span data-stu-id="58ec9-109">[in] Flags for the parameter.</span></span> <span data-ttu-id="58ec9-110">To je bitová maska z `CorParamAttr` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="58ec9-110">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="58ec9-111">[in] `ELEMENT_TYPE_` *\** pro konstantní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="58ec9-111">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="58ec9-112">[in] Konstantní hodnota parametru.</span><span class="sxs-lookup"><span data-stu-id="58ec9-112">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="58ec9-113">[in] Velikost v znaky Unicode z `pValue`.</span><span class="sxs-lookup"><span data-stu-id="58ec9-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="58ec9-114">[out] `mdParamDef` Token přiřazený.</span><span class="sxs-lookup"><span data-stu-id="58ec9-114">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58ec9-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="58ec9-115">Remarks</span></span>  
 <span data-ttu-id="58ec9-116">Pořadí hodnot v `ulParamSeq` začínají znakem 1 pro parametry.</span><span class="sxs-lookup"><span data-stu-id="58ec9-116">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="58ec9-117">Návratová hodnota má pořadové číslo 0.</span><span class="sxs-lookup"><span data-stu-id="58ec9-117">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58ec9-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="58ec9-118">Requirements</span></span>  
 <span data-ttu-id="58ec9-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58ec9-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58ec9-120">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="58ec9-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="58ec9-121">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="58ec9-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="58ec9-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58ec9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58ec9-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="58ec9-123">See also</span></span>
- [<span data-ttu-id="58ec9-124">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="58ec9-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="58ec9-125">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="58ec9-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
