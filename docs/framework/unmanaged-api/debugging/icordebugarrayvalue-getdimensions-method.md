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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a52075f33d594787c516f84b65b3319991380907
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645692"
---
# <a name="icordebugarrayvaluegetdimensions-method"></a><span data-ttu-id="f2f7d-102">ICorDebugArrayValue::GetDimensions – metoda</span><span class="sxs-lookup"><span data-stu-id="f2f7d-102">ICorDebugArrayValue::GetDimensions Method</span></span>
<span data-ttu-id="f2f7d-103">Získá počet elementů v každé dimenzi tohoto pole.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-103">Gets the number of elements in each dimension of this array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2f7d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2f7d-104">Syntax</span></span>  
  
```  
HRESULT GetDimensions (  
    [in] ULONG32         cdim,  
    [out, size_is(cdim), length_is(cdim)]   
        ULONG32          dims[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2f7d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f2f7d-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="f2f7d-106">[in] Počet dimenzí tohoto objektu icordebugarrayvalue –.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-106">[in] The number of dimensions of this ICorDebugArrayValue object.</span></span>  
  
 <span data-ttu-id="f2f7d-107">Tato hodnota je také velikost `dims` pole, protože jeho velikost se rovná počet rozměrů `ICorDebugArrayValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-107">This value is also the size of the `dims` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `dims`  
 <span data-ttu-id="f2f7d-108">[out] Pole celých čísel, z nichž každý určuje počet prvků v dimenzi v tomto `ICorDebugArrayValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="f2f7d-108">[out] An array of integers, each of which specifies the number of elements in a dimension in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2f7d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f2f7d-109">Requirements</span></span>  
 <span data-ttu-id="f2f7d-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2f7d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2f7d-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2f7d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2f7d-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2f7d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2f7d-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2f7d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
