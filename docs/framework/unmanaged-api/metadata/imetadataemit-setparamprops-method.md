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
ms.openlocfilehash: b710f966f519e2702607b7e186fff5986110d391
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007816"
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="0d6a8-102">IMetaDataEmit::SetParamProps – metoda</span><span class="sxs-lookup"><span data-stu-id="0d6a8-102">IMetaDataEmit::SetParamProps Method</span></span>
<span data-ttu-id="0d6a8-103">Nastaví nebo změní funkce parametru metody, které byly definovány předchozím voláním [IMetaDataEmit::D efineparam](imetadataemit-defineparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="0d6a8-103">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d6a8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d6a8-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="0d6a8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0d6a8-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="0d6a8-106">pro Token pro cílový parametr</span><span class="sxs-lookup"><span data-stu-id="0d6a8-106">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="0d6a8-107">pro Název parametru v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="0d6a8-107">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="0d6a8-108">pro Příznaky pro parametr</span><span class="sxs-lookup"><span data-stu-id="0d6a8-108">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="0d6a8-109">pro ELEMENT_TYPE_ \* pro hodnotu konstanty.</span><span class="sxs-lookup"><span data-stu-id="0d6a8-109">[in] The ELEMENT_TYPE_\* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="0d6a8-110">pro Hodnota konstanty pro parametr</span><span class="sxs-lookup"><span data-stu-id="0d6a8-110">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="0d6a8-111">pro Velikost v (Unicode) znaků `pValue` .</span><span class="sxs-lookup"><span data-stu-id="0d6a8-111">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d6a8-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0d6a8-112">Requirements</span></span>  
 <span data-ttu-id="0d6a8-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d6a8-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d6a8-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0d6a8-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0d6a8-115">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="0d6a8-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d6a8-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d6a8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d6a8-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d6a8-117">See also</span></span>

- [<span data-ttu-id="0d6a8-118">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0d6a8-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="0d6a8-119">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0d6a8-119">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
