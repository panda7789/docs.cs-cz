---
title: ICorDebugArrayValue::GetDimensions – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetDimensions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetDimensions
helpviewer_keywords:
- ICorDebugArrayValue::GetDimensions method [.NET Framework debugging]
- GetDimensions method [.NET Framework debugging]
ms.assetid: 6c116592-134b-4ef2-a319-680e92d013aa
topic_type:
- apiref
ms.openlocfilehash: 35e043c56977bf644efe1dd9cee1409f50cc877f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179018"
---
# <a name="icordebugarrayvaluegetdimensions-method"></a><span data-ttu-id="d5b45-102">ICorDebugArrayValue::GetDimensions – metoda</span><span class="sxs-lookup"><span data-stu-id="d5b45-102">ICorDebugArrayValue::GetDimensions Method</span></span>
<span data-ttu-id="d5b45-103">Získá počet prvků v každé dimenzi tohoto pole.</span><span class="sxs-lookup"><span data-stu-id="d5b45-103">Gets the number of elements in each dimension of this array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5b45-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5b45-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDimensions (  
    [in] ULONG32         cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32          dims[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5b45-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5b45-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="d5b45-106">[v] Počet dimenzí tohoto objektu ICorDebugArrayValue.</span><span class="sxs-lookup"><span data-stu-id="d5b45-106">[in] The number of dimensions of this ICorDebugArrayValue object.</span></span>  
  
 <span data-ttu-id="d5b45-107">Tato hodnota je také `dims` velikost pole, protože jeho velikost se rovná `ICorDebugArrayValue` počtu dimenzí objektu.</span><span class="sxs-lookup"><span data-stu-id="d5b45-107">This value is also the size of the `dims` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `dims`  
 <span data-ttu-id="d5b45-108">[out] Pole celých čísel, z nichž každá určuje počet prvků v `ICorDebugArrayValue` dimenzi v tomto objektu.</span><span class="sxs-lookup"><span data-stu-id="d5b45-108">[out] An array of integers, each of which specifies the number of elements in a dimension in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5b45-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d5b45-109">Requirements</span></span>  
 <span data-ttu-id="d5b45-110">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5b45-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5b45-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d5b45-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5b45-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5b45-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5b45-113">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5b45-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
