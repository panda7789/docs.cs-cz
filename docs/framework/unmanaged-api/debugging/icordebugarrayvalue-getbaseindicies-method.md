---
title: ICorDebugArrayValue::GetBaseIndicies – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetBaseIndicies
helpviewer_keywords:
- ICorDebugArrayValue::GetBaseIndicies method [.NET Framework debugging]
- GetBaseIndicies method [.NET Framework debugging]
ms.assetid: 868b339b-acdb-4fe0-91c7-b85f4fba99eb
topic_type:
- apiref
ms.openlocfilehash: 7c6d1905cdbd12b960014e687034ea9d163b68d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179041"
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a><span data-ttu-id="7e643-102">ICorDebugArrayValue::GetBaseIndicies – metoda</span><span class="sxs-lookup"><span data-stu-id="7e643-102">ICorDebugArrayValue::GetBaseIndicies Method</span></span>
<span data-ttu-id="7e643-103">Získá základní index každé dimenze v poli.</span><span class="sxs-lookup"><span data-stu-id="7e643-103">Gets the base index of each dimension in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e643-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e643-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32           indicies[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e643-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e643-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="7e643-106">[v] Počet rozměrů tohoto `ICorDebugArrayValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="7e643-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span> <span data-ttu-id="7e643-107">Tato hodnota je také `indicies` velikost pole, protože jeho velikost se rovná `ICorDebugArrayValue` počtu dimenzí objektu.</span><span class="sxs-lookup"><span data-stu-id="7e643-107">This value is also the size of the `indicies` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indicies`  
 <span data-ttu-id="7e643-108">[out] Pole celých čísel, z nichž každý je základní index (to znamená počáteční index) dimenze tohoto `ICorDebugArrayValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="7e643-108">[out] An array of integers, each of which is the base index (that is, the starting index) of a dimension of this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e643-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7e643-109">Requirements</span></span>  
 <span data-ttu-id="7e643-110">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e643-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e643-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e643-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e643-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e643-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e643-113">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e643-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
