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
ms.openlocfilehash: e103401b85626e53db53e1894c22b161774e5163
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088690"
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a><span data-ttu-id="d1864-102">ICorDebugArrayValue::GetBaseIndicies – metoda</span><span class="sxs-lookup"><span data-stu-id="d1864-102">ICorDebugArrayValue::GetBaseIndicies Method</span></span>
<span data-ttu-id="d1864-103">Získá základní index každé dimenze v poli.</span><span class="sxs-lookup"><span data-stu-id="d1864-103">Gets the base index of each dimension in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1864-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1864-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]   
        ULONG32           indicies[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1864-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1864-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="d1864-106">pro Počet dimenzí tohoto objektu `ICorDebugArrayValue`.</span><span class="sxs-lookup"><span data-stu-id="d1864-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span> <span data-ttu-id="d1864-107">Tato hodnota je také velikost pole `indicies`, protože jeho velikost je rovna počtu rozměrů `ICorDebugArrayValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="d1864-107">This value is also the size of the `indicies` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indicies`  
 <span data-ttu-id="d1864-108">mimo Pole celých čísel, z nichž každý je základní index (tj. počáteční index) dimenze tohoto `ICorDebugArrayValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="d1864-108">[out] An array of integers, each of which is the base index (that is, the starting index) of a dimension of this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1864-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d1864-109">Requirements</span></span>  
 <span data-ttu-id="d1864-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1864-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1864-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d1864-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1864-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d1864-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1864-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1864-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
