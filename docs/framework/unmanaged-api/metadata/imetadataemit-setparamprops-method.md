---
title: IMetaDataEmit::SetParamProps – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e51cb1049737e6b325656057060a88123f69a9b4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493320"
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="0438f-102">IMetaDataEmit::SetParamProps – metoda</span><span class="sxs-lookup"><span data-stu-id="0438f-102">IMetaDataEmit::SetParamProps Method</span></span>
<span data-ttu-id="0438f-103">Nastavuje nebo mění parametru metody, která byla definována v předchozím volání funkce [imetadataemit::defineparam –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="0438f-103">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0438f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0438f-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="0438f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0438f-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="0438f-106">[in] Token pro parametr target.</span><span class="sxs-lookup"><span data-stu-id="0438f-106">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="0438f-107">[in] Název parametru v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="0438f-107">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="0438f-108">[in] Příznaky pro parametr.</span><span class="sxs-lookup"><span data-stu-id="0438f-108">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="0438f-109">[in] Typ ELEMENT_TYPE_ \* pro konstantní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0438f-109">[in] The ELEMENT_TYPE_\* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="0438f-110">[in] Konstantní hodnota parametru.</span><span class="sxs-lookup"><span data-stu-id="0438f-110">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="0438f-111">[in] Velikost v znaky (Unicode) `pValue`.</span><span class="sxs-lookup"><span data-stu-id="0438f-111">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0438f-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0438f-112">Requirements</span></span>  
 <span data-ttu-id="0438f-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0438f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0438f-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0438f-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0438f-115">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0438f-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0438f-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0438f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0438f-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0438f-117">See also</span></span>
- [<span data-ttu-id="0438f-118">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0438f-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="0438f-119">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0438f-119">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
