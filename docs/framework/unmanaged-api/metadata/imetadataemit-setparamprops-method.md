---
title: "IMetaDataEmit::SetParamProps – metoda"
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
- IMetaDataEmit.SetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParamProps
helpviewer_keywords:
- IMetaDataEmit::SetParamProps method [.NET Framework metadata]
- SetParamProps method [.NET Framework metadata]
ms.assetid: a95a3908-9f87-4084-937e-8e01ef03ad63
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e8ada9deddf8528321797c1f9bd06b5b775ac4bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="de819-102">IMetaDataEmit::SetParamProps – metoda</span><span class="sxs-lookup"><span data-stu-id="de819-102">IMetaDataEmit::SetParamProps Method</span></span>
<span data-ttu-id="de819-103">Nastaví nebo změny funkcí parametru metody, která byla definována voláním předchozí [imetadataemit::defineparam –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="de819-103">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de819-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de819-104">Syntax</span></span>  
  
```  
HRESULT SetParamProps (   
    [in]  mdParamDef  pd,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwParamFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de819-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="de819-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="de819-106">[v] Token pro parametr cíl.</span><span class="sxs-lookup"><span data-stu-id="de819-106">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="de819-107">[v] Název parametru v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="de819-107">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="de819-108">[v] Příznaky pro parametr.</span><span class="sxs-lookup"><span data-stu-id="de819-108">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="de819-109">[v] Typ ELEMENT_TYPE_ \* pro konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="de819-109">[in] The ELEMENT_TYPE_\* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="de819-110">[v] Konstantní hodnota pro parametr.</span><span class="sxs-lookup"><span data-stu-id="de819-110">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="de819-111">[v] Velikost v znaků (Unicode) `pValue`.</span><span class="sxs-lookup"><span data-stu-id="de819-111">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de819-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="de819-112">Requirements</span></span>  
 <span data-ttu-id="de819-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de819-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de819-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="de819-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="de819-115">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="de819-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="de819-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de819-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de819-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="de819-117">See Also</span></span>  
 [<span data-ttu-id="de819-118">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="de819-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="de819-119">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="de819-119">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
