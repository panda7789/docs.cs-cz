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
ms.openlocfilehash: f8448de17ad974bc77021a7880b7d8576c69ae75
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750909"
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="d44c3-102">IMetaDataEmit::SetParamProps – metoda</span><span class="sxs-lookup"><span data-stu-id="d44c3-102">IMetaDataEmit::SetParamProps Method</span></span>
<span data-ttu-id="d44c3-103">Nastavuje nebo mění parametru metody, která byla definována v předchozím volání funkce [imetadataemit::defineparam –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="d44c3-103">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d44c3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d44c3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetParamProps (   
    [in]  mdParamDef  pd,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwParamFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d44c3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d44c3-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="d44c3-106">[in] Token pro parametr target.</span><span class="sxs-lookup"><span data-stu-id="d44c3-106">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="d44c3-107">[in] Název parametru v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="d44c3-107">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="d44c3-108">[in] Příznaky pro parametr.</span><span class="sxs-lookup"><span data-stu-id="d44c3-108">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="d44c3-109">[in] Typ ELEMENT_TYPE_ \* pro konstantní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d44c3-109">[in] The ELEMENT_TYPE_\* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="d44c3-110">[in] Konstantní hodnota parametru.</span><span class="sxs-lookup"><span data-stu-id="d44c3-110">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="d44c3-111">[in] Velikost v znaky (Unicode) `pValue`.</span><span class="sxs-lookup"><span data-stu-id="d44c3-111">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d44c3-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d44c3-112">Requirements</span></span>  
 <span data-ttu-id="d44c3-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d44c3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d44c3-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d44c3-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d44c3-115">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d44c3-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d44c3-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d44c3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d44c3-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d44c3-117">See also</span></span>

- [<span data-ttu-id="d44c3-118">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d44c3-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="d44c3-119">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d44c3-119">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
