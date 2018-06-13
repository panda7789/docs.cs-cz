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
ms.openlocfilehash: 5d49ac70aceb76f69711ea4bf514f69697ac156c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447369"
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="4f5b5-102">IMetaDataEmit::DefineParam – metoda</span><span class="sxs-lookup"><span data-stu-id="4f5b5-102">IMetaDataEmit::DefineParam Method</span></span>
<span data-ttu-id="4f5b5-103">Vytvoří definici parametru podpisem zadaný pro metodu odkazuje zadaný token a získá token pro tuto definici parametru.</span><span class="sxs-lookup"><span data-stu-id="4f5b5-103">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f5b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f5b5-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="4f5b5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4f5b5-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="4f5b5-106">[v] Token pro metodu, jejichž parametr je definovaný.</span><span class="sxs-lookup"><span data-stu-id="4f5b5-106">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="4f5b5-107">[v] Pořadové číslo parametru.</span><span class="sxs-lookup"><span data-stu-id="4f5b5-107">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="4f5b5-108">[v] Název parametru v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="4f5b5-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="4f5b5-109">[v] Příznaky pro parametr.</span><span class="sxs-lookup"><span data-stu-id="4f5b5-109">[in] Flags for the parameter.</span></span> <span data-ttu-id="4f5b5-110">Toto je bitová maska s `CorParamAttr` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4f5b5-110">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="4f5b5-111">[v] `ELEMENT_TYPE_` *\** pro konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4f5b5-111">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="4f5b5-112">[v] Konstantní hodnota pro parametr.</span><span class="sxs-lookup"><span data-stu-id="4f5b5-112">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="4f5b5-113">[v] Velikost v znaky Unicode z `pValue`.</span><span class="sxs-lookup"><span data-stu-id="4f5b5-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="4f5b5-114">[out] `mdParamDef` Token přiřazený.</span><span class="sxs-lookup"><span data-stu-id="4f5b5-114">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f5b5-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4f5b5-115">Remarks</span></span>  
 <span data-ttu-id="4f5b5-116">Pořadí hodnot v `ulParamSeq` začínat 1 pro parametry.</span><span class="sxs-lookup"><span data-stu-id="4f5b5-116">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="4f5b5-117">Vrácená hodnota má pořadové číslo 0.</span><span class="sxs-lookup"><span data-stu-id="4f5b5-117">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f5b5-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4f5b5-118">Requirements</span></span>  
 <span data-ttu-id="4f5b5-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f5b5-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f5b5-120">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4f5b5-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4f5b5-121">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4f5b5-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4f5b5-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f5b5-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f5b5-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="4f5b5-123">See Also</span></span>  
 [<span data-ttu-id="4f5b5-124">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4f5b5-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="4f5b5-125">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4f5b5-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
