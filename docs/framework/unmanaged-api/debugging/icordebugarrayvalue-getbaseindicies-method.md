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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f24a1434f737e8281a0c68dd09d2e17b34371694
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471651"
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a><span data-ttu-id="0df7e-102">ICorDebugArrayValue::GetBaseIndicies – metoda</span><span class="sxs-lookup"><span data-stu-id="0df7e-102">ICorDebugArrayValue::GetBaseIndicies Method</span></span>
<span data-ttu-id="0df7e-103">Získá základní index každé dimenze v poli.</span><span class="sxs-lookup"><span data-stu-id="0df7e-103">Gets the base index of each dimension in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0df7e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0df7e-104">Syntax</span></span>  
  
```  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]   
        ULONG32           indicies[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0df7e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0df7e-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="0df7e-106">[in] Počet dimenzí tohoto `ICorDebugArrayValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="0df7e-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span> <span data-ttu-id="0df7e-107">Tato hodnota je také velikost `indicies` pole, protože jeho velikost se rovná počet rozměrů `ICorDebugArrayValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="0df7e-107">This value is also the size of the `indicies` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indicies`  
 <span data-ttu-id="0df7e-108">[out] Pole celých čísel, z nichž každý je základní index (to znamená, počáteční index) dimenzi tohoto objektu `ICorDebugArrayValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="0df7e-108">[out] An array of integers, each of which is the base index (that is, the starting index) of a dimension of this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0df7e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0df7e-109">Requirements</span></span>  
 <span data-ttu-id="0df7e-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0df7e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0df7e-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0df7e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0df7e-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0df7e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0df7e-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0df7e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
